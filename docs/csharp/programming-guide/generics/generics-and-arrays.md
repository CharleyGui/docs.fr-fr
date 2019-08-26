---
title: Génériques et tableaux - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: fee66cf7bd0ab3c051ea67acc323efa02a21a017
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659790"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="cd5e3-102">Génériques et tableaux (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="cd5e3-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="cd5e3-103">En C# 2.0 et versions ultérieures, les tableaux unidimensionnels qui ont une limite inférieure de zéro implémentent automatiquement <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="cd5e3-104">Cela vous permet de créer des méthodes génériques qui peuvent utiliser le même code pour itérer au sein de tableaux et d’autres types de collections.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="cd5e3-105">Cette technique est essentiellement utile pour lire les données dans des collections.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="cd5e3-106">L’interface <xref:System.Collections.Generic.IList%601> ne peut pas être utilisée pour ajouter ni supprimer des éléments dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="cd5e3-107">Une exception est levée si vous essayez d’appeler une méthode <xref:System.Collections.Generic.IList%601> telle que <xref:System.Collections.Generic.IList%601.RemoveAt%2A> sur un tableau dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="cd5e3-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="cd5e3-108">L’exemple de code suivant montre comment une méthode générique seule qui prend un paramètre d’entrée <xref:System.Collections.Generic.IList%601> peut itérer à la fois au sein d’une liste et d’un tableau (en l’occurrence un tableau d’entiers).</span><span class="sxs-lookup"><span data-stu-id="cd5e3-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="cd5e3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd5e3-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="cd5e3-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cd5e3-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cd5e3-111">Génériques</span><span class="sxs-lookup"><span data-stu-id="cd5e3-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="cd5e3-112">Tableaux</span><span class="sxs-lookup"><span data-stu-id="cd5e3-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="cd5e3-113">Génériques</span><span class="sxs-lookup"><span data-stu-id="cd5e3-113">Generics</span></span>](../../../standard/generics/index.md)
