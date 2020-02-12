---
title: Visite guidée de F#
description: Examiner certaines des fonctionnalités clés de la langue dans cette visite guidée avec exemples de code de programmation F#.
ms.date: 02/09/2020
ms.openlocfilehash: ac2eef40e2dbc494e41a9760f0a70edb0f7ce399
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124570"
---
# <a name="tour-of-f"></a>Présentation de F\#

La meilleure façon d’en savoir plus sur F# consiste à lire et écrire du code F#. Cet article sera agissent comme une visite guidée de certaines des fonctionnalités clés du langage F# et vous donner quelques extraits de code que vous pouvez exécuter sur votre ordinateur. Pour en savoir plus sur la configuration d’un environnement de développement, consultez [prise en main](get-started/index.md).

Il existe deux concepts principaux en F#: les types et les fonctions.  Cette visite guidée met en évidence les fonctionnalités du langage qui entrent dans ces deux concepts.

## <a name="executing-the-code-online"></a>Exécution du code en ligne

Si vous n’avez F# pas installé sur votre ordinateur, vous pouvez exécuter tous les exemples de votre navigateur à l’aide de l' [instruction try F# sur webassembly](https://tryfsharp.fsbolero.io/). Fable est un dialecte F# de qui s’exécute directement dans votre navigateur. Pour afficher les exemples qui suivent dans les exemples REPL, consultez les **exemples > en savoir plus F# > présentation de** dans la barre de menus de gauche de la réplication fable.

## <a name="functions-and-modules"></a>Fonctions et modules

Les éléments essentiels de n’importe quel programme F# sont ***fonctions*** organisées en ***modules***.  [Fonctions](./language-reference/functions/index.md) effectuer le travail sur les entrées pour produire des sorties, et ils sont organisés sous [Modules](./language-reference/modules.md), qui sont le principal moyen de regrouper de choses en F#.  Ils sont définis à l’aide de la [liaison`let`](./language-reference/functions/let-bindings.md), qui donne un nom à la fonction et définit ses arguments.

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

les liaisons de `let` sont également la manière dont vous liez une valeur à un nom, semblable à une variable dans d’autres langages.  les liaisons `let` sont ***immuables*** par défaut, ce qui signifie qu’il n’est pas possible de modifier sur place une fois qu’une valeur ou une fonction est liée à un nom.  Cela diffère des variables dans d’autres langages, qui sont ***mutables***, ce qui signifie que leurs valeurs peuvent être modifiées à tout moment.  Si vous avez besoin d’une liaison mutable, vous pouvez utiliser la syntaxe `let mutable ...`.

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Nombres, booléens et chaînes

Comme un langage .NET, F# prend en charge même sous-jacent [types primitifs](language-reference/basic-types.md) qui existent dans .NET.

Voici comment différents types numériques sont représentées en F#:

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

Voici à quoi ressemblent les valeurs booléennes et l’exécution de la logique conditionnelle de base :

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

Et voici à quoi ressemble la manipulation de [chaînes](./language-reference/strings.md) de base :

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuples

[Tuples](./language-reference/tuples.md) sont considérables en F#.  Il s’agit d’un regroupement de valeurs sans nom, mais ordonnées, qui peuvent être traitées comme des valeurs elles-mêmes.  Considérez-les comme des valeurs agrégées à partir d’autres valeurs.  Elles ont de nombreuses utilisations, telles que le retour de plusieurs valeurs à partir d’une fonction ou le regroupement de valeurs pour une pratique ad hoc.

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

Vous pouvez également créer des `struct` des tuples.  Ils interagissent également avec les tuples C# 7/Visual Basic 15, qui sont également `struct` des tuples :

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

Il est important de noter que, dans la mesure où `struct` tuples sont des types valeur, ils ne peuvent pas être convertis implicitement en tuples de référence, ou vice versa.  Vous devez effectuer une conversion explicite entre une référence et un tuple de struct.

## <a name="pipelines-and-composition"></a>Pipelines et composition

