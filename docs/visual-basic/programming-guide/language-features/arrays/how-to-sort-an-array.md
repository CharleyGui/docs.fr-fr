---
title: 'Procédure : Trier un tableau dans Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700975"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="4044d-102">Comment : trier un tableau dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4044d-102">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="4044d-103">Cet article montre un exemple de tri d’un tableau de chaînes dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4044d-103">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="4044d-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="4044d-104">Example</span></span>

<span data-ttu-id="4044d-105">Cet exemple déclare un tableau d’objets `String` nommés `zooAnimals`, le remplit, puis le trie par ordre alphabétique :</span><span class="sxs-lookup"><span data-stu-id="4044d-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="4044d-106">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="4044d-106">Robust programming</span></span>

<span data-ttu-id="4044d-107">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="4044d-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="4044d-108">Le tableau est vide (classe <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="4044d-108">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="4044d-109">Le tableau est multidimensionnel (classe <xref:System.RankException>).</span><span class="sxs-lookup"><span data-stu-id="4044d-109">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="4044d-110">Un ou plusieurs éléments du tableau n’implémentent pas l’interface <xref:System.IComparable> (classe <xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="4044d-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="4044d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4044d-111">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4044d-112">Tableaux</span><span class="sxs-lookup"><span data-stu-id="4044d-112">Arrays</span></span>](index.md)
- [<span data-ttu-id="4044d-113">Dépannage des tableaux</span><span class="sxs-lookup"><span data-stu-id="4044d-113">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="4044d-114">Collections</span><span class="sxs-lookup"><span data-stu-id="4044d-114">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="4044d-115">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="4044d-115">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
