# MCP for RMS v2

## 📌 Aperçu
MCP for RMS v2 est une simulation avancée de planification et de pilotage de systèmes de production reconfigurables (RMS). Le script `mcp_rms_enhanced_v5_1_complete.py` implémente plusieurs heuristiques multicritères pour orchestrer machines, configurations et opérations, puis génère automatiquement des visualisations et un rapport de synthèse.

## ✨ Fonctionnalités principales
- **Planification intelligente** : heuristiques MCP améliorées (lookahead, momentum, équilibrage de charge) en plus des règles classiques (EDD, SPT, FIFO, etc.).
- **Simulation réaliste** : génération de jeux de jobs multi-opérations avec analyse des goulots d'étranglement et suivi des états machine/operation.
- **Analyse complète** : indicateurs de performance, historiques de décisions, validations (Gantt, contraintes) et rapport de recherche en Markdown.
- **Visualisations prêtes à l'emploi** : tableaux de bord Plotly interactifs (et export PNG via `kaleido` si disponible).
- **CLI unique** : configuration par arguments (`--num-machines`, `--heuristic`, `--all-heuristics`, etc.) pour lancer des campagnes d'expérimentation reproductibles.

## 🧱 Structure du dépôt
```
.
├── README.md
└── mcp_rms_enhanced_v5_1_complete.py   # Script principal avec l'environnement, le scheduler et la CLI
```

## 🚀 Prise en main
### 1. Prérequis
- Python 3.10+
- Outils scientifiques : `numpy`, `pandas`, `scipy`
- Visualisation : `plotly`
- Export PNG (optionnel) : `kaleido`

Installez les dépendances :
```bash
python -m venv .venv
source .venv/bin/activate  # Windows : .venv\Scripts\activate
pip install numpy pandas scipy plotly kaleido
```
> `kaleido` est facultatif mais recommandé pour exporter automatiquement les graphiques en PNG.

### 2. Lancer une expérience
```bash
python mcp_rms_enhanced_v5_1_complete.py \
  --output-dir runs/mcp_demo \
  --num-machines 6 \
  --num-jobs 25 \
  --heuristic MCP_INTELLIGENT_V2
```
Options utiles :
- `--all-heuristics` : compare toutes les stratégies implémentées.
- `--seed` : fixe la graine aléatoire pour reproductibilité.
- `--debug` : active des logs détaillés dans `experiment.log`.

### 3. Résultats générés
Après exécution, consultez le dossier `runs/<nom>` :
- `experiment.log` : trace complète.
- `detailed_results.json` : métriques agrégées par heuristique.
- `visualizations/` : graphiques Plotly (HTML + PNG si `kaleido`).
- `research_report.md` : rapport de synthèse intégrant performances, validations et recommandations.

## 🧪 Conseils pour l'expérimentation
- Ajustez `--num-machines` et `--num-jobs` pour tester l'évolutivité.
- Explorez les heuristiques spécialisées (`MCP_ENERGY_OPTIMIZED`, `MCP_BOTTLENECK_AWARE`) selon vos objectifs.
- Utilisez l'argument `--all-heuristics` pour comparer les résultats et identifier la meilleure stratégie (`completion_rate`).

## 🤝 Contribution
Les issues et propositions d'amélioration sont les bienvenues. Avant de soumettre une PR :
1. Exécutez le script avec vos nouveaux paramètres pour valider la stabilité.
2. Documentez toute nouvelle option ou heuristique dans ce README.

## 📄 Licence
Aucune licence n'est fournie dans le dépôt d'origine. Ajoutez-en une si nécessaire avant diffusion.
