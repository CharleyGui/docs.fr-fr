---
title: ICLRMetadataLocator, interface
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
ms.openlocfilehash: ec92214e33cd1acda8b2702d93deba1f0fb2aaa2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111029"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="76243-102">ICLRMetadataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="76243-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="76243-103">Utilisé par la couche des services d’accès aux données pour localiser les métadonnées des assemblys dans un processus cible.</span><span class="sxs-lookup"><span data-stu-id="76243-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="76243-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="76243-104">Methods</span></span>  
  
|<span data-ttu-id="76243-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="76243-105">Method</span></span>|<span data-ttu-id="76243-106">Description</span><span class="sxs-lookup"><span data-stu-id="76243-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="76243-107">GetMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="76243-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="76243-108">Récupère les métadonnées d’une image à partir du processus cible.</span><span class="sxs-lookup"><span data-stu-id="76243-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76243-109">Notes</span><span class="sxs-lookup"><span data-stu-id="76243-109">Remarks</span></span>  
 <span data-ttu-id="76243-110">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="76243-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="76243-111">Par exemple, l’implémentation d’un processus actif est différente de celle d’une image mémoire.</span><span class="sxs-lookup"><span data-stu-id="76243-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76243-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="76243-112">Requirements</span></span>  
 <span data-ttu-id="76243-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76243-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76243-114">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="76243-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="76243-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76243-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76243-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76243-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76243-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76243-117">See also</span></span>

- [<span data-ttu-id="76243-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="76243-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
