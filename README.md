📊 Superstore Sales Dashboard — Projet BI (Semaines 2 & 3)
Projet réalisé dans le cadre du Data Analytics Internship Programme — AnalystLab Africa.
Mission : transformer les ventes 2014-2017 d'un distributeur américain (dataset Superstore) en
tableaux de bord exécutifs interactifs et en recommandations actionnables.

Dashboard Semaine 3 

Page 1: Vue d'ensemble

<img width="1236" height="746" alt="Capture d&#39;écran 2026-08-23 221419" src="https://github.com/user-attachments/assets/1732fe84-56eb-476e-be0b-2a2eb59eb7cf" />

Page 2: Tendances Temporelles

<img width="701" height="419" alt="image" src="https://github.com/user-attachments/assets/f06bdede-5bf3-4c5c-b6aa-a42ecea45ade" />

Page 3: Produits et Rentabilité

<img width="1359" height="834" alt="Capture d&#39;écran 2026-08-23 223908" src="https://github.com/user-attachments/assets/77e9dee8-50af-4d0b-b028-451ee4ad4748" />

Page 4:Clients et régions

<img width="663" height="413" alt="image" src="https://github.com/user-attachments/assets/eeb51e7c-68c6-42f6-a529-34789c995caf" />





🎯 Contexte & problème business
L'entreprise ne disposait d'aucune vue consolidée de sa performance. Objectifs :

Semaine 2 : dashboard exécutif initial — performance globale, régions, catégories, segments,
produits ; 5 KPI, 8 visuels, 4 slicers.
Semaine 3 : approfondissement — analyse temporelle, rentabilité par produit, impact des
remises, performance clients/régions ; dashboard 4 pages, 12 mesures DAX, modélisation
avec table de dates.
📁 Jeu de données
Superstore Sales Dataset (Kaggle)
— commandes 2014-2017 : dates, régions, États, segments, catégories/sous-catégories, produits,
ventes, profits, remises.

🛠️ Outils
Microsoft Power BI Desktop · Power Query · DAX · GitHub · Google Drive

🧹 Préparation & modélisation des données
Power Query : doublons supprimés, TotalCharges-type corrigé (N/A : champ Discount numérique),
types corrigés (Sales/Profit décimal, Order Date date), devise USD.
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

📊 Le dashboard — 4 pages interactives
Page	Contenu
1. Vue d'ensemble	5 KPI (Sales $2,30M, Profit $286,4K, Orders 5K, Avg Sales $229,86, Marge 12 %) · carte des États · catégories · segments · top produits · matrice conditionnelle
2. Tendances temporelles	Growth YoY, profit/commande, produits en perte · saisonnalité par année · croissance annuelle · trimestres · top 5 mois · profit mensuel
3. Produits & rentabilité	Nuage ventes/profit · matrice rentabilité+remises (rouge si perte) · sous-catégories en perte · marge par tranche de remise (30 % → -123 %) · produits en perte par catégorie
4. Clients & régions	Top 10 clients · profit par État (zones rouges) · profit par segment · ventes/profit par région · remise moyenne par région
Interactivité : 5 slicers synchronisés sur les 4 pages (Année, Region, Category, Segment,
Sub-Category) ; mises en forme conditionnelles ; titres métiers ; palette cohérente
(#1F4E79 / #2E9E97 / rouge alerte).

🔍 Principaux enseignements (Semaine 3)
Croissance 2014→2017 (+50 %) et saisonnalité Q4 (novembre-décembre meilleurs mois) ;
Remises : 30 % de marge sans remise → -15 % dès 21-40 % → -123 % au-delà de 60 % ;
299 produits en perte, concentrés Furniture/Office Supplies (Tables : -17,7 K$) ;
West domine (~0,72 M$), South ferme la marche ; Central = région la plus remisée ;
Consumer = 46,8 % du profit ; Home Office (21 %) = relais de croissance.
✅ Recommandations
Plafonner les remises (> 20 % soumise à validation) ; 2. Assainir le catalogue Furniture ;
Plan de rattrapage pour la région Sud ; 4. Développer & fidéliser Home Office ;
Revue mensuelle de la performance via ce dashboard.
Détail : 
Week3_Business_Insights_Report.docx
.
📂 Structure du repository
text

├── README.md
├── Superstore_Dashboard.pbix              ← dashboard 4 pages (Semaines 2+3)
├── Dashboard_Export.pdf                   ← export PDF du dashboard
├── Week2_Rapport_BI_Overview.docx         ← Semaine 2, Partie 1
├── Week2_Executive_Summary_Insights.docx  ← Semaine 2, Parties 4-5
├── Week3_Business_Insights_Report.docx    ← Semaine 3 : continuité, problèmes, insights, reco
├── Week3_DAX_Documentation.docx           ← Semaine 3 : modèle + mesures DAX
└── assets/                                ← captures des 4 pages du dashboard
🚀 Utilisation
Installer Power BI Desktop ;
Ouvrir Superstore_Dashboard.pbix ;
Naviguer entre les 4 pages et filtrer via les 5 slicers synchronisés.

👤 Auteur

SOME Oho Prisca Gaelle — Data Analytics Intern @ AnalystLab Africa
LinkedIn : www.linkedin.com/in/oho-prisca-gaëlle-some-01391a303 

X : @PriscaSomd3ho

#AnalystLabAfrica — merci à AnalystLab Africa pour l'encadrement. 🙌
