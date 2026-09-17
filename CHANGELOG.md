# Journal du référentiel IA Act

Ce journal dit ce qui a changé dans [`ia-act.v1.json`](ia-act.v1.json), quand, et
**sur quelle source**. La règle du dépôt est simple : sans source, pas de
modification.

Il conserve les erreurs plutôt que de les effacer. L'entrée 1.3.0 documente deux
faits de droit que nous avions publiés et qui étaient faux, avec l'article et les
pages officielles qui ont permis de les corriger. C'est délibéré : un référentiel
qui réécrit son passé ne peut pas être vérifié.

Les versions suivent le versionnage sémantique. Un correctif ne touche pas au
droit ; une version mineure ajoute ou corrige un fait.

## `ia-act.v1.json` 1.0.0, 11 septembre 2026

Première version. Établie à partir du règlement 2024/1689 et de sa modification par le
règlement 2026/1744 du 8 juillet 2026, publié au Journal officiel le 24 juillet 2026 et entré
en vigueur le 27 juillet 2026.

Contenu : les deux textes, sept échéances, les neuf pratiques interdites de l'article 5, les
huit domaines de l'annexe III et la dérogation de l'article 6(3), l'annexe I, les quatre
règles de transparence de l'article 50, la littératie de l'article 4, la bascule de rôle de
l'article 25, les obligations des modèles à usage général, les trois paliers de sanction de
l'article 99.

Points portés au registre `a_verifier` : l'autorité de surveillance désignée en France.

Vérifié à la source le 11 septembre 2026.

## `ia-act.v1.json` 1.1.0, 11 septembre 2026

Le référentiel devient la source d'affichage. Ajout de `numero` sur les deux textes, et sur
trois échéances de `frise: true`, `titre_court` et `frise_texte`. Motif : les dates étaient
écrites quatre fois dans la page, dont un « dans 14 mois » calculé à la main qui devenait faux
le mois suivant. Elles ne vivent plus qu'ici, et le délai se calcule au rendu.

Aucun fait réglementaire modifié. Vérification à la source inchangée, 11 septembre 2026.

## `veille.v1.json` 1.1.0, 11 septembre 2026

Première version publiée, créée directement en 1.1.0 pour suivre le référentiel qu'elle
surveille. Cinq sources officielles, leur empreinte de référence, un seuil d'ancienneté de
90 jours et une taille minimale de réponse.

EUR-Lex est délibérément hors de cette liste : le site répond `202` avec un corps vide à une
requête faite depuis un serveur. Sans le seuil de taille, l'empreinte de la chaîne vide
serait parfaitement stable et la veille se croirait verte pour toujours.

## `ia-act.v1.json` 1.2.0, 13 septembre 2026

Le champ `supervision_nationale_depuis` de l'obligation de littératie portait la date
2026-08-03 sans qu'aucune des sources du dépôt ne l'explique. Constat FAIBLE de l'audit du
13/09/2026, et il avait raison : un fait daté sans source, dans un dépôt dont la règle est
« sans source, pas de modification ».

La date est juste et reste inchangée. Ce qui est ajouté, c'est ce qui manquait :

- `supervision_nationale_source` pointe la page de la Commission sur la littératie IA, ajoutée
  aux `sources_primaires` ;
- `supervision_nationale_note` explique le décalage d'un jour avec le 2 août. Il vient de la
  source elle-même, qui écrit « the supervision and enforcement rules apply from 3 August 2026
  onwards » à un endroit et « as of 2 August 2026 » à un autre. Le 3 août est retenu comme la
  lecture la plus prudente pour un déployeur, qui n'a rien à gagner à se croire hors
  surveillance un jour de plus.

Aucun fait réglementaire modifié. Vérifié à la source le 13 septembre 2026.

## `ia-act.v1.json` 1.3.0, 13 septembre 2026

