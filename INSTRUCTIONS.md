# INSTRUCTIONS.md - Brief du projet Portfolio

> Ce document est autoportant : il contient tout le contexte nécessaire pour démarrer, sans accès à
> d'autres conversations. Lis aussi `CLAUDE.md` (les règles de travail). Rappel : **jamais de tiret
> long, uniquement "-"**.

---

## 1. Le projet en une phrase

Construire la **vitrine web de John** (page unique, statique, souveraine) à mettre en lien depuis son
profil LinkedIn, pour que, **quand il prospecte en outbound**, la personne qui clique comprenne **en 5
secondes** ce qu'il apporte, voie des **preuves concrètes**, et puisse le **contacter**.

## 2. L'objectif précis

- Cible : **TPE / PME** (langage clair, orienté bénéfices). Public secondaire : pairs tech / CTO
  (pour la crédibilité technique).
- Usage : John envoie des messages de prospection sur LinkedIn avec son compte perso. Le prospect
  clique sur son profil, puis sur le lien de la vitrine. La vitrine doit convertir l'attention en
  "ah, je vois ce qu'il fait et ce que ça m'apporte" puis en prise de contact.
- Boucle visée : message LinkedIn -> profil clair -> vitrine qui prouve -> contact.

## 3. Qui est John et architecture de marque (IMPORTANT, ne pas confondre)

- **John (Jonathan Demory)** : auto-entrepreneur, **Agentic Engineer**. Philosophie local-first,
  souveraineté, GitOps. C'est LUI qui prospecte ; la vitrine met en avant la personne + ses preuves.
- **La Boutique à Automatisations** : sa **marque SOLO**, et c'est **déjà un SaaS en production**
  (l'app vit sur son VPS, domaine `la-boutique-a-automatisations.com`, déjà enregistré). C'est son
  offre produit. La vitrine peut être le visage public de cette marque + de ses services sur-mesure.
- **Obvious Agence** : sa **boîte de communication** (créa / publicité / prospection), lancée il y a
  environ 3 semaines (soit ~début juin 2026), **avec son associé Baptiste**. C'est une entité SÉPARÉE :
  on peut la citer comme une expérience, mais on ne la mélange pas avec La Boutique (solo).
- Deux registres de discours : "Agentic Engineer" = crédibilité côté pairs/tech ; "La Boutique à
  Automatisations" / "j'automatise vos tâches" = côté client TPE/PME (ce qu'ils comprennent).

## 4. La matière : preuves vérifiées (à transformer en contenu)

Ce sont des réalisations réelles de John, utilisables comme preuves (sans nommer de client tiers) :

