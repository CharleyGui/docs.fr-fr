---
title: Les tableaux déclarés en tant que membres de structures ne peuvent pas être déclarés avec une taille initiale
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250150"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="4b8ee-102">Les tableaux déclarés en tant que membres de structures ne peuvent pas être déclarés avec une taille initiale</span><span class="sxs-lookup"><span data-stu-id="4b8ee-102">Arrays declared as structure members cannot be declared with an initial size</span></span>

<span data-ttu-id="4b8ee-103">Un tableau dans une structure est déclaré avec une taille initiale.</span><span class="sxs-lookup"><span data-stu-id="4b8ee-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="4b8ee-104">Vous ne pouvez pas initialiser un élément de structure, et la déclaration d’une taille de tableau est une forme d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="4b8ee-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>

<span data-ttu-id="4b8ee-105">**ID d’erreur :** BC31043</span><span class="sxs-lookup"><span data-stu-id="4b8ee-105">**Error ID:** BC31043</span></span>

## <a name="example"></a><span data-ttu-id="4b8ee-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b8ee-106">Example</span></span>

<span data-ttu-id="4b8ee-107">L’exemple suivant génère l’BC31043 :</span><span class="sxs-lookup"><span data-stu-id="4b8ee-107">The following example generates BC31043:</span></span>

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a><span data-ttu-id="4b8ee-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="4b8ee-108">To correct this error</span></span>

1. <span data-ttu-id="4b8ee-109">Définissez le tableau dans votre structure en tant que dynamique (aucune taille initiale).</span><span class="sxs-lookup"><span data-stu-id="4b8ee-109">Define the array in your structure as dynamic (no initial size).</span></span>

2. <span data-ttu-id="4b8ee-110">Si vous avez besoin d’une certaine taille de tableau, vous pouvez redimensionner un tableau dynamique à l’aide d’une [instruction ReDim](../statements/redim-statement.md) lorsque votre code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4b8ee-110">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="4b8ee-111">L'exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="4b8ee-111">The following example illustrates this:</span></span>
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a><span data-ttu-id="4b8ee-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b8ee-112">See also</span></span>

- [<span data-ttu-id="4b8ee-113">Tableaux</span><span class="sxs-lookup"><span data-stu-id="4b8ee-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="4b8ee-114">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="4b8ee-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
