# Eoxia Dataset Receipts (Notes de Frais)

Ce dépôt contient un jeu de données annoté pour l'entraînement et le test d'outils d'extraction d'informations (OCR + IA) sur des tickets de caisse et notes de frais.

## Structure du dépôt

L'organisation du jeu de données est la suivante :

- **`images/`** : Contient les photos brutes des tickets de caisse au format JPG, renommées séquentiellement (`1001_receipt.jpg`, `1002_receipt.jpg`, etc.).
- **`entities/`** : Contient les métadonnées extraites (vérité terrain) au format JSON. Pour chaque image, il existe un fichier correspondant (ex: `1001_receipt.json`).
- **`homography.csv`** : Fichier optionnel contenant des matrices d'homographie (si disponibles) pour le redressement des images.

## Format des métadonnées (JSON)

Chaque fichier JSON dans le dossier `entities/` respecte le schéma suivant :

```json
{
  "file_name": "Nom du fichier image (ex: 1001_receipt.jpg)",
  "document_type": "receipt",
  "merchant": {
    "name": "Nom du commerçant",
    "address": "Adresse complète (si disponible)",
    "siret_tva": "SIRET ou Numéro de TVA (si disponible)"
  },
  "date": "Date au format YYYY-MM-DD",
  "time": "Heure au format HH:MM (si disponible)",
  "amounts": {
    "total_ttc": "Montant total TTC (nombre flottant)",
    "total_ht": "Montant total HT (nombre flottant)",
    "taxes": [
      {
        "rate": "Taux de TVA (ex: 20.0)",
        "amount": "Montant de la TVA (nombre flottant)"
      }
    ],
    "currency": "Devise (ex: EUR)"
  },
  "category": "Catégorie de la dépense (restaurant, transport, fuel, hotel, supplies, other)",
  "confidence": "Niveau de confiance de l'extraction (high, medium, low)"
}
```