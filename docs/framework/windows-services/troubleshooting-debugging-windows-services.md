---
title: 'Résolution des problèmes : débogage des services Windows'
description: Prise en main du débogage des services Windows. Quand vous déboguez une application de service Windows, votre service et le Gestionnaire des services Windows interagissent.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
ms.openlocfilehash: 5846692fa0d90a62dd569253abbd81aa63b5798d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608892"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="4f384-104">Résolution des problèmes : débogage des services Windows</span><span class="sxs-lookup"><span data-stu-id="4f384-104">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="4f384-105">Quand vous déboguez une application de service Windows, votre service et le **Gestionnaire des services Windows** interagissent.</span><span class="sxs-lookup"><span data-stu-id="4f384-105">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="4f384-106">Le **Gestionnaire des services** démarre votre service en appelant la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, puis attend 30 secondes que la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="4f384-106">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="4f384-107">Si la méthode ne retourne aucune valeur au terme de ce délai, le gestionnaire affiche une erreur indiquant que le service ne peut pas être démarré.</span><span class="sxs-lookup"><span data-stu-id="4f384-107">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="4f384-108">Quand vous déboguez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> comme décrit dans [Guide pratique pour déboguer des applications de service Windows](how-to-debug-windows-service-applications.md), tenez compte de ce délai de 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="4f384-108">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="4f384-109">Si vous placez un point d’arrêt dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et que vous n’effectuez aucun pas à pas détaillé dans un délai de 30 secondes, le gestionnaire ne démarre pas le service.</span><span class="sxs-lookup"><span data-stu-id="4f384-109">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f384-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f384-110">See also</span></span>

- [<span data-ttu-id="4f384-111">Procédure : déboguer les applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="4f384-111">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="4f384-112">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="4f384-112">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
