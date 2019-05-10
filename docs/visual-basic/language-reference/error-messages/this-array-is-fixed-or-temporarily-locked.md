---
title: Ce tableau est prédéfini ou est temporairement verrouillé (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: c7b5372b6046e25aad87131ba141cb71c580e12c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625940"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="6b173-102">Ce tableau est prédéfini ou est temporairement verrouillé (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b173-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="6b173-103">Cette erreur a les causes possibles suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b173-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="6b173-104">À l’aide de `ReDim` pour modifier le nombre d’éléments d’un tableau de taille fixe.</span><span class="sxs-lookup"><span data-stu-id="6b173-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="6b173-105">Redimensionnement d’un tableau dynamique au niveau du module, dans lequel un élément a été passé en tant qu’argument à une procédure.</span><span class="sxs-lookup"><span data-stu-id="6b173-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="6b173-106">Si un élément est passé, le tableau est verrouillé pour empêcher la désallocation de mémoire pour le paramètre de référence dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="6b173-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="6b173-107">Tentative d’assigner une valeur à un `Variant` variable contenant un tableau, mais la `Variant` est actuellement verrouillé.</span><span class="sxs-lookup"><span data-stu-id="6b173-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b173-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6b173-108">To correct this error</span></span>  
  
1. <span data-ttu-id="6b173-109">Rendre le tableau d’origine dynamique non fixe en le déclarant avec `ReDim` (si le tableau est déclaré dans une procédure), ou en le déclarant sans spécifier le nombre d’éléments (si le tableau est déclaré au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="6b173-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="6b173-110">Déterminer s’il faut vraiment transmettre l’élément, dans la mesure où il est visible dans toutes les procédures dans le module.</span><span class="sxs-lookup"><span data-stu-id="6b173-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="6b173-111">Déterminez ce qui verrouille le `Variant` et y remédier.</span><span class="sxs-lookup"><span data-stu-id="6b173-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b173-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b173-112">See also</span></span>

- [<span data-ttu-id="6b173-113">Tableaux</span><span class="sxs-lookup"><span data-stu-id="6b173-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
