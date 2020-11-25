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
ms.openlocfilehash: dee5108439610b67c3397cebcd8ee5f84d4eacea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723634"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="eda99-102">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="eda99-102">ICLRDataTarget2 Interface</span></span>

<span data-ttu-id="eda99-103">Sous-classe de [ICLRDataTarget](iclrdatatarget-interface.md) qui est utilisée par la couche des services d’accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="eda99-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eda99-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="eda99-104">Methods</span></span>  
  
|<span data-ttu-id="eda99-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="eda99-105">Method</span></span>|<span data-ttu-id="eda99-106">Description</span><span class="sxs-lookup"><span data-stu-id="eda99-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eda99-107">AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="eda99-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="eda99-108">Alloue de la mémoire dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="eda99-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="eda99-109">FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="eda99-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="eda99-110">Libère de la mémoire qui a été précédemment allouée dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="eda99-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eda99-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="eda99-111">Remarks</span></span>  

 <span data-ttu-id="eda99-112">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="eda99-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="eda99-113">Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="eda99-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="eda99-114">La cible ne prend peut-être pas en charge la modification de ses régions de mémoire.</span><span class="sxs-lookup"><span data-stu-id="eda99-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda99-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eda99-115">Requirements</span></span>  

 <span data-ttu-id="eda99-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eda99-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eda99-117">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="eda99-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="eda99-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eda99-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eda99-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eda99-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda99-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eda99-120">See also</span></span>

- [<span data-ttu-id="eda99-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="eda99-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="eda99-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="eda99-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
