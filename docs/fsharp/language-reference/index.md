---
title: Référence du langage
description: 'Recherchez des informations sur les fonctionnalités du langage F # à partir de cette référence vers les jetons de langage, les concepts, les types, les expressions et les rubriques de construction prises en charge par le compilateur.'
ms.date: 05/16/2016
ms.openlocfilehash: 43272c6684c8fc763e8f99611901f35695f48981
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854956"
---
# <a name="f-language-reference"></a>Informations de référence sur le langage F#

Cette section est une référence pour le langage F #, un langage de programmation à plusieurs paradigmes ciblant .NET. Le langage F # prend en charge les modèles de programmation fonctionnel, orienté objet et impératif.

## <a name="f-tokens"></a>Jetons F#

Le tableau suivant répertorie les Articles de référence qui fournissent des tables de mots clés, de symboles et de littéraux utilisés comme jetons en F #.

|Intitulé|Description|
|-----|-----------|
|[Référence des mots clés](keyword-reference.md)|Contient des liens vers des informations sur tous les mots clés du langage F#.|
|[Informations de référence des symboles et opérateurs](./symbol-and-operator-reference/index.md)|Contient un tableau des symboles et des opérateurs utilisés en langage F#.|
|[Littéraux](literals.md)|Décrit la syntaxe des valeurs littérales en F# et comment spécifier des informations de type pour les littéraux F#.|

## <a name="f-language-concepts"></a>Concepts du langage F#

Le tableau suivant liste les rubriques de référence disponibles qui décrivent les concepts du langage.

