---
title: Débogage Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 91f311818b615ea8f166bb3362ec52d39fcd0297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790325"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="0930d-102">Débogage Silverlight</span><span class="sxs-lookup"><span data-stu-id="0930d-102">Silverlight Debugging</span></span>
<span data-ttu-id="0930d-103">Les rubriques de cette section décrivent l'environnement et les interfaces fournis par le Common Language Runtime (CLR) pour prendre en charge le débogage des applications Silverlight qui s'exécutent sur le système d'exploitation Windows ou sur la plateforme Macintosh.</span><span class="sxs-lookup"><span data-stu-id="0930d-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0930d-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0930d-104">In This Section</span></span>  
 [<span data-ttu-id="0930d-105">EnumerateCLRs, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-105">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="0930d-106">Fournit un mécanisme pour énumérer les CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="0930d-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="0930d-107">CloseCLREnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-107">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="0930d-108">Ferme tous les événements continue-Startup valides du CLR situés dans un tableau de handles retournés par la [fonction EnumerateCLRs](enumerateclrs-function.md)et libère la mémoire pour les tableaux de handles et de chemins d’accès de chaîne.</span><span class="sxs-lookup"><span data-stu-id="0930d-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="0930d-109">CreateCoreClrDebugTarget, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-109">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="0930d-110">Crée une connexion à une cible distante pour l'énumération des processus et du runtime.</span><span class="sxs-lookup"><span data-stu-id="0930d-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0930d-111">CreateCordbObject, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-111">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="0930d-112">Crée une interface de débogueur qui fournit les fonctionnalités d'instanciation d'une session de débogage managée sur un processus distant.</span><span class="sxs-lookup"><span data-stu-id="0930d-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="0930d-113">CreateVersionStringFromModule, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-113">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="0930d-114">Crée une chaîne de version à partir d'un chemin d'accès au CLR dans un processus cible.</span><span class="sxs-lookup"><span data-stu-id="0930d-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="0930d-115">CreateDebuggingInterfaceFromVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-115">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="0930d-116">Accepte une chaîne de version CLR retournée par la fonction de [fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md)et retourne une interface de débogueur correspondante.</span><span class="sxs-lookup"><span data-stu-id="0930d-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="0930d-117">CoreClrDebugProcInfo, structure</span><span class="sxs-lookup"><span data-stu-id="0930d-117">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="0930d-118">Représente un processus qui s'exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="0930d-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="0930d-119">CoreClrDebugRuntimeInfo, structure</span><span class="sxs-lookup"><span data-stu-id="0930d-119">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="0930d-120">Représente une instance du CLR qui est chargée dans un processus sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="0930d-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="0930d-121">GetStartupNotificationEvent, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-121">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="0930d-122">Crée ou ouvre un gestionnaire d'événements qui sera signalé par un Common Language Runtime (CLR) qui est chargé dans le processus cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="0930d-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="0930d-123">ICoreClrDebugTarget, interface</span><span class="sxs-lookup"><span data-stu-id="0930d-123">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="0930d-124">Crée une connexion à une cible distante pour l'énumération des processus et du runtime.</span><span class="sxs-lookup"><span data-stu-id="0930d-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0930d-125">InitDbgTransportManager, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-125">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="0930d-126">Initialise le gestionnaire de transport pour se connecter à une cible distante pour l'énumération des processus et du runtime.</span><span class="sxs-lookup"><span data-stu-id="0930d-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0930d-127">ShutdownDbgTransportManager, fonction</span><span class="sxs-lookup"><span data-stu-id="0930d-127">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="0930d-128">Arrête le gestionnaire de transport pour une connexion à un ordinateur cible distant.</span><span class="sxs-lookup"><span data-stu-id="0930d-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0930d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0930d-129">See also</span></span>

- [<span data-ttu-id="0930d-130">Coclasses de débogage</span><span class="sxs-lookup"><span data-stu-id="0930d-130">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="0930d-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0930d-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0930d-132">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="0930d-132">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="0930d-133">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="0930d-133">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="0930d-134">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="0930d-134">Debugging Structures</span></span>](debugging-structures.md)