- **Mon Village Viking** : un système **multi-agents souverain**, conteneurisé (Docker), avec ~9 agents
  spécialisés nommés (orchestrateur, prospection, veille techno, finance/trésorerie, messagerie e-mail,
  agenda, mémoire/RAG, admin, forge d'agents). Ils collaborent via un tableau partagé (Supabase) et se
  pilotent depuis Telegram. Tourne 24/7 sur un VPS, inférence sur GPU local (Ollama) avec fallback cloud
  (GPT-5.5 via OAuth, sans clé API en dur).
- **L'Atelier à Agents** : une **bibliothèque de blueprints d'agents réutilisables** + un registre
  d'instances clients + une logique de "boutique" (catalogue de rôles). Principe : forger une fois,
  réparer une fois, profiter partout.
- **Intégrations réelles livrées** : bots Telegram ; **Open Banking** (veille de trésorerie temps réel,
  anti-spam déterministe) ; tri/classement d'e-mails (Gmail/Proton, IMAP) ; Google Calendar ; recherche
  web souveraine (SearXNG) ; base Supabase.
- **Patterns d'ingénierie d'agents** : "wake-gate / delta-gate" (un agent ne se réveille que s'il y a du
  neuf, donc zéro bruit et zéro coût inutile) ; GitOps de bout en bout (repo = source, runtime = sortie),
  déploiement idempotent, auto-déploiement pull-based ; secrets chiffrés (sops + age) ; réseau privé
  (Tailscale / Headscale) ; isolation par client (un dépôt par client, zéro fuite inter-client).
- **Calculateur de coût d'API** : un outil HTML autonome que John a déjà construit, calibré sur la conso
  réelle de tokens. Repères : prospection ~1,50 $ et audit ~1,15 $ de **coût de compute** par tâche.
  ATTENTION : ces chiffres sont le **coût d'inférence**, PAS le tarif facturé au client. Ne jamais les
  présenter comme un prix de vente. Cet outil est un **asset à intégrer** dans la vitrine (preuve par les
  chiffres). Le fichier source vit dans le repo Atelier de John (`outils/calculateur-cout-api.html`) :
  demander à John de te le fournir/copier si tu veux l'embarquer.
- **Obvious Agence** (com, avec Baptiste) : audit créatif automatisé (analyse concurrentielle vidéo,
  ~25 signaux, rapport PDF), prospection. A citer comme expérience séparée si pertinent.

## 5. Copy de départ (pack LinkedIn déjà rédigé et corrigé)

Réutilisable comme base pour la copy du site. A adapter au format web. Déjà nettoyé (aucun tiret long).

**Titre / accroche possible :**
- "Agentic Engineer | Fondateur de La Boutique à Automatisations | Agents IA souverains pour TPE/PME,
  local-first et coût maîtrisé"
- Accroche hero plus directe : "J'automatise les tâches répétitives des TPE/PME avec des agents IA qui
  tournent chez vous, pas chez un SaaS opaque."

**À propos (à transformer en sections web) :**
- Accroche : "Arrêtons d'être l'esclave de nos outils informatiques."
- Promesse : des systèmes d'agents IA qui tournent (pas des prototypes, pas des wrappers ChatGPT), du
  code en production 24/7.
- Concret : des agents spécialisés (prospection, veille, trésorerie, e-mail, agenda, compta) qui
  collaborent et se pilotent depuis Telegram ; inférence locale + fallback cloud ; tout versionné,
  secrets chiffrés, déploiement idempotent.
- Différenciateurs : souveraineté (données chez le client), ça tient en prod (GitOps, reproductible),
  isolation client totale, coût mesuré au token réel.

**Compétences (pour une section "expertise") :** architecture multi-agents ; inférence LLM locale
(Ollama) + routage par tier + fallback cloud ; GitOps de bout en bout ; gestion de secrets (sops/age) ;
patterns d'agents (wake-gate, delta-gate) ; prospection automatisée ; veille ; automatisation financière
(Open Banking) ; gestion e-mail (IMAP) ; intégrations API (Telegram, Google Calendar, Supabase) ;
Docker ; réseau privé (Tailscale/Headscale) ; Python/Bash.

**Mots-clés (SEO / clarté) :** agents IA, automatisation, prospection, veille, trésorerie, e-mail,
local-first, souveraineté numérique, GitOps, TPE/PME, Open Banking, coût maîtrisé.

## 6. Plan de page recommandé (V1, une page)

1. **Hero** : accroche comprise en 5 secondes + sous-titre bénéfice + 1 CTA contact. Visuel sobre.
2. **Le problème / la promesse** : "vos tâches répétitives mangent votre temps ; je les confie à des
   agents qui tournent chez vous, à coût visible".
3. **Preuves** : 3-4 cartes concrètes (le village 9 agents en prod ; automations métier livrées :
   prospection, veille, trésorerie, e-mail ; l'Atelier ; patterns d'ingénierie). Concret, chiffré.
4. **L'offre** : La Boutique à Automatisations (le SaaS) + les builds sur-mesure. Distinguer les deux.
5. **Calculateur de coût intégré** : preuve par les chiffres (bien préciser : coût de compute, pas prix).
6. **Qui suis-je** : John, Agentic Engineer, philosophie souveraineté. (Parcours : voir trous à combler.)
7. **CTA contact** : moyen de contact à confirmer (voir questions). Aperçu LinkedIn propre (Open Graph).

## 7. Questions techniques d'ouverture (à poser à John dès le début)

Pour la cible de déploiement (vitrine statique posée sur le VPS, à côté du SaaS Boutique) :
1. **Qui sert la boutique aujourd'hui ?** reverse proxy : nginx, Caddy ou Traefik ? Et c'est dans Docker
   ou en natif ?
2. **L'app SaaS est-elle à la racine** (`la-boutique-a-automatisations.com`) **ou déjà sur un sous-domaine** ?
3. **Quel VPS ?** (John a notamment un VPS "johnserver" qui héberge son village ; confirmer si la boutique
   est sur le même serveur ou un autre).
4. **Schéma d'URL retenu :** vitrine sur l'apex + app déplacée sur `app.la-boutique-a-automatisations.com`
   (pattern SaaS classique, URL la plus propre pour LinkedIn), OU vitrine sur un sous-domaine en laissant
   l'app intacte (zéro risque sur le SaaS en prod). Recommandation : apex pour la vitrine si la migration
   de l'app est indolore, sinon sous-domaine.

Une fois ces points connus : fournir le bloc reverse proxy + l'enregistrement DNS + la commande TLS
(Let's Encrypt), prêts à copier-coller. Ne rien déployer sans le feu vert de John.

## 8. Infos à obtenir de John (NE PAS inventer ; placeholder sinon)

- **Parcours AVANT les agents** : études, expériences pro, postes, années (la matière actuelle démarre
  ~2026 ; il manque sa trajectoire pour la section "qui suis-je").
- **Date de démarrage** de l'activité agents / du village (année, idéalement mois).
- **Localisation** (Lorient, Bretagne ? à confirmer).
- **Coordonnées de contact** à afficher : e-mail pro ? formulaire ? lien de prise de rendez-vous
  (idéalement souverain, pas un SaaS si possible) ? lien LinkedIn ?
- **Affichage des prix** : veut-il afficher des tarifs ? Rappel : les ~1,50 $ / ~1,15 $ sont du coût de
  compute, pas un prix de vente. A clarifier avant toute mention de prix.
- **Certifications / formation** à mentionner ?
- **Rassembler Lorient** (projet civique local de John) : à inclure dans la vitrine ou non ?
- **La Boutique (SaaS)** : la présenter en détail et mettre un lien vers l'app ? Ou rester sur l'offre
  générale ?

## 9. Première étape suggérée pour la session

1. Saluer John, confirmer que tu as lu CLAUDE.md + INSTRUCTIONS.md.
2. Poser les questions de la section 7 (technique) et les manques bloquants de la section 8 (contact,
   parcours, prix).
3. Proposer le plan de page (section 6) pour validation.
4. Construire la V1 statique (mobile-first, zéro tiret long, zéro SaaS tiers), avec placeholders clairs
   pour les infos en attente.
5. Fournir la conf de déploiement quand les points techniques sont connus. Déployer sur accord.
