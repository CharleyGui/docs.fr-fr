---
title: Visite guidée de F#
description: Examiner certaines des fonctionnalités clés de la langue dans cette visite guidée avec exemples de code de programmation F#.
ms.date: 11/06/2018
ms.openlocfilehash: 64394342777003b33dd77028739fb7209b9f3c86
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301254"
---
# <a name="tour-of-f"></a>Présentation du langage F\#

La meilleure façon d’en savoir plus sur F# consiste à lire et écrire du code F#. Cet article sera agissent comme une visite guidée de certaines des fonctionnalités clés du langage F# et vous donner quelques extraits de code que vous pouvez exécuter sur votre ordinateur. Pour en savoir plus sur la configuration d’un environnement de développement, consultez [mise en route](tutorials/getting-started/index.md).

Il existe deux concepts principaux en F#: les types et les fonctions.  Cette visite guidée sera mettre l’accent sur les fonctionnalités du langage qui appartiennent à ces deux concepts.

## <a name="executing-the-code-online"></a>L’exécution du code en ligne

Si vous n’avez pas F# installé sur votre ordinateur, vous pouvez exécuter tous les exemples dans votre navigateur avec [essayez F# sur WebAssembly](https://tryfsharp.fsbolero.io/). Fable est un dialecte F# qui s’exécute directement dans votre navigateur. Pour afficher les exemples qui suivent dans la boucle REPL, consultez **exemples > en savoir plus > visite guidée de F#**  dans la barre de menu de gauche de l’intervalle de Fable

## <a name="functions-and-modules"></a>Fonctions et des Modules

Les éléments essentiels de n’importe quel programme F# sont ***fonctions*** organisées en ***modules***.  [Fonctions](language-reference/functions/index.md) effectuer le travail sur les entrées pour produire des sorties, et ils sont organisés sous [Modules](language-reference/modules.md), qui sont le principal moyen de regrouper de choses en F#.  Elles sont définies à l’aide de la [ `let` liaison](language-reference/functions/let-bindings.md), donnez un nom à la fonction et définir ses arguments.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` les liaisons sont également comment vous lier une valeur à un nom, semblable à une variable dans d’autres langages.  `let` les liaisons sont ***immuable*** par défaut, ce qui signifie qu’une fois qu’une valeur ou une fonction est liée à un nom, il ne peut pas être modifié sur place.  Ce comportement diffère variables dans d’autres langues, qui sont ***mutable***, ce qui signifie que leurs valeurs peut être modifié à n’importe quel point dans le temps.  Si vous avez besoin d’une liaison mutable, vous pouvez utiliser `let mutable ...` syntaxe.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Nombres, les valeurs booléennes et les chaînes

Comme un langage .NET, F# prend en charge même sous-jacent [types primitifs](language-reference/primitive-types.md) qui existent dans .NET.

Voici comment différents types numériques sont représentées en F#:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Voici les valeurs booléennes et exécution d’une logique conditionnelle base ressemble à :

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

Et Voici quelles basic [chaîne](language-reference/strings.md) manipulation ressemble à :

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuples

[Tuples](language-reference/tuples.md) sont considérables en F#.  Il s’agit d’un regroupement de valeurs sans nom, mais ordonnées, qui peut être traité en tant que valeurs elles-mêmes.  Imaginez qu’elles en tant que valeurs qui sont agrégées à partir d’autres valeurs.  Ils ont de nombreuses utilisations, telles que facilement retourner plusieurs valeurs à partir d’une fonction ou de regroupement pour des raisons pratiques ad-hoc.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

À compter de F# 4.1, vous pouvez également créer `struct` tuples.  Ces également interagissent entièrement avec C# 7/Visual Basic 15 tuples, qui sont également `struct` tuples :

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

Il est important de noter que, étant donné que `struct` tuples sont des types valeur, ils ne peuvent pas être convertis implicitement pour référencer des tuples, ou vice versa.  Vous devez explicitement convertir entre un tuple de référence et de struct.

