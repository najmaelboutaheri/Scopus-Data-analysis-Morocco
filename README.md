# Analyse des Données Scopus - Performance Académique des Universités Marocaines

## **Description du Projet**

Ce projet vise à analyser les publications scientifiques des universités marocaines en exploitant les données de la base **Scopus**.  
L'objectif principal est d'évaluer les **performances académiques**, d'identifier les **tendances de recherche**, les **collaborations internationales**, ainsi que les **domaines dominants**.

Cette analyse fournit des **insights stratégiques** pour renforcer l'impact des institutions académiques marocaines et orienter les politiques de recherche.

---

## **Architecture du Projet**

L'architecture du projet suit plusieurs étapes :

1. **Extraction des Données** :
   Collecter les données brutes en exportant les fichiers .csv directement de cite.
2. **Stockage des Données** :
   Stockage initial dans **Snowflake** pour assurer l'accessibilité et la sécurité.
3. **Transformation des Données** :
   Nettoyage, prétraitement et modélisation des données avec **Python**.
4. **Stockage Final** :
   Stockage des tables finales (tables de faits et dimensions) dans **SQL Server**.
5. **Visualisation** :
   Création de tableaux de bord interactifs avec **Power BI**.

### **Schéma de l'Architecture**

 <img width="605" alt="image" src="https://github.com/user-attachments/assets/2e3d0738-42f7-49ab-bd8e-bd0532f54e3c" />
 
---

## **Structure du Projet**
```bash
📁 Projet_Analyse_Scopus
│
├── 📂 DataModeling
│ ├── Modèle_de_données.png # Schéma du modèle de données (étoile)
│
├── 📂 Documents
│ ├── Ensah-BPMN.svg # Diagramme BPMN de processus
│ ├── Etat-D'avancement-Rapport.pdf # Rapport d'état d avancement
│ ├── Presentation-scopus-powerbi.pdf # Présentation Power BI Scopus
│ ├── Presentation_de_la_digitalisation.pdf # Présentation digitalisation
│ ├── Scopus-Dashboard.pbix # Tableau de bord Power BI
│
├── 📂 PreprocessingSteps
│ ├── AffiliationsExctraction.ipynb # Extraction des affiliations
│ ├── Data_Combination.ipynb # Combinaison des tables de données
│ ├── Exctraction_Regions.ipynb # Extraction des régions géographiques
│ ├── ScopusDataUnderstanding.ipynb # Analyse exploratoire des données
│ ├── affiliation_dimension_exctraction.ipynb # Table dimension affiliation
│ ├── author_dimension_exctraction.ipynb # Table dimension auteur
│
├── 📂 Regions_Data
│ ├── country.csv # Liste des pays
│ ├── list-cities-morocco-98j.csv # Liste des villes marocaines
│
├── 📂 Sample-of-data
│ ├── Raw-Data.xlsx # Exemple de données brutes
│
├── README.md # Fichier README (ce fichier)
└── Modèle_de_données.png # Schéma principal
```
---

## **Description des Données**

Le dataset extrait contient :

- **Nombre total d'enregistrements** : 31,006 lignes  
- **Nombre de tables** : 6 tables principales  

### **Contenu des Données :**
**Auteurs** : Informations sur les chercheurs.
**Affiliations** : Institutions liées aux auteurs.
**Pays et Villes** : Distribution géographique des publications.
**Universités** : Distinction entre universités marocaines et étrangères.
**Publications** : Références, citations, domaines de recherche.

---

