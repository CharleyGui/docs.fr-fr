---
title: Un tableau déclaré en tant que variable de contrôle de boucle for ne peut pas être déclaré avec une taille initiale
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: 9e8bb7b79b5a770c3c92e47d8e7c01c5b83d6061
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701209"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="ffd76-102">Un tableau déclaré en tant que variable de contrôle de boucle for ne peut pas être déclaré avec une taille initiale</span><span class="sxs-lookup"><span data-stu-id="ffd76-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="ffd76-103">Une boucle `For Each` utilise un tableau comme variable d’itération d' *élément* , mais Initialise ce tableau.</span><span class="sxs-lookup"><span data-stu-id="ffd76-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="ffd76-104">Les instructions suivantes montrent comment cette erreur peut être générée.</span><span class="sxs-lookup"><span data-stu-id="ffd76-104">The following statements show how this error can be generated.</span></span>  
  
```vb  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="ffd76-105">La première instruction `For Each` est la méthode correcte pour accéder aux éléments de `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="ffd76-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="ffd76-106">La deuxième instruction `For Each` génère cette erreur.</span><span class="sxs-lookup"><span data-stu-id="ffd76-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="ffd76-107">**ID d’erreur :** BC32039</span><span class="sxs-lookup"><span data-stu-id="ffd76-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ffd76-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ffd76-108">To correct this error</span></span>  
  
- <span data-ttu-id="ffd76-109">Supprimez l’initialisation de la déclaration de la variable d’itération de l' *élément* .</span><span class="sxs-lookup"><span data-stu-id="ffd76-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd76-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffd76-110">See also</span></span>

- [<span data-ttu-id="ffd76-111">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="ffd76-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="ffd76-112">Tableaux</span><span class="sxs-lookup"><span data-stu-id="ffd76-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="ffd76-113">Collections</span><span class="sxs-lookup"><span data-stu-id="ffd76-113">Collections</span></span>](../../../standard/collections/index.md)
