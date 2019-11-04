---
title: Référence des mots clés
description: Recherchez des liens vers des informations sur tous F# les mots clés du langage.
ms.date: 05/16/2016
ms.openlocfilehash: 2be6d078653a4595cbdfe97be7aab8e3b3c10ea9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425082"
---
# <a name="keyword-reference"></a>Référence des mots clés

Cette rubrique contient des liens vers des informations F# sur tous les mots clés de langage.

## <a name="f-keyword-table"></a>F#Table des mots clés

Le tableau suivant répertorie F# tous les mots clés dans l’ordre alphabétique, ainsi que des descriptions succinctes et des liens vers des rubriques pertinentes qui contiennent plus d’informations.

|Mot clé|Lien|Description|
|-------|----|-----------|
|`abstract`|[Membres](./members/index.md)<br /><br />[Classes abstraites](abstract-classes.md)|Indique une méthode qui n’a aucune implémentation dans le type dans lequel elle est déclarée ou qui est virtuelle et qui a une implémentation par défaut.|
|`and`|[Liaisons de `let`](./functions/let-bindings.md)<br /><br />[Enregistrements](records.md)<br /><br />[Membres](./members/index.md)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé dans les liaisons et les enregistrements mutuellement récursifs, dans les déclarations de propriété et avec plusieurs contraintes sur les paramètres génériques.|
|`as`|[Classes](classes.md)<br /><br />[Critères spéciaux](Pattern-Matching.md)|Utilisé pour attribuer un nom d’objet à l’objet de classe actuel. Permet également de fournir un nom à un modèle entier dans une correspondance de modèle.|
|`assert`|[Assertions](assertions.md)|Utilisé pour vérifier le code pendant le débogage.|
|`base`|[Classes](classes.md)<br /><br />[Héritage](inheritance.md)|Utilisé comme nom de l’objet de classe de base.|
|`begin`|[Syntaxe détaillée](verbose-syntax.md)|En syntaxe détaillée, indique le début d’un bloc de code.|
|`class`|[Classes](classes.md)|En syntaxe détaillée, indique le début d’une définition de classe.|
|`default`|[Membres](./members/index.md)|Indique une implémentation d’une méthode abstraite ; utilisé avec une déclaration de méthode abstraite pour créer une méthode virtuelle.|
|`delegate`|[Délégués](delegates.md)|Utilisé pour déclarer un délégué.|
|`do`|[Liaisons do](./functions/do-bindings.md)<br /><br />[Boucles : expression `for...to`](loops-for-to-expression.md)<br /><br />[Boucles : expression `for...in`](loops-for-in-expression.md)<br /><br />[Boucles : expression `while...do`](loops-while-do-expression.md)|Utilisé dans les constructions de bouclage ou pour exécuter le code impératif.|
|`done`|[Syntaxe détaillée](verbose-syntax.md)|En syntaxe détaillée, indique la fin d’un bloc de code dans une expression de boucle.|
|`downcast`|[Casts et conversions](casting-and-conversions.md)|Utilisé pour convertir en un type qui est inférieur dans la chaîne d’héritage.|
|`downto`|[Boucles : expression `for...to`](loops-for-to-expression.md)|Dans une expression `for`, utilisée lors du comptage en sens inverse.|
|`elif`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans la branche conditionnelle. Forme abrégée de `else if`.|
|`else`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans la branche conditionnelle.|
|`end`|[Structures](structures.md)<br /><br />[Unions discriminées](discriminated-unions.md)<br /><br />[Enregistrements](records.md)<br /><br />[Extensions de type](type-extensions.md)<br /><br />[Syntaxe détaillée](verbose-syntax.md)|Dans les définitions de type et les extensions de type, indique la fin d’une section de définitions de membre.<br /><br />En syntaxe détaillée, permet de spécifier la fin d’un bloc de code qui commence par le mot clé `begin`.|
|`exception`|[Gestion des exceptions](./exception-handling/index.md)<br /><br />[Types d'exceptions](./exception-handling/exception-types.md)|Utilisé pour déclarer un type d’exception.|
|`extern`|[Fonctions externes](./functions/external-functions.md)|Indique qu’un élément de programme déclaré est défini dans un autre binaire ou assembly.|
|`false`|[Types primitifs](basic-types.md)|Utilisé comme littéral booléen.|
|`finally`|[Exceptions : expression `try...finally`](./exception-handling/the-try-finally-expression.md)|Utilisé avec `try` pour introduire un bloc de code qui s’exécute, qu’une exception se produise ou non.|
|`fixed`|[Des](fixed.md)|Utilisé pour « épingler » un pointeur sur la pile pour l’empêcher d’être récupéré par le garbage collector.|
|`for`|[Boucles : expression `for...to`](loops-for-to-expression.md)<br /><br />[Boucles : expression for...in](loops-for-in-expression.md)|Utilisé dans les constructions de bouclage.|
|`fun`|[Expressions lambda : mot clé `fun`](./functions/lambda-expressions-the-fun-keyword.md)|Utilisé dans les expressions lambda, également appelées fonctions anonymes.|
|`function`|[Expressions match](match-expressions.md)<br /><br />[Expressions lambda : mot clé fun](./functions/lambda-expressions-the-fun-keyword.md)|Utilisé comme une alternative plus petite au mot clé `fun` et à une expression `match` dans une expression lambda qui a des critères spéciaux sur un argument unique.|
|`global`|[Espaces de noms](namespaces.md)|Utilisé pour référencer l’espace de noms .NET de niveau supérieur.|
|`if`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans les constructions de création de branche conditionnelle.|
|`in`|[Boucles : expression for...in](loops-for-in-expression.md)<br /><br />[Syntaxe détaillée](verbose-syntax.md)|Utilisé pour les expressions de séquence et, en syntaxe détaillée, pour séparer les expressions des liaisons.|
|`inherit`|[Héritage](inheritance.md)|Utilisé pour spécifier une classe de base ou une interface de base.|
|`inline`|[Fonctions](./functions/index.md)<br /><br />[Fonctions inline](./functions/inline-functions.md)|Permet d’indiquer une fonction qui doit être intégrée directement dans le code de l’appelant.|
|`interface`|[Interfaces](interfaces.md)|Utilisé pour déclarer et implémenter des interfaces.|
|`internal`|[Contrôle d'accès](access-control.md)|Utilisé pour spécifier qu’un membre est visible à l’intérieur d’un assembly, mais pas à l’extérieur de celui-ci.|
|`lazy`|[Expressions différées](lazy-expressions.md)|Utilisé pour spécifier une expression qui doit être exécutée uniquement lorsqu’un résultat est nécessaire.|
|`let`|[Liaisons de `let`](./functions/let-bindings.md)|Utilisé pour associer ou lier un nom à une valeur ou à une fonction.|
|`let!`|[Flux de travail asynchrones](asynchronous-workflows.md)<br /><br />[Expressions de calcul](computation-expressions.md)|Utilisé dans les flux de travail asynchrones pour lier un nom au résultat d’un calcul asynchrone, ou, dans d’autres expressions de calcul, utilisé pour lier un nom à un résultat, qui est du type de calcul.|
|`match`|[Expressions match](match-expressions.md)|Utilisé pour créer une branche en comparant une valeur à un modèle.|
|`match!`|[Expressions de calcul](computation-expressions.md#match)|Utilisé pour Inline un appel à une expression de calcul et une correspondance de modèle sur son résultat.|
|`member`|[Membres](./members/index.md)|Utilisé pour déclarer une propriété ou une méthode dans un type d’objet.|
|`module`|[Modules](modules.md)|Utilisé pour associer un nom à un groupe de types, valeurs et fonctions connexes, pour le séparer logiquement d’un autre code.|
|`mutable`|[Liaisons let](./functions/let-bindings.md)|Utilisé pour déclarer une variable, c’est-à-dire une valeur qui peut être modifiée.|
|`namespace`|[Espaces de noms](namespaces.md)|Utilisé pour associer un nom à un groupe de types et de modules associés, afin de le séparer logiquement d’un autre code.|
|`new`|[Constructeurs](./members/constructors.md)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé pour déclarer, définir ou appeler un constructeur qui crée ou qui peut créer un objet.<br /><br />Également utilisé dans les contraintes de paramètre générique pour indiquer qu’un type doit avoir un certain constructeur.|
|`not`|[Informations de référence des symboles et opérateurs](./symbol-and-operator-reference/index.md)<br /><br />[Contraintes](./generics/constraints.md)|Il ne s’agit pas d’un mot clé. Toutefois, `not struct` en association est utilisé en tant que contrainte de paramètre générique.|
|`null`|[Valeurs Null](./values/null-values.md)<br /><br />[Contraintes](./generics/constraints.md)|Indique l’absence d’un objet.<br /><br />Également utilisé dans les contraintes de paramètre générique.|
|`of`|[Unions discriminées](discriminated-unions.md)<br /><br />[Délégués](delegates.md)<br /><br />[Types d'exceptions](./exception-handling/exception-types.md)|Utilisé dans les unions discriminées pour indiquer le type des catégories de valeurs et dans les déclarations de délégué et d’exception.|
|`open`|[Déclarations d’importation : mot clé `open`](import-declarations-the-open-keyword.md)|Utilisé pour rendre le contenu d’un espace de noms ou d’un module disponible sans qualification.|
|`or`|[Informations de référence des symboles et opérateurs](./symbol-and-operator-reference/index.md)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé avec des conditions booléennes comme opérateur de `or` booléen. Équivalent à `||`.<br /><br />Également utilisé dans les contraintes de membre.|
|`override`|[Membres](./members/index.md)|Utilisé pour implémenter une version d’une méthode abstraite ou virtuelle qui diffère de la version de base.|
|`private`|[Contrôle d'accès](access-control.md)|Restreint l’accès à un membre au code dans le même type ou module.|
|`public`|[Contrôle d'accès](access-control.md)|Autorise l’accès à un membre à l’extérieur du type.|
|`rec`|[Fonctions](./functions/index.md)|Permet d’indiquer qu’une fonction est récursive.|
|`return`|[Flux de travail asynchrones](Asynchronous-Workflows.md)<br /><br />[Expressions de calcul](computation-expressions.md)|Permet d’indiquer une valeur à fournir comme résultat d’une expression de calcul.|
|`return!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Flux de travail asynchrones](asynchronous-workflows.md)|Permet d’indiquer une expression de calcul qui, lorsqu’elle est évaluée, fournit le résultat de l’expression de calcul conteneur.|
|`select`|[Expressions de requête](query-expressions.md)|Utilisé dans les expressions de requête pour spécifier les champs ou les colonnes à extraire. Notez qu’il s’agit d’un mot clé contextuel, ce qui signifie qu’il ne s’agit pas d’un mot réservé et qu’il agit uniquement comme un mot clé dans le contexte approprié.|
|`static`|[Membres](./members/index.md)|Permet d’indiquer une méthode ou une propriété qui peut être appelée sans instance d’un type, ou un membre de valeur qui est partagé entre toutes les instances d’un type.|
|`struct`|[Structures](structures.md)<br /><br /> [Tuples](tuples.md)<br/><br/>[Contraintes](./generics/constraints.md)|Utilisé pour déclarer un type structure.<br /><br/>Utilisé pour spécifier un tuple de struct.<br/><br />Également utilisé dans les contraintes de paramètre générique.<br /><br />Utilisé pour la compatibilité OCaml dans les définitions de module.|
|`then`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Constructeurs](./members/constructors.md)|Utilisé dans les expressions conditionnelles.<br /><br />Également utilisé pour effectuer des effets secondaires après la construction de l’objet.|
|`to`|[Boucles : expression `for...to`](loops-for-to-expression.md)|Utilisé dans les boucles `for` pour indiquer une plage.|
|`true`|[Types primitifs](basic-types.md)|Utilisé comme littéral booléen.|
|`try`|[Exceptions : le bloc try... Expression with](./exception-handling/the-try-with-expression.md)<br /><br />[Exceptions : le bloc try... Expression finally](./exception-handling/the-try-finally-expression.md)|Utilisé pour introduire un bloc de code susceptible de générer une exception. Utilisé avec `with` ou `finally`.|
|`type`|[Types F#](fsharp-types.md)<br /><br />[Classes](classes.md)<br /><br />[Enregistrements](records.md)<br /><br />[Structures](structures.md)<br /><br />[Énumérations](enumerations.md)<br /><br />[Unions discriminées](discriminated-unions.md)<br /><br />[Abréviations de types](type-abbreviations.md)<br /><br />[Unités de mesure](units-of-measure.md)|Utilisé pour déclarer une classe, un enregistrement, une structure, une union discriminée, un type énumération, une unité de mesure ou une abréviation de type.|
|`upcast`|[Casts et conversions](casting-and-conversions.md)|Utilisé pour convertir en un type qui est plus haut dans la chaîne d’héritage.|
|`use`|[Gestion des ressources : mot clé `use`](resource-management-the-use-keyword.md)|Utilisé à la place de `let` pour les valeurs qui requièrent l’appel de `Dispose` pour libérer des ressources.|
|`use!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Flux de travail asynchrones](asynchronous-workflows.md)|Utilisé à la place de `let!` dans les flux de travail asynchrones et d’autres expressions de calcul pour les valeurs qui requièrent l’appel de `Dispose` pour libérer des ressources.|
|`val`|[Champs explicites : mot clé `val`](./members/explicit-fields-the-val-keyword.md)<br /><br />[Signatures](signature-files.md)<br /><br />[Membres](./members/index.md)|Utilisé dans une signature pour indiquer une valeur, ou dans un type pour déclarer un membre, dans des situations limitées.|
|`void`|[Types primitifs](basic-types.md)|Indique le type de `void` .NET. Utilisé lors de l’interopérabilité avec d’autres langages .NET.|
|`when`|[Contraintes](./generics/constraints.md)|Utilisé pour les conditions booléennes (*lorsque les gardes*) sur les correspondances de modèle et pour introduire une clause de contrainte pour un paramètre de type générique.|
|`while`|[Boucles : expression `while...do`](loops-while-do-expression.md)|Introduit une construction de bouclage.|
|`with`|[Expressions match](match-expressions.md)<br /><br />[Expressions d'objet](object-expressions.md)<br /><br />[Copie et mise à jour des expressions d’enregistrement](copy-and-update-record-expressions.md)<br /><br />[Extensions de type](type-extensions.md)<br /><br />[Exceptions : expression `try...with`](./exception-handling/the-try-with-expression.md)|Utilisé avec le mot clé `match` dans les expressions de critères spéciaux. Également utilisé dans les expressions d’objet, les expressions de copie d’enregistrement et les extensions de type pour introduire des définitions de membres et pour introduire des gestionnaires d’exceptions.|
|`yield`|[Séquences](sequences.md)|Utilisé dans une expression de séquence pour produire une valeur pour une séquence.|
|`yield!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Flux de travail asynchrones](asynchronous-workflows.md)|Utilisé dans une expression de calcul pour ajouter le résultat d’une expression de calcul donnée à une collection de résultats pour l’expression de calcul conteneur.|

Les jetons suivants sont réservés dans F# , car il s’agit de mots clés dans le langage ocaml :

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

Si vous utilisez l’option de compilateur `--mlcompatibility`, les mots clés ci-dessus peuvent être utilisés comme identificateurs.

Les jetons suivants sont réservés en tant que Mots clés pour une expansion F# future du langage :

- `atomic`
- `break`
- `checked`
- `component`
- `const`
- `constraint`
- `constructor`
- `continue`
- `eager`
- `event`
- `external`
- `functor`
- `include`
- `method`
- `mixin`
- `object`
- `parallel`
- `process`
- `protected`
- `pure`
- `sealed`
- `tailcall`
- `trait`
- `virtual`
- `volatile`

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F#](index.md)
- [Informations de référence des symboles et opérateurs](./symbol-and-operator-reference/index.md)
- [Options du compilateur](compiler-options.md)
