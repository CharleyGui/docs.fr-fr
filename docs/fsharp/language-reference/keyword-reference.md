---
title: Référence des mots clés
description: 'Recherchez des liens vers des informations sur tous les mots clés du langage F #.'
f1_keywords:
- new_FS
- use_FS
- end_FS
- lsl_FS
- exception_FS
- asr_FS
- if_FS
- internal_FS
- default_FS
- in_FS
- lsr_FS
- open_FS
- static_FS
- assert_FS
- match_FS
- land_FS
- with_FS
- inherit_FS
- mutable_FS
- downto_FS
- false_FS
- sig_FS
- and_FS
- true_FS
- namespace_FS
- public_FS
- lxor_FS
- val_FS
- void_FS
- downcast_FS
- function_FS
- while_FS
- for_FS
- class_FS
- done_FS
- to_FS
- module_FS
- let_FS
- delegate_FS
- abstract_FS
- then_FS
- when_FS
- lazy_FS
- try_FS
- inline_FS
- do_FS
- upcast_FS
- begin_FS
- base_FS
- fun_FS
- struct_FS
- as_FS
- extern_FS
- null_FS
- lor_FS
- return_FS
- mod_FS
- private_FS
- of_FS
- or_FS
- member_FS
- type_FS
- rec_FS
- elif_FS
- override_FS
- interface_FS
- yield_FS
- else_FS
- finally_FS
- global_FS
- select_FS
- use!_FS
- const_FS
dev_langs:
- FSharp
ms.date: 08/15/2020
ms.openlocfilehash: 15505c123dd0d6497fbc80c8fc9f0910018911ea
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558099"
---
# <a name="keyword-reference"></a>Référence des mots clés

Cette rubrique contient des liens vers des informations sur tous les mots clés du langage F #.

## <a name="f-keyword-table"></a>Tableau de mots clés F #

Le tableau suivant répertorie tous les mots clés F # par ordre alphabétique, ainsi que des descriptions succinctes et des liens vers des rubriques pertinentes qui contiennent davantage d’informations.

