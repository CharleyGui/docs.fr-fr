---
title: Initialiseur attendu
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: cbe77bab3e4f8bf2094c70c1c16d95ee897c729e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163010"
---
# <a name="bc30996-initializer-expected"></a><span data-ttu-id="8e445-102">BC30996 : initialiseur ATTENDU</span><span class="sxs-lookup"><span data-stu-id="8e445-102">BC30996: Initializer expected</span></span>

<span data-ttu-id="8e445-103">Vous avez tenté de déclarer une instance d’une classe à l’aide d’un initialiseur d’objet dans lequel la liste d’initialisation est vide, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8e445-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 <span data-ttu-id="8e445-104">Au moins un champ ou une propriété doit être initialisé dans la liste d’initialiseurs, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8e445-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>

 `Dim aStudent As New Student With {.year = "Senior"}`

 <span data-ttu-id="8e445-105">**ID d’erreur :** BC30996</span><span class="sxs-lookup"><span data-stu-id="8e445-105">**Error ID:** BC30996</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8e445-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="8e445-106">To correct this error</span></span>

- <span data-ttu-id="8e445-107">Initialisez au moins un champ ou une propriété dans l’initialiseur, ou n’utilisez pas d’initialiseur d’objet.</span><span class="sxs-lookup"><span data-stu-id="8e445-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e445-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e445-108">See also</span></span>

- [<span data-ttu-id="8e445-109">Initialiseurs d'objets : types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="8e445-109">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="8e445-110">Comment : déclarer un objet à l'aide d'un initialiseur d'objet</span><span class="sxs-lookup"><span data-stu-id="8e445-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
