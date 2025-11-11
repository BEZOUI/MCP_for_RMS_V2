# MCP for RMS v5.1

## Présentation
Ce dépôt contient une version améliorée du simulateur **MCP-RMS Enhanced v5.1**. L'objectif est d'explorer et de comparer différentes heuristiques de planification pour un système de production reconfigurable (RMS). Le script principal `mcp_rms_enhanced_v5_1_complete.py` génère un environnement de simulation réaliste, exécute les heuristiques disponibles et produit automatiquement des tableaux de bord, des graphiques interactifs et un rapport de synthèse.

## Fonctionnalités clés
- Génération d'ateliers RMS avec machines, configurations et opérations réalistes.
- Implémentation de plusieurs heuristiques MCP, dont `MCP_INTELLIGENT_V2` et les variantes historiques.
- Analyse des goulets d'étranglement, adaptation dynamique des priorités et allocation des ressources.
- Visualisations Plotly de qualité publication (Gantt, heatmaps, convergence, etc.).
- Rapport d'expérimentation complet (Markdown) et export des résultats en JSON.

## Structure du dépôt
```
.
├── README.md
└── mcp_rms_enhanced_v5_1_complete.py  # Script unique regroupant l'ensemble de la logique
```

## Prérequis
Python 3.9+ est recommandé. Les dépendances principales sont :

- numpy
- pandas
- scipy
- plotly
- kaleido *(optionnel, requis uniquement pour l'export PNG des figures)*

Installez-les via pip :
```bash
pip install -r requirements.txt
```
> Si aucun fichier `requirements.txt` n'est fourni, vous pouvez installer les paquets manuellement :
> ```bash
> pip install numpy pandas scipy plotly kaleido
> ```

## Utilisation
L'entrée du programme est le script Python principal. Exemple minimal :

```bash
python mcp_rms_enhanced_v5_1_complete.py
```

Les principaux arguments disponibles :

| Option | Description | Valeur par défaut |
| ------ | ----------- | ----------------- |
| `--output-dir` | Dossier de sortie pour les logs, graphiques et rapports | `runs/mcp_enhanced_v5_1` |
| `--num-machines` | Nombre de machines simulées | `6` |
| `--num-jobs` | Nombre de jobs générés | `25` |
| `--heuristic` | Heuristique à évaluer (`MCP_INTELLIGENT_V2`, `MCP_ADAPTIVE_V2`, `EDD`, `SPT`, etc.) | `MCP_INTELLIGENT_V2` |
| `--all-heuristics` | Active l'évaluation successive de toutes les heuristiques | *(désactivé)* |
| `--seed` | Graine aléatoire pour la reproductibilité | `42` |
| `--debug` | Active les logs détaillés | *(désactivé)* |

### Exemple complet
```bash
python mcp_rms_enhanced_v5_1_complete.py \
    --output-dir runs/mcp_demo \
    --num-machines 8 \
    --num-jobs 40 \
    --all-heuristics
```

## Résultats générés
Après exécution, le dossier `--output-dir` contient notamment :

- `experiment.log` : journal d'exécution détaillé.
- `detailed_results.json` : synthèse chiffrée par heuristique.
- `visualizations/` : graphiques Plotly interactifs (et PNG si `kaleido` est disponible).
- `research_report.md` : rapport de validation et d'analyse des performances.

## Contribution
Les contributions sont les bienvenues ! Merci de :
1. Créer une branche dédiée (`git checkout -b feat/ma-fonctionnalite`).
2. Ajouter des tests ou jeux de données de démonstration si nécessaire.
3. Soumettre une Pull Request décrivant clairement la modification.

## Licence
Aucune licence explicite n'est fournie dans ce dépôt. Vérifiez auprès de l'auteur avant toute utilisation commerciale.
