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
| `index.html` | La page complète (HTML + CSS + JS) |
| `camera_commande_vocale.mp4` | Flux 01 - 1280x720, 3 min 27 s |
| `reponse_robot_execution.mp4` | Flux 02 - 1746x392, 3 min 03 s |

Vidéos ré-encodées en H.264/AAC avec l'index (`moov`) placé en tête de fichier,
pour un démarrage immédiat en lecture progressive.
