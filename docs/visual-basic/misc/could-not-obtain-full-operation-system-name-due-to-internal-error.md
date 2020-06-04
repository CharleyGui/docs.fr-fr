---
title: Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 67e8fb5e906800d28bf15714463b7ff6ae585693
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402276"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="228f2-102">Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne</span><span class="sxs-lookup"><span data-stu-id="228f2-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="228f2-103">Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne.</span><span class="sxs-lookup"><span data-stu-id="228f2-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="228f2-104">Ceci peut être dû au fait que WMI est absent de l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="228f2-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="228f2-105">Un appel à la propriété `My.Computer.Info.OSFullName` a échoué.</span><span class="sxs-lookup"><span data-stu-id="228f2-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="228f2-106">WMI (Windows Management Instrumentation) n’est peut-être pas installé sur l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="228f2-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="228f2-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="228f2-107">To correct this error</span></span>  
  
1. <span data-ttu-id="228f2-108">Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété `My.Computer.Info.OSFullName` .</span><span class="sxs-lookup"><span data-stu-id="228f2-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="228f2-109">Pour plus d’informations sur WMI et son installation, consultez la rubrique et recherchez « Windows Management Instrumentation Core ».</span><span class="sxs-lookup"><span data-stu-id="228f2-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228f2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="228f2-110">See also</span></span>

- [<span data-ttu-id="228f2-111">My. Computer. info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="228f2-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="228f2-112">Gestion et levée d’exceptions dans .NET</span><span class="sxs-lookup"><span data-stu-id="228f2-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="228f2-113">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="228f2-113">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
