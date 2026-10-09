# DIAMONDS DRILL CLOTHING — site v1 (9 oct 2026)

## État
- LIVE:  https://danslamine.com (surge, option B: A @ → 138.197.235.123 + CNAME www → geo.surge.world chez Spaceship; cert LE custom émis 9 oct, renouvelé auto par Surge; www→apex 301)
- LIVE:  https://cotcollective.github.io/diamondsdrillclothing/  (canonical → indexable ✓)
- Repo:  github.com/cotcollective/diamondsdrillclothing (push direct, main)
- Archive locale: /home/portefolio/Desktop/diamondsdrillclothing/

## Todo prochaines étapes (par Dave + client)
- [ ] .com acheté par Dave → Cloudflare en front (CNAME GH Pages ou apex sur 185.199.108.x), ajouter le domaine custom dans Settings→Pages du repo + 4 A records
- [ ] Mettre canonical sur le .com une fois live (1 sed dans index.html + site-info + sitemap + robots, puis push + surge)
- [ ] Compte Stripe client → remplir les 10 slots STRIPE_LINKS={id:{standard:'',custom:''}} dans index.html (cherche "STRIPE_LINKS" dans index.html, les ids: resiste/muckeurs_rose/muckeurs_jaune/conventional/surface × tee/hoodie)
- [ ] [EMAIL] / [PHONE] placeholders dans llms.txt, llms-full.txt, ai.txt, .well-known/ai-plugin.json — remplacer quand client fournit
- [ ] Prix quand fixés: remplacer l'UI "Prix à venir" (i18n keys price/soon dans shopUi)

## Composition du site (source: d-mo-3d-brand-de-v-tements-mine(2).html, 18 MB)
- index.html 76 KB (tout le JS), assets/ 17 photos/designs + 2 tracks audio (m4a+mp3 fallback)
- Extract: 19 data URIs b64 → fichiers (design/backTee/backHoodie × 5 ids + logo-front-tee/hoodie + tracks)
- 5 produits: resiste / muckeurs_rose / muckeurs_jaune / conventional / surface — id×tee ou id×hoodie = key STRIPE_LINKS
- Expérience: bouton DESCENDRE → descente 280m → 4 filons (Quartz=essentiels, Diamant=Foreur, Or=éd. limitées, Équipe=entreprise) — règle «3 forages ou 10 s — le premier gagne» — scoop avance sur tapis roulant
- Boutique: deep-link #shop-resiste etc. ouvert par sitemap, boutons gated par STRIPE_LINKS (bientôt disponible tant que vide)

## Fichiers SEO/LLM déjà en place
- robots.txt (GPTBot/CCBot/Google-Extended disallow, PerplexityBot allow, sitemap)
- sitemap.xml (root + 5 #shop-*), llms.txt, llms-full.txt, ai.txt, .well-known/ai-plugin.json
- og-image.jpg + twitter-image.jpg (composés PIL: 5 designs + bandeau titre), favicon.ico + apple-touch-icon.png (logo front tee sur fond ink)
- 404.html branded («Filon introuvable — T'es rendu trop profond dans la mine»), site-info.html (mini-page SEO sans JS avec meta refresh)
- noscript: menu sans JS + lien vers site-info.html

## Leçons session
- Surge hardcode son propre robots.txt (Disallow tout le monde) pis bloque .well-known/ → tout le SEO passe par GH Pages; surge = preview client seulement
- Le sous-texte i18n: shopUi.price='Prix à venir' (et PAS de chiffres) — l'UI affiche 'Bientôt disponible' automatiquement tant que les liens Stripe sont vides
- Les 5 products design jpegs se distinguent: resiste=tout le monde (rouge/noir), rose=femmes du fond, jaune=muckeurs, conventional=cycle souterrain, surface=rigs dehors