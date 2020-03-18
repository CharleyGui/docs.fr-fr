---
title: Comparaisons d'égalité - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: f09d9891f79eda44c428d5509e341a54ad3a3eee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157102"
---
# <a name="equality-comparisons-c-programming-guide"></a>Comparaisons d’égalité (Guide de programmation C#)

Il est parfois nécessaire de comparer l’égalité de deux valeurs. Dans certains cas, vous testez *l’égalité de valeur*, également appelée *équivalence*, qui signifie que les valeurs contenues dans les deux variables sont égales. Dans d’autres cas, vous devez déterminer si deux variables référencent le même objet sous-jacent en mémoire. Ce type d’égalité est appelée *l’égalité de référence* ou *identité*. Cette rubrique décrit ces deux genres d’égalité et fournit des liens vers d’autres rubriques pour obtenir plus d’informations.  
  
## <a name="reference-equality"></a>Égalité des références

 L’égalité de références signifie que deux références d’objets référencent le même objet sous-jacent. Cela peut se produire par simple assignation, comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 Dans ce code, deux objets sont créés, mais après l’instruction d’assignation, les deux références référencent le même objet. Elles présentent donc une égalité de référence. Utilisez la méthode <xref:System.Object.ReferenceEquals%2A> pour déterminer si deux références référencent le même objet.  
  
Le concept d’égalité de référence s’applique uniquement aux types référence. Les objets de type valeur ne peuvent pas avoir une égalité de référence, car quand une instance d’un type valeur est assignée à une variable, une copie de la valeur est effectuée. Ainsi, vous ne pouvez jamais avoir deux structs unboxed qui référencent le même emplacement en mémoire. De plus, si vous utilisez <xref:System.Object.ReferenceEquals%2A> pour comparer deux types valeur, le résultat est toujours `false`, même si les valeurs contenues dans les objets sont toutes identiques. Cela est dû au fait que chaque variable est convertie en une instance d’objet distincte. Pour plus d’informations, voir [Comment tester l’égalité de référence (Identité)](./how-to-test-for-reference-equality-identity.md).

## <a name="value-equality"></a>Égalité des valeurs

 L’égalité de valeur signifie que deux objets contiennent les mêmes valeurs. Pour les types valeur primitifs tels que [int](../../language-reference/builtin-types/integral-numeric-types.md) ou [bool](../../language-reference/builtin-types/bool.md), les tests d’égalité de valeur sont simples. Vous pouvez [==](../../language-reference/operators/equality-operators.md#equality-operator-) utiliser l’opérateur, comme indiqué dans l’exemple suivant.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.
if (b == a)
{  
    // The two integers are equal.  
}  
```  
  
 Pour la plupart des autres types, les tests d’égalité de valeur sont plus complexes parce qu’ils vous demandent de comprendre comment le type la définit. Pour les classes et structs qui ont plusieurs champs ou propriétés, l’égalité de valeur signifie souvent que tous les champs ou propriétés ont la même valeur. Par exemple, deux objets `Point` peuvent être définis comme équivalents si pointA.X est égal à pointB.X et que pointA.Y est égal à pointB.Y.  
  
Toutefois, il n’est pas obligatoire que l’équivalence soit basée sur tous les champs dans un type. Elle peut être basée sur une partie. Quand vous comparez des types dont vous n’êtes pas propriétaire, vous devez bien comprendre comment l’équivalence est définie pour ce type. Pour plus d’informations sur la façon de définir l’égalité des valeurs dans vos propres classes et structs, voir [Comment définir l’égalité de valeur pour un type](./how-to-define-value-equality-for-a-type.md).
  
### <a name="value-equality-for-floating-point-values"></a>Égalité des valeurs à virgule flottante

 Les comparaisons d’égalité des valeurs à virgule flottante ([double](../../language-reference/builtin-types/floating-point-numeric-types.md) et [float](../../language-reference/builtin-types/floating-point-numeric-types.md)) sont problématiques en raison de l’imprécision de l’arithmétique à virgule flottante sur les ordinateurs binaires. Pour plus d’informations, consultez les notes dans la rubrique <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Comment tester l’égalité de référence (Identité)](./how-to-test-for-reference-equality-identity.md)|Décrit comment déterminer si deux variables présentent une égalité de référence.|  
|[Comment définir une égalité de valeurs pour un type](./how-to-define-value-equality-for-a-type.md)|Décrit comment fournir une définition personnalisée de l’égalité de valeur pour un type.|  
|[Guide de programmation C#](../index.md)|Fournit des liens vers des informations détaillées sur les fonctionnalités et les fonctions clés du langage C# disponibles en C# par l’intermédiaire du .NET Framework.|  
|[Types](../types/index.md)|Fournit des informations sur le système de typeC# et des liens vers des informations supplémentaires.|  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