**Correction d'une erreur de droit publiée.** Deux faits étaient faux, tous les deux sur des
dates d'application, tous les deux servis sur oriq.fr et repris dans le diagnostic envoyé par
email aux dirigeants qui font l'auto-évaluation.

Source des deux corrections : article 113 du règlement 2024/1689, dans sa version modifiée par
le règlement 2026/1744. Lecture article par article sur
https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-113 et sur
https://artificialintelligenceact.eu/article/113/, qui sert le texte consolidé. EUR-Lex reste
injoignable depuis un serveur, comme documenté plus haut.

### 1. Le régime de sanctions n'est pas applicable depuis le 2 août 2026

`sanctions.applicable_depuis` passe de `2026-08-02` à `2025-08-02`.

L'article 113, point b), dit : « Chapter III Section 4, Chapter V, Chapter VII and Chapter XII
and Article 78 shall apply from 2 August 2025, with the exception of Article 101 ». Le
chapitre XII est celui des sanctions. Il s'applique donc depuis le 2 août 2025, un an plus tôt
que ce que le référentiel annonçait.

L'erreur venait d'un amalgame dans l'échéance du 2 août 2026, qui portait sous un seul objet
l'application générale du règlement, l'article 50 et le régime de sanctions. Les deux premiers
y sont bien à leur place, le troisième non. L'entrée est scindée :

- le **2 août 2025** porte désormais les modèles à usage général (chapitre V), la gouvernance
  (chapitre VII), les organismes notifiants et notifiés (chapitre III section 4), le régime de
  sanctions (chapitre XII) et la confidentialité (article 78) ;
- le **2 août 2026** garde l'application générale, l'article 50 et la surveillance du marché
  (chapitre IX), et reçoit l'article 101.

Le nombre d'échéances ne change pas : le 2 août 2025 existait déjà, il était incomplet.

**L'exception de l'article 101 est traitée.** Le référentiel descend au niveau des paliers de
sanction, il devait donc la porter. Nouveau bloc `sanctions.exception_article_101` : les
amendes que la Commission peut infliger aux fournisseurs de modèles d'IA à usage général
suivent le calendrier général et ne valent que depuis le 2 août 2026. Le libellé dit
explicitement qu'elles ne concernent pas une entreprise qui se contente d'utiliser ces
modèles, pour qu'aucun dirigeant ne se croie visé.

Ajout de `sanctions.note_calendrier`, sans laquelle la correction se lit comme une menace : le
régime existe depuis le 2 août 2025, mais une sanction suppose un manquement à une obligation
elle-même applicable. Les obligations des systèmes à haut risque n'étant pas en vigueur, elles
ne peuvent pas être sanctionnées aujourd'hui.

### 2. Deux des neuf pratiques interdites ne valent pas depuis le 2 février 2025

Erreur trouvée en relisant l'ensemble de l'article 113, et de même nature que la première.

Le référentiel affichait les neuf pratiques de l'article 5 sous un seul `applicable_depuis` au
2 février 2025. C'est faux pour les deux qu'a ajoutées l'omnibus. L'article 113, point a),
dit : « Chapters I and II shall apply from 2 February 2025, with the exception of Article 5(1),
first subparagraph, points (ba) and (bb), and Article 5(1a) and (1b) which shall apply from
2 December 2026 ». Ce sont exactement les contenus intimes non consentis et les contenus
pédocriminels.

La pratique `contenus_intimes` porte maintenant `applicable_a_partir_de: "2026-12-02"` et une
note qui cite le point a). Un champ `interdictions.exception` le dit au niveau du bloc, pour
que la règle générale au 2 février 2025 ne se lise plus seule. L'échéance du 2 décembre 2026,
qui ne portait que la fin de la tolérance de marquage de l'article 50.2, porte aussi ces deux
interdictions.

### 3. Traçabilité du calendrier

Chaque échéance reçoit un champ `fondement` qui nomme le point de l'article 113 dont elle
sort, et le référentiel reçoit un `calendrier_source`. C'est ce qui manquait pour qu'une
relecture attrape l'erreur ci-dessus sans rouvrir le texte. `usage_general` reçoit
`transitoire_article: "111.3"` pour la même raison. L'URL de l'article 113 entre dans
`sources_primaires`.

