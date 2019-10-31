---
title: Erreur Automation
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 25c3b71eb818223c58ab17d9be885033a5d4ded0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197033"
---
# <a name="automation-error"></a><span data-ttu-id="2ae03-102">Erreur Automation</span><span class="sxs-lookup"><span data-stu-id="2ae03-102">Automation error</span></span>
<span data-ttu-id="2ae03-103">Une erreur s'est produite pendant l'exécution d'une méthode ou l'obtention / la définition d'une propriété de variable objet.</span><span class="sxs-lookup"><span data-stu-id="2ae03-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="2ae03-104">L'application qui a créé l'objet a signalé l'erreur.</span><span class="sxs-lookup"><span data-stu-id="2ae03-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ae03-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2ae03-105">To correct this error</span></span>  
  
1. <span data-ttu-id="2ae03-106">Vérifiez les propriétés de l'objet `Err` pour déterminer la source et la nature de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="2ae03-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="2ae03-107">Utilisez l’instruction `On Error Resume Next` immédiatement avant l’instruction d’accès, puis recherchez les erreurs immédiatement après l’accès à l’instruction.</span><span class="sxs-lookup"><span data-stu-id="2ae03-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae03-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ae03-108">See also</span></span>

- [<span data-ttu-id="2ae03-109">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="2ae03-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="2ae03-110">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="2ae03-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
