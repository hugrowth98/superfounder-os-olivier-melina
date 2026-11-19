# contexte.md : comment vous prospectez

> Le profil de prospection. `02_Contexte/` dit qui vous êtes, ce que vous vendez, qui vous visez et comment vous parlez : ce fichier ne le recopie pas, il le traduit en critères de prospection (scoring, personas par taille, signaux, canaux, garde-fous). Le niveau opérationnel (décisionnaires par taille, requêtes booléennes, mots-clés d'exclusion) vit dans `Ciblage/`. Tous les skills du module GTM lisent ce fichier avant d'agir ; aucun ne contient de donnée sur vous. Rempli par `installer-gtm` ("Installe ma prospection"), une question à la fois. Pour changer une chose : modifier la ligne. Tant qu'il reste un crochet `[...]` dans les sections 2 et 3, l'OS n'est pas installé. Les exemples en commentaire `<!-- ex : ... -->` ne sont pas des valeurs par défaut : un champ inconnu reste vide, jamais inventé.

## 1. Offre et preuves

Source : `02_Contexte/Offer-Positioning.md` (pré-rempli le 2026-11-19). Les champs ci-dessous résument ce fichier pour la prospection.

- Ce que vous vendez, en une phrase dite à l'oral : "On trouve, on vend ou on loue les locaux des entreprises du Morbihan, et on aide les investisseurs à acheter des murs déjà loués."
- Le problème que ça règle, dans les mots du client : [ ]
- Format et prix : honoraires de transaction [ ]
- Preuve 1 (client, résultat, chiffre) : installation de Carrefour City et de Panorama Paysages
- Preuve 2 et preuve 3 : plus de 160 000 m² d'entrepôts et locaux d'activité vendus / Kerpont Park à Caudan commercialisé à 60 %
- Ce que vous ne faites pas (pour couper court en appel) : [ ]

## 2. Client idéal (ICP) en 3 couches, scoring sur 100

Source pour la cible : `02_Contexte/Clients-Problems-and-Messages.md`. Ici, sa traduction en grille de points : c'est cette grille que `qualifier-liste` applique.

Le score sert à trier : un compte sous le seuil est écarté, un compte entre deux est appelé en dernier. Les pondérations par défaut (40 / 20 / 40) se modifient ici. `qualifier_liste` applique ce barème et écrit `score_icp` et `tier`.

### Couche 1 : firmographique (40 points par défaut)

| Critère | Valeur cible | Points si exact | Points si adjacent | Sinon |
|---|---|---|---|---|
| Secteur | artisans, TPE et PME de production, de négoce, de BTP et de services qui ont besoin de locaux d'activité ou d'entrepôts ; adjacent : enseignes de commerce | 15 | 7 | 0 |
| Effectif | [ ] | 10 | 5 | 0 |
| Zone géographique | Morbihan (Vannes, Auray, Lorient, Caudan) ; adjacent : entreprises qui veulent s'implanter dans le Morbihan | 8 | 4 | 0 |
| Stade ou chiffre d'affaires | entreprise en croissance [ ] | 7 | 3 | 0 |

### Couche 2 : technographique (20 points par défaut)

Votre offre ne dépend d'aucun outil : couche mise à 0, ses 20 points sont à redistribuer sur les couches 1 et 3. [à valider : répartition]

| Critère | Valeur cible | Points si présent | Neutre | Sinon |
|---|---|---|---|---|
| Outil ou stack qui rend votre offre pertinente | sans objet | 0 | 0 | 0 |
| Outil concurrent en place | sans objet | 0 | 0 | 0 |

Adjacent = un cran à côté de la cible. Détection par `detecter_techno`. Si votre offre ne dépend d'aucun outil, mettre cette couche à 0 et redistribuer ses 20 points sur les couches 1 et 3.

### Couche 3 : comportementale (40 points par défaut)

| Critère | Points |
|---|---|
| Signal prioritaire n°1 de la section 4, daté de moins de [30] jours | 15 |
| Signal prioritaire n°2 à n°5, daté de moins de [60] jours | 10 |
| Deux signaux ou plus qui s'empilent | 10 |
| Engagement direct avec vous (commentaire, réponse passée, présent à un de vos events) | 5 |

### Tiers (modifiables)

| Tier | Score | Ce qu'on en fait |
|---|---|---|
| A | [75] à 100 | contact cette semaine, message écrit à la main, téléphone en priorité |
| B | [55] à [74] | séquence multicanal standard |
| C | [35] à [54] | nurturing, pas de téléphone |
| D | sous [35] | exclu, colonne `exclu = oui` |

### Exclusions (jamais dans une liste, quel que soit le score)

- B2C : [oui pour la prospection sortante : les particuliers passent par l'habitation]
- Concurrents (nommer) : [ ] <!-- autres agences d'immobilier d'entreprise du Morbihan -->
- Secteurs exclus : [ ]
- Tailles exclues, autres : [ ]

## 3. Personas : ATL, BTL et comité d'achat

Source pour qui ils sont : `02_Contexte/Clients-Problems-and-Messages.md`. Ici, le résumé en dix lignes ; le détail par tranche d'effectif dans `Ciblage/decisionnaires-par-taille.md`. ATL (above the line) : la personne qui signe et porte le résultat. BTL (below the line) : celle qui vit le problème tous les jours et devient votre champion. On contacte les deux, avec un angle différent. `trouver_personnes` cherche ces titres ; `cold-email` et `cold-call` adaptent le message.

### ATL : le décideur

- Titres à chercher : [ ] <!-- ex : CEO, DG, Directeur Paiements, VP Sales -->
- Ce qui l'empêche de dormir : [ ] <!-- ex : une échéance réglementaire avec sanction à la clé -->
- Ce qu'il mesure : [ ] <!-- ex : délai tenu, risque, marge -->
- Angle d'approche : [ ] <!-- ex : priorités, risque, échéances ; jamais TJM ni méthode -->
- Canal qui marche le mieux : [ ] <!-- ex : téléphone puis email -->

### BTL : celui qui vit le problème

- Titres à chercher : [ ] <!-- ex : Head of SWIFT, responsable prospection, CTO -->
- Ce qu'il vit au quotidien : [ ] <!-- ex : tout repose sur deux têtes, projets qui patinent -->
- Ce qu'il mesure : [ ] <!-- ex : charge, délais, incidents -->
- Angle d'approche : [ ] <!-- ex : lui donner de quoi convaincre en interne -->
- Canal qui marche le mieux : [ ] <!-- ex : LinkedIn puis email -->

### Comité d'achat chez vos clients

| Rôle | Qui c'est chez vos clients (titre) | Ce qu'il attend de vous | Poids dans la décision |
|---|---|---|---|
| Champion (porte le sujet en interne) | [ ] | [ ] | [ ] <!-- ex : 40 % --> |
| Décideur économique (signe) | [ ] | [ ] | [ ] |
| Utilisateur (vit le résultat) | [ ] | [ ] | [ ] |
| Évaluateur (technique, achats, juridique) | [ ] | [ ] | [ ] |
| Bloqueur possible | [ ] | [ ] | à surveiller |

Dans une TPE, décideur et champion sont souvent la même personne : ne remplir que les lignes qui existent vraiment.

## 4. Les 5 signaux prioritaires

Un signal dit "c'est le bon moment". Choisir cinq signaux parmi ces dix, les classer, dire pourquoi chacun compte pour votre offre. `detecter-signaux` ne surveille que ceux-là. Les trois derniers (visite de profil, abonnés de la page, a publié) demandent Sales Navigator et coûtent le prix de l'abonnement : ce sont les moins chers à mettre en place.

| Signal | Ce que c'est | Fenêtre utile | Verbe |
|---|---|---|---|
| Changement de poste | un décideur arrive dans une nouvelle fonction | jours 14 à 45 (pic), jusqu'à 90 | detecter_signal |
| Levée de fonds | budget neuf, plan de croissance | semaines 2 à 4 (pic), jusqu'à 8 ; Série C et plus : semaines 5 à 12 | detecter_signal |
| Recrutement | une offre ouverte sur un poste lié à votre offre | jours 14 à 30 après publication, frais 60 jours | scraper_offres_emploi |
| Événement | salon, conférence, webinaire, live où votre cible est | 7 jours avant à 7 jours après | scraper_engagement |
| Techno | adopte ou abandonne un outil lié à votre offre | jours 0 à 30 (pic), frais 60 jours | detecter_techno |
| Engagement contenu | like, commentaire sur votre sujet | jours 0 à 7 (pic), frais 30 jours | scraper_engagement |
| Concurrents | engagement sur leurs posts (7 jours), avis négatif (60 jours), client identifié (permanent), pub active (tant qu'elle tourne) | selon le cas | scraper_engagement, scraper_pubs, detecter_techno |
| Visite de profil | quelqu'un de votre cible a consulté votre profil LinkedIn | jours 0 à 7 après la détection, frais 30 jours | construire_requete_salesnav, trouver_personnes |
| Abonnés de la page | quelqu'un de votre cible suit votre page entreprise | jours 0 à 2 pour un nouvel abonné | construire_requete_salesnav, trouver_personnes |
| A publié | quelqu'un de votre cible a publié sur LinkedIn ce mois-ci : joignable, et son post donne l'accroche | jours 0 à 7 après le post | construire_requete_salesnav, trouver_personnes |

| Rang | Signal choisi | Pourquoi il compte pour cette offre | Fraîcheur max |
|---|---|---|---|
| 1 | [ ] <!-- ex : Recrutement d'un expert SWIFT --> | [ ] <!-- ex : ils cherchent un profil qu'on place en 3 semaines --> | [ ] <!-- ex : 60 jours ; le détail des fenêtres est dans detecter-signaux/ressources/fenetres-fraicheur.md --> |
| 2 | [ ] | [ ] | [ ] |
| 3 | [ ] | [ ] | [ ] |
| 4 | [ ] | [ ] | [ ] |
| 5 | [ ] | [ ] | [ ] |

## 5. Canaux et volumes

Les plafonds absolus sont dans `05_Departements/Go-to-Market/GARDE-FOUS.md`, le choix technique (LinkedIn via Unipile ou Lemlist) dans `05_Departements/Go-to-Market/OUTILS.md`. Ici, ce que vous voulez faire chaque semaine.

| Canal | Actif | Volume par semaine | Rôle dans la séquence |
|---|---|---|---|
| LinkedIn (invitations et messages) | [oui / non] | [ ] <!-- ex : 60 invitations --> | premier contact, dernier rappel avant appel |
| Email | [oui / non] | [ ] <!-- ex : 100 emails, 2 boîtes --> | argument, preuve, relance |
| Téléphone | [oui / non] | [ ] <!-- ex : 2 sessions d'1 h, 40 appels --> | conversion, réservé aux tiers A et B |

- Nouveaux prospects entrés en séquence par semaine : [ ] <!-- ex : 20 -->
- Rendez-vous visés par semaine : [ ] <!-- ex : 5 -->
- Séquence de référence, multicanal : LinkedIn J0, email J+2, email J+5, LinkedIn J+7, téléphone J+9 à J+12 (détail dans `10_Skills/cold-call/ressources/sequence-multicanal.md`). Email seul : 3 emails au plus (J0, J+3, J+10). Jamais plus de 3 relances après silence, tous canaux confondus. Variante voulue : [ ]
- Jours et heures d'envoi : [ ] <!-- ex : mardi à jeudi, 8h30 à 11h et 14h à 17h -->

## 6. Voix

Source : `02_Contexte/Tone-and-Voice.md` et `01_About-Me/anti-ai-voice.md`. Ici, seulement ce qui est propre à la prospection.

- Tutoiement ou vouvoiement en prospection : [vouvoiement] <!-- défaut : vouvoiement -->
- Longueur d'un premier message : [ ] <!-- ex : 3 phrases sur LinkedIn, 80 mots par email -->
- Trois expressions à vous, qu'on entend quand vous parlez : [ ] <!-- ex : "on se cale ça quand ?", "une bonne discussion", "concrètement" -->
- Mots et tournures interdits : [ ] <!-- ex : "synergie", "accompagnement sur mesure", "je me permets" -->
- Signature d'email (nom, fonction, une ligne de preuve) : [ ]

## 7. Garde-fous propres à vous

Les règles générales sont dans `05_Departements/Go-to-Market/GARDE-FOUS.md`. Ici, ce qui ne s'applique qu'à vous. Une ligne vide vaut mieux qu'une ligne fausse.

- Clients actuels et passés à ne jamais contacter (domaines ou entreprises) : [ ] <!-- ex : transactis.fr, bpce.fr -->
- Partenaires, apporteurs d'affaires, investisseurs : [ ]
- Listes ou fichiers à croiser avant tout envoi (chemin) : [ ] <!-- ex : 05_Departements/Go-to-Market/Listes-prospection/ne_plus_contacter.csv -->
- Zones ou pays exclus : [ ]
- Limite de volume plus basse que le défaut : [ ] <!-- ex : 15 invitations par jour, compte LinkedIn récent -->
- Sujets, angles ou mots à ne jamais utiliser en message : [ ]
- Qui valide avant envoi si ce n'est pas vous : [ ]

## 8. Précisions libres

Ce qui ne rentre pas au-dessus et que Claude doit savoir avant d'agir : saisonnalité, événement à venir, campagne en cours ailleurs, compte LinkedIn qui sort d'une restriction, changement d'offre prévu.

- [ ]

Rempli le : [date]. Dernière revue : [date]. À relire à chaque changement d'offre, de cible ou de canal.
