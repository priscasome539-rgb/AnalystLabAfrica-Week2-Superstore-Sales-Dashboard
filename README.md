📊 Data Analytics Internship — AnalystLab Africa
Portfolio de stage : Semaines 2-3 → Superstore Sales Dashboard (Power BI, 4 pages) ·
Semaine 4+ → HealthConnect Experience Lab (track Data Analytics : rendez-vous manqués).

Mission : transformer des données brutes en tableaux de bord exécutifs interactifs et en
recommandations actionnables.

📈 Semaine 6 — HealthConnect : validations & intégration
Ce qui a été fait
Validation des KPI Semaine 5 : rappel (effet présent dans toutes les tranches de délai,
mais insuffisant >30 j : 59,3 % même rappelés) · Sunday validé par l'effectif (n=737 ;
incohérence Sunday/Knowledge Base escaladée) · distance robuste (analyse de sensibilité sans
imputation : 46,5 / 47,3 / 54,1 %) · récidive renforcée (47,5 % des absences).
Analyses nouvelles : interaction rappel × délai · concentration des no-shows chez les
récidivistes · type de RDV (follow-up 51,2 %) · âge / genre (effets modestes ou nuls).
Hiérarchie des effets : délai (~33 pts) ≫ récidive (~12) > distance (~8) >
type ≈ âge ≈ rappel ≈ jour (~4-5) > genre (~0) → leviers prioritaires : délai, récidive, rappel.
KPI raffinés : écart rappel par tranche de délai · part des absences attribuables aux
récidivistes (47,5 %) · règle de méthode n ≥ 100.
Nouvelle page Power BI « Semaine 6 : Validations & Intégrations » : 5 cartes KPI,
effet du rappel par tranche de délai, taux par type de RDV, table jour × taux × volume,
anneau récidivistes.
Intégration cross-track — Data Science (Alia Al-Qadri)
Reçu : exigences de modélisation (1 ligne/RDV, patient_id conservé, appointment_outcome
original avec Cancelled identifiable, colonnes originales, features dérivées documentées, CSV).
Fourni : HealthConnect_features_for_DS.csv (5 000 × 20) + note d'analyse
(classement des features, finding délai, interaction rappel × délai, incohérence Sunday/KB,
pièges de fuite, suggestions de tests Semaine 7).
Preuve : commit Week6/ + capture de l'échange sur le canal du pod.
Fichiers
Week6/HealthConnect_Week6.ipynb · Week6/HealthConnect_features_for_DS.csv
Week6/Note_Analyse_pour_DS.md · Week6/HealthConnect_Dashboard_W6.pbix
Dashboard Semaine 6
Dashboard Semaine 6 — Validations & Intégrations

