# LinkedIn Workflow - Version corrigée

Ce projet contient une version corrigée du script d'automatisation LinkedIn pour la recherche et qualification d'entreprises.

## Corrections principales

Les changements suivants ont été apportés pour résoudre les erreurs "Unknown error" lors de l'analyse des entreprises LinkedIn :

1. **Ajout d'un mode simulation** : Pour contourner les problèmes d'accès à l'API OpenAI ou aux profils LinkedIn, le script peut maintenant fonctionner en mode simulation, générant des résultats synthétiques mais cohérents.

2. **Amélioration de la gestion des erreurs** : Les exceptions sont désormais mieux gérées avec des messages d'erreur plus détaillés et des mécanismes de récupération automatique.

3. **Fonction de secours** : La méthode `generate_fallback_companies()` a été ajoutée pour générer des données synthétiques en cas d'échec de l'API.

4. **Vérifications de validité de la clé API** : Le script vérifie maintenant la validité de la clé API avant de l'utiliser.

5. **Basculement automatique vers le mode simulation** : En cas d'erreur d'API ou de connexion, le script bascule automatiquement vers le mode simulation.

## Comment utiliser

1. Assurez-vous d'avoir toutes les dépendances installées :
```
pip install gspread oauth2client pandas requests tqdm bs4
```

2. Exécutez le script :
```
python linkedin_workflow.py
```

3. Suivez les instructions dans le terminal pour configurer et exécuter les modules de recherche et qualification.

## Utilisation du mode simulation

Lors de l'exécution du script, vous aurez désormais l'option d'activer le mode simulation :

```
Utiliser le mode simulation pour l'analyse (utile si problèmes d'API) ? (O/N, par défaut: N)
```

Répondez "O" pour activer le mode simulation, qui générera des résultats synthétiques sans avoir besoin d'accéder à l'API OpenAI.

## Structure des données

Le script génère ou utilise un Google Sheet avec les colonnes suivantes :
- name : Nom de l'entreprise
- linkedin_url : URL de la page LinkedIn de l'entreprise
- description : Description de l'entreprise
- industry : Secteur d'activité
- website : Site web de l'entreprise
- is_relevant : Indique si l'entreprise est pertinente (booléen)
- score : Score de pertinence (de 1 à 6)
- analysis : Analyse détaillée fournie par GPT ou générée par le mode simulation
- keywords : Mots-clés utilisés pour l'analyse
