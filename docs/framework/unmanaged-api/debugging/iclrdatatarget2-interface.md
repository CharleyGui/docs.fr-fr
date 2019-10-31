---
title: ICLRDataTarget2, interface
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: 1f0f4331302e56a90b4aefd657e07981994022ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112314"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="72a24-102">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="72a24-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="72a24-103">Sous-classe de [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) qui est utilisée par la couche des services d’accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="72a24-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72a24-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="72a24-104">Methods</span></span>  
  
|<span data-ttu-id="72a24-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="72a24-105">Method</span></span>|<span data-ttu-id="72a24-106">Description</span><span class="sxs-lookup"><span data-stu-id="72a24-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72a24-107">AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="72a24-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="72a24-108">Alloue de la mémoire dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="72a24-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="72a24-109">FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="72a24-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="72a24-110">Libère de la mémoire qui a été précédemment allouée dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="72a24-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72a24-111">Notes</span><span class="sxs-lookup"><span data-stu-id="72a24-111">Remarks</span></span>  
 <span data-ttu-id="72a24-112">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="72a24-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="72a24-113">Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="72a24-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="72a24-114">La cible ne prend peut-être pas en charge la modification de ses régions de mémoire.</span><span class="sxs-lookup"><span data-stu-id="72a24-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a24-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="72a24-115">Requirements</span></span>  
 <span data-ttu-id="72a24-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a24-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a24-117">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="72a24-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="72a24-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72a24-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72a24-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a24-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a24-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72a24-120">See also</span></span>

- [<span data-ttu-id="72a24-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="72a24-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="72a24-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="72a24-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
