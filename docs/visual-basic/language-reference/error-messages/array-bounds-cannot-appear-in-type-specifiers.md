---
title: Les tailles de tableau ne peuvent pas figurer dans les spécificateurs de type
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512759"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="89b27-102">Les tailles de tableau ne peuvent pas figurer dans les spécificateurs de type</span><span class="sxs-lookup"><span data-stu-id="89b27-102">Array bounds cannot appear in type specifiers</span></span>

<span data-ttu-id="89b27-103">Les tailles de tableau ne peuvent pas être déclarées dans le cadre d’un spécificateur de type de données.</span><span class="sxs-lookup"><span data-stu-id="89b27-103">Array sizes cannot be declared as part of a data type specifier.</span></span>

<span data-ttu-id="89b27-104">**ID d’erreur:** BC30638</span><span class="sxs-lookup"><span data-stu-id="89b27-104">**Error ID:** BC30638</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="89b27-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="89b27-105">To correct this error</span></span>

- <span data-ttu-id="89b27-106">Spécifiez la taille du tableau immédiatement après le nom de la variable au lieu de placer la taille du tableau après le type, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="89b27-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>

  ```vb
  Dim Array(8) As Integer
  ```

- <span data-ttu-id="89b27-107">Définissez un tableau et initialisez-le avec le nombre d’éléments souhaité, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="89b27-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a><span data-ttu-id="89b27-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89b27-108">See also</span></span>

- [<span data-ttu-id="89b27-109">Tableaux</span><span class="sxs-lookup"><span data-stu-id="89b27-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
