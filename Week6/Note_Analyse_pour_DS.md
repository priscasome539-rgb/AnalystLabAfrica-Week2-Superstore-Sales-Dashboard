# Note d'analyse — Data Analytics → Data Science (Semaine 6)

**Auteure :** SOME Oho Prisca Gaëlle (Data Analytics) · **Destinataire :** Alia Al-Qadri (Data Science)
**Fichier joint :** `HealthConnect_features_for_DS.csv` (5 000 lignes, une par rendez-vous)

## 1. Cible recommandée

- `no_show` (1 = No-Show, 0 = Attended) pour la modélisation binaire ;
- **Exclure Cancelled (263 lignes)** du training binaire ; `appointment_outcome` est conservé
  dans le fichier pour te permettre de les identifier et de faire tes propres arbitrages.

## 2. Classement des features (preuves Semaine 6)

| Rang | Feature | Effet observé (écart de taux de no-show) |
|---|---|---|
| 1 | `booking_lead_days` (+ `long_lead`) | 27,8 % (≤7 j) → 60,5 % (>30 j) ≈ **33 pts** |
| 2 | `previous_no_shows` (+ `recidiviste`, `ratio_no_shows_passes`) | 43,5 % → 55,4 % ≈ 12 pts ; **47,5 % des no-shows** viennent de récidivistes |
| 3 | `reminder_sent` | -2,8 à -4,3 pts selon la tranche de délai ; **insuffisant >30 j** (59,3 % même rappelés) → tester une interaction lead×reminder |
| 4 | `distance_to_clinic_km` | 46,5 % → 54,1 % ≈ 8 pts ; **robuste** au test de sensibilité (sans imputation) |
| 5 | `appointment_type` | Follow-up 51,2 % vs General 46,6 % (~5 pts) |
| 6 | `age_group` | 45,1 % (65+) → 50,7 % (25-34, 55-64) (~5 pts) |
| 7 | `gender` | ~0 pt → **excluable** sans perte |

## 3. Features dérivées fournies (documentation de calcul)

| Feature | Calcul | Justification |
|---|---|---|
| `no_show` | outcome == « No-Show » → 1 | cible binaire |
| `recidiviste` | previous_no_shows > 0 → 1 | signal n°2 du classement |
| `long_lead` | booking_lead_days > 30 → 1 | seuil où le taux bascule (60,5 %) |
| `lead_band` | tranches ≤7 j / 8-30 j / >30 j | lecture non linéaire du délai |
| `dist_band` | tranches <5 / 5-15 / >15 km (sur distance imputée) | lecture par paliers |
| `ratio_no_shows_passes` | previous_no_shows ÷ previous_appointments (0 si dénominateur 0) | intensité de la récidive, indépendante du volume |
| `distance_manquante` | 1 si distance manquante dans l'original (90 lignes) | transparence sur l'imputation médiane |

## 4. Pièges à éviter (fuite & qualité)

- **Fuite** : aucune feature ne doit dériver de `appointment_outcome` ; `waiting_time_minutes`
  (60 manquants) pose question sur sa disponibilité au moment de la prédiction → **teste avec/sans**.
- **Imputation** : distance imputée par la médiane sur 90 lignes → le flag `distance_manquante`
  te permet de tester avec/sans aussi.
- **Sunday** : 737 RDV avec le taux le plus élevé (50,5 %), mais la Knowledge Base annonce la
  clinique **fermée le dimanche** → incohérence données/documentation ; je recommande un test de
  robustesse du modèle **avec vs sans les Sundays**.

## 5. Suggestions de validation Semaine 7

- Stabilité des métriques (accuracy, recall no-show, ROC-AUC) avec/sans Sundays ;
- Importance des features comparée au classement ci-dessus ;
- Calibration du rappel sur la tranche >30 j (le modèle y est-il sensible ?).

Bonne modélisation ! 🤝
