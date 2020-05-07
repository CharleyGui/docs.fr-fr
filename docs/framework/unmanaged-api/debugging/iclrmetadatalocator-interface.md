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
ms.openlocfilehash: 734f8eaa7c520bbf1ad1208ece42751e967a208a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859720"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="ef562-102">ICLRMetadataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="ef562-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="ef562-103">Utilisé par la couche des services d’accès aux données pour localiser les métadonnées des assemblys dans un processus cible.</span><span class="sxs-lookup"><span data-stu-id="ef562-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef562-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ef562-104">Methods</span></span>  
  
|<span data-ttu-id="ef562-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ef562-105">Method</span></span>|<span data-ttu-id="ef562-106">Description</span><span class="sxs-lookup"><span data-stu-id="ef562-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef562-107">GetMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="ef562-107">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="ef562-108">Récupère les métadonnées d’une image à partir du processus cible.</span><span class="sxs-lookup"><span data-stu-id="ef562-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef562-109">Notes </span><span class="sxs-lookup"><span data-stu-id="ef562-109">Remarks</span></span>  
 <span data-ttu-id="ef562-110">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="ef562-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="ef562-111">Par exemple, l’implémentation d’un processus actif est différente de celle d’une image mémoire.</span><span class="sxs-lookup"><span data-stu-id="ef562-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef562-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ef562-112">Requirements</span></span>  
 <span data-ttu-id="ef562-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef562-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef562-114">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ef562-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ef562-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef562-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef562-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef562-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef562-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef562-117">See also</span></span>

- [<span data-ttu-id="ef562-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ef562-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
