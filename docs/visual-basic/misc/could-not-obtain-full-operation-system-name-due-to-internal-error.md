---
title: Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 744d549b9313727af2feb82e45c24b729cae7262
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079085"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="6cadc-102">Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne</span><span class="sxs-lookup"><span data-stu-id="6cadc-102">Could not obtain full operation system name due to internal error</span></span>

<span data-ttu-id="6cadc-103">Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne.</span><span class="sxs-lookup"><span data-stu-id="6cadc-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="6cadc-104">Ceci peut être dû au fait que WMI est absent de l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="6cadc-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="6cadc-105">Un appel à la propriété `My.Computer.Info.OSFullName` a échoué.</span><span class="sxs-lookup"><span data-stu-id="6cadc-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="6cadc-106">WMI (Windows Management Instrumentation) n’est peut-être pas installé sur l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="6cadc-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6cadc-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6cadc-107">To correct this error</span></span>  
  
1. <span data-ttu-id="6cadc-108">Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété `My.Computer.Info.OSFullName` .</span><span class="sxs-lookup"><span data-stu-id="6cadc-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="6cadc-109">Pour plus d’informations sur WMI et son installation, consultez la rubrique et recherchez « Windows Management Instrumentation Core ».</span><span class="sxs-lookup"><span data-stu-id="6cadc-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cadc-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cadc-110">See also</span></span>

- [<span data-ttu-id="6cadc-111">My. Computer. info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="6cadc-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="6cadc-112">Gestion et levée d’exceptions dans .NET</span><span class="sxs-lookup"><span data-stu-id="6cadc-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="6cadc-113">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="6cadc-113">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
