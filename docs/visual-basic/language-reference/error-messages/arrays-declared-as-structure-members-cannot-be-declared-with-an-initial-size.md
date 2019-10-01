---
title: Les tableaux déclarés en tant que membres de structures ne peuvent pas être déclarés avec une taille initiale
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701253"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="a1296-102">Les tableaux déclarés en tant que membres de structures ne peuvent pas être déclarés avec une taille initiale</span><span class="sxs-lookup"><span data-stu-id="a1296-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="a1296-103">Un tableau dans une structure est déclaré avec une taille initiale.</span><span class="sxs-lookup"><span data-stu-id="a1296-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="a1296-104">Vous ne pouvez pas initialiser un élément de structure, et la déclaration d’une taille de tableau est une forme d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="a1296-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="a1296-105">**ID d’erreur :** BC31043</span><span class="sxs-lookup"><span data-stu-id="a1296-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a1296-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a1296-106">To correct this error</span></span>  
  
1. <span data-ttu-id="a1296-107">Définissez le tableau dans votre structure en tant que dynamique (aucune taille initiale).</span><span class="sxs-lookup"><span data-stu-id="a1296-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2. <span data-ttu-id="a1296-108">Si vous avez besoin d’une certaine taille de tableau, vous pouvez redimensionner un tableau dynamique à l’aide d’une [instruction ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) lorsque votre code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a1296-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="a1296-109">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a1296-109">The following example illustrates this.</span></span>  
  
    ```vb  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a1296-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1296-110">See also</span></span>

- [<span data-ttu-id="a1296-111">Tableaux</span><span class="sxs-lookup"><span data-stu-id="a1296-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="a1296-112">Guide pratique pour déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="a1296-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
