Cette compétition demande de modéliser des flux de données financières complexes. (Les défis de cette compétition sont : la présence de séries temporelles non stationnaires, des données anonymisées et des restrictions d’API)


- Le problème implique des flux de données dynamiques, difficiles à prévoir avec précision.
- L'objectif est d'améliorer un score de validation (`Q`), estimé autour de 0,007. Un modèle dépassant ce seuil sur le long terme sera remarqué.
- Il est imposé des restrictions sur l’utilisation des API, compliquant l’intégration et les tests.


Le fichier `train.parquet` contient des données historiques et des métadonnées, structurées en plusieurs parties :

  - `date_id` et `time_id` : Identifient l’ordre des données. Pas de garantie sur la correspondance avec le temps réel.
  - `symbol_id` : Identifie les actifs financiers.
  - `weight` : Sert de coefficient pour les fonctions de score.
  - `feature_[00...78]` : Caractéristiques anonymisées.
  - `responder_[0...8]` : Valeurs entre -5 et 5. `responder_6` est la cible principale.

  Les Particularités:
  - Les valeurs extrêmes et les ajouts fréquents de nouvelles données rendent les prédictions instables.
  - Les tests nécessitent une soumission complète, même pour des vérifications simples.

    En résumé, les données comprennent des valeurs extrêmes, et les données suivent une structure linéaire. Cependant, l'ajout progressif de nouvelles données entraîne une volatilité importante des prédictions.
    De plus, la méthode API utilisée impose de soumettre une version de test complète à chaque fois ! 
    Cela signifie que je dois préparer une version fictive pour m'assurer que la soumission fonctionne (même lorsque je souhaite uniquement tester ou debug).
    En réalité, ce processus est plutôt complexe à manipuler.
