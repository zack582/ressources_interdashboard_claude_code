# Générateur de Dashboards avec Claude Code

Générez des dashboards HTML autonomes et soignés en quelques secondes grâce à Claude Code et un ensemble de compétences réutilisables.

## Ce que ça fait

Décrivez le dashboard souhaité → Claude lit les skills de design → génère un fichier `.html` unique contenant :
- Une rangée de cartes KPI (4 métriques, responsive)
- Au moins 2 graphiques interactifs (Chart.js)
- Un tableau de données avec recherche et pagination
- Une navigation latérale (sidebar)
- Un bouton bascule mode sombre / clair
- Des micro-animations et une typographie distinctive

Aucune étape de build. Aucun framework. Ouvrez le `.html` directement dans votre navigateur.

---

## Exemple de projet

**[AI Market Dashboard →](https://iamarketdash.netlify.app/)**

![Aperçu du dashboard AI Market](preview.png)

> Dashboard généré en une seule commande Claude Code — données marché IA 2025/2026, graphiques multi-sources, filtres dynamiques, mode sombre.

---

## Prérequis

| Outil | Version | Utilité |
|-------|---------|---------|
| [Claude Code CLI](https://docs.anthropic.com/claude-code) | dernière | Agent IA qui lit les skills et génère les fichiers |
| [Bun](https://bun.sh) _(optionnel)_ | dernière | Runtime rapide pour le script de recherche web |

---

## Démarrage rapide

### 1. Cloner le dépôt

```bash
git clone https://github.com/your-username/dashboard-generator.git
cd dashboard-generator
```

### 2. Ouvrir Claude Code

```bash
claude
```

### 3. Demander un dashboard

Décrivez simplement ce que vous voulez — Claude fait le reste :

```
Crée un dashboard analytique SaaS avec le revenu, les utilisateurs actifs,
le taux de churn et le MRR en KPIs. Inclus un graphique en ligne pour le revenu mensuel
et un graphique en camembert pour la répartition des abonnements. Le tableau affiche les souscriptions récentes.
```

Claude va :
1. Lire [`skeels/Dashboard_creation.md`](skeels/Dashboard_creation.md) pour les règles de génération HTML
2. Appliquer les patterns de [`skeels/Dashboard_design.md`](skeels/Dashboard_design.md)
3. Générer `<nom>-dashboard.html` avec des données fictives réalistes

### 4. Ouvrir votre dashboard

```bash
# macOS / Linux
open mon-dashboard.html

# Windows
start mon-dashboard.html
```

---

## Utiliser des données réelles

Quand votre dashboard a besoin de chiffres à jour, utilisez le skill de recherche web avant de générer :

```bash
bun skeels/scripts/search.ts "SaaS benchmark metrics 2026"
bun skeels/scripts/search.ts "Chart.js 4 API reference"
```

**Conseils :**
- 2 à 4 mots-clés donnent les meilleurs résultats
- Incluez le nom de la bibliothèque ou du framework pour les docs

Dites ensuite à Claude d'utiliser ces résultats lors de la génération du dashboard.

---

## Structure du projet

```
dashboard-generator/
├── skeels/
│   ├── Dashboard_creation.md   # Règles HTML (CSS/JS inline, données fictives, Chart.js)
│   ├── Dashboard_design.md     # Patterns de mise en page : KPI, graphiques, tableaux, temps réel
│   └── data_web_serach.md      # Skill de recherche web
├── CLAUDE.md                   # Instructions projet Claude Code (chargées automatiquement)
└── README.md
```

---

## Référence des Skills

### Dashboard Design — [`skeels/Dashboard_design.md`](skeels/Dashboard_design.md)

Définit les règles structurelles et visuelles que Claude applique :

| Pattern | Description |
|---------|-------------|
| **Cartes KPI** | Rangée de 4 colonnes, flèches de tendance, variation % vs période précédente |
| **Cartes Graphique** | Wrapper titré, plage temporelle cohérente, rendu Chart.js |
| **Tableau de données** | Champ de recherche + pagination, 10 lignes par page |
| **Temps réel** | Hook WebSocket + indicateur live animé |
| **Grille responsive** | Système 12 colonnes — breakpoints sm / md / lg |
| **Bonnes pratiques** | Règle des 5 secondes, données critiques au-dessus du pli, divulgation progressive |

### Dashboard Creation — [`skeels/Dashboard_creation.md`](skeels/Dashboard_creation.md)

Règles pour le fichier HTML généré :

- **Autonome** — tout le CSS et JS est inline ; seul Chart.js (CDN) est autorisé
- **Mode sombre / clair** — variables CSS + bouton bascule
- **Esthétique distinctive** — typographie forte, palette de couleurs affirmée, aucun look IA générique
- **Données fictives** — données réalistes intégrées pour un rendu immédiat sans backend

---

## Exemples de prompts

```
# E-commerce
Crée un dashboard e-commerce : commandes, revenu, taux de conversion, abandon de panier.
Graphique en ligne pour les ventes journalières, barre pour les meilleurs produits. Tableau des commandes récentes.

# Monitoring DevOps
Crée un dashboard de surveillance serveur : CPU, mémoire, disque, uptime en KPIs.
Graphiques en temps réel pour CPU et mémoire. Tableau des alertes actives.

# Analytics Marketing
Génère un dashboard marketing : impressions, clics, CTR, CPA.
Graphique en ligne pour le trafic hebdomadaire, camembert par canal. Tableau des campagnes.

# Finance
Crée un dashboard financier : MRR, ARR, burn rate, runway.
Graphique en aire pour la croissance MRR, barre pour les catégories de dépenses. Tableau des transactions.
```

---

## Règles de design (résumé)

1. **Autonome** — fichier `.html` unique, aucune dépendance externe sauf Chart.js CDN
2. **Bascule sombre / clair** — toujours incluse, via des propriétés CSS personnalisées
3. **Esthétique distinctive** — pas d'Inter/Roboto, pas de dégradés violet sur blanc
4. **Responsive** — fonctionne sur mobile, tablette et desktop
5. **Rendu immédiat** — données fictives intégrées, fonctionne hors ligne

---

## Dépannage

**`bun` introuvable pour la recherche web**
→ Installez Bun : `curl -fsSL https://bun.sh/install | bash`
→ Ou utilisez `node` si une version compatible Node du script est disponible.

**Claude ne respecte pas les règles de design**
→ Vérifiez que `CLAUDE.md` est à la racine du projet — Claude Code le charge automatiquement.
→ Démarrez une nouvelle session : `claude` depuis le dossier projet.

---

## Licence

MIT
