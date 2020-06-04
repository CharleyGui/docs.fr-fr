---
title: Erreur Automation
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: d62ba57db8bffefb2cfebed705251d87fe285602
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409892"
---
# <a name="automation-error"></a><span data-ttu-id="d9569-102">Erreur Automation</span><span class="sxs-lookup"><span data-stu-id="d9569-102">Automation error</span></span>

<span data-ttu-id="d9569-103">Une erreur s'est produite pendant l'exécution d'une méthode ou l'obtention / la définition d'une propriété de variable objet.</span><span class="sxs-lookup"><span data-stu-id="d9569-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="d9569-104">L'application qui a créé l'objet a signalé l'erreur.</span><span class="sxs-lookup"><span data-stu-id="d9569-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9569-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d9569-105">To correct this error</span></span>  
  
1. <span data-ttu-id="d9569-106">Vérifiez les propriétés de l'objet `Err` pour déterminer la source et la nature de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="d9569-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="d9569-107">Utilisez l' `On Error Resume Next` instruction juste avant l’instruction d’accès, puis recherchez les erreurs immédiatement après l’accès à l’instruction.</span><span class="sxs-lookup"><span data-stu-id="d9569-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9569-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9569-108">See also</span></span>

- [<span data-ttu-id="d9569-109">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="d9569-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="d9569-110">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="d9569-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
