# Interaction par reconnaissance vocale avec un robot industriel

Page de démonstration : deux flux vidéo lus côte à côte et verrouillés l'un sur l'autre.

- **01 — Caméra** : l'opérateur donne la commande vocale.
- **02 — Réponse** : exécution de la commande par le robot KUKA.

Le flux 02 démarre avec un décalage réglable (3 s par défaut) sur le flux 01,
et ce décalage est tenu en permanence : pause, déplacement dans la timeline,
ou ralentissement du réseau. Si un flux manque de données, l'autre l'attend
puis les deux repartent réalignés.

Chaque panneau accepte aussi le chargement d'un fichier vidéo local,
par clic ou par glisser-déposer.

Page autonome : un seul fichier HTML, sans dépendance ni librairie externe.

## Contenu

| Fichier | Description |
|---|---|
| `index.html` | La page de démonstration (HTML + CSS + JS) |
| `camera_commande_vocale.mp4` | Flux 01 - 1280x720, 3 min 27 s |
| `reponse_robot_execution.mp4` | Flux 02 - 1746x392, 3 min 03 s |
| `rapport/index.html` | Le dossier technique du modèle de reconnaissance |

Vidéos ré-encodées en H.264/AAC avec l'index (`moov`) placé en tête de fichier,
pour un démarrage immédiat en lecture progressive.

## Dossier technique — le modèle derrière la reconnaissance

**[Lire le dossier](https://mxhaned.github.io/Demo-interaction-vocale-kuka/rapport/)**

La commande vocale de la démonstration s'appuie sur `models_best`, un
pré-entraînement auto-supervisé *noise-to-noise* avec distillation
multi-professeurs : un réseau étudiant de 37,7 M de paramètres apprend une
représentation de la parole robuste au bruit **sans jamais voir le signal
propre**, puis sert d'encodeur à un reconnaisseur de commandes à vocabulaire
fermé.

Le dossier expose en 17 sections la méthode, l'architecture, chaque paramètre
et son effet mesuré, les grilles de performance par niveau de bruit, le système
de reconnaissance embarqué — et les limites du travail, déclarées.

| Résultat | Valeur |
|---|---|
| Sensibilité au bruit | **1,78 × moindre** que le modèle dont l'étudiant part |
| Commandes reconnues (propre à −5 dB) | **80,8 %** contre 64,6 %, **0 %** de fausse acceptation |
| WER de la chaîne du robot | **0,251 → 0,186** |
| Coût d'inférence | RTF **0,012** sur CPU, 151 Mo |

Page autonome elle aussi : un seul fichier HTML, graphiques tracés en SVG sans
librairie. Elle suit le thème du système et propose une bascule clair / sombre.