📊 Semaine 5 — HealthConnect : KPI, visualisations & dashboard
Ce qui a été fait
Préparation : conversion des dates, imputation médiane de la distance (documentée),
manquants d'attente conservés, création de no_show, lead_band, dist_band,
recidiviste ; sauvegarde HealthConnect_processed.csv (original intact).
EDA : 6 visualisations interprétées (issues, rappel, antécédents, délai, distance, jour).
KPI calculés : taux global 48,5 % · sans rappel 51,4 % vs avec 47,4 % ·
délai 27,8 % / 40,2 % / 60,5 % · distance 46,5 % / 47,5 % / 54,1 % ·
récidivistes 55,4 % vs 43,5 % · pire créneau vendredi soir 58,5 %, dimanche pire journée.
Dashboard Power BI interactif : 5 cartes KPI, 5 visuels, 3 slicers déroulants,
couleurs conditionnelles vert→rouge, étiquettes de données.
5 insights + 5 recommandations, limites mises à jour, collaborations cross-track
(Data Science : cible & features ; Generative AI : incohérence dimanche/KB).
Recommandations clés
Rappel systématique + rappel à mi-chemin pour les réservations > 30 j ;
Double confirmation des RDV du dimanche et du vendredi soir ;
Suivi prioritaire des récidivistes (confirmation téléphonique) ;
Accompagnement renforcé des patients > 15 km ;
Gouvernance des données (documenter l'incohérence dimanche/KB et les manquants).
Fichiers
Week5/HealthConnect_Week5.ipynb · Week5/HealthConnect_processed.csv
Week5/HealthConnect_Dashboard.pbix + capture du dashboard
Week5/Week5_Project_Summary.pdf · Initial_HealthConnect_Analytics_Report.pdf
Dashboard Semaine 5
<img width="567" height="331" alt="image" src="https://github.com/user-attachments/assets/8459352c-0b9f-4b30-978a-55d35dd7abfd" />
🏥 Semaine 4 — HealthConnect Clinic (kickoff)
Contexte & problème
HealthConnect Clinic (fictive) subit un taux élevé de rendez-vous manqués (no-shows) :
créneaux perdus, argent gaspillé, efficacité opérationnelle dégradée. Ma mission
(track Data Analytics) : explorer les données de rendez-vous, identifier les facteurs associés
au no-show et poser les bases d'une analyse quantitative exploitable par la direction.

Ressources
HealthConnect_Appointment_Data.csv — 5 000 rendez-vous × 18 variables ;
Data Dictionary (définitions, règles de cohérence) ;
Knowledge Base (contexte clinique).
Analyse initiale (notebook Jupyter)
Dataset overview : 1 ligne = 1 rendez-vous ; variable cible = appointment_outcome
(Attended / No-Show / Cancelled).
Data quality : 0 doublon ; 3 colonnes à manquants (reminder_channel = manquant logique,
distance_to_clinic_km et waiting_time_minutes = vrais manquants documentés) ;
dates en texte (mm/jj/aaaa) à convertir ; règle de cohérence historique vérifiée.
Variables clés : previous_no_shows (signal le plus fort), reminder_sent,
booking_lead_days, appointment_day (dimanche), appointment_time (soir),
distance_to_clinic_km — waiting_time_minutes testée puis écartée.
6 business questions et 5 KPI proposés : écart de no-show avec/sans rappel ·
taux par créneau (jour × horaire) · par tranche de distance · par tranche de délai ·
récidivistes vs jamais manqué.
Approche : conversion/nettoyage → calcul des KPI → visualisations → recommandations.
Observations clés
Taux de no-show retenu : 48,5 % des rendez-vous réservés ;
Récidive : de 43,5 % de no-show (sans antécédent) à 100 % (5 antécédents) ;
Sans rappel : 51,4 % de no-show vs 47,4 % avec rappel ;
No-shows réservés ~34,5 j à l'avance vs ~24,5 j pour les présents.
Considérations & focus Semaine 5
Données fictives · manquants documentés · Cancelled ≠ No-Show (traité à part) ·
corrélation ≠ causalité · périmètre adultes.

🛒 Semaines 2 & 3 — Superstore Sales Dashboard
Projet réalisé dans le cadre du Data Analytics Internship Programme — AnalystLab Africa.
Mission : transformer les ventes 2014-2017 d'un distributeur américain (dataset Superstore) en
tableaux de bord exécutifs interactifs et en recommandations actionnables.

Page 1 : Vue d'ensemble
<img width="1236" height="746" alt="Capture d&#39;écran 2026-08-23 221419" src="https://github.com/user-attachments/assets/1732fe84-56eb-476e-be0b-2a2eb59eb7cf" />
Page 2 : Tendances Temporelles
<img width="701" height="419" alt="image" src="https://github.com/user-attachments/assets/f06bdede-5bf3-4c5c-b6aa-a42ecea45ade" />
Page 3 : Produits et Rentabilité
<img width="1359" height="834" alt="Capture d&#39;écran 2026-08-23 223908" src="https://github.com/user-attachments/assets/77e9dee8-50af-4d0b-b028-451ee4ad4748" />
Page 4 : Clients et régions
<img width="663" height="413" alt="image" src="https://github.com/user-attachments/assets/eeb51e7c-68c6-42f6-a529-34789c995caf" />
🎯 Contexte & problème business
L'entreprise ne disposait d'aucune vue consolidée de sa performance. Objectifs :

Semaine 2 : dashboard exécutif initial — performance globale, régions, catégories,
segments, produits ; 5 KPI, 8 visuels, 4 slicers.
Semaine 3 : approfondissement — analyse temporelle, rentabilité par produit, impact des
remises, performance clients/régions ; dashboard 4 pages, 12 mesures DAX, modélisation
avec table de dates.
📁 Jeu de données
Superstore Sales Dataset (Kaggle)
— commandes 2014-2017 : dates, régions, États, segments, catégories/sous-catégories, produits,
ventes, profits, remises.

🛠️ Outils
Microsoft Power BI Desktop · Power Query · DAX · Python (pandas, Jupyter) · GitHub · Google Drive

🧹 Préparation & modélisation des données
Power Query : doublons supprimés, types corrigés (Sales/Profit décimal, Order Date date),
devise USD.
Table de dates Date créée en DAX (CALENDAR), marquée table de dates, relation
1→plusieurs active à sens unique vers Order Date (attributs Année/Mois/Trimestre/Mois Année).
Colonne calculée Discount Bucket (tranches de remise) pour l'analyse d'impact des remises.
🧮 Mesures DAX (12, table dédiée _Mesures)
Total Sales · Total Profit · Total Orders · Average Sales · Profit Margin ·
Average Sales per Order · Average Profit per Order · Average Discount ·
Sales Previous Year (SAMEPERIODLASTYEAR) · Sales Growth YoY · Loss-Making Products ·
Etat en perte (indicateur binaire de la carte rouge/vert, page 4).
Formules et explications détaillées : 
Week3_DAX_Documentation.docx
.

🔍 Principaux enseignements (Semaine 3)
Croissance 2014→2017 (+50 %) et saisonnalité Q4 (novembre-décembre meilleurs mois) ;
Remises : 30 % de marge sans remise → -15 % dès 21-40 % → -123 % au-delà de 60 % ;
299 produits en perte, concentrés Furniture/Office Supplies (Tables : -17,7 K$) ;
West domine (~0,72 M$), South ferme la marche ; Central = région la plus remisée ;
Consumer = 46,8 % du profit ; Home Office (21 %) = relais de croissance.
✅ Recommandations
Plafonner les remises (> 20 % soumise à validation) ;
Assainir le catalogue Furniture ;
Plan de rattrapage pour la région Sud ;
Développer & fidéliser Home Office ;
Revue mensuelle de la performance via ce dashboard.
Détail : 
Week3_Business_Insights_Report.docx
.

📂 Structure du repository
text

├── README.md
├── Week6/
│   ├── HealthConnect_Week6.ipynb          ← validations, KPI raffinés, intégration DS
│   ├── HealthConnect_features_for_DS.csv  ← features pour le track Data Science
│   ├── Note_Analyse_pour_DS.md            ← note d'analyse pour Alia
│   └── HealthConnect_Dashboard_W6.pbix    ← dashboard + page Validations
├── Week5/
│   ├── HealthConnect_Week5.ipynb          ← préparation, EDA, KPI, insights
│   ├── HealthConnect_processed.csv        ← données nettoyées (original intact)
│   ├── HealthConnect_Dashboard.pbix       ← dashboard Power BI interactif
│   └── Week5_Project_Summary.pdf
├── Week4/
│   ├── HealthConnect_Week4.ipynb          ← analyse initiale (aperçu, qualité, Q, KPI)
│   └── Week4_Project_Summary.pdf
├── Superstore_Dashboard.pbix              ← dashboard 4 pages (Semaines 2+3)
├── Dashboard_Export.pdf                   ← export PDF du dashboard
├── Week2_Rapport_BI_Overview.docx         ← Semaine 2, Partie 1
├── Week2_Executive_Summary_Insights.docx  ← Semaine 2, Parties 4-5
├── Week3_Business_Insights_Report.docx    ← Semaine 3 : continuité, problèmes, insights, reco
├── Week3_DAX_Documentation.docx           ← Semaine 3 : modèle + mesures DAX
└── assets/                                ← captures des dashboards
🚀 Utilisation
Installer Power BI Desktop ; ouvrir
Superstore_Dashboard.pbix, Week5/HealthConnect_Dashboard.pbix ou
Week6/HealthConnect_Dashboard_W6.pbix ; naviguer et filtrer.
Notebooks : ouvrir dans Jupyter ; Kernel → Restart & Run All.
👤 Auteure
SOME Oho Prisca Gaelle — Data Analytics Intern @ AnalystLab Africa
X : @PriscaSomd3ho ·
LinkedIn : oho-prisca-gaëlle-some

#AnalystLabAfrica — merci à AnalystLab Africa pour l'encadrement. 🙌


