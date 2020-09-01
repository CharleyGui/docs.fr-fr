---
description: yield, mot clé contextuel - Référence C#
title: yield, mot clé contextuel - Référence C#
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: c8caf7e34397faf9f7085d6634287cffcb37eb08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141879"
---
# <a name="yield-c-reference"></a>yield (Référence C#)

Lorsque vous utilisez le `yield` [mot clé contextuel](index.md#contextual-keywords) dans une instruction, vous indiquez que la méthode, l'opérateur ou l'accesseur `get` dans lequel il apparaît est un itérateur. L'utilisation de `yield` pour définir un itérateur rend une classe explicite supplémentaire inutile (la classe qui contient l'état d'une énumération ; pour obtenir un exemple, consultez <xref:System.Collections.Generic.IEnumerator%601>) lorsque vous implémentez les modèles <xref:System.Collections.IEnumerable> et <xref:System.Collections.IEnumerator> pour un type de collection personnalisé.

L'exemple suivant montre les deux formulaires de l'instruction `yield`.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Remarques

Utilisez une instruction `yield return` pour retourner chaque élément un par un.

La séquence retournée par une méthode d’itérateur peut être consommée à l’aide d’une instruction [foreach](foreach-in.md) ou d’une requête LINQ. Chaque itération de la boucle `foreach` appelle la méthode Iterator. Lorsqu'une instruction `yield return` est atteinte dans la méthode Iterator, `expression` est retourné, et l'emplacement dans le code est conservé. L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.

Utilisez une instruction `yield break` pour terminer l'itération.

Pour plus d’informations sur les itérateurs, consultez [Itérateurs](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Méthodes Iterator et accesseurs get

La déclaration d’un itérateur doit respecter les exigences suivantes :

- Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.

- La déclaration ne peut avoir aucun paramètre [in, ](in-parameter-modifier.md) [ref](ref.md) ou [out](out-parameter-modifier.md).

Le type `yield` d'un itérateur qui retourne <xref:System.Collections.IEnumerable> ou <xref:System.Collections.IEnumerator> est `object`.  Si l'itérateur retourne <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.Generic.IEnumerator%601>, il doit exister une conversion implicite du type de l'expression dans l'instruction `yield return` au paramètre de type générique.

Vous ne pouvez pas inclure une instruction `yield return` ou `yield break` dans :

- [Expressions lambda](../operators/lambda-expressions.md) et [méthodes anonymes](../operators/delegate-operator.md).

- Méthodes qui contiennent des blocs unsafe. Pour plus d’informations, consultez [unsafe](unsafe.md).

## <a name="exception-handling"></a>Gestion des exceptions

Il ne peut pas y avoir d'instruction `yield return` dans un bloc try-catch. Une instruction `yield return` peut se trouver dans le bloc try d'une instruction try-finally.

Une instruction `yield break` peut se trouver dans un bloc try ou un bloc catch mais pas dans un bloc finally.

Si le corps `foreach` (en dehors de la méthode Iterator) lève une exception, un bloc `finally` de la méthode Iterator est exécuté.

## <a name="technical-implementation"></a>Implémentation technique

Le code suivant retourne `IEnumerable<string>` depuis une méthode Iterator, puis itère au sein de ses éléments.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

L'appel à `MyIteratorMethod` n'exécute pas le corps de la méthode. À la place, l'appel retourne `IEnumerable<string>` dans la variable `elements`.

Dans une itération de la boucle `foreach`, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`. Cet appel exécute le corps de `MyIteratorMethod` jusqu'à ce que l'instruction `yield return` suivante soit atteinte. L’expression retournée par l’instruction `yield return` détermine non seulement la valeur de la variable `element` pour la consommation par le corps de boucle, mais également la propriété <xref:System.Collections.Generic.IEnumerator%601.Current%2A> de `elements`, qui est `IEnumerable<string>`.

À chaque itération suivante de la boucle `foreach`, l'exécution du corps de l'itérateur reprend à partir de l'emplacement où elle s'est interrompue, et s'arrête encore lorsqu'elle atteint une instruction `yield return`. La boucle `foreach` se termine lorsque à la fin de la méthode Iterator ou lorsqu'une instruction `yield break` est atteinte.

## <a name="example"></a>Exemple

L'exemple suivant comprend une instruction `yield return` située dans une boucle `for`. Chaque itération du corps d’instruction `foreach` dans la méthode `Main` crée un appel à la fonction d’itérateur `Power`. Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `yield return`, qui se produit pendant l'itération suivante de la boucle `for`.

Le type de retour de la méthode Iterator est <xref:System.Collections.IEnumerable>, qui est un type interface itérateur. Lorsque la méthode Iterator est appelée, elle retourne un objet énumérable contenant les puissances d'un nombre.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Exemple

L'exemple suivant illustre un accesseur `get` qui est un itérateur. Dans cet exemple, chaque instruction `yield return` retourne une instance d'une classe définie par l'utilisateur.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iterators](../../iterators.md)
