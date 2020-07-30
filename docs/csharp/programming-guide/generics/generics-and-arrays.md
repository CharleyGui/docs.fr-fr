---
title: Génériques et tableaux - Guide de programmation C#
description: En savoir plus sur les génériques et les tableaux en programmation C#. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f3d9e9e0c84d954278780e7598545f80aea0e58c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299043"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="06474-104">Génériques et tableaux (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="06474-104">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="06474-105">En C# 2.0 et versions ultérieures, les tableaux unidimensionnels qui ont une limite inférieure de zéro implémentent automatiquement <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="06474-105">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="06474-106">Cela vous permet de créer des méthodes génériques qui peuvent utiliser le même code pour itérer au sein de tableaux et d’autres types de collections.</span><span class="sxs-lookup"><span data-stu-id="06474-106">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="06474-107">Cette technique est essentiellement utile pour lire les données dans des collections.</span><span class="sxs-lookup"><span data-stu-id="06474-107">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="06474-108">L’interface <xref:System.Collections.Generic.IList%601> ne peut pas être utilisée pour ajouter ni supprimer des éléments dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="06474-108">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="06474-109">Une exception est levée si vous essayez d’appeler une méthode <xref:System.Collections.Generic.IList%601> telle que <xref:System.Collections.Generic.IList%601.RemoveAt%2A> sur un tableau dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="06474-109">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="06474-110">L’exemple de code suivant montre comment une méthode générique seule qui prend un paramètre d’entrée <xref:System.Collections.Generic.IList%601> peut itérer à la fois au sein d’une liste et d’un tableau (en l’occurrence un tableau d’entiers).</span><span class="sxs-lookup"><span data-stu-id="06474-110">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="06474-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06474-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="06474-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="06474-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="06474-113">Génériques</span><span class="sxs-lookup"><span data-stu-id="06474-113">Generics</span></span>](./index.md)
- [<span data-ttu-id="06474-114">Tableaux</span><span class="sxs-lookup"><span data-stu-id="06474-114">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="06474-115">Génériques</span><span class="sxs-lookup"><span data-stu-id="06474-115">Generics</span></span>](../../../standard/generics/index.md)