Diriger des opérateurs tels que `|>` sont largement utilisées lors du traitement des données en F#. Ces opérateurs sont des fonctions qui vous permettent d’établir des « pipelines » de fonctions de manière flexible. L’exemple suivant explique comment tirer parti de ces opérateurs pour créer un pipeline fonctionnel simple :

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

L’exemple précédent apportée utiliser de nombreuses fonctionnalités de F#, y compris les fonctions de traitement de liste, les fonctions de première classe, et [application partielle](./language-reference/functions/index.md#partial-application-of-arguments). Bien qu’une connaissance approfondie de chacun de ces concepts puisse devenir un peu plus complexe, il doit être clair que les fonctions peuvent facilement être utilisées pour traiter les données lors de la création de pipelines.

## <a name="lists-arrays-and-sequences"></a>Listes, tableaux et séquences

Listes, tableaux et séquences existe trois types de collection principale dans la bibliothèque principale F#.

Les [listes](./language-reference/lists.md) sont des collections ordonnées et immuables d’éléments du même type.  Il s’agit de listes à liaison unique, ce qui signifie qu’elles sont destinées à l’énumération, mais qu’il s’agit d’un mauvais choix pour l’accès aléatoire et la concaténation si elles sont volumineuses.  Cela diffère des listes dans d’autres langages populaires, qui n’utilisent généralement pas une liste à liaison unique pour représenter des listes.

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

Les [tableaux](./language-reference/arrays.md) sont des collections de taille fixe et *mutables* d’éléments du même type.  Ils prennent en charge un accès aléatoire rapide d’éléments et sont plus rapides que les listes F#, car elles sont simplement contiguës blocs de mémoire.

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

Les [séquences](./language-reference/sequences.md) sont une série logique d’éléments, tous du même type.  Il s’agit d’un type plus général que des listes et des tableaux, qui peuvent être votre « vue » dans une série logique d’éléments.  Ils sont également dépendants, car ils peuvent être ***paresseux***, ce qui signifie que les éléments ne peuvent être calculés que lorsqu’ils sont nécessaires.

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Fonctions récursives