## **Prétraitement des Données**

 Les étapes de prétraitement incluent :

 ![Capture d'écran 2024-12-18 092301](https://github.com/user-attachments/assets/f62275e5-bbe0-472c-a11e-6cf11f770c9d)

1. **La compréhension des données** :  
   Vérfication des doublons et des valeurs manquantes.
     
 ![Capture d'écran 2024-12-18 095509](https://github.com/user-attachments/assets/1356f7c0-7ca1-482d-9033-096c5e48d002)
 
2. **Exctraction des noms d'auteurs**
   
 ![Capture d'écran 2024-12-17 115754](https://github.com/user-attachments/assets/39709c84-6c94-4e14-ac46-0c5108b842f1)

3. **Exctraction des noms d'universtès marocaines et etrangères avec les données géographiques**

 ![Capture d'écran 2024-12-17 120658](https://github.com/user-attachments/assets/b89d1152-ef74-452e-8160-c523cf7b024e)

4. **Modélisation:**
   
 ![Capture d'écran 2024-12-17 081113](https://github.com/user-attachments/assets/f8eedae2-024a-4f6a-a7da-7e6cf3c3ae7e)

 Nous avons modeliser les données en suivant le modéle shema étoile pour faciliter l'accée par les requètes SQL et garantir une bonne pérformance.
 - **les tables de dimension:**
   
  ![Capture d'écran 2024-12-18 095431](https://github.com/user-attachments/assets/cd055b89-d6ba-4445-807c-6108cbd2245d)

 - **la table de fait**:
   
  ![Capture d'écran 2024-12-18 095602](https://github.com/user-attachments/assets/98123a4c-8eb9-49c9-89fc-846ef33ef15c)

5. **Réduction des données** :  
   - Spécification d'un échantillon représentatif à 10% de chaque intervalle de date pour une distribution équilibrée.
6. **Normalisation dans POWER BI** :  
   - Transformation des dates et formats de texte.  
7. **Crier les mesures et afficher les visualisations** :  
   - Le projet contient 6 pages  chacune orienté vers une dimension ce qui permet de comprendre profondement les patterns dans les données explorées.
     
---

## **Exécution des Scripts**  

1. **La compréhension des données et exctraction de la table Auteur** :  
   - Ouvrir `ScopusDataUnderstanding.ipynb` et exécuter chaque cellule.    
2. **Exctraction des Données** :  
   - Lancer `AffiliationsExctraction.ipynb` pour exctraire les affiliations.  
3. **Combinaison des Données** :  
   - Exécuter `Data_Combination.ipynb`.
4. **Exctraction des données géographiques** :  
   - Exécuter `Exctraction_Regions.ipynb`.
5. **Exctraction de la table de la dimension affiliation** :  
   - Exécuter `affiliation_dimension_exctraction`.
6. **Exctraction de la table de la dimension auteur** :   
   - Exécuter `author_dimension_exctraction.ipynb`. 
7. **Visualisation** :  
   - Importer `Scopus-Dashboard.pbix` dans Power BI pour afficher les résultats.
     
---  

## **Visualisation des Résultats**

Les tableaux de bord **Power BI** présentent :  

- **Statistiques générales** des publications.
  
  <img width="608" alt="image" src="https://github.com/user-attachments/assets/369470fa-18af-45b6-86ee-885a1df57a63" />

- **Analyse géographique** des collaborations internationales.
  
  <img width="601" alt="image" src="https://github.com/user-attachments/assets/66602e8c-5884-4265-b21a-05e83a221015" />

- **Tendances des domaines de recherche** par université.  
- **Comparaison des performances** entre universités marocaines et étrangères.
  
---

## **Contenu des Données**  
- **Raw-Data.xlsx** : Données brutes extraites de Scopus.  
- **Pays et Régions** : `country.csv`, `list-cities-morocco-98j.csv`.  

Les tables incluent :  
- **Auteurs** : Identification et informations.  
- **Affiliations** : Institutions académiques.  
- **Publications** : Références, citations et sujets.
- **Conferences**: date de fin et de debut.
- **WEB**: Les liens sur internet et les idetifiants DOI.
- **Données Géographieque**:cites and countries.

---

## **Outils et Technologies**  
- **Stockage** : Snowflake  
- **Nettoyage & Prétraitement** : Python (Pandas, NumPy)  
- **Environnement** : Google Colab  
- **Modélisation** : Power BI  
- **Visualisation** : Power BI Dashboards  

---

## **Résultats Principaux**  
- **Analyse de 31,006 enregistrements** répartis sur 6 tables principales.  
- **Distribution équilibrée des données** à 10% par intervalle de date pour éviter les biais temporels.  
- **Tableau de bord Power BI** pour une analyse visuelle des collaborations, performances et tendances.  

---

## **Documents Importants**  
- [Diagramme BPMN](Documents/Ensah-BPMN.svg)  
- [Rapport d'État d'Avancement](Documents/Etat-D'avancement-Rapport.pdf)  
- [Présentation Power BI](Documents/Presentation-scopus-powerbi.pdf)  
- [Présentation Digitalisation](Documents/Presentation_de_la_digitalisation.pdf)  

---

## **Contact**  
Pour toute question ou collaboration :  
- **Email** : najmaelboutaheri@gmail.com  
- **LinkedIn** : [Lien vers le profil](https://www.linkedin.com/in/najma-el-boutaheri-8185a1267/)  
---

## **Licence**  
Projet sous licence **MIT**.  
---