### Ce qui a été vérifié sans avoir eu à être corrigé

- **2 février 2025**, chapitres I et II, interdictions et littératie : juste, sous la réserve
  du point 2 ci-dessus.
- **2 août 2027**, article 111(3), modèles à usage général déjà sur le marché avant le
  2 août 2025 : le texte du champ `usage_general.transitoire` est exact.
- **2 décembre 2027** et **2 août 2028**, annexe III et annexe I : conformes à l'article 113,
  point c), dans sa version modifiée par l'omnibus, y compris les deux `ancienne_date`.
- **2 décembre 2026**, tolérance de quatre mois sur le marquage lisible par machine de
  l'article 50.2 pour les systèmes déjà sur le marché avant le 2 août 2026 : confirmé.
- **Article 50**, application au 2 août 2026 : confirmé, il relève du calendrier général.
- **Article 99**, les trois plafonds : inchangés, et volontairement figés à leur valeur
  dans le validateur du dépôt. Un schéma générique laisserait passer 3 500 000 là où le
  texte dit 35 000 000.

### Reste ouvert

L'échéance du **2 août 2027** de l'article 111(3) n'est pas une entrée du tableau `echeances`,
elle ne vit que dans le texte de `usage_general.transitoire`. Elle n'apparaît donc ni dans le
calendrier de la page, ni dans `llms-full.txt`. Ce n'est pas une erreur, c'est un choix de
périmètre qui n'a jamais été écrit : le calendrier public ne retient que les échéances qui
peuvent toucher une entreprise ordinaire, et celle-ci ne vise que les éditeurs de modèles.
L'ajouter est une décision, pas une correction, et elle attend un arbitrage.

Vérifié à la source le 13 septembre 2026.

## `ia-act.v1.json` 1.3.1, 15 septembre 2026

**Aucun changement de droit.** L'échéance du 2 décembre 2026 entre dans la frise du hero de
`/ia-act/`, dont elle était absente depuis l'origine.

Le fait juridique était déjà là, correct et sourcé, depuis la 1.0.0 : l'entrée `2026-12-02`
porte la fin de la tolérance pour le marquage lisible par machine des contenus générés par les
systèmes déjà sur le marché avant le 2 août 2026 (article 50.2), et les deux interdictions
ajoutées à l'article 5 par l'omnibus. Elle était donc bien servie dans le calendrier complet de
`/ia-act/sanctions-et-calendrier/`, qui rend toutes les échéances, et dans `llms-full.txt`.

Ce qui manquait est un attribut de présentation. `blocFrise()` de `build-ia-act.mjs` filtre sur
`e.frise`, et cette entrée n'avait ni `frise`, ni `titre_court`, ni `frise_texte`. Le hero
affichait donc trois cartes, 2 août 2026, 2 décembre 2027 et 2 août 2028, en sautant la seule
échéance à venir dans les douze prochains mois. Un lecteur qui s'arrête au hero, ce que fait un
dirigeant pressé, en repartait avec la prochaine date à quinze mois au lieu de onze semaines.

Ajoutés : `frise: true`, `titre_court: "Marquage des contenus"`, et `frise_texte`. La frise
passe de trois à quatre repères, toujours dans l'ordre chronologique. La frise est verticale,
un quatrième repère ne change pas la mise en page.

Version incrémentée en correctif et non en mineur : le contenu juridique du fichier est
identique octet pour octet en dehors de ces trois attributs, et `verifie_le` reste au
13 septembre 2026, aucune source n'ayant été relue.

## `ia-act.v1.json` 1.3.2, 16 septembre 2026

**Aucun changement de droit.** Le référentiel déclare où il est déposé.

