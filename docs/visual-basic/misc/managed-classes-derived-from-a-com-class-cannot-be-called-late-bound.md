---
title: Les classes managées dérivées d’une classe COM ne peuvent pas être appelées à liaison tardive
ms.date: 07/20/2015
f1_keywords:
- vbrLateboundCallToInheritedComClass
ms.assetid: 7bc16e84-8d29-4f8e-bc4f-002c65c71099
ms.openlocfilehash: 401cb5d7194cbef616c87d59e5b1ed7f923fe6f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402120"
---
# <a name="managed-classes-derived-from-a-com-class-cannot-be-called-late-bound"></a><span data-ttu-id="ad6a6-102">Les classes managées dérivées d’une classe COM ne peuvent pas être appelées à liaison tardive</span><span class="sxs-lookup"><span data-stu-id="ad6a6-102">Managed classes derived from a COM class cannot be called late-bound.</span></span>

<span data-ttu-id="ad6a6-103">Vous avez tenté d’effectuer un appel à liaison tardive vers une classe managée dérivée d’une classe COM. Ces appels ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ad6a6-103">You attempted to make a late-bound call to a managed class derived from a COM Class; such calls are not supported.</span></span>

## <a name="to-correct-the-problem"></a><span data-ttu-id="ad6a6-104">Pour corriger le problème</span><span class="sxs-lookup"><span data-stu-id="ad6a6-104">To correct the problem</span></span>

<span data-ttu-id="ad6a6-105">Effectuez un appel à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="ad6a6-105">Make the call early bound.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad6a6-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad6a6-106">See also</span></span>

- [<span data-ttu-id="ad6a6-107">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="ad6a6-107">Error Types</span></span>](../programming-guide/language-features/error-types.md)
