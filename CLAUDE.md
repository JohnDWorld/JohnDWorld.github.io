# CLAUDE.md - Manuel d'opération (Portfolio de John)

Tu es Claude Code, au service de **John** (Jonathan Demory), auto-entrepreneur, **Agentic Engineer**.
Philosophie : **local-first, souveraineté numérique, GitOps**. Tagline : "Arrêtons d'être l'esclave de nos outils informatiques."

Ce projet = construire la **vitrine / portfolio web** de John, à exposer depuis son profil LinkedIn
quand il prospecte. Lis **INSTRUCTIONS.md** pour le brief complet (objectif, contenu, matière, déploiement,
infos à obtenir de John). Ce fichier-ci, c'est comment tu travailles.

> Convention : "tu" = Claude Code. John est le décideur.

---

## Règles dures (non négociables)

1. **PONCTUATION : jamais de tiret long.** Ni cadratin "—" (em-dash) ni demi-cadratin "–" (en-dash),
   nulle part : prose, code, commentaires, fichiers, commits, contenu du site. **Toujours le trait
   d'union "-"** (ou reformuler : virgules, parenthèses, deux phrases). Vérifie AVANT d'écrire/d'envoyer.
   C'est une exigence ferme et répétée de John.
2. **Français**, toujours. Ton de John : direct, concret, un brin rebelle assumé, zéro flagornerie,
   zéro buzzword creux. Chaque affirmation s'appuie sur une preuve, pas sur des adjectifs.
3. **Souveraineté jusque dans le site.** John VEND la souveraineté : le site doit en être une preuve
   vivante. Donc : **100 % statique** (HTML/CSS, JS vanilla si besoin), **zéro SaaS tiers, zéro tracker,
   zéro CDN externe obligatoire** (polices et assets servis en local de préférence). Pas de Carrd, pas
   de Notion, pas de Wix. Léger, rapide, accessible, **mobile-first** (un prospect clique depuis LinkedIn,
   souvent sur mobile).
4. **Ne JAMAIS inventer de fait.** Parcours pro, dates, chiffres, certifications, coordonnées : si
   l'info n'est pas fournie, tu la DEMANDES à John ou tu poses un placeholder clairement marqué
   (`[[À COMPLÉTER : ...]]`). Mieux vaut un trou visible qu'une donnée fausse postée en public.
5. **Client-safe.** Aucun nom de client tiers ni donnée confidentielle dans le site public. Citer ses
   propres projets (Mon Village Viking, l'Atelier à Agents, La Boutique à Automatisations, Obvious Agence)
   est OK car ce sont les siens.
6. **Zéro secret commité** (clés, tokens, mots de passe, identifiants serveur). Si un déploiement a besoin
   de secrets, ils vivent hors du repo (variables d'environnement / fichier gitignoré).
7. **GitOps.** Le repo est la source, le site déployé est la sortie. Versionne tout. Commits clairs.
   Tu commits en local et tu montres le diff ; tu ne pousses/déploies que sur accord explicite de John.

---

## Stack et conventions

- **HTML/CSS statique**, structure simple et lisible. JS vanilla uniquement si nécessaire (ex. brancher
  le calculateur de coût). Pas de framework lourd pour une vitrine 1 page.
- **Mobile-first**, responsive, performant (Lighthouse soigné), accessible (contrastes, alt, sémantique).
- **SEO de base** : balises title/meta description, Open Graph (aperçu propre quand le lien est partagé
  sur LinkedIn), favicon.
- Garde le code propre et commenté sobrement, dans le même esprit que l'artefact existant de John
  `outils/calculateur-cout-api.html` (une page HTML autonome, sans dépendance).

## Déploiement (cible)

- Le site est servi depuis **le VPS de John, à côté de son SaaS "La Boutique à Automatisations"**
  (dossier statique posé à côté de l'app, une URL pointée dessus via le reverse proxy + TLS Let's Encrypt).
- Domaine **enregistré** : `la-boutique-a-automatisations.com`.
- Le schéma d'URL exact (apex pour la vitrine + app sur `app.`, ou vitrine sur un sous-domaine) et le
  reverse proxy utilisé sont à confirmer avec John : voir INSTRUCTIONS.md (questions techniques d'ouverture).
- Tu fournis la conf de déploiement (bloc reverse proxy + enregistrement DNS + commande TLS) prête à
  copier-coller une fois ces points connus. Tu ne déploies pas sans le feu vert de John.

## Definition of done

- Vitrine 1 page (ou peu de pages), statique, autoportante, mobile-first, **zéro tiret long**.
- Accroche comprise en 5 secondes ; preuves concrètes ; offre claire ; CTA contact.
- Aucun fait inventé (placeholders explicites pour les trous), aucun secret commité, `git status` propre.
- Conf de déploiement fournie ; déploiement effectué uniquement sur accord de John.

## Comment démarrer

1. Lis **INSTRUCTIONS.md** en entier (objectif, marque, matière/preuves, copy de départ, plan de page,
   questions ouvertes).
2. Pose à John les **questions techniques d'ouverture** (reverse proxy, position du SaaS, VPS, URL) et
   les **infos manquantes** (parcours, dates, contact, prix, certifs).
3. Propose le plan de page, puis construis la V1 statique. Itère avec John. Déploie sur accord.
