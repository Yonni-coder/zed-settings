# Zed settings (opinionated)

Ce repo contient mon fichier `settings.json` pour l’éditeur **Zed**.

L’objectif est double:

- **Reproductibilité**: je peux retrouver ma config rapidement sur une nouvelle machine.
- **Partage**: tu peux cloner, piocher des idées, et adapter.

## Installation

Zed lit un fichier `settings.json` (en pratique **JSONC**: commentaires `//` acceptés).

- **Option A (recommandée)**: copier/coller le contenu de ce repo dans tes settings Zed.
- **Option B**: remplacer ton fichier settings local par celui-ci.

Emplacement typique (à adapter selon OS / installation):

- Linux: `~/.config/zed/settings.json`
- macOS: `~/Library/Application Support/Zed/settings.json`
- Windows: `%APPDATA%/Zed/settings.json`

## Points notables

### UX / UI

- `use_system_window_tabs: false`
  - Laisse Zed gérer les tabs de fenêtre.
- `scrollbar.axes.vertical: false`
  - Cache la scrollbar verticale pour gagner de la place.
- `max_tabs: 6`
  - Limite volontairement le nombre d’onglets pour rester focus.

### Formatage et sauvegarde

- `autosave.after_delay.milliseconds: 1000`
  - Autosave après 1 seconde d’inactivité.
- `format_on_save: "on"`
  - Lance le formatage à chaque sauvegarde.
- `formatter: "prettier"`
  - Formatter global par défaut.

Si tu trouves que ça « bouge trop de code » ou que c’est lent:

- passe `format_on_save` à `"off"`
- ou garde-le activé uniquement pour certains langages dans `languages.{Lang}`

### TypeScript / JavaScript

- `languages.TypeScript` / `TSX` / `JavaScript` / `JSX`
  - `language_servers: ["emmet-ls", "..."]`
  - `code_actions_on_format` pour:
    - `source.organizeImports`
    - `source.fixAll.eslint`
    - etc.

Pré-requis côté projet (si tu veux profiter à fond):

- **Prettier** installé dans le projet (`npm i -D prettier`) ou disponible globalement
- **ESLint** configuré (idéalement avec `eslint.config.*` si tu utilises flat config)

### PHP / Laravel

- LSP: `intelephense`
- Formatter externe: `./vendor/bin/pint`

Ça suppose que:

- tu es dans un projet avec `composer install`
- `laravel/pint` est installé

Sinon, tu peux supprimer/adapter le bloc `languages.PHP.formatter.external`.

## Sécurité / secrets

Ce fichier contient un placeholder:

- `lsp.intelephense.initialization_options.licenceKey: "VOTRE_CLÉ_ICI"`

- **Ne commit jamais** une vraie clé licence dans un repo public.
- Remplace-la **localement** sur ta machine.

## Personnalisation rapide

- **Keymap**: `base_keymap` (ici: `VSCode`)
- **Fonts**: `buffer_font_family`, `ui_font_size`, `buffer_font_size`
- **Thèmes**: `theme.light` / `theme.dark`

## Notes

- Le fichier `settings.json` ici est volontairement commenté pour servir de référence.
- Les commentaires `// ...` impliquent du **JSONC**; si tu as besoin de JSON strict, il faudra enlever les commentaires et les virgules finales.