## <a name="pipelines-and-composition"></a>Pipelines et Composition

Diriger des opérateurs tels que `|>` sont largement utilisées lors du traitement des données en F#. Ces opérateurs sont des fonctions qui vous permettent d’établir un « pipelines » des fonctions de manière flexible. L’exemple suivant décrit comment vous pouvez tirer parti de ces opérateurs pour créer un pipeline fonctionnel simple :

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L282)]

L’exemple précédent apportée utiliser de nombreuses fonctionnalités de F#, y compris les fonctions de traitement de liste, les fonctions de première classe, et [application partielle](language-reference/functions/index.md#partial-application-of-arguments). Bien qu’une compréhension approfondie de chacun de ces concepts peut devenir un peu avancée, il doit être clair comment facilement les fonctions peuvent être utilisées pour traiter les données lors de la création de pipelines.

## <a name="lists-arrays-and-sequences"></a>Listes, tableaux et séquences

Listes, tableaux et séquences existe trois types de collection principale dans la bibliothèque principale F#.

[Répertorie les](language-reference/lists.md) sont ordonnées, immuables des collections d’éléments du même type.  Ils sont des listes liées uniques, ce qui signifie qu’ils sont destinés à énumération, mais un choix médiocre pour un accès aléatoire et concaténation s’ils sont volumineux.  Cela Contrairement aux listes dans d’autres langages populaires, qui généralement n’utilisent pas une liste liée unique pour représenter les listes.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Tableaux](language-reference/arrays.md) sont de taille fixe, *mutable* collections d’éléments du même type.  Ils prennent en charge un accès aléatoire rapide d’éléments et sont plus rapides que les listes F#, car elles sont simplement contiguës blocs de mémoire.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Séquences](language-reference/sequences.md) sont une série logique d’éléments, tous du même type.  Il s’agit d’un type plus général que les listes et des tableaux, susceptibles d’être votre « vue » dans n’importe quelle série logique d’éléments.  Ils également se démarquent car ils peuvent être ***différé***, ce qui signifie que les éléments peuvent être calculées uniquement lorsqu’elles sont nécessaires.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Fonctions récursives

