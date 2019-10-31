---
title: ICLRDataTarget, interface
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 51b246e45b8bbdf809f5e90ac2bc29ca724751fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113488"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="b6a7c-102">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="b6a7c-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="b6a7c-103">Fournit des méthodes pour l’interaction avec un élément cible du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b6a7c-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6a7c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b6a7c-104">Methods</span></span>  
  
|<span data-ttu-id="b6a7c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-105">Method</span></span>|<span data-ttu-id="b6a7c-106">Description</span><span class="sxs-lookup"><span data-stu-id="b6a7c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6a7c-107">GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="b6a7c-108">Obtient l’identificateur de système d’exploitation pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="b6a7c-109">GetImageBase, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="b6a7c-110">Obtient l’adresse mémoire de base pour l’image spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="b6a7c-111">GetMachineType, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="b6a7c-112">Obtient un identificateur pour le type de jeu d’instructions que le processus cible utilise.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="b6a7c-113">GetPointerSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="b6a7c-114">Obtient la taille, en octets, d’un pointeur vers la cible actuelle.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="b6a7c-115">GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="b6a7c-116">Obtient un pointeur vers le contexte du thread avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="b6a7c-117">GetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="b6a7c-118">Obtient une valeur dans le stockage local des threads (TLS) à l’index spécifié pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="b6a7c-119">ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="b6a7c-120">Lit les données à partir de l’adresse mémoire virtuelle spécifiée dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="b6a7c-121">Request, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="b6a7c-122">Appelée par les services d’accès aux données common language runtime (CLR) pour demander une opération, comme défini par l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="b6a7c-123">SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="b6a7c-124">Définit le contexte actuel du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="b6a7c-125">SetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="b6a7c-126">Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="b6a7c-127">WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="b6a7c-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="b6a7c-128">Écrit des données à partir de la mémoire tampon spécifiée dans l’adresse mémoire virtuelle spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6a7c-129">Notes</span><span class="sxs-lookup"><span data-stu-id="b6a7c-129">Remarks</span></span>  
 <span data-ttu-id="b6a7c-130">Le client API (autrement dit, le débogueur) doit implémenter cette interface en fonction de l’élément cible particulier.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="b6a7c-131">Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="b6a7c-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6a7c-132">spécifications</span><span class="sxs-lookup"><span data-stu-id="b6a7c-132">Requirements</span></span>  
 <span data-ttu-id="b6a7c-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6a7c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6a7c-134">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b6a7c-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b6a7c-135">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6a7c-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6a7c-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6a7c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a7c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6a7c-137">See also</span></span>

- [<span data-ttu-id="b6a7c-138">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="b6a7c-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="b6a7c-139">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b6a7c-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
