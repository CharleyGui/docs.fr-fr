---
title: ICLRAssemblyReferenceList, interface
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: f1aa40ef868bf6ff7730e01ab66a6fec58af1196
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615876"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="f0411-102">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="f0411-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="f0411-103">Gère une liste d’assemblys qui sont chargés par le common language runtime (CLR) et non par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="f0411-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0411-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f0411-104">Methods</span></span>  
  
|<span data-ttu-id="f0411-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f0411-105">Method</span></span>|<span data-ttu-id="f0411-106">Description</span><span class="sxs-lookup"><span data-stu-id="f0411-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0411-107">IsAssemblyReferenceInList, méthode</span><span class="sxs-lookup"><span data-stu-id="f0411-107">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="f0411-108">Obtient une valeur qui indique si le pointeur fourni référence un assembly de la liste.</span><span class="sxs-lookup"><span data-stu-id="f0411-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="f0411-109">IsStringAssemblyReferenceInList, méthode</span><span class="sxs-lookup"><span data-stu-id="f0411-109">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="f0411-110">Obtient une valeur qui indique si le nom fourni correspond au nom d’un assembly dans la liste.</span><span class="sxs-lookup"><span data-stu-id="f0411-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0411-111">Notes</span><span class="sxs-lookup"><span data-stu-id="f0411-111">Remarks</span></span>  
 <span data-ttu-id="f0411-112">Appelez la méthode [ICLRAssemblyIdentityManager :: GetCLRAssemblyReferenceList,](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) pour obtenir un pointeur vers une instance de `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="f0411-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0411-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="f0411-113">Requirements</span></span>  
 <span data-ttu-id="f0411-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0411-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0411-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0411-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0411-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f0411-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0411-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0411-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0411-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0411-118">See also</span></span>

- [<span data-ttu-id="f0411-119">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="f0411-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="f0411-120">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="f0411-120">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="f0411-121">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="f0411-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
