---
title: Interfaces génériques - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 7fc79874c8e1ff24c38d288d3f6708e2851419e3
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423477"
---
# <a name="generic-interfaces-c-programming-guide"></a>Interfaces génériques (guide de programmation C#)
Il est souvent utile de définir des interfaces pour les classes de collections génériques, ou pour les classes génériques qui représentent des éléments dans la collection. Pour les classes génériques, il est préférable d’utiliser des interfaces génériques, comme <xref:System.IComparable%601> à la place d’<xref:System.IComparable>, pour éviter les opérations de boxing et d’unboxing sur les types valeur. La bibliothèque de classes .NET Framework définit plusieurs interfaces génériques à utiliser avec les classes de collections dans l’espace de noms <xref:System.Collections.Generic>.  
  
 Quand une interface est spécifiée comme une contrainte sur un paramètre de type, seuls les types qui implémentent l’interface peuvent être utilisés. L’exemple de code suivant illustre une classe `SortedList<T>` qui dérive de la classe `GenericList<T>`. Pour plus d’informations, consultez [Introduction aux génériques](../../../csharp/programming-guide/generics/index.md). `SortedList<T>` ajoute la contrainte `where T : IComparable<T>`. Ceci permet à la méthode `BubbleSort` dans `SortedList<T>` d’utiliser la méthode générique <xref:System.IComparable%601.CompareTo%2A> sur les éléments de liste. Dans cet exemple, les éléments de liste sont une classe simple, `Person`, qui implémente `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Plusieurs interfaces peuvent être spécifiées en tant que contraintes sur un seul type, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Une interface peut définir plusieurs paramètres de type, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Les règles d’héritage qui s’appliquent aux classes s’appliquent également aux interfaces :  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Les interfaces génériques peuvent hériter d’interfaces non génériques si l’interface générique est de type contravariant, ce qui signifie qu’elle utilise uniquement son paramètre de type comme valeur de retour. Dans la bibliothèque de classes .NET Framework, <xref:System.Collections.Generic.IEnumerable%601> hérite d’<xref:System.Collections.IEnumerable>, car <xref:System.Collections.Generic.IEnumerable%601> utilise uniquement `T` dans la valeur de retour de <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> et dans l’accesseur Get de propriété <xref:System.Collections.Generic.IEnumerator%601.Current%2A>.  
  
 Les classes concrètes peuvent implémenter des interfaces construites fermées, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Les classes génériques peuvent implémenter des interfaces génériques ou des interfaces construites fermées tant que la liste de paramètres de classe fournit tous les arguments requis par l’interface, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Les règles qui déterminent la surcharge des méthodes sont les mêmes pour les méthodes dans les classes génériques, les structs génériques ou les interfaces génériques. Pour plus d’informations, consultez [Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Introduction aux génériques](../../../csharp/programming-guide/generics/index.md)
- [interface](../../../csharp/language-reference/keywords/interface.md)
- [Génériques](~/docs/standard/generics/index.md)
