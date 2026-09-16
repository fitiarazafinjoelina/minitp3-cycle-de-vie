# Mini-TP 3 — Prédictions et observations

**Étudiant :** ETU002630 — Razafinjoelina Fitia Elie Evah

## Étape 1 — Prédictions avant lancement

| Scénario | Séquence exacte prédite | Réponse à la question « + » |
|---|---|---|
| A — Rotation de l’écran | `onPause → onStop → onDestroy → onCreate → onStart → onResume` | L’ancienne Activity est détruite et une nouvelle instance est créée : un compteur stocké uniquement dans l’Activity revient à sa valeur initiale. |
| B — Accueil, puis retour | `onPause → onStop → onRestart → onStart → onResume` | Contrairement à la rotation, l’Activity n’est normalement pas détruite ni recréée : la même instance revient au premier plan et son compteur est conservé. |

## Étape 2 — Observations au Logcat

| Scénario | Séquence observée | Écart avec la prédiction et explication |
|---|---|---|
| Rotation de l’écran | `onPause → onStop → onDestroy → onCreate → onStart → onResume` | Aucun écart. L’instance `63123861` a été détruite et remplacée par l’instance `240961446`, ce qui confirme la recréation de l’Activity. |
| Accueil, puis retour | `onPause → onStop → onRestart → onStart → onResume` | Aucun écart. Il n’y a ni `onDestroy` ni `onCreate` : la même instance reprend au premier plan. |

## Question d’observation

Le changement du numéro d’instance à la rotation prouve que l’ancienne Activity a été détruite et qu’une nouvelle a été créée ; un compteur conservé seulement dans l’Activity serait donc réinitialisé.

## Bonus — Ouverture du second écran

Séquence observée : `MainActivity.onPause`, puis `SecondActivity.onCreate → onStart → onResume`, puis `MainActivity.onStop`. L’écran principal se met donc en pause avant la création du second écran.
