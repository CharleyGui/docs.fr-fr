---
title: Types pointeur - Guide de programmation C#
description: En savoir plus sur les types pointeur. Consultez des exemples de différents pointeurs, des exemples de code et des ressources disponibles supplémentaires.
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 9c62a31f9a4a090fe56fb10ac45fe2f93f1b036e
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382033"
---
# <a name="pointer-types-c-programming-guide"></a>Types pointeur (Guide de programmation C#)

Dans un contexte unsafe, un type peut être un type pointeur, un type valeur ou un type référence. La déclaration d'un type pointeur peut prendre l'une des formes suivantes :

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Le type spécifié avant `*` dans un type de pointeur est appelé **type référent**. Seul un [type non managé](../../language-reference/builtin-types/unmanaged-types.md) peut être un type référent.

Les types pointeur n’héritent pas de [object](../../language-reference/builtin-types/reference-types.md), et aucune conversion n’est possible entre les types pointeur et `object`. Par ailleurs, le boxing et l'unboxing ne prennent pas en charge les pointeurs. Cependant, vous pouvez effectuer des conversions entre différents types pointeur ainsi qu'entre des types pointeur et des types intégraux.

Lorsque vous déclarez plusieurs pointeurs dans la même déclaration, l'astérisque (*) est écrit conjointement au type sous-jacent uniquement, il n'est pas utilisé en tant que préfixe de chaque nom de pointeur. Par exemple :

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Un pointeur ne peut pas pointer vers une référence ou vers un [struct](../../language-reference/builtin-types/struct.md) qui contient des références, car une référence d’objet peut être collectée par le récupérateur de mémoire, même si un pointeur pointe vers elle. Le récupérateur de mémoire ne se préoccupe pas de savoir si un objet est pointé par des types pointeur.

La valeur de la variable pointeur de type `myType*` est l'adresse d'une variable de type `myType`. Les éléments suivants sont des exemples de déclarations de type pointeur :

|Exemple|Description|
|-------------|-----------------|
|`int* p`|`p` est un pointeur vers un entier.|
|`int** p`|`p` est un pointeur vers un pointeur vers un entier.|
|`int*[] p`|`p` est un tableau unidimensionnel de pointeurs vers des entiers.|
|`char* p`|`p` est un pointeur vers un caractère.|
|`void* p`|`p` est un pointeur vers un type inconnu.|

L'opérateur d'indirection de pointeur * peut être utilisé pour accéder au contenu à l'emplacement vers lequel pointe la variable pointeur. Observez par exemple la déclaration suivante :

```csharp
int* myVariable;
```

L'expression `*myVariable` désigne la variable `int` trouvée à l'adresse contenue dans `myVariable`.

Plusieurs exemples de pointeurs sont présentés dans les rubriques [fixed, instruction](../../language-reference/keywords/fixed-statement.md) et [Conversions de pointeur](./pointer-conversions.md). L’exemple suivant utilise le mot clé `unsafe` et les instructions `fixed`, et montre comment incrémenter un pointeur intérieur.  Vous pouvez coller ce code dans la fonction Main d'une application console pour l'exécuter. Ces exemples doivent être compilés avec l’ensemble d’options de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).

[!code-csharp[Using pointer types](snippets/FixedKeywordExamples.cs#5)]

L'opérateur d'indirection ne peut pas être appliqué à un pointeur de type `void*`. Toutefois, vous pouvez utiliser un cast pour convertir un pointeur void en n'importe quel autre type pointeur, et inversement.

Un pointeur peut être `null`. Le fait d'appliquer un opérateur d'indirection à un pointeur Null donne lieu à un comportement défini par l'implémentation.

Le passage de pointeurs entre méthodes peut engendrer un comportement non défini. Supposons une méthode qui retourne un pointeur à une variable locale par le biais d’un paramètre `in`, `out` ou `ref`, ou comme résultat de fonction. Si le pointeur a été défini dans un bloc fixed, la variable vers laquelle il pointe peut ne plus être fixed.

Le tableau suivant répertorie les opérateurs et les instructions qui peuvent fonctionner sur des pointeurs dans un contexte unsafe :

|Opérateur/Instruction|Utilisation|
|-------------------------|---------|
|`*`|Exécute l'indirection de pointeur.|
|`->`|Accède à un membre d'un struct via un pointeur.|
|`[]`|Indexe un pointeur.|
|`&`|Obtient l'adresse d'une variable.|
|`++` et `--`|Incrémente et décrémente les pointeurs.|
|`+` et `-`|Exécute des opérations arithmétiques sur les pointeurs.|
|`==`, `!=`, `<`, `>`, `<=` et `>=`|Compare des pointeurs.|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|Alloue de la mémoire sur la pile.|
|[`fixed`gestion](../../language-reference/keywords/fixed-statement.md)|Résout temporairement une variable afin de pouvoir rechercher son adresse.|

Pour plus d’informations sur les opérateurs associés au pointeur, consultez [Opérateurs associés au pointeur](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Pointeurs et code unsafe](index.md)
- [Conversions de pointeur](pointer-conversions.md)
- [Types référence](../../language-reference/keywords/reference-types.md)
- [Types de valeur](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
