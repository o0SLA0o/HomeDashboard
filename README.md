# Ma Maison — dashboard Home Assistant

Tableau de bord web en un seul fichier (`maison.html`), sans dépendance, qui pilote Home Assistant via son API WebSocket.

## Fonctionnalités

- **Plan interactif multi-niveaux** : plan stylisé généré depuis les pièces HA, étages HA + niveaux personnalisés (ex. dépendance), halos de la vraie couleur des lumières, sol teinté selon la température, alertes d'ouverture, ondes de présence, pochette et titre défilant des médias.
- **Panneaux latéraux** : occupation (personnes), scénarios rapides, état de la maison (alarme, portail, garage, ouvertures, serrures), température moyenne avec historique 24 h, consommation électrique, raccourcis lumières / volets / chauffage.
- **Vues Pièces et Types**, regroupement par appareil, sections repliables.
- **Caméras** : aperçus rafraîchis et flux en direct en plein écran.
- **Mode édition** : masquer entités / appareils / personnes, déplacer et redimensionner les pièces, placer les icônes, image de fond par niveau.

## Installation

1. Copier `maison.html` dans le dossier `/config/www/` de Home Assistant (redémarrer HA si le dossier `www` vient d'être créé).
2. Ouvrir `http://<adresse-ha>:8123/local/maison.html`.
3. Se connecter avec un jeton d'accès longue durée (profil HA → Sécurité → Jetons d'accès longue durée).

Les réglages d'affichage (masquage, plan, niveaux) sont mémorisés dans le navigateur de chaque appareil.