Le traitement des collections ou des séquences d’éléments est généralement effectué avec [récursivité](language-reference/functions/index.md#recursive-functions) en F#.  Bien que F# offre la prise en charge des boucles et la programmation impérative, la récursivité est préférée, car il est plus facile de garantir l’exactitude.

> [!NOTE]
> L’exemple suivant utilise les critères spéciaux le `match` expression.  Cette construction fondamentale est couvert plus loin dans cet article.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F# a également une prise en charge complète pour l’optimisation d’appel Tail, qui est une façon d’optimiser les appels récursifs afin qu’ils soient tout aussi rapides comme une construction en boucle.

## <a name="record-and-discriminated-union-types"></a>Enregistrement et les Types d’Union discriminée

Enregistrement et types Union sont deux types de données fondamentaux utilisés dans le code F# et sont généralement la meilleure façon de représenter les données dans un programme F#.  Bien que cela les rend semblables aux classes dans d’autres langues, une de leurs principales différences est qu’ils ont une sémantique d’égalité structurelle.  Cela signifie qu’ils sont comparables « en mode natif » et l’égalité est simple : simplement vérifier si un est égal à l’autre.

[Enregistrements](language-reference/records.md) sont un agrégat de valeurs nommées, avec des membres facultatifs (par exemple, les méthodes).  Si vous êtes familiarisé avec c# ou Java, puis ces devraient sembler similaires à oct ou POJO - tout avec l’égalité structurelle et moins de cérémonie.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

À compter de F# 4.1, vous pouvez également représenter des enregistrements sous la forme `struct`s.  Cette opération est effectuée avec la `[<Struct>]` attribut :

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[(DUs) d’Unions discriminées](language-reference/discriminated-unions.md) sont des valeurs qui peut être un nombre de formulaires nommés ou de cas.  Données stockées dans le type peuvent être une de plusieurs valeurs distinctes.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Vous pouvez également utiliser DUs en tant que *Unions discriminées de cas unique*, pour faciliter la modélisation sur les types primitifs de domaine.  Souvent, les chaînes et autres types primitifs sont utilisés pour représenter un élément et bénéficient ainsi d’une signification particulière.  Toutefois, l’utilisation uniquement la primitive représentation des données peut entraîner par inadvertance affectation d’une valeur incorrecte !  Représentant chaque type d’informations sous la forme d’une union de cas unique distincte peut imposer l’exactitude dans ce scénario.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Comme illustré dans l’exemple ci-dessus, pour obtenir la valeur sous-jacente dans un cas unique Union discriminée, vous devez le déballer explicitement.

En outre, DUs prennent également en charge les définitions récursives, ce qui vous permet de représenter facilement des arborescences et, par nature, les données récursives.  Par exemple, voici comment vous pouvez représenter une arborescence de recherche binaire avec `exists` et `insert` fonctions.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Étant donné que DUs vous autorisent à représenter la structure récursive de l’arborescence dans le type de données, d’exploitation sur cette structure récursive est simple et garantit l’exactitude.  Il est également pris en charge dans les critères spéciaux, comme indiqué ci-dessous.

En outre, vous pouvez représenter DUs en tant que `struct`s avec la `[<Struct>]` attribut :

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

Toutefois, il existe deux éléments clés à prendre en compte lorsque vous procédez ainsi :

1. Un struct de base de données ne peut pas être défini de manière récursive.
2. Un struct est FACTURÉE possèdent des noms uniques pour chacun de ses cas.

Suivez la méthode ci-dessus entraîne une erreur de compilation.

## <a name="pattern-matching"></a>Critères spéciaux

[Correspondance de modèle](language-reference/pattern-matching.md) est la fonctionnalité du langage F# qui est correct pour l’exploitation de types F#.  Dans les exemples ci-dessus, vous avez probablement remarqué un peu de `match x with ...` syntaxe.  Cette construction permet au compilateur, ce qui peut comprendre la « forme » des types de données, à vous obliger à prendre en compte pour tous les cas possibles lors de l’utilisation d’un type de données via ce qui est connu comme Exhaustive des critères spéciaux.  Cela est incroyablement puissante est correcte et peut être intelligemment à « élèvent » ce qui serait normalement pas un problème d’exécution dans la compilation.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L742)]

Quelque chose que vous avez peut-être remarqué est l’utilisation de la `_` modèle.  Il s’agit du [modèle de caractère générique](language-reference/pattern-matching.md#wildcard-pattern), qui est une façon de dire « Peu importe ce que quelque chose est ».  Bien que pratique, vous pouvez accidentellement contourner Exhaustive des critères spéciaux et ne bénéficie plus des mises en conformité de la compilation si vous ne faites pas attention à l’aide de `_`.  Il est particulièrement adapté lorsque vous ne vous souciez certains éléments d’un type décomposé lorsque modèle mise en correspondance ou la clause finale lorsque vous avez énuméré tous les cas significatives dans une expression de critères spéciaux.

[Modèles actifs](language-reference/active-patterns.md) sont une autre construction puissants à utiliser avec les critères spéciaux.  Ils permettent de partitionner les données d’entrée de formulaires personnalisés, les décomposer au site d’appel de correspondance de modèle.  Ils peuvent également être paramétrés, ce qui permet de définir la partition en tant que fonction.  Développe l’exemple précédent pour prendre en charge les modèles actifs ressemble à ceci :

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>Types facultatifs

Un cas spécial de types Union discriminée est le Type d’Option, ce qui est donc utile qu’il fait partie de la bibliothèque principale F#.

[Le Type d’Option](language-reference/options.md) est un type qui représente un des deux cas : une valeur ou rien du tout.  Il est utilisé dans les scénarios où une valeur peut ou ne peut-être pas provenir d’une opération particulière.  Cela force ensuite pour prendre en compte les deux cas, en rendant un problème lors de la compilation plutôt que d’un problème d’exécution.  Ceux-ci sont souvent utilisés dans les API où `null` est utilisé pour représenter « nothing » au lieu de cela, ce qui évite à vous soucier `NullReferenceException` dans de nombreux cas.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Unités de mesure

Une fonctionnalité unique de système de type F# est la possibilité de fournir un contexte pour les littéraux numériques par le biais des unités de mesure.

[Unités de mesure](language-reference/units-of-measure.md) vous permettent d’associer un type numérique à une unité, par exemple, en mètres, et ont les fonctions ne fonctionnent sur les unités au lieu de littéraux numériques.  Cela permet au compilateur vérifier que les types de littéraux numériques passés dans les sens sous un contexte particulier, ce qui évite des erreurs d’exécution associé à ce type de travail.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L817-L842)]