Le traitement des collections ou des séquences d’éléments est généralement effectué avec [récursivité](./language-reference/functions/index.md#recursive-functions) en F#.  Bien que F# offre la prise en charge des boucles et la programmation impérative, la récursivité est préférée, car il est plus facile de garantir l’exactitude.

> [!NOTE]
> L’exemple suivant utilise les critères spéciaux à l’aide de l’expression `match`.  Cette construction fondamentale est traitée plus loin dans cet article.

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

F# a également une prise en charge complète pour l’optimisation d’appel Tail, qui est une façon d’optimiser les appels récursifs afin qu’ils soient tout aussi rapides comme une construction en boucle.

## <a name="record-and-discriminated-union-types"></a>Enregistrements et types d’union discriminée

Enregistrement et types Union sont deux types de données fondamentaux utilisés dans le code F# et sont généralement la meilleure façon de représenter les données dans un programme F#.  Bien que cela les rend similaires aux classes dans d’autres langages, l’une de leurs principales différences est qu’elles ont une sémantique d’égalité structurelle.  Cela signifie qu’elles sont comparables en mode « natif » et que l’égalité est simple. il suffit de vérifier si l’une d’entre elles est égale à l’autre.

Les [enregistrements](./language-reference/records.md) sont un agrégat des valeurs nommées, avec des membres facultatifs (tels que des méthodes).  Si vous êtes familiarisé avec C# ou Java, ceux-ci doivent ressembler à des poco ou à des POJO, tout simplement avec l’égalité structurelle et une cérémonie moins importante.

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

Vous pouvez également représenter des enregistrements comme des structs. Cette opération s’effectue avec l’attribut `[<Struct>]` :

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

Les [unions discriminées (unions discriminées)](./language-reference/discriminated-unions.md) sont des valeurs qui peuvent être un certain nombre de formulaires ou de cas nommés.  Les données stockées dans le type peuvent être de l’une des différentes valeurs distinctes.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

Vous pouvez également utiliser unions discriminées comme *unions discriminées à cas unique*, pour faciliter la modélisation de domaine sur des types primitifs.  Souvent, les chaînes et d’autres types primitifs sont utilisés pour représenter un résultat, et ont donc une signification particulière.  Toutefois, l’utilisation de la représentation primitive des données uniquement peut entraîner l’attribution par erreur d’une valeur incorrecte.  La représentation de chaque type d’informations sous la forme d’une Union distincte à cas unique peut garantir l’exactitude dans ce scénario.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

Comme le montre l’exemple ci-dessus, pour obtenir la valeur sous-jacente dans une union discriminée à cas unique, vous devez la désencapsuler explicitement.

En outre, unions discriminées prend également en charge les définitions récursives, ce qui vous permet de représenter facilement des arborescences et des données récursives par nature.  Par exemple, voici comment vous pouvez représenter un arbre de recherche binaire avec les fonctions `exists` et `insert`.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

Étant donné que unions discriminées vous permet de représenter la structure récursive de l’arborescence dans le type de données, l’utilisation de cette structure récursive est simple et garantit l’exactitude.  Il est également pris en charge dans les critères spéciaux, comme indiqué ci-dessous.

En outre, vous pouvez représenter unions discriminées comme `struct`s avec l’attribut `[<Struct>]` :

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

Toutefois, il y a deux points importants à garder à l’esprit quand vous procédez ainsi :

1. Un struct DU ne peut pas être défini de manière récursive.
2. Un struct DU doit avoir des noms uniques pour chacun de ses cas.

Si vous ne suivez pas le problème ci-dessus, une erreur de compilation se produit.

## <a name="pattern-matching"></a>Critères spéciaux

[Correspondance de modèle](./language-reference/pattern-matching.md) est la fonctionnalité du langage F# qui est correct pour l’exploitation de types F#.  Dans les exemples ci-dessus, vous avez probablement remarqué un peu de `match x with ...` syntaxe.  Cette construction autorise le compilateur, qui peut comprendre la « forme » des types de données, pour vous obliger à tenir compte de tous les cas possibles lors de l’utilisation d’un type de données via ce qui est connu sous le nom de critères spéciaux exhaustifs.  Cela est incroyablement puissant et peut être utilisé pour « élever » ce qui devrait normalement être une préoccupation du Runtime au moment de la compilation.

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

Vous avez peut-être remarqué l’utilisation du modèle de `_`.  C’est ce que l’on appelle le [modèle de caractère générique](./language-reference/pattern-matching.md#wildcard-pattern), qui est un moyen de dire « je ne me préoccupe pas de quoi ».  Bien que pratique, vous pouvez contourner accidentellement une correspondance de modèle exhaustive et ne plus tirer parti des mises en œuvre au moment de la compilation si vous n’êtes pas prudent dans l’utilisation de `_`.  Il est préférable de l’utiliser lorsque vous ne vous souciez pas de certains éléments d’un type décomposé lors de la mise en correspondance d’un modèle ou de la clause finale quand vous avez énuméré tous les cas significatifs dans une expression de critères spéciaux.

Dans l’exemple suivant, le cas de `_` est utilisé en cas d’échec d’une opération d’analyse.

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L744-L762)]

Les [modèles actifs](./language-reference/active-patterns.md) sont une autre construction puissante à utiliser avec les critères spéciaux.  Elles vous permettent de partitionner les données d’entrée dans des formulaires personnalisés, en les décomposant au niveau du site d’appel de correspondance du modèle.  Elles peuvent également être paramétrées, ce qui permet de définir la partition en tant que fonction.  Le développement de l’exemple précédent pour la prise en charge des modèles actifs ressemble à ceci :

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>Types facultatifs

Un cas spécial de types Union discriminée est le Type d’Option, ce qui est donc utile qu’il fait partie de la bibliothèque principale F#.

