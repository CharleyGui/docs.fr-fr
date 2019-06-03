---
title: typeof - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 7962a3d0a5885e64701cb9d9a4d689cd982b9830
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422557"
---
# <a name="typeof-c-reference"></a>typeof (référence C#)

Permet d’obtenir l’objet <xref:System.Type?displayProperty=nameWithType> pour un type. Une expression `typeof` prend la forme suivante :

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a>Notes

Pour obtenir le type au moment de l’exécution d’une expression, vous pouvez utiliser la méthode <xref:System.Object.GetType%2A> du .NET Framework, comme dans l’exemple suivant :

```csharp
int i = 0;
System.Type type = i.GetType();
```

L’opérateur `typeof` ne peut pas être surchargé.

L’opérateur `typeof` peut également être utilisé sur les types génériques ouverts. Les types avec plusieurs paramètres de type doivent avoir le nombre approprié de virgules dans la spécification. Par exemple, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> a deux arguments de type ; on utilise donc une virgule :

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

L’exemple suivant montre comment déterminer si le type de retour d’une méthode est un <xref:System.Collections.Generic.IEnumerable%601> générique. <xref:System.Type.GetInterface%2A?displayProperty=nameWithType> retourne `null` si le type de retour n’est pas un type générique <xref:System.Collections.Generic.IEnumerable%601>.

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a>Exemple

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a>Exemple

Cet exemple utilise la méthode <xref:System.Object.GetType%2A> pour déterminer le type utilisé pour contenir le résultat d’un calcul numérique. Cela dépend des besoins de stockage du nombre résultant.

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [Opérateur typeof](~/_csharplang/spec/expressions.md#the-typeof-operator) dans la [spécification du langage C#](../language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- <xref:System.Type?displayProperty=nameWithType>
- [Référence C#](../../../csharp/language-reference/index.md)
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Mots clés C#](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)
