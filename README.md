# Site vitrine ISO 9001 Lead Auditor

Site statique de l’app iOS/Android **ISO 9001 Lead Auditor** : page d’accueil,
aide et pages légales. Hébergé sur GitHub Pages.

- **En ligne** : https://pierro0t.github.io/ISO-9001-website/
- **Technique** : HTML/CSS/JS sans build. Bilingue EN/FR par bascule côté
  client : la préférence est gardée dans `localStorage` (clé `i9001-lang`) et
  appliquée avant le premier affichage, sans flash.
- **Dépôt public** : `Pierro0t/ISO-9001-website`, GitHub Pages sur la branche
  `main`, à la racine (`.nojekyll`).

## Pages

| Fichier | Rôle |
|---------|------|
| `index.html` | Page d’accueil |
| `privacy.html` | Politique de confidentialité (exigée par Apple et Google) |
| `terms.html` | Conditions d’utilisation |
| `support.html` | Aide et contact (URL de support exigée par Apple et Google) |
| `legal.html` | Mentions légales |

Les textes légaux de `privacy.html` et `terms.html` sont ceux de l’app :
`mobile/scripts/gen-site-legal.cjs` les écrit depuis `mobile/src/i18n.ts`
(`legalUpdated`, `privacyBody`, `termsBody`) entre les marqueurs
`<!-- legal:... -->`. Ce qui se trouve entre ces marqueurs se modifie dans
l’app, jamais dans le HTML.

## Publier

Depuis la racine du dépôt `ISO-9001-Lead-Auditor` :

1. Modifier les pages de `website/`.
2. Si les textes légaux de l’app ont changé : `node mobile/scripts/gen-site-legal.cjs`.
3. Vérifier en local, dans deux terminaux :
   ```bash
   python3 -m http.server 8102 -d website
   SITE_URL=http://localhost:8102 node mobile/scripts/check-site.mjs
   ```
4. Committer `website/`.
5. Avec l’accord de Pierre uniquement : `./website/publish.sh`. Le script
   vérifie que `website/` est commité et que les textes légaux sont à jour,
   pousse le site sur `Pierro0t/ISO-9001-website` (`main`) et active GitHub
   Pages au besoin. Prérequis : `gh` authentifié avec le droit d’écriture sur
   ce dépôt.

## Contact

pidotis+ISO9001@gmail.com

---

Outil d’étude indépendant. Non affilié à ISO, PECB ni à aucun organisme de
certification.