|Mot clé|Lien|Description|
|-------|----|-----------|
|`abstract`|[Members](./members/index.md) (Membres)<br /><br />[classes abstraites](abstract-classes.md)|Indique une méthode qui n’a aucune implémentation dans le type dans lequel elle est déclarée ou qui est virtuelle et qui a une implémentation par défaut.|
|`and`|[`let` Liaisons](./functions/let-bindings.md)<br /><br />[Enregistrements](records.md)<br /><br />[Members](./members/index.md) (Membres)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé dans les liaisons et les enregistrements mutuellement récursifs, dans les déclarations de propriété et avec plusieurs contraintes sur les paramètres génériques.|
|`as`|[Classes](classes.md)<br /><br />[Critères spéciaux](Pattern-Matching.md)|Utilisé pour attribuer un nom d’objet à l’objet de classe actuel. Permet également de fournir un nom à un modèle entier dans une correspondance de modèle.|
|`assert`|[Assertions](assertions.md)|Utilisé pour vérifier le code pendant le débogage.|
|`base`|[Classes](classes.md)<br /><br />[Héritage](inheritance.md)|Utilisé comme nom de l’objet de classe de base.|
|`begin`|[Syntaxe détaillée](verbose-syntax.md)|En syntaxe détaillée, indique le début d’un bloc de code.|
|`class`|[Classes](classes.md)|En syntaxe détaillée, indique le début d’une définition de classe.|
|`default`|[Members](./members/index.md) (Membres)|Indique une implémentation d’une méthode abstraite ; utilisé avec une déclaration de méthode abstraite pour créer une méthode virtuelle.|
|`delegate`|[Délégués](delegates.md)|Utilisé pour déclarer un délégué.|
|`do`|[Liaisons do](./functions/do-bindings.md)<br /><br />[Boucles : expression `for...to`](loops-for-to-expression.md)<br /><br />[Boucles : expression `for...in`](loops-for-in-expression.md)<br /><br />[Boucles : expression `while...do`](loops-while-do-expression.md)|Utilisé dans les constructions de bouclage ou pour exécuter le code impératif.|
|`done`|[Syntaxe détaillée](verbose-syntax.md)|En syntaxe détaillée, indique la fin d’un bloc de code dans une expression de boucle.|
|`downcast`|[Cast et conversions](casting-and-conversions.md)|Utilisé pour convertir en un type qui est inférieur dans la chaîne d’héritage.|
|`downto`|[Boucles : expression `for...to`](loops-for-to-expression.md)|Dans une `for` expression, utilisé lors du comptage en sens inverse.|
|`elif`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans la branche conditionnelle. Forme abrégée de `else if` .|
|`else`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans la branche conditionnelle.|
|`end`|[Structures](structures.md)<br /><br />[Unions discriminées](discriminated-unions.md)<br /><br />[Enregistrements](records.md)<br /><br />[Extensions de type](type-extensions.md)<br /><br />[Syntaxe détaillée](verbose-syntax.md)|Dans les définitions de type et les extensions de type, indique la fin d’une section de définitions de membre.<br /><br />En syntaxe détaillée, permet de spécifier la fin d’un bloc de code qui commence par le `begin` mot clé.|
|`exception`|[Gestion des exceptions](./exception-handling/index.md)<br /><br />[Types d'exceptions](./exception-handling/exception-types.md)|Utilisé pour déclarer un type d’exception.|
|`extern`|[Fonctions externes](./functions/external-functions.md)|Indique qu’un élément de programme déclaré est défini dans un autre binaire ou assembly.|
|`false`|[Types primitifs](basic-types.md)|Utilisé comme littéral booléen.|
|`finally`|[Exceptions : expression `try...finally`](./exception-handling/the-try-finally-expression.md)|Utilisé avec `try` pour introduire un bloc de code qui s’exécute, qu’une exception se produise ou non.|
|`fixed`|[Des](fixed.md)|Utilisé pour « épingler » un pointeur sur la pile pour l’empêcher d’être récupéré par le garbage collector.|
|`for`|[Boucles : expression `for...to`](loops-for-to-expression.md)<br /><br />[Boucles : expression for...in](loops-for-in-expression.md)|Utilisé dans les constructions de bouclage.|
|`fun`|[Expressions lambda : `fun` mot clé](./functions/lambda-expressions-the-fun-keyword.md)|Utilisé dans les expressions lambda, également appelées fonctions anonymes.|
|`function`|[Expressions de correspondance](match-expressions.md)<br /><br />[Expressions lambda : mot clé fun](./functions/lambda-expressions-the-fun-keyword.md)|Utilisé comme une alternative plus petite au `fun` mot clé et une `match` expression dans une expression lambda qui a des critères spéciaux sur un argument unique.|
|`global`|[Espaces de noms](namespaces.md)|Utilisé pour référencer l’espace de noms .NET de niveau supérieur.|
|`if`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans les constructions de création de branche conditionnelle.|
|`in`|[Boucles : expression for...in](loops-for-in-expression.md)<br /><br />[Syntaxe détaillée](verbose-syntax.md)|Utilisé pour les expressions de séquence et, en syntaxe détaillée, pour séparer les expressions des liaisons.|
|`inherit`|[Héritage](inheritance.md)|Utilisé pour spécifier une classe de base ou une interface de base.|
|`inline`|[Fonctions](./functions/index.md)<br /><br />[Fonctions inline](./functions/inline-functions.md)|Permet d’indiquer une fonction qui doit être intégrée directement dans le code de l’appelant.|
|`interface`|[Interfaces](interfaces.md)|Utilisé pour déclarer et implémenter des interfaces.|
|`internal`|[Access Control](access-control.md)|Utilisé pour spécifier qu’un membre est visible à l’intérieur d’un assembly, mais pas à l’extérieur de celui-ci.|
|`lazy`|[Expressions différées](lazy-expressions.md)|Utilisé pour spécifier une expression qui doit être exécutée uniquement lorsqu’un résultat est nécessaire.|
|`let`|[`let` Liaisons](./functions/let-bindings.md)|Utilisé pour associer ou lier un nom à une valeur ou à une fonction.|
|`let!`|[Workflows asynchrones](asynchronous-workflows.md)<br /><br />[Expressions de calcul](computation-expressions.md)|Utilisé dans les flux de travail asynchrones pour lier un nom au résultat d’un calcul asynchrone, ou, dans d’autres expressions de calcul, utilisé pour lier un nom à un résultat, qui est du type de calcul.|
|`match`|[Expressions de correspondance](match-expressions.md)|Utilisé pour créer une branche en comparant une valeur à un modèle.|
|`match!`|[Expressions de calcul](computation-expressions.md#match)|Utilisé pour Inline un appel à une expression de calcul et une correspondance de modèle sur son résultat.|
|`member`|[Members](./members/index.md) (Membres)|Utilisé pour déclarer une propriété ou une méthode dans un type d’objet.|
|`module`|[Modules](modules.md)|Utilisé pour associer un nom à un groupe de types, valeurs et fonctions connexes, pour le séparer logiquement d’un autre code.|
|`mutable`|[Liaisons let](./functions/let-bindings.md)|Utilisé pour déclarer une variable, c’est-à-dire une valeur qui peut être modifiée.|
|`namespace`|[Espaces de noms](namespaces.md)|Utilisé pour associer un nom à un groupe de types et de modules associés, afin de le séparer logiquement d’un autre code.|
|`new`|[Constructeurs](./members/constructors.md)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé pour déclarer, définir ou appeler un constructeur qui crée ou qui peut créer un objet.<br /><br />Également utilisé dans les contraintes de paramètre générique pour indiquer qu’un type doit avoir un certain constructeur.|
|`not`|[Informations de référence sur les symboles et les opérateurs](./symbol-and-operator-reference/index.md)<br /><br />[Contraintes](./generics/constraints.md)|Il ne s’agit pas d’un mot clé. Toutefois, `not struct` en combinaison, est utilisé en tant que contrainte de paramètre générique.|
|`null`|[Valeurs null](./values/null-values.md)<br /><br />[Contraintes](./generics/constraints.md)|Indique l’absence d’un objet.<br /><br />Également utilisé dans les contraintes de paramètre générique.|
|`of`|[Unions discriminées](discriminated-unions.md)<br /><br />[Délégués](delegates.md)<br /><br />[Types d'exceptions](./exception-handling/exception-types.md)|Utilisé dans les unions discriminées pour indiquer le type des catégories de valeurs et dans les déclarations de délégué et d’exception.|
|`open`|[Déclarations d’importation : mot clé `open`](import-declarations-the-open-keyword.md)|Utilisé pour rendre le contenu d’un espace de noms ou d’un module disponible sans qualification.|
|`or`|[Informations de référence sur les symboles et les opérateurs](./symbol-and-operator-reference/index.md)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé avec des conditions booléennes comme `or` opérateur booléen. Équivalent à `||`.<br /><br />Également utilisé dans les contraintes de membre.|
|`override`|[Members](./members/index.md) (Membres)|Utilisé pour implémenter une version d’une méthode abstraite ou virtuelle qui diffère de la version de base.|
|`private`|[Access Control](access-control.md)|Restreint l’accès à un membre au code dans le même type ou module.|
|`public`|[Access Control](access-control.md)|Autorise l’accès à un membre à l’extérieur du type.|
|`rec`|[Fonctions](./functions/index.md)|Permet d’indiquer qu’une fonction est récursive.|
|`return`|[Workflows asynchrones](Asynchronous-Workflows.md)<br /><br />[Expressions de calcul](computation-expressions.md)|Permet d’indiquer une valeur à fournir comme résultat d’une expression de calcul.|
|`return!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Workflows asynchrones](asynchronous-workflows.md)|Permet d’indiquer une expression de calcul qui, lorsqu’elle est évaluée, fournit le résultat de l’expression de calcul conteneur.|
|`select`|[Expressions de requête](query-expressions.md)|Utilisé dans les expressions de requête pour spécifier les champs ou les colonnes à extraire. Notez qu’il s’agit d’un mot clé contextuel, ce qui signifie qu’il ne s’agit pas d’un mot réservé et qu’il agit uniquement comme un mot clé dans le contexte approprié.|
|`static`|[Members](./members/index.md) (Membres)|Permet d’indiquer une méthode ou une propriété qui peut être appelée sans instance d’un type, ou un membre de valeur qui est partagé entre toutes les instances d’un type.|
|`struct`|[Structures](structures.md)<br /><br /> [Tuples](tuples.md)<br/><br/>[Contraintes](./generics/constraints.md)|Utilisé pour déclarer un type structure.<br /><br/>Utilisé pour spécifier un tuple de struct.<br/><br />Également utilisé dans les contraintes de paramètre générique.<br /><br />Utilisé pour la compatibilité OCaml dans les définitions de module.|
|`then`|[Expressions conditionnelles : `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Constructeurs](./members/constructors.md)|Utilisé dans les expressions conditionnelles.<br /><br />Également utilisé pour effectuer des effets secondaires après la construction de l’objet.|
|`to`|[Boucles : expression `for...to`](loops-for-to-expression.md)|Utilisé dans les `for` boucles pour indiquer une plage.|
|`true`|[Types primitifs](basic-types.md)|Utilisé comme littéral booléen.|
|`try`|[Exceptions : expression try...with](./exception-handling/the-try-with-expression.md)<br /><br />[Exceptions : expression try...finally](./exception-handling/the-try-finally-expression.md)|Utilisé pour introduire un bloc de code susceptible de générer une exception. Utilisé avec `with` ou `finally` .|
|`type`|[Types F#](fsharp-types.md)<br /><br />[Classes](classes.md)<br /><br />[Enregistrements](records.md)<br /><br />[Structures](structures.md)<br /><br />[Énumérations](enumerations.md)<br /><br />[Unions discriminées](discriminated-unions.md)<br /><br />[Abréviations de types](type-abbreviations.md)<br /><br />[Unités de mesure](units-of-measure.md)|Utilisé pour déclarer une classe, un enregistrement, une structure, une union discriminée, un type énumération, une unité de mesure ou une abréviation de type.|
|`upcast`|[Cast et conversions](casting-and-conversions.md)|Utilisé pour convertir en un type qui est plus haut dans la chaîne d’héritage.|
|`use`|[Gestion des ressources : mot clé `use`](resource-management-the-use-keyword.md)|Utilisé à la place de `let` pour les valeurs qui nécessitent `Dispose` d’être appelées pour libérer des ressources.|
|`use!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Workflows asynchrones](asynchronous-workflows.md)|Utilisé à la place de `let!` dans les flux de travail asynchrones et d’autres expressions de calcul pour les valeurs qui nécessitent `Dispose` d’être appelées pour libérer des ressources.|
|`val`|[Champs explicites : le `val` mot clé](./members/explicit-fields-the-val-keyword.md)<br /><br />[Signatures](signature-files.md)<br /><br />[Members](./members/index.md) (Membres)|Utilisé dans une signature pour indiquer une valeur, ou dans un type pour déclarer un membre, dans des situations limitées.|
|`void`|[Types primitifs](basic-types.md)|Indique le `void` type .net. Utilisé lors de l’interopérabilité avec d’autres langages .NET.|
|`when`|[Contraintes](./generics/constraints.md)|Utilisé pour les conditions booléennes (*lorsque les gardes*) sur les correspondances de modèle et pour introduire une clause de contrainte pour un paramètre de type générique.|
|`while`|[Boucles : expression `while...do`](loops-while-do-expression.md)|Introduit une construction de bouclage.|
|`with`|[Expressions de correspondance](match-expressions.md)<br /><br />[Expressions d'objet](object-expressions.md)<br /><br />[Copie et mise à jour des expressions d’enregistrement](copy-and-update-record-expressions.md)<br /><br />[Extensions de type](type-extensions.md)<br /><br />[Exceptions : expression `try...with`](./exception-handling/the-try-with-expression.md)|Utilisé conjointement avec le `match` mot clé dans les expressions de critères spéciaux. Également utilisé dans les expressions d’objet, les expressions de copie d’enregistrement et les extensions de type pour introduire des définitions de membres et pour introduire des gestionnaires d’exceptions.|
|`yield`|[Listes](lists.md), [tableaux](arrays.md), [séquences](sequences.md)|Utilisé dans une liste, un tableau ou une expression de séquence pour produire une valeur pour une séquence. En général, peut être omis, car il est implicite dans la plupart des cas.|
|`yield!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Workflows asynchrones](asynchronous-workflows.md)|Utilisé dans une expression de calcul pour ajouter le résultat d’une expression de calcul donnée à une collection de résultats pour l’expression de calcul conteneur.|
|`const`|[Fournisseurs de type](../tutorials/type-providers/index.md)| Les fournisseurs de type autorisent l’utilisation de `const` en tant que mot clé pour spécifier un littéral de constante en tant qu’argument de paramètre de type.|

Les jetons suivants sont réservés en F #, car ce sont des mots clés dans le langage OCaml :

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

Si vous utilisez l' `--mlcompatibility` option du compilateur, les mots clés ci-dessus peuvent être utilisés comme identificateurs.

Les jetons suivants sont réservés en tant que Mots clés pour une future expansion du langage F # :

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

- [Informations de référence sur le langage F #](index.md)
- [Informations de référence sur les symboles et les opérateurs](./symbol-and-operator-reference/index.md)
- [Options du compilateur](compiler-options.md)
