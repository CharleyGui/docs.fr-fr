---
title: IHostIoCompletionManager, interface
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 095872f8d4bd4f7d3351b8b3e3f8f8445b615cd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501534"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="6344b-102">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="6344b-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="6344b-103">Fournit des méthodes qui permettent au common language runtime (CLR) d’interagir avec les ports de terminaison d’e/s fournis par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="6344b-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6344b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6344b-104">Methods</span></span>  
  
|<span data-ttu-id="6344b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-105">Method</span></span>|<span data-ttu-id="6344b-106">Description</span><span class="sxs-lookup"><span data-stu-id="6344b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6344b-107">Bind, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-107">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="6344b-108">Lie un handle à un port de terminaison d’e/s.</span><span class="sxs-lookup"><span data-stu-id="6344b-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="6344b-109">CloseIoCompletionPort, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-109">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="6344b-110">Ferme un port qui a été créé à l’aide d’un appel antérieur à `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="6344b-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="6344b-111">CreateIoCompletionPort, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-111">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="6344b-112">Demande que l’hôte crée un port de terminaison d’e/s.</span><span class="sxs-lookup"><span data-stu-id="6344b-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="6344b-113">GetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-113">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="6344b-114">Obtient le nombre de threads de terminaison d’e/s qui ne sont pas en cours de traitement des demandes.</span><span class="sxs-lookup"><span data-stu-id="6344b-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="6344b-115">GetHostOverlappedSize, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-115">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="6344b-116">Obtient la taille des données personnalisées que l’hôte envisage d’ajouter aux demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="6344b-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="6344b-117">GetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-117">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="6344b-118">Obtient le nombre maximal de threads que l’hôte peut allouer aux demandes d’e/s de service.</span><span class="sxs-lookup"><span data-stu-id="6344b-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="6344b-119">GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-119">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="6344b-120">Obtient le nombre minimal de threads que l’hôte fournit pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="6344b-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="6344b-121">InitializeHostOverlapped, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-121">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="6344b-122">Fournit à l’hôte la possibilité d’initialiser toutes les données personnalisées relatives à une demande d’e/s.</span><span class="sxs-lookup"><span data-stu-id="6344b-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="6344b-123">SetCLRIoCompletionManager, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-123">SetCLRIoCompletionManager Method</span></span>](ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="6344b-124">Fournit à l’hôte un pointeur d’interface vers une instance [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) implémentée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="6344b-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="6344b-125">SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-125">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="6344b-126">Définit le nombre maximal de threads que l’hôte alloue aux demandes d’e/s de service.</span><span class="sxs-lookup"><span data-stu-id="6344b-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="6344b-127">SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="6344b-127">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="6344b-128">Définit le nombre minimal de threads que l’hôte doit allouer à l’achèvement d’e/s.</span><span class="sxs-lookup"><span data-stu-id="6344b-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6344b-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="6344b-129">Remarks</span></span>  
 <span data-ttu-id="6344b-130">`IHostIoCompletionManager`correspond à l' `ICLRIoCompletionManager` interface implémentée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="6344b-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="6344b-131">Le CLR appelle les méthodes de `IHostIoCompletionManager` pour lier des handles aux ports fournis par l’hôte, et l’hôte appelle les méthodes de `ICLRIoCompletionManager` pour signaler l’achèvement des demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="6344b-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6344b-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6344b-132">Requirements</span></span>  
 <span data-ttu-id="6344b-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6344b-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6344b-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6344b-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6344b-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6344b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6344b-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6344b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6344b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6344b-137">See also</span></span>

- [<span data-ttu-id="6344b-138">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="6344b-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
