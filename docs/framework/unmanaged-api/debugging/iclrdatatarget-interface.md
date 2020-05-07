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
ms.openlocfilehash: 30806394a8895084068acaec6f7d03c6b67bb14b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860568"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="e9dd1-102">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="e9dd1-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="e9dd1-103">Fournit des méthodes pour l’interaction avec un élément cible du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e9dd1-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9dd1-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e9dd1-104">Methods</span></span>  
  
|<span data-ttu-id="e9dd1-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-105">Method</span></span>|<span data-ttu-id="e9dd1-106">Description</span><span class="sxs-lookup"><span data-stu-id="e9dd1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9dd1-107">GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-107">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="e9dd1-108">Obtient l’identificateur de système d’exploitation pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="e9dd1-109">GetImageBase, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-109">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="e9dd1-110">Obtient l’adresse mémoire de base pour l’image spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="e9dd1-111">GetMachineType, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-111">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="e9dd1-112">Obtient un identificateur pour le type de jeu d’instructions que le processus cible utilise.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="e9dd1-113">GetPointerSize, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-113">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="e9dd1-114">Obtient la taille, en octets, d’un pointeur vers la cible actuelle.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="e9dd1-115">GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-115">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="e9dd1-116">Obtient un pointeur vers le contexte du thread avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="e9dd1-117">GetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-117">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="e9dd1-118">Obtient une valeur dans le stockage local des threads (TLS) à l’index spécifié pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="e9dd1-119">ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-119">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="e9dd1-120">Lit les données à partir de l’adresse mémoire virtuelle spécifiée dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="e9dd1-121">Méthode de demande</span><span class="sxs-lookup"><span data-stu-id="e9dd1-121">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="e9dd1-122">Appelée par les services d’accès aux données common language runtime (CLR) pour demander une opération, comme défini par l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="e9dd1-123">SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-123">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="e9dd1-124">Définit le contexte actuel du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="e9dd1-125">SetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-125">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="e9dd1-126">Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="e9dd1-127">WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="e9dd1-127">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="e9dd1-128">Écrit des données à partir de la mémoire tampon spécifiée dans l’adresse mémoire virtuelle spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9dd1-129">Notes </span><span class="sxs-lookup"><span data-stu-id="e9dd1-129">Remarks</span></span>  
 <span data-ttu-id="e9dd1-130">Le client API (autrement dit, le débogueur) doit implémenter cette interface en fonction de l’élément cible particulier.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="e9dd1-131">Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e9dd1-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9dd1-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e9dd1-132">Requirements</span></span>  
 <span data-ttu-id="e9dd1-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9dd1-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9dd1-134">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e9dd1-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e9dd1-135">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9dd1-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9dd1-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9dd1-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9dd1-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9dd1-137">See also</span></span>

- [<span data-ttu-id="e9dd1-138">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="e9dd1-138">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="e9dd1-139">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e9dd1-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