[Le type d’option](./language-reference/options.md) est un type qui représente l’un des deux cas suivants : une valeur, ou rien du tout.  Il est utilisé dans tout scénario où une valeur peut ou non résulter d’une opération particulière.  Cela vous oblige alors à prendre en compte dans les deux cas, en faisant en sorte qu’il s’agit d’un problème au moment de la compilation plutôt que d’un problème d’exécution.  Elles sont souvent utilisées dans les API où `null` est utilisé pour représenter « Nothing » à la place, ce qui évite d’avoir à se soucier de la `NullReferenceException` dans de nombreux cas.

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Unités de mesure

Une fonctionnalité unique de système de type F# est la possibilité de fournir un contexte pour les littéraux numériques par le biais des unités de mesure.

Les [unités de mesure](./language-reference/units-of-measure.md) vous permettent d’associer un type numérique à une unité, telle que des mètres, et de faire en sorte que les fonctions effectuent le travail sur des unités plutôt que sur des littéraux numériques.  Cela permet au compilateur de vérifier que les types de littéraux numériques passés ont un sens dans un certain contexte, ce qui élimine les erreurs d’exécution associées à ce genre de travail.

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

La bibliothèque principale F# définit plusieurs types d’unités SI et conversions d’unité.  Pour plus d’informations, consultez l' [espace de noms Microsoft.FSharp.Data.UnitSystems.si](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Classes et interfaces

F# offre également une prise en charge complète pour les classes .NET, [Interfaces](./language-reference/interfaces.md), [Classes abstraites](./language-reference/abstract-classes.md), [héritage](./language-reference/inheritance.md), et ainsi de suite.

Les [classes](./language-reference/classes.md) sont des types qui représentent des objets .net, qui peuvent avoir des propriétés, des méthodes et des événements comme [membres](./language-reference/members/index.md).

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

La définition de classes génériques est également très simple.

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

Pour implémenter une interface, vous pouvez utiliser la syntaxe `interface ... with` ou une [expression d’objet](./language-reference/object-expressions.md).

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Types à utiliser

La présence de classes, d’enregistrements, d’unions discriminées et de tuples génère une question importante : que devez-vous utiliser ?  Tout comme la plupart des éléments de la vie, la réponse dépend de vos circonstances.

Les tuples sont très utiles pour retourner plusieurs valeurs à partir d’une fonction, et à l’aide d’un agrégat ad hoc de valeurs en tant que valeur proprement dite.

Les enregistrements sont un « pas à pas détaillé » des tuples, avec des étiquettes nommées et la prise en charge des membres facultatifs.  Elles sont idéales pour une représentation à faible cérémonie des données transitant par votre programme.  Comme elles ont une égalité structurelle, elles sont faciles à utiliser avec la comparaison.

Les unions discriminées ont de nombreuses utilisations, mais l’avantage principal est de pouvoir les utiliser conjointement avec les critères spéciaux pour prendre en compte toutes les « formes » possibles qu’une donnée peut avoir.  

Les classes sont idéales pour un grand nombre de raisons, par exemple lorsque vous devez représenter des informations et associer ces informations à des fonctionnalités.  En règle générale, lorsque vous disposez d’une fonctionnalité qui est conceptuellement liée à certaines données, l’utilisation de classes et des principes de la programmation orientée objet est un grand avantage.  Les classes sont également le type de données par défaut lors C# de l’interopérabilité avec et Visual Basic, car ces langages utilisent des classes pour presque tout.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez vu certaines des principales fonctionnalités du langage, vous devez être prêt à écrire vos premiers programmes F# !  Consultez [prise en main](get-started/index.md) pour savoir comment configurer votre environnement de développement et écrire du code.

Les étapes suivantes pour en savoir plus peuvent être les mêmes que vous le souhaitez, mais nous vous recommandons d' [introduire la programmation fonctionnelle dans F# ](./introduction-to-functional-programming/index.md) pour vous familiariser avec les concepts fondamentaux de la programmation fonctionnelle.  Il s’agira essentielles dans la création de programmes robustes en F#.

Consultez également le [référence du langage F#](./language-reference/index.md) pour voir un ensemble complet de contenu conceptuel sur F#.