La bibliothèque principale F# définit plusieurs types d’unités SI et conversions d’unité.  Pour plus d’informations, consultez le [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Classes et Interfaces

F# offre également une prise en charge complète pour les classes .NET, [Interfaces](language-reference/interfaces.md), [Classes abstraites](language-reference/abstract-classes.md), [héritage](language-reference/inheritance.md), et ainsi de suite.

[Classes](language-reference/classes.md) sont des types qui représentent des objets .NET, qui peut avoir des propriétés, méthodes et événements en tant que son [membres](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L845-L880)]

Définition des classes génériques est également très simple.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L883-L908)]

Pour implémenter une Interface, vous pouvez utiliser `interface ... with` syntaxe ou un [Expression d’objet](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Les Types à utiliser

La présence de Classes, les enregistrements, les Unions discriminées et les Tuples mène à une question importante : lequel devez-vous utiliser ?  Comme pour la plupart des tout dans la vie, la réponse dépend de votre situation.

Les tuples sont exceptionnelles afin de retourner plusieurs valeurs à partir d’une fonction et à l’aide d’un agrégat ad-hoc de valeurs en tant que valeur lui-même.

Les enregistrements sont un « step up » à partir de Tuples, avoir nommé étiquettes et la prise en charge des membres facultatifs.  Elles sont idéales pour une représentation sous forme de cérémonie de faible des données en transit via votre programme.  Parce qu’ils ont l’égalité structurelle, ils sont faciles à utiliser avec la comparaison.

Les Unions discriminées ont de nombreuses utilisations, mais les principaux avantages sont de pouvoir les utiliser conjointement avec les critères spéciaux pour prendre en compte pour toutes les possibles « formes » disposant de données.  

Les classes sont idéales pour un très grand nombre de raisons, par exemple lorsque vous devez représentent des informations et également comment lier ces informations à la fonctionnalité.  En règle générale, lorsque vous disposez de fonctionnalités sur le plan conceptuel lié à des données, à l’aide des Classes et les principes de programmation orientée objet est un grand avantage.  Les classes sont également le type de données par défaut lors de l’interaction avec c# et Visual Basic, comme ces langues utilisent des classes pour quasiment tous les éléments.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez vu certaines des principales fonctionnalités du langage, vous devez être prêt à écrire vos premiers programmes F# !  Découvrez [mise en route](tutorials/getting-started/index.md) pour savoir comment configurer votre environnement de développement et d’écrire du code.

Les étapes suivantes pour en savoir plus peuvent être comme vous le souhaitez, mais nous vous recommandons de [Introduction à la programmation fonctionnelle dans F# ](introduction-to-functional-programming/index.md) à se familiariser avec les principaux concepts de programmation fonctionnelle.  Il s’agira essentielles dans la création de programmes robustes en F#.

Consultez également le [référence du langage F#](language-reference/index.md) pour voir un ensemble complet de contenu conceptuel sur F#.
