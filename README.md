# Référentiel IA Act

Les dates, les articles et les montants du règlement européen sur l'intelligence
artificielle, dans un fichier JSON daté, versionné et lisible par machine.

Sous licence **CC BY 4.0**. Utilisable librement, y compris commercialement, en
créditant la source.

- Fichier : [`ia-act.v1.json`](ia-act.v1.json)
- Servi en ligne : <https://oriq.fr/ia-act/ia-act.v1.json>
- Page de présentation : <https://oriq.fr/ia-act/>
- Journal des modifications : [`CHANGELOG.md`](CHANGELOG.md)

## Pourquoi il existe

Un modèle de langage interrogé sur l'AI Act répond de mémoire, et se trompe de
date. Beaucoup annoncent encore les obligations des systèmes à haut risque au
2 août 2026, alors que le règlement (UE) 2026/1744 du 8 juillet 2026 les a
reportées au 2 décembre 2027. Une erreur d'un an, sur une question où l'erreur
coûte cher.

Ce référentiel existe pour que la date vienne d'un fichier daté plutôt que de la
mémoire d'un modèle. Chaque fait porte l'article qui le fonde. Le journal dit
quand il a été vérifié, à quelle source, et ce qui a changé depuis.

Il a lui-même servi à corriger deux erreurs de droit que nous avions publiées :
voir l'entrée 1.3.0 du journal, qui les documente au lieu de les effacer.

## Ce qu'il contient

| Bloc | Contenu |
|---|---|
| `echeances` | Les dates d'application, avec leur `fondement` dans l'article 113 |
| `interdictions` | Les pratiques interdites de l'article 5, dont les deux ajoutées par l'omnibus |
| `haut_risque` | Les domaines de l'annexe III, la dérogation de l'article 6(3), l'annexe I |
| `transparence` | Les règles de l'article 50 |
| `obligations_transverses` | La littératie de l'article 4, la bascule de rôle de l'article 25 |
| `usage_general` | Les obligations des modèles à usage général, et leur régime transitoire |
| `sanctions` | Les trois paliers de l'article 99, leurs plafonds, et l'exception de l'article 101 |
| `a_verifier` | Ce qui n'est pas tranché, dont l'autorité de surveillance en France |
| `sources_primaires` | Les URL officielles dont tout le reste dérive |

Deux champs à lire en premier : `version` et `verifie_le`. Le second dit la date
à laquelle les sources ont été relues, pas la date du dernier commit.

## Le catalogue d'obligations

`obligations.v1.json` est le second fichier de données. Là où `ia-act.v1.json`
répond « quelles échéances » et « quelles interdictions », celui-ci répond
**« quelles obligations pèsent sur moi, article par article »**, qui est la
question d'un dirigeant.

Vingt-cinq entrées. Chacune porte son article, le ou les acteurs visés
(fournisseur, déployeur, fournisseur de modèle), sa date d'exigibilité, la
condition qui déclenche son application, les exceptions que le texte énonce
lui-même, ses renvois vers d'autres articles, et le palier de sanction dont elle
relève.

Le chapitre III y est couvert en entier : les dix-sept articles du régime des
systèmes à haut risque, collectés un par un sur le site de la Commission le
17 septembre 2026.

Deux points méritent d'être signalés, parce qu'ils sont souvent mal compris :

- l'**analyse d'impact sur les droits fondamentaux** de l'article 27 ne pèse pas
  sur tous les déployeurs. Le texte vise les organismes de droit public, les
  entités privées fournissant des services publics, et les déployeurs des
  systèmes des points 5 b) et 5 c) de l'annexe III. Et elle **complète** l'analyse
  d'impact du RGPD, elle ne s'y substitue pas ;
- pour les points 2 à 8 de l'annexe III, l'évaluation de la conformité se fait
  **par contrôle interne**, sans organisme notifié.

Comme le référentiel, ce fichier porte un champ `a_verifier` qui dit ce qui n'a
pas été lu à la source. Les rubriques de l'annexe IV en font partie : la page de
l'article 11 y renvoie sans les reproduire, elles n'ont donc pas été collectées et
ne figurent pas ici.

## Comment le citer

Le dépôt porte un [`CITATION.cff`](CITATION.cff) au format standard. GitHub
l'affiche, Zenodo le lit, les gestionnaires bibliographiques le comprennent.

En texte :

> Oriq, référentiel IA Act, version 1.3.1, vérifié le 13 septembre 2026,
> <https://oriq.fr/ia-act/>

## Comment l'utiliser dans un programme

```bash
curl -s https://oriq.fr/ia-act/ia-act.v1.json | jq '.echeances[] | {date, objet}'
```

Le fichier est aussi exposé comme outil appelable par un assistant, via un
serveur Model Context Protocol en lecture seule. Le verdict y est calculé par un
moteur de règles fixe, jamais produit par un modèle : deux appels identiques
rendent le même résultat.

## Ce que ce référentiel n'est pas

Il informe, il ne constitue pas un avis juridique opposable. Les textes
officiels font seule foi. Voir [`LICENSE`](LICENSE), et [`LICENCE-FR.txt`](LICENCE-FR.txt)
pour le résumé en français.

## À propos du journal

`CHANGELOG.md` est le journal de conception, publié tel quel. Il mentionne
parfois des chemins de fichiers du dépôt privé où le référentiel est maintenu, et
d'un questionnaire qui ne fait pas partie de cette publication. Ces références
sont conservées : les retirer casserait la traçabilité, qui est précisément ce
qui donne sa valeur au document.

## Signaler une erreur

Une erreur de droit dans ce fichier est un défaut sérieux. Ouvrez une issue avec
l'article concerné et la source qui vous fait dire que nous nous trompons, ou
écrivez à contact@oriq.fr. La règle du dépôt est « sans source, pas de
modification », et elle vaut aussi pour les corrections qu'on nous propose.

---

Maintenu par [Oriq](https://oriq.fr/), Toulouse.
