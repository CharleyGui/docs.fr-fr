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
ms.openlocfilehash: 6b2700b2f12e312f06640a06e5ec82fbc58f2ca9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860464"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="13cb3-102">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="13cb3-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="13cb3-103">Sous-classe de [ICLRDataTarget](iclrdatatarget-interface.md) qui est utilisée par la couche des services d’accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="13cb3-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13cb3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="13cb3-104">Methods</span></span>  
  
|<span data-ttu-id="13cb3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="13cb3-105">Method</span></span>|<span data-ttu-id="13cb3-106">Description</span><span class="sxs-lookup"><span data-stu-id="13cb3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13cb3-107">AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="13cb3-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="13cb3-108">Alloue de la mémoire dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="13cb3-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="13cb3-109">FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="13cb3-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="13cb3-110">Libère de la mémoire qui a été précédemment allouée dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="13cb3-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13cb3-111">Notes </span><span class="sxs-lookup"><span data-stu-id="13cb3-111">Remarks</span></span>  
 <span data-ttu-id="13cb3-112">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="13cb3-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="13cb3-113">Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="13cb3-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="13cb3-114">La cible ne prend peut-être pas en charge la modification de ses régions de mémoire.</span><span class="sxs-lookup"><span data-stu-id="13cb3-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13cb3-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="13cb3-115">Requirements</span></span>  
 <span data-ttu-id="13cb3-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13cb3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13cb3-117">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="13cb3-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="13cb3-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13cb3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13cb3-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13cb3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13cb3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13cb3-120">See also</span></span>

- [<span data-ttu-id="13cb3-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="13cb3-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="13cb3-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="13cb3-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
