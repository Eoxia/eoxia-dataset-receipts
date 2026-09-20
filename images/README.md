# Dataset de Tickets de Caisse (Notes de Frais)

Ce dossier contient les images de tickets de caisse ainsi que leurs métadonnées extraites au format JSON.

## Format des fichiers

Pour chaque fichier image (ex: `1001_receipt.jpg`), il existe un fichier JSON associé (ex: `1001_receipt.json`) contenant les données structurées.

### Schéma JSON

```json
{
  "file_name": "Nom du fichier image",
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
