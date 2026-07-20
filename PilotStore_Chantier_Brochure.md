# PilotStore — Chantier Brochure & Commercialisation

*Document de travail — ouvert le 18/07/2026*

---

## 1. Contexte / déclencheur

- Discussion informelle avec **Stan**, actuel gérant du **Carrefour 220 Grammont**, au sujet de PilotStore.
- Ce matin (18/07), message de Stan à Olivier : **« ton logiciel m'intéresse »**.
- Premier intérêt externe spontané, sans démarchage → signal produit fort.
- Contexte interne : Grammont en cours d'onboarding, Caen à ~2 mois.

---

## 2. Brochure — cadrage

### Identité
- **Couleurs PilotStore** (charte du logiciel).
- Tagline / positionnement : **« Le copilote du quotidien pour votre point de vente »** — *un vrai compagnon pour votre équipe* (validé 18/07, remplace « outil de gestion d'un point de vente » jugé plus froid).

### Angle principal
- **L'aide à l'organisation des tâches et de l'équipe.**
- Pas un argumentaire technique : montrer que l'outil parle le langage du métier (gérant Carrefour proximité = il connaît le terrain, pas besoin de vulgariser).

### Trame narrative retenue ✅
- **« Du matin au soir… de l'ouverture à la clôture »** — raconter une journée du magasin, chaque module apparaît comme un moment de la journée (validé 18/07).

### Idées en vrac (à enrichir)
- Enregistrer les contrôles de caisse
- Enregistrer les températures
- La traçabilité (tout est horodaté, photographié, historisé — on retrouve qui a fait quoi et quand)

### Modules candidats pour illustrer l'angle "organisation tâches & équipe"
- Tâches quotidiennes récurrentes (avec notes journalières)
- Contrôles caisse (génération automatique, clôtures + photos)
- Gestion DLC (contrôles, anti-gaspi, stats)
- Planning équipe (Combo)
- Clôtures du soir + email récapitulatif automatique
- Incidents / réclamations
- Notifications push (FCM) — l'info arrive à l'équipe sans qu'on la cherche
- Étiquettes F&L (Zebra), suivi TGTG, commandes clients, économat…
- Températures frigo (Danfoss) — surveillance sans y penser

### Cible
- Gérants Carrefour proximité (City / Express / Contact).
- Premier lecteur : **Stan**.

### Format (à décider)
- [ ] PDF 2–4 pages ? One-pager ? Mini-site ?
- [ ] Démo à l'appui (capture d'écran, accès démo ?)

---

## 3. Questions à trancher AVANT engagement avec un client externe

### 3.1 Modèle commercial
- [ ] Vendre / louer ? Abonnement mensuel par magasin ?
- [ ] Quel prix ? Quel périmètre inclus (modules, support, matériel Zebra/tablettes) ?
- [ ] Qui assure le **support** (pannes, questions, formation) ?
- [ ] Statut juridique de l'activité (facturation, structure) ?

### 3.2 Technique / sécurité
- [ ] Isolation multi-tenant : architecture actuelle conçue pour des magasins *de confiance*. Un client externe dans la même base = exigence d'isolation supérieure (leçon de l'audit DLC F1–F4).
- [ ] Option : base séparée par client externe ? Instance dédiée ?
- [ ] **Rate limiting API** (dette connue) → devient prioritaire.
- [ ] **2FA** (déjà approuvée, prévue avant Caen) → devient prioritaire.
- [ ] Sauvegardes / PRA : quel engagement vis-à-vis d'un client ?

### 3.3 Juridique / RGPD
- [ ] RGPD : données salariés (plannings), photos de surveillance, emails.
- [ ] CGV / contrat de service, clauses de responsabilité (perte de données, indisponibilité).
- [ ] Propriété du code et des données du client.

### 3.4 Marque
- [ ] Le nom « PilotStore » est-il libre / protégeable ?
- [ ] Rapport à l'enseigne Carrefour : outil indépendant, aucune affiliation → à clarifier dans la communication.

---

## 4. Stratégie court terme

1. **Brochure d'abord** — n'engage à rien, permet de montrer l'outil proprement à Stan et de jauger son intérêt réel.
2. En parallèle, mûrir le modèle (§3.1) sans se laisser bloquer.
3. Les chantiers sécurité (rate limiting, 2FA) montent en priorité si l'intérêt de Stan se confirme.

---

## 5. Journal des décisions

| Date | Décision |
|------|----------|
| 18/07/2026 | Ouverture du chantier. Brochure : couleurs PilotStore, « outil de gestion d'un point de vente », angle organisation des tâches et de l'équipe. |
| 18/07/2026 | Positionnement affiné : « Le copilote du quotidien pour votre point de vente ». Trame narrative validée : du matin au soir, de l'ouverture à la clôture. |
| 18/07/2026 | Idée d'Olivier (store DEMO sur la prod) **écartée** — pas de données de démo dans la base de production. Si besoin d'une démo plus tard : instance CC séparée, ou démo live à Giraudeau. Sujet reporté, non prioritaire. |
| 18/07/2026 | **Brochure V1 maquettée** (PDF 4 pages, charte du référentiel, timeline « du matin au soir »). Texte validé. Reste : coordonnées de contact + captures écran (magasin fictif en local). |
| 18/07/2026 | **Site pilotstore.fr lancé** : repo public `pilotstore-site` (index.html + CNAME), DNS OVH configuré (4 A GitHub Pages + CNAME www) et vérifié fonctionnel. Reste : check GitHub vert + Enforce HTTPS + email contact@pilotstore.fr (redirection OVH à créer). |
| 20/07/2026 | **Intégration V2 complète** (relance de Stan). 8 captures anonymisées du magasin fictif intégrées au site (légendes « fin de la paperasse ») + section « En pratique » (modules activables/masquables, tablette Android + wifi indispensable, Zebra ZD421d à acquérir) + mention Combo (planning collaborateurs). Brochure V2 PDF 6 pages avec captures. Retouches Claude : floutage vignettes traçabilité, gommage « crf » résiduel. |