Nouveau champ `depots`, qui porte l'adresse du dépôt public
<https://github.com/ORIQ-IA/referentiel-ia-act>. Motif : un jeu de données qui n'existe
qu'à une seule adresse ne se cite pas durablement, et rien ne permet à une machine de
rattacher la copie qu'elle lit à sa source. Le champ alimente `sameAs` dans le balisage
`Dataset` de la page publique, et il accueillera `doi` dès qu'un identifiant pérenne aura
été délivré.

`verifie_le` reste au 13 septembre 2026, aucune source n'ayant été relue. `CITATION.cff`
suit la version, comme le validateur l'exige.

## `ia-act.v1.json` 1.3.3, 17 septembre 2026

**Aucun changement de droit.** Le référentiel déclare son second dépôt.

`depots` accueille l'adresse de la fiche data.gouv.fr, à côté de celle de GitHub. Motif mesuré
le 17/09 : le `Dataset` JSON-LD servi sur `/ia-act/` portait un `sameAs` vers le seul dépôt
GitHub. Notre jeu de données n'était donc relié à aucun domaine d'État, alors que la fiche
existe et qu'elle est vivante. Un moissonneur, et un modèle qui lit la page, n'avaient aucun
moyen de rattacher l'un à l'autre.

Constat associé, non résolu par cette version : `data.europa.eu` ne connaît pas encore ce jeu de
données (zéro résultat le 17/09), alors qu'il moissonne data.gouv.fr. Délai probable, à
revérifier, pas à supposer bloqué.

`verifie_le` reste au 13 septembre 2026, aucune source n'ayant été relue. `CITATION.cff` suit la
version, comme le validateur l'exige.

## `ia-act.v1.json` 1.3.4, 17 septembre 2026

**Aucun changement de droit.** Le référentiel porte son identifiant pérenne.

Le dépôt Zenodo a délivré le DOI de concept `10.5281/zenodo.22810935` le 17 septembre 2026, à
la release `v1.4.0` du dépôt public. C'est celui de concept, pas celui de version : il pointe
toujours vers le dernier dépôt, il ne changera plus. Le DOI de version, `10.5281/zenodo.22810936`,
n'est pas porté par le référentiel, il change à chaque release.

Trois champs suivent, et un seul endroit les alimente : `doi` le porte, `citation` le recopie
dans la formule prête à citer, `depots` reçoit `https://doi.org/10.5281/zenodo.22810935`. Le
générateur du site attendait déjà `doi` pour l'émettre en `identifier` du `Dataset`, et
`depots` alimente `sameAs` : rien n'a été codé côté site pour ce champ.

`CITATION.cff` reçoit le même DOI en `doi` et en `identifiers`, ce qui fait apparaître la
citation correcte sur GitHub et pré-remplit Zenodo à la release suivante.

Relevé en relisant, non corrigé par cette version : la fiche Zenodo affiche le type de ressource
**Software**, alors que `CITATION.cff` déclare `type: dataset`. L'intégration GitHub de Zenodo
impose Software par défaut. La correction se fait sur la fiche, à la main, avec le compte de
Brice.

`verifie_le` reste au 13 septembre 2026, aucune source n'ayant été relue.

## `obligations.v1.json` 1.1.0, 17 septembre 2026

**Le chapitre III est atomisé.** Dix-sept articles du régime des systèmes à haut risque
s'ajoutent aux huit obligations de la version précédente. Le catalogue en porte vingt-cinq.

**Source, et c'est le point qui compte** : collecte article par article sur
`ai-act-service-desk.ec.europa.eu`, le site de la Commission, versions anglaise et française.
**Dix-sept sur dix-sept depuis la source officielle**, aucun recours à une source de repli. La
règle du dépôt tient : rien ici ne vient de la mémoire d'un modèle.

Trois familles, qui ne pèsent pas sur les mêmes personnes :

- **Le fournisseur** : articles 9 (gestion des risques), 10 (gouvernance des données),
  11 (documentation technique), 12 (journalisation), 13 (information du déployeur),
  14 (contrôle humain), 15 (exactitude, robustesse, cybersécurité), 16 (ses douze obligations),
  17 (système de gestion de la qualité), 72 (surveillance après commercialisation),
  73 (incidents graves).