|Intitulé|Description|
|-----|-----------|
|[Fonctions](./functions/index.md)|Les fonctions sont l’unité fondamentale de l’exécution d’un programme dans tout langage de programmation. Comme dans d’autres langages, une fonction F# a un nom, peut avoir des paramètres et accepter des arguments, et contient un corps. F# prend également en charge des constructions de programmation fonctionnelle, telles que le traitement des fonctions comme valeurs, l’utilisation de fonctions sans nom dans les expressions, la composition de fonctions pour former de nouvelles fonctions, les fonctions curryfiées et la définition implicite de fonctions par l’intermédiaire de l’application partielle d’arguments de fonction.|
|[Types F#](fsharp-types.md)|Décrit les types utilisés en F# et explique comment les types F# sont nommés et décrits.|
|[Inférence de type](type-inference.md)|Décrit comment le compilateur F # déduit les types de valeurs, de variables, de paramètres et de valeurs de retour.|
|[Généralisation automatique](./generics/automatic-generalization.md)|Décrit les constructions génériques en F#.|
|[Héritage](inheritance.md)|Décrit l’héritage, qui est utilisé pour modéliser la relation « is-a » (est-un), ou sous-typage, dans la programmation orientée objet.|
|[Membres](./members/index.md)|Décrit les membres de types d’objet F#.|
|[Paramètres et arguments](Parameters-and-Arguments.md)|Décrit la prise en charge du langage pour la définition de paramètres et le passage d’arguments à des fonctions, méthodes et propriétés. Elle comprend des informations sur le passage par référence.|
|[Surcharge d’opérateur](operator-overloading.md)|Décrit comment surcharger des opérateurs arithmétiques dans un type classe ou d’enregistrement, et au niveau global.|
|[Cast et conversions](casting-and-conversions.md)|Décrit la prise en charge pour les conversions de type en F#.|
|[Access Control](access-control.md)|Décrit le contrôle d’accès en F#. Le contrôle d’accès signifie déclarer quels clients sont en mesure d’utiliser certains éléments de programme, tels que des types, des méthodes, des fonctions, etc.|
|[Critères spéciaux](pattern-matching.md)|Décrit les modèles, qui sont des règles de transformation des données d’entrée et qui sont utilisés dans tout le langage F #. Vous pouvez comparer des données avec un modèle, décomposer des données en parties constituantes ou extraire des informations de données de différentes façons.|
|[Modèles actifs](active-patterns.md)|Décrit des modèles actifs. Les modèles actifs vous permettent de définir des partitions nommées qui subdivisent les données d’entrée. Vous pouvez utiliser des modèles actifs pour décomposer des données de façon personnalisée pour chaque partition.|
|[Assertions](assertions.md)|Décrit l’expression `assert`, qui est une fonctionnalité de débogage que vous pouvez utiliser pour tester une expression. En cas d’échec en mode débogage, une assertion génère une boîte de dialogue d’erreur système.|
|[Gestion des exceptions](./exception-handling/index.md)|Contient des informations sur la prise en charge de la gestion des exceptions en langage F#.|
|[attributes](attributes.md)|Décrit les attributs, qui activent les métadonnées à appliquer à une construction de programmation.|
|[Gestion des ressources : mot clé `use`](resource-management-the-use-keyword.md)|Décrit les mots clés `use` et `using` qui peuvent contrôler l’initialisation et la libération de ressources.|
|[namespaces](namespaces.md)|Décrit la prise en charge des espaces de noms en F#. Un espace de noms vous permet d’organiser le code en zones de fonctionnalités connexes. Pour cela, vous attachez un nom à un regroupement d’éléments de programme.|
|[Modules](modules.md)|Décrit les modules. Un module F# est un regroupement de segments de code F#, notamment des valeurs, des types et des valeurs de fonction, dans un programme F#. Le regroupement de code en modules vous permet de centraliser le code connexe et d’éviter les conflits de nom dans votre programme.|
|[Déclarations d’importation : mot clé `open`](import-declarations-the-open-keyword.md)|Décrit comment `open` fonctionne. Une déclaration d’importation spécifie un module ou un espace de noms dont vous pouvez référencer les éléments sans utiliser de nom qualifié complet.|
|[Signatures](signature-files.md)|Décrit les signatures et les fichiers de signature. Un fichier de signature contient des informations sur les signatures publiques d’un jeu d’éléments de programme F#, tels que des types, des espaces de noms et des modules. Il peut être utilisé pour spécifier l’accessibilité de ces éléments de programme.|
|[Documentation XML](xml-documentation.md)|Décrit la prise en charge de la génération de fichiers de documentation pour des commentaires de document XML, aussi appelés commentaires avec triple barre oblique. Vous pouvez produire une documentation à partir de commentaires de code en F #, comme dans d’autres langages .NET.|
|[Syntaxe détaillée](verbose-syntax.md)|Décrit la syntaxe des constructions F# quand la syntaxe simplifiée n’est pas activée. La syntaxe détaillée est indiquée par la directive `#light "off"` en haut du fichier de code.|
|[Mise en forme de texte brut](plaintext-formatting.md)|Découvrez comment utiliser sprintf et une autre mise en forme de texte brut dans des scripts et des applications F #.|

## <a name="f-types"></a>Types F#

Le tableau suivant répertorie les rubriques de référence disponibles qui décrivent les types pris en charge par le langage F#.

|Intitulé|Description|
|-----|-----------|
|[valeurs](./values/index.md)|Décrit les valeurs, qui sont des quantités immuables de type spécifique ; les valeurs peuvent être des nombres intégraux ou à virgule flottante, des caractères ou du texte, des listes, des séquences, des tableaux, des tuples, des unions discriminées, des enregistrements, des types de classe ou des valeurs de fonction.|
|[Types de base](basic-types.md)|Décrit les types de base fondamentaux utilisés dans le langage F #. Elle fournit également les types .NET correspondants et les valeurs minimales et maximales pour chaque type.|
|[Unit, type](unit-type.md)|Décrit le type `unit`, qui est un type qui indique l’absence d’une valeur spécifique ; le type `unit` n’a qu’une valeur unique, qui joue le rôle d’espace réservé quand aucune autre valeur n’existe ou n’est exigée.|
|[Chaînes](strings.md)|Décrit les chaînes en F#. Le type `string` représente le texte immuable en tant que séquence de caractères Unicode. `string` est un alias pour `System.String` dans le .NET Framework.|
|[Tuples](tuples.md)|Décrit les tuples, qui sont des regroupements de valeurs sans nom, mais ordonnées, de types pouvant être différents.|
|[Types de collection F#](fsharp-collection-types.md)|Vue d’ensemble des types de collection fonctionnels F#, notamment les types pour les tableaux, listes, séquences (seq), cartes et jeux.|
|[Listes](lists.md)|Décrit les listes. En F#, une liste est une série immuable et ordonnée d’éléments du même type.|
|[Options](options.md)|Décrit le type d’option. En F#, une option est utilisée quand une valeur peut ou non exister. Une option a un type sous-jacent et peut soit contenir une valeur de ce type, soit ne pas avoir de valeur.|
|[Séquences](sequences.md)|Décrit les séquences. Une séquence est une série logique d’éléments d’un même type. Les éléments de séquence individuels sont calculés uniquement si nécessaire, si bien que la représentation peut être plus petite que le nombre d’éléments littéraux.|
|[Tableaux](arrays.md)|Décrit les tableaux. Les tableaux sont des séquences de taille fixe, de base zéro et mutables d’éléments de données consécutifs, tous du même type.|
|[Documents](records.md)|Décrit les enregistrements. Les enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.|
|[Unions discriminées](discriminated-unions.md)|Décrit les unions discriminées, qui assurent la prise en charge des valeurs pouvant être une variété de cas nommés, chacun avec des valeurs et des types éventuellement différents.|
|[Énumérations](enumerations.md)|Explique que les énumérations sont des types qui ont un jeu défini de valeurs nommées. Vous pouvez les utiliser à la place de littéraux pour rendre le code plus lisible et plus facile à gérer.|
|[Cellules de référence](reference-cells.md)|Décrit les cellules de référence, qui sont des emplacements de stockage vous permettant de créer des variables mutables avec la sémantique de référence.|
|[Abréviations de types](type-abbreviations.md)|Décrit les abréviations de type, qui sont d’autres noms pour les types.|
|[Classes](classes.md)|Décrit les classes, qui sont des types représentant des objets qui peuvent avoir des propriétés, des méthodes et des événements.|
|[Structures](structures.md)|Décrit les structures, qui sont des types d’objet compacts pouvant se révéler plus efficaces qu’une classe pour les types ayant une petite quantité de données et un comportement simple.|
|[Interfaces](interfaces.md)|Décrit les interfaces, qui spécifient les jeux de membres connexes implémentés par une autre classe.|
|[Classes abstraites](abstract-classes.md)|Décrit les classes abstraites, qui sont des classes qui laissent une partie ou la totalité des membres non implémentés, de manière à ce que les implémentations puissent être fournies par des classes dérivées.|
|[Extensions de type](type-extensions.md)|Décrit les extensions de type, qui vous permettent d’ajouter de nouveaux membres à un type d’objet précédemment défini.|
|[Types flexibles](flexible-types.md)|Décrit les types flexibles. Une annotation de type flexible est une indication qu’un paramètre, une variable ou une valeur a un type qui est compatible avec le type spécifié, où la compatibilité est déterminée par la position dans une hiérarchie orientée objet de classes ou d’interfaces.|
|[Délégués](delegates.md)|Décrit les délégués, qui représentent un appel de fonction comme objet.|
|[Unités de mesure](units-of-measure.md)|Décrit les unités de mesure. En F#, les valeurs à virgule flottante peuvent avoir des unités de mesure associées, qui sont généralement utilisées pour indiquer la longueur, le volume, la masse, etc.|
|[Fournisseurs de type](../tutorials/type-providers/index.md)|Décrit les fournisseurs de type et fournit des liens vers des procédures pas à pas sur l’utilisation des fournisseurs de type intégrés pour accéder à des bases de données et à des services web.|

## <a name="f-expressions"></a>Expressions F#

Le tableau suivant répertorie les rubriques qui décrivent les expressions F#.

|Intitulé|Description|
|-----|-----------|
|[Expressions conditionnelles :`if...then...else`](conditional-expressions-if-then-else.md)|Décrit l’expression `if...then...else`, qui exécute différentes branches de code et qui prend une valeur différente selon l’expression booléenne donnée.|
|[Expressions de correspondance](match-expressions.md)|Décrit l’expression `match`, qui fournit le contrôle de branchement basé sur la comparaison d’une expression à un jeu de modèles.|
|[Boucles : expression `for...to`](loops-for-to-expression.md)|Décrit l’expression `for...to`, qui est utilisée pour itérer en boucle au sein d’une plage de valeurs d’une variable de boucle.|
|[Boucles : expression `for...in`](loops-for-in-expression.md)|Décrit l’expression `for...in`, une construction en boucle utilisée pour itérer au sein des correspondances d’un modèle dans une collection énumérable telle qu’une expression de plage, une séquence, une liste, un tableau ou une autre construction qui prend en charge l’énumération.|
|[Boucles : expression `while...do`](loops-while-do-expression.md)|Décrit l’expression `while...do`, qui est utilisée pour exécuter l’exécution itérative (boucle) quand une condition de test spécifiée a la valeur true.|
|[Expressions d'objet](object-expressions.md)|Décrit les expressions d’objet, qui sont des expressions qui créent des instances d’un type d’objet créé dynamiquement, anonyme et basé sur un type de base, une interface ou un jeu d’interfaces existant.|
|[Expressions différées](lazy-expressions.md)|Décrit les expressions tardives, qui sont des calculs qui ne sont pas évalués immédiatement, mais qui sont à la place évalués lorsque le résultat est réellement nécessaire.|
|[Expressions de calcul](computation-expressions.md)|Décrit des expressions de calcul en F# qui fournissent une syntaxe pratique pour l’écriture de calculs qui peuvent être séquencés et combinés à l’aide de liaisons et de constructions de flux de contrôle. Ils peuvent être utilisés pour fournir une syntaxe pratique pour *monades*, une fonctionnalité de programmation fonctionnelle qui peut être utilisée pour gérer les données, le contrôle et les effets secondaires dans les programmes fonctionnels. Un type d’expression de calcul, le flux de travail asynchrone, assure la prise en charge des calculs asynchrones et parallèles. Pour plus d’informations, consultez [Flux de travail asynchrones](asynchronous-workflows.md).|
|[Workflows asynchrones](asynchronous-workflows.md)|Décrit les flux de travail asynchrones, fonctionnalité de langage qui vous permet d’écrire du code asynchrone d’une façon très proche de l’écriture naturelle de code synchrone.|
|[Quotations de code](code-quotations.md)|Décrit les quotations de code, fonctionnalité de langage qui vous permet de générer et d’utiliser des expressions de code F# par programmation.|
|[Expressions de requête](query-expressions.md)|Décrit les expressions de requête, fonctionnalité de langage qui implémente LINQ pour F# et vous permet d’écrire des requêtes sur une source de données ou une collection énumérable.|

## <a name="compiler-supported-constructs"></a>Constructions prises en charge par le compilateur

Le tableau suivant liste les rubriques qui décrivent des constructions spéciales prises en charge par le compilateur.

|Rubrique|Description|
|-----|-----------|
|[Options du compilateur](compiler-options.md)|Décrit les options de ligne de commande du compilateur F#.|
|[Directives de compilateur](compiler-directives.md)|Décrit les directives de processeur et de compilateur.|
|[Identificateurs de ligne, de fichier et de chemin source](source-line-file-path-identifiers.md)|Décrit les identificateurs `__LINE__` , `__SOURCE_DIRECTORY__` , et `__SOURCE_FILE__` , qui sont des valeurs intégrées qui vous permettent d’accéder au numéro de ligne source, au répertoire et au nom de fichier dans votre code.|
