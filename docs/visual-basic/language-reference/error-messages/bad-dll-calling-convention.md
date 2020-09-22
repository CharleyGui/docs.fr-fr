---
title: Convention d’appel de DLL incorrecte
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 0481bd5e4dfe7a24dff454d0754b519509fa967f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875734"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="ab936-102">Convention d’appel de DLL incorrecte</span><span class="sxs-lookup"><span data-stu-id="ab936-102">Bad DLL calling convention</span></span>

<span data-ttu-id="ab936-103">Les arguments passés à une bibliothèque de liens dynamiques (DLL) doivent correspondre exactement à ceux attendus par la routine.</span><span class="sxs-lookup"><span data-stu-id="ab936-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="ab936-104">Les conventions d’appel traitent le nombre, le type et l’ordre des arguments.</span><span class="sxs-lookup"><span data-stu-id="ab936-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="ab936-105">Votre programme peut appeler une routine dans une DLL qui reçoit un type ou un nombre d’arguments incorrect.</span><span class="sxs-lookup"><span data-stu-id="ab936-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab936-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ab936-106">To correct this error</span></span>  
  
1. <span data-ttu-id="ab936-107">Assurez-vous que tous les types d’arguments correspondent à ceux spécifiés dans la déclaration de la routine que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="ab936-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="ab936-108">Assurez-vous que vous passez le même nombre d’arguments spécifiés dans la déclaration de la routine que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="ab936-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="ab936-109">Si la routine DLL attend des arguments par valeur, assurez-vous que `ByVal` est spécifié pour ces arguments dans la déclaration pour la routine.</span><span class="sxs-lookup"><span data-stu-id="ab936-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab936-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab936-110">See also</span></span>

- [<span data-ttu-id="ab936-111">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="ab936-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="ab936-112">Call (instruction)</span><span class="sxs-lookup"><span data-stu-id="ab936-112">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="ab936-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="ab936-113">Declare Statement</span></span>](../statements/declare-statement.md)