- **La mise sur le marché** : 43 (évaluation de la conformité), 47 (déclaration UE),
  48 (marquage CE), 49 (enregistrement).
- **Le déployeur** : 26 (ses obligations) et 27 (analyse d'impact sur les droits fondamentaux).

**Ce que la collecte a permis de trancher, et que le marché se trompe.** L'article 27 ne vise
**pas tous les déployeurs** : seulement les organismes de droit public, les entités privées
fournissant des services publics, et les déployeurs des systèmes des points 5 b) et 5 c) de
l'annexe III. Une PME ordinaire n'y est pas soumise. Et l'analyse d'impact sur les droits
fondamentaux **complète** l'analyse d'impact RGPD, elle ne s'y substitue pas : c'est la
confusion la plus répandue chez les concurrents examinés le 17/09.

Deux autres précisions qui changent une conclusion d'audit : pour les points 2 à 8 de
l'annexe III, l'évaluation de la conformité se fait **par contrôle interne, sans organisme
notifié** (article 43) ; et l'article 26 impose d'**informer les représentants des travailleurs
avant toute mise en service sur le lieu de travail**, ce qui est l'obligation la plus concrète
pour une entreprise française.

**Quatre points ouverts, déclarés plutôt que comblés de mémoire** : les rubriques de l'annexe IV
n'ont pas été lues, la page de l'article 11 y renvoyant sans les reproduire ; le plafond des
amendes de l'article 101 ; les articles 54 et 55 ; et les articles 18, 19, 20 et 40 auxquels
l'article 16 renvoie. Tant que l'annexe IV n'est pas collectée, **ne jamais en énumérer les
rubriques dans un document client**.

Ce fichier entre dans le paquet public avec cette version.

## `obligations.v1.json` 1.0.0, 17 septembre 2026

**Aucun fait de droit nouveau.** Fichier neuf, qui réorganise en obligations atomiques ce que
`ia-act.v1.json` portait déjà en sections. Chaque entrée nomme son article, ses acteurs et sa
date d'exigibilité. Rien n'y a été ajouté qui ne figurait pas déjà, vérifié et sourcé, dans le
référentiel du 13 septembre.

Motif : le référentiel répondait « quelles échéances » et « quelles interdictions ». Il ne
répondait pas « quelles obligations pèsent sur moi, article par article », qui est la question
d'un audit et celle d'un dirigeant. Une analyse d'écart ne se fait pas sur des sections.

Périmètre de cette version : les huit obligations exigibles au 17 septembre 2026, plus les
modèles à usage général. Articles 4, 5, 25, 50.1, 50.2, 50.3, 50.4 et 53. Le chapitre III
n'est pas atomisé : il reste en prose dans `ia-act.v1.json`, section `haut_risque`.

Fichier séparé de `ia-act.v1.json`, qui reste la source du calendrier, des sanctions et des
définitions. Aucune date n'est redite ici de son propre chef : chaque `exigible_le` correspond à
une échéance de `ia-act.v1.json`, et le validateur le contrôle.

Deux points ouverts, portés dans `a_verifier` : le plafond des amendes de l'article 101 pour
les fournisseurs de modèles à usage général, que le référentiel décrit sans le chiffrer, et
les articles 54 et 55, cités à l'échéance du 2 août 2025 sans contenu.

**Question de calendrier posée par ce travail, tranchée depuis.** L'article 25 est daté ici au
2 décembre 2027, parce qu'il appartient au chapitre III et que l'échéance de cette date couvre
« chapitre III, annexe III ». Un déployeur qui appose sa marque sur un outil du marché n'est pas
en écart en septembre 2026 : le fait générateur existe, ses effets arrivent. Le compter comme un
écart est le type d'erreur de calendrier reproché au reste du marché.
