# Ma Maison — dashboard Home Assistant

Tableau de bord web en un seul fichier (`maison.html`), sans dépendance, qui pilote Home Assistant via son API WebSocket.

## Fonctionnalités

- **Plan interactif multi-niveaux** : plan stylisé généré depuis les pièces HA, étages HA + niveaux personnalisés (ex. dépendance), halos de la vraie couleur des lumières, sol teinté selon la température, alertes d'ouverture, ondes de présence, pochette et titre défilant des médias.
- **Panneaux latéraux flottants** (repliés par défaut, repli automatique après 30 s) : occupation (personnes), scénarios rapides, état de la maison (alarme, portail, garage, ouvertures, serrures), température moyenne avec historique 24 h, consommation électrique, raccourcis lumières / volets / chauffage.
- **Vues Pièces et Types**, regroupement par appareil, sections repliables.
- **Mode jour / mode nuit** : bouton ☀️/🌙 dans la barre du haut ; thème clair le jour, thème bleu nuit la nuit, et une image de fond distincte par mode et par niveau (stockée dans IndexedDB).
- **Caméras** : aperçus rafraîchis et flux en direct en plein écran.
- **Mode édition** : masquer entités / appareils / personnes, déplacer et redimensionner les pièces, image de fond par niveau.
- **Appareils du plan au choix** : les pièces sont vides par défaut ; le bouton « + » d'une pièce (mode édition) ouvre la liste à cocher de ses entités Home Assistant, et « × » retire un appareil du plan.

## Installation

1. Copier `maison.html` dans le dossier `/config/www/` de Home Assistant (redémarrer HA si le dossier `www` vient d'être créé).
2. Ouvrir `http://<adresse-ha>:8123/local/maison.html`.
3. Cliquer sur **Se connecter avec Home Assistant** : connexion OAuth via la page de connexion habituelle de HA (identifiant, mot de passe, double authentification). Le jeton d'accès (30 min) est renouvelé automatiquement ; chaque appareil apparaît dans le profil HA sous « Jetons d'actualisation » et peut y être révoqué.
   - Alternative pour un écran en mode kiosque : « Utiliser plutôt un jeton d'accès longue durée » (profil HA → Sécurité → Jetons d'accès longue durée).
   - Si la page n'est pas servie par Home Assistant, autoriser son origine dans `configuration.yaml` (`http: cors_allowed_origins:`).

Les réglages d'affichage (masquage, plan, niveaux) sont mémorisés dans le navigateur de chaque appareil.
