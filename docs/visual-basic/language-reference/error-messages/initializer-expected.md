---
title: Initialiseur attendu
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 2c5a65443dc16a600e25fcf6dfd11c4597b3a086
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873947"
---
# <a name="initializer-expected"></a><span data-ttu-id="f7695-102">Initialiseur attendu</span><span class="sxs-lookup"><span data-stu-id="f7695-102">Initializer expected</span></span>

<span data-ttu-id="f7695-103">Vous avez tenté de déclarer une instance d’une classe à l’aide d’un initialiseur d’objet dans lequel la liste d’initialisation est vide, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f7695-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="f7695-104">Au moins un champ ou une propriété doit être initialisé dans la liste d’initialiseurs, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f7695-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="f7695-105">**ID d’erreur :** BC30996</span><span class="sxs-lookup"><span data-stu-id="f7695-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7695-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f7695-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f7695-107">Initialisez au moins un champ ou une propriété dans l’initialiseur, ou n’utilisez pas d’initialiseur d’objet.</span><span class="sxs-lookup"><span data-stu-id="f7695-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7695-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7695-108">See also</span></span>

- [<span data-ttu-id="f7695-109">Initialiseurs d'objets : types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="f7695-109">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f7695-110">Comment : déclarer un objet à l'aide d'un initialiseur d'objet</span><span class="sxs-lookup"><span data-stu-id="f7695-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
