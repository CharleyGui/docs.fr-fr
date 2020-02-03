---
title: Boxing et unboxing - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 62df08bf4ae3580e9b8d5b3aab0697d396674ca1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745412"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Boxing et unboxing (Guide de programmation C#)

Le boxing est la conversion d’un [type valeur](../../language-reference/builtin-types/value-types.md) en type `object` ou en un type interface implémenté par ce type valeur. Lorsque le common language runtime (CLR) convertit un type valeur, il encapsule la valeur à l’intérieur d’une instance <xref:System.Object?displayProperty=nameWithType> et la stocke sur le tas managé. L'unboxing extrait le type valeur de l'objet. La conversion boxing est implicite ; la conversion unboxing est explicite. Le concept de boxing et de unboxing repose sur la vue unifiée par C# du système de type, dans lequel une valeur de n'importe quel type peut être traitée en tant qu'objet.

Dans l’exemple suivant, la variable de type entier `i` est convertie (*boxed*) et assignée à l’objet `o`.

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

L’objet `o` peut ensuite être unboxed et assigné à la variable de type entier `i` :

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

Les exemples suivants montrent comment le boxing est utilisé dans C#.

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a>Performances

Par rapport aux assignations simples, le boxing et l'unboxing sont des processus qui coûtent cher en calcul. Lorsqu'un type valeur est boxed, un nouvel objet doit être alloué et construit. À un degré moindre, le cast requis pour l'unboxing coûte également cher en calcul. Pour plus d’informations, consultez [Performances](../../../framework/performance/performance-tips.md).

## <a name="boxing"></a>Boxing

Le boxing est utilisé pour stocker des types valeur dans le tas rassemblé par garbage collection. Le boxing est une conversion implicite d’un [type valeur](../../language-reference/builtin-types/value-types.md) en type `object` ou en un type interface implémenté par ce type valeur. Le boxing d'un type valeur alloue une instance d'objet sur le tas et copie la valeur dans le nouvel objet.

Dans l'exemple suivant, une variable de type valeur est déclarée :

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

L'instruction ci-dessous réalise implicitement une opération de boxing sur la variable `i` :

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

Le résultat de cette instruction crée, sur la pile, un objet `o` qui fait référence à une valeur de type `int` sur le tas. Cette valeur est une copie de la valeur de type valeur qui a été assignée à la variable `i`. La différence entre les deux variables, `i` et `o`, est illustrée dans l’image de conversion boxing ci-dessous :

![Graphique illustrant la différence entre les variables i et o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

Il est également possible, mais jamais obligatoire, d'effectuer un boxing explicite comme dans l'exemple suivant :

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a>Description

Cet exemple utilise le boxing pour convertir une variable `i` (entier) en un objet `o`. Ensuite, la valeur `i` stockée dans la variable `123` est remplacée par la valeur `456`. L'exemple montre que le type valeur d'origine et que l'objet boxed utilisent des emplacements de mémoire distincts et peuvent, par conséquent, stocker des valeurs différentes.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a>Unboxing

L’unboxing est une conversion explicite du type `object` en un [type valeur](../../language-reference/builtin-types/value-types.md), ou d’un type interface en un type valeur qui implémente l’interface. Une opération d'unboxing comprend les étapes suivantes :

- Vérification de l'instance de l'objet pour s'assurer qu'il s'agit bien d'une valeur boxed du type valeur spécifié.

- Copie de la valeur de l'instance dans la variable de type valeur.

Les instructions suivantes expliquent les opérations de boxing et d'unboxing :

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

L’illustration suivante montre le résultat de ces instructions :

![Image illustrant une conversion unboxing.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

Pour que l'unboxing de types valeur réussisse au moment de l'exécution, l'élément qui est unboxed doit être une référence à un objet précédemment créé par boxing d'une instance de ce type valeur. La tentative d'extraction de `null` provoque un <xref:System.NullReferenceException>. La tentative d'extraction d'une référence vers un type de valeur incompatible provoque un <xref:System.InvalidCastException>.

## <a name="example"></a>Exemple

L'exemple suivant montre un cas d'unboxing non valide et l'`InvalidCastException` qui en résulte. Avec `try` et `catch`, un message d'erreur est affiché lorsque l'erreur se produit.

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

Sortie de ce programme :

`Specified cast is not valid. Error: Incorrect unboxing.`

Si vous modifiez l'instruction :

```csharp
int j = (short) o;
```

en :

```csharp
int j = (int) o;
```

la conversion sera réalisée, avec le résultat suivant :

`Unboxing OK.`

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Types référence](../../language-reference/keywords/reference-types.md)
- [Types de valeur](../../language-reference/builtin-types/value-types.md)
