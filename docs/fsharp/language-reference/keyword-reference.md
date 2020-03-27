---
title: Référence des mots clés
description: Trouvez des liens vers des informations sur tous les mots clés de langue F.
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
dev_langs:
- FSharp
ms.date: 11/04/2019
ms.openlocfilehash: 34959f471406643e85990c2c80a38a684759a7f9
ms.sourcegitcommit: b16eacb6f94a5b601882a861ad17cc5470a8d5d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80352305"
---
# <a name="keyword-reference"></a>Référence des mots clés

Ce sujet contient des liens vers des informations sur tous les mots clés de langue F.

## <a name="f-keyword-table"></a>Tableau des mots-clés FMD

Le tableau suivant affiche tous les mots-clés de Fmd par ordre alphabétique, ainsi que de brèves descriptions et des liens vers des sujets pertinents qui contiennent plus d’informations.

|Mot clé|Lien|Description|
|-------|----|-----------|
|`abstract`|[Membres](./members/index.md)<br /><br />[Classes abstraites](abstract-classes.md)|Indique une méthode qui n’a pas d’implémentation dans le type dans lequel elle est déclarée ou qui est virtuelle et a une implémentation par défaut.|
|`and`|[`let`Liaisons](./functions/let-bindings.md)<br /><br />[Dossiers](records.md)<br /><br />[Membres](./members/index.md)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé dans les fixations et les dossiers récursifs, dans les déclarations de propriété, et avec de multiples contraintes sur les paramètres génériques.|
|`as`|[Classes](classes.md)<br /><br />[Critères spéciaux](Pattern-Matching.md)|Utilisé pour donner à l’objet de classe actuelle un nom d’objet. Également utilisé pour donner un nom à un modèle entier dans un match de modèle.|
|`assert`|[Assertions](assertions.md)|Utilisé pour vérifier le code lors du débogage.|
|`base`|[Classes](classes.md)<br /><br />[Héritage](inheritance.md)|Utilisé comme nom de l’objet de classe de base.|
|`begin`|[Syntaxe détaillée](verbose-syntax.md)|En syntaxe verbeuse, indique le début d’un bloc de code.|
|`class`|[Classes](classes.md)|En syntaxe verbeuse, indique le début d’une définition de classe.|
|`default`|[Membres](./members/index.md)|Indique la mise en œuvre d’une méthode abstraite; utilisé avec une déclaration de méthode abstraite pour créer une méthode virtuelle.|
|`delegate`|[Délégués](delegates.md)|Utilisé pour déclarer un délégué.|
|`do`|[Liaisons do](./functions/do-bindings.md)<br /><br />[Boucles : expression `for...to`](loops-for-to-expression.md)<br /><br />[Boucles : expression `for...in`](loops-for-in-expression.md)<br /><br />[Boucles : expression `while...do`](loops-while-do-expression.md)|Utilisé dans les constructions en boucle ou pour exécuter le code impératif.|
|`done`|[Syntaxe détaillée](verbose-syntax.md)|En syntaxe verbeuse, indique la fin d’un bloc de code dans une expression en boucle.|
|`downcast`|[Cast et conversions](casting-and-conversions.md)|Utilisé pour convertir à un type qui est plus bas dans la chaîne d’héritage.|
|`downto`|[Boucles : expression `for...to`](loops-for-to-expression.md)|Dans `for` une expression, utilisé lors du comptage à l’envers.|
|`elif`|[Expressions conditionnelles :`if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans la branchement conditionnelle. Une forme `else if`courte de .|
|`else`|[Expressions conditionnelles :`if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans la branchement conditionnelle.|
|`end`|[Structures](structures.md)<br /><br />[Unions discriminées](discriminated-unions.md)<br /><br />[Dossiers](records.md)<br /><br />[Extensions de type](type-extensions.md)<br /><br />[Syntaxe détaillée](verbose-syntax.md)|Dans les définitions de type et les extensions de type, indique la fin d’une section des définitions des membres.<br /><br />En syntaxe verbeuse, utilisée pour spécifier `begin` la fin d’un bloc de code qui commence par le mot clé.|
|`exception`|[Gestion des exceptions](./exception-handling/index.md)<br /><br />[Types d’exception](./exception-handling/exception-types.md)|Utilisé pour déclarer un type d’exception.|
|`extern`|[Fonctions externes](./functions/external-functions.md)|Indique qu’un élément de programme déclaré est défini dans un autre binaire ou un autre assemblage.|
|`false`|[Types primitifs](basic-types.md)|Utilisé comme un Boolean littéral.|
|`finally`|[Exceptions : expression `try...finally`](./exception-handling/the-try-finally-expression.md)|Utilisé avec `try` pour introduire un bloc de code qui exécute indépendamment de savoir si une exception se produit.|
|`fixed`|[Fixed](fixed.md)|Utilisé pour "pin" un pointeur sur la pile pour éviter qu’il soit des ordures collectées.|
|`for`|[Boucles : expression `for...to`](loops-for-to-expression.md)<br /><br />[Boucles : expression for...in](loops-for-in-expression.md)|Utilisé dans les constructions en boucle.|
|`fun`|[Lambda Expressions: `fun` Le Mot-clé](./functions/lambda-expressions-the-fun-keyword.md)|Utilisé dans les expressions lambda, également connu sous le nom de fonctions anonymes.|
|`function`|[Expressions de correspondance](match-expressions.md)<br /><br />[Lambda Expressions: Le mot-clé amusant](./functions/lambda-expressions-the-fun-keyword.md)|Utilisé comme une alternative `fun` plus `match` courte au mot clé et une expression dans une expression lambda qui a le modèle correspondant à un seul argument.|
|`global`|[Espaces de noms](namespaces.md)|Utilisé pour référencer l’espace de nom .NET de haut niveau.|
|`if`|[Expressions conditionnelles :`if...then...else`](conditional-expressions-if-then-else.md)|Utilisé dans les constructions de ramification conditionnelles.|
|`in`|[Boucles : expression for...in](loops-for-in-expression.md)<br /><br />[Syntaxe détaillée](verbose-syntax.md)|Utilisé pour les expressions séquences et, en syntaxe verbeuse, pour séparer les expressions des fixations.|
|`inherit`|[Héritage](inheritance.md)|Utilisé pour spécifier une classe de base ou une interface de base.|
|`inline`|[Fonctions](./functions/index.md)<br /><br />[Fonctions inline](./functions/inline-functions.md)|Utilisé pour indiquer une fonction qui doit être intégrée directement dans le code de l’appelant.|
|`interface`|[Interfaces](interfaces.md)|Utilisé pour déclarer et implémenter des interfaces.|
|`internal`|[Contrôle d’accès](access-control.md)|Utilisé pour spécifier qu’un membre est visible à l’intérieur d’une assemblée, mais pas à l’extérieur.|
|`lazy`|[Expressions différées](lazy-expressions.md)|Utilisé pour spécifier une expression qui ne doit être effectuée que lorsqu’un résultat est nécessaire.|
|`let`|[`let`Liaisons](./functions/let-bindings.md)|Utilisé pour associer, ou lier, un nom à une valeur ou une fonction.|
|`let!`|[Workflows asynchrones](asynchronous-workflows.md)<br /><br />[Expressions de calcul](computation-expressions.md)|Utilisé dans des flux de travail asynchrones pour lier un nom au résultat d’un calcul asynchrone, ou, dans d’autres expressions de calcul, utilisé pour lier un nom à un résultat, qui est du type de calcul.|
|`match`|[Expressions de correspondance](match-expressions.md)|Utilisé pour brancher en comparant une valeur à un modèle.|
|`match!`|[Expressions de calcul](computation-expressions.md#match)|Utilisé pour inline un appel à une expression de calcul et de modèle match sur son résultat.|
|`member`|[Membres](./members/index.md)|Utilisé pour déclarer une propriété ou une méthode dans un type d’objet.|
|`module`|[Modules](modules.md)|Utilisé pour associer un nom à un groupe de types, de valeurs et de fonctions connexes, pour le séparer logiquement des autres codes.|
|`mutable`|[Liaisons let](./functions/let-bindings.md)|Utilisé pour déclarer une variable, c’est-à-dire une valeur qui peut être changée.|
|`namespace`|[Espaces de noms](namespaces.md)|Utilisé pour associer un nom à un groupe de types et de modules connexes, pour le séparer logiquement des autres codes.|
|`new`|[Constructeurs](./members/constructors.md)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé pour déclarer, définir ou invoquer un constructeur qui crée ou qui peut créer un objet.<br /><br />Également utilisé dans les contraintes de paramètres génériques pour indiquer qu’un type doit avoir un certain constructeur.|
|`not`|[Informations de référence des symboles et opérateurs](./symbol-and-operator-reference/index.md)<br /><br />[Contraintes](./generics/constraints.md)|Pas vraiment un mot-clé. Cependant, `not struct` en combinaison est utilisé comme une contrainte de paramètre générique.|
|`null`|[Valeurs nulles](./values/null-values.md)<br /><br />[Contraintes](./generics/constraints.md)|Indique l’absence d’un objet.<br /><br />Également utilisé dans les contraintes de paramètres génériques.|
|`of`|[Unions discriminées](discriminated-unions.md)<br /><br />[Délégués](delegates.md)<br /><br />[Types d’exception](./exception-handling/exception-types.md)|Utilisé dans les syndicats discriminés pour indiquer le type de catégories de valeurs, et dans les déclarations de délégués et d’exception.|
|`open`|[Déclarations d’importation : mot clé `open`](import-declarations-the-open-keyword.md)|Utilisé pour rendre le contenu d’un espace de nom ou d’un module disponible sans qualification.|
|`or`|[Informations de référence des symboles et opérateurs](./symbol-and-operator-reference/index.md)<br /><br />[Contraintes](./generics/constraints.md)|Utilisé avec des conditions Boolean en tant qu’opérateur Boolean. `or` Équivaut à `||`.<br /><br />Également utilisé dans les contraintes des membres.|
|`override`|[Membres](./members/index.md)|Utilisé pour implémenter une version d’une méthode abstraite ou virtuelle qui diffère de la version de base.|
|`private`|[Contrôle d’accès](access-control.md)|Limite l’accès à un membre pour coder dans le même type ou le même module.|
|`public`|[Contrôle d’accès](access-control.md)|Permet l’accès à un membre de l’extérieur du type.|
|`rec`|[Fonctions](./functions/index.md)|Utilisé pour indiquer qu’une fonction est récursive.|
|`return`|[Workflows asynchrones](Asynchronous-Workflows.md)<br /><br />[Expressions de calcul](computation-expressions.md)|Utilisé pour indiquer une valeur à fournir à la suite d’une expression de calcul.|
|`return!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Workflows asynchrones](asynchronous-workflows.md)|Utilisé pour indiquer une expression de calcul qui, une fois évaluée, fournit le résultat de l’expression de calcul contenant.|
|`select`|[Expressions de requête](query-expressions.md)|Utilisé dans les expressions de requête pour spécifier quels champs ou colonnes extraire. Notez qu’il s’agit d’un mot clé contextuel, ce qui signifie qu’il n’est pas réellement un mot réservé et il agit seulement comme un mot clé dans le contexte approprié.|
|`static`|[Membres](./members/index.md)|Utilisé pour indiquer une méthode ou une propriété qui peut être appelée sans une instance d’un type, ou un membre de valeur qui est partagé entre tous les cas d’un type.|
|`struct`|[Structures](structures.md)<br /><br /> [Tuples](tuples.md)<br/><br/>[Contraintes](./generics/constraints.md)|Utilisé pour déclarer un type de structure.<br /><br/>Utilisé pour spécifier un tuple struct.<br/><br />Également utilisé dans les contraintes de paramètres génériques.<br /><br />Utilisé pour la compatibilité OCaml dans les définitions de modules.|
|`then`|[Expressions conditionnelles :`if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[Constructeurs](./members/constructors.md)|Utilisé dans les expressions conditionnelles.<br /><br />Également utilisé pour effectuer des effets secondaires après la construction de l’objet.|
|`to`|[Boucles : expression `for...to`](loops-for-to-expression.md)|Utilisé `for` en boucles pour indiquer une plage.|
|`true`|[Types primitifs](basic-types.md)|Utilisé comme un Boolean littéral.|
|`try`|[Exceptions : expression try...with](./exception-handling/the-try-with-expression.md)<br /><br />[Exceptions : expression try...finally](./exception-handling/the-try-finally-expression.md)|Utilisé pour introduire un bloc de code qui pourrait générer une exception. Utilisé avec `with` `finally`ou .|
|`type`|[Types F#](fsharp-types.md)<br /><br />[Classes](classes.md)<br /><br />[Dossiers](records.md)<br /><br />[Structures](structures.md)<br /><br />[Énumérations](enumerations.md)<br /><br />[Unions discriminées](discriminated-unions.md)<br /><br />[Abréviations de types](type-abbreviations.md)<br /><br />[Unités de mesure](units-of-measure.md)|Utilisé pour déclarer une classe, un dossier, une structure, une union discriminée, un type de recensement, une unité de mesure ou une abréviation de type.|
|`upcast`|[Cast et conversions](casting-and-conversions.md)|Utilisé pour convertir à un type qui est plus élevé dans la chaîne d’héritage.|
|`use`|[Gestion des ressources : mot clé `use`](resource-management-the-use-keyword.md)|Utilisé au `let` lieu de `Dispose` pour les valeurs qui nécessitent d’être appelé à des ressources gratuites.|
|`use!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Workflows asynchrones](asynchronous-workflows.md)|Utilisé au `let!` lieu de dans les flux de travail asynchrones `Dispose` et d’autres expressions de calcul pour les valeurs qui nécessitent d’être appelé à des ressources gratuites.|
|`val`|[Champs explicites : mot clé `val`](./members/explicit-fields-the-val-keyword.md)<br /><br />[Signatures](signature-files.md)<br /><br />[Membres](./members/index.md)|Utilisé dans une signature pour indiquer une valeur, ou dans un type de déclarer un membre, dans des situations limitées.|
|`void`|[Types primitifs](basic-types.md)|Indique le `void` type .NET. Utilisé lors de l’interopération avec d’autres langues .NET.|
|`when`|[Contraintes](./generics/constraints.md)|Utilisé pour les conditions Boolean (*lorsque les gardes*) sur les allumettes de modèle et d’introduire une clause de contrainte pour un paramètre de type générique.|
|`while`|[Boucles : expression `while...do`](loops-while-do-expression.md)|Introduit une construction en boucle.|
|`with`|[Expressions de correspondance](match-expressions.md)<br /><br />[Expressions d'objet](object-expressions.md)<br /><br />[Copie et mise à jour des expressions d’enregistrement](copy-and-update-record-expressions.md)<br /><br />[Extensions de type](type-extensions.md)<br /><br />[Exceptions : expression `try...with`](./exception-handling/the-try-with-expression.md)|Utilisé avec `match` le mot clé dans les expressions de correspondance de modèle. Également utilisé dans les expressions d’objets, enregistrer des expressions de copie, et des extensions de type pour introduire des définitions de membre, et d’introduire des gestionnaires d’exception.|
|`yield`|[Listes](lists.md), [Arrays](arrays.md), [Séquences](sequences.md)|Utilisé dans une liste, un tableau ou une séquence d’expression pour produire une valeur pour une séquence. Typiquement peut être omis, car il est implicite dans la plupart des situations.|
|`yield!`|[Expressions de calcul](computation-expressions.md)<br /><br />[Workflows asynchrones](asynchronous-workflows.md)|Utilisé dans une expression de calcul pour apprener le résultat d’une expression de calcul donnée à une collection de résultats pour l’expression de calcul contenant.|

Les jetons suivants sont réservés en F parce qu’ils sont des mots clés dans la langue OCaml:

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

Si vous `--mlcompatibility` utilisez l’option compilateur, les mots clés ci-dessus sont disponibles pour une utilisation comme identifiants.

Les jetons suivants sont réservés comme mots clés pour l’expansion future de la langue F :

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

- [Référence linguistique F](index.md)
- [Informations de référence des symboles et opérateurs](./symbol-and-operator-reference/index.md)
- [Options Compilateur](compiler-options.md)
