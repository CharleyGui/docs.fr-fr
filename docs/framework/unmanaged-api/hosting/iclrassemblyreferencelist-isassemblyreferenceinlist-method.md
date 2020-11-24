---
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
ms.openlocfilehash: f74e0f111ff7869d0bfed61d420f3788f65876dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679154"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="71fd3-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList, méthode</span><span class="sxs-lookup"><span data-stu-id="71fd3-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>

<span data-ttu-id="71fd3-103">Obtient une valeur qui indique si le pointeur fourni fait référence à un assembly dans la liste.</span><span class="sxs-lookup"><span data-stu-id="71fd3-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71fd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71fd3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71fd3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="71fd3-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="71fd3-106">dans Pointeur d’interface vers l’assembly pour lequel effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="71fd3-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="71fd3-107">Les valeurs valides sont de type `IAssemblyName` ou `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="71fd3-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71fd3-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="71fd3-108">Return Value</span></span>  
  
|<span data-ttu-id="71fd3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71fd3-109">HRESULT</span></span>|<span data-ttu-id="71fd3-110">Description</span><span class="sxs-lookup"><span data-stu-id="71fd3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71fd3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="71fd3-111">S_OK</span></span>|<span data-ttu-id="71fd3-112">La chaîne apparaît dans la liste.</span><span class="sxs-lookup"><span data-stu-id="71fd3-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="71fd3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="71fd3-113">S_FALSE</span></span>|<span data-ttu-id="71fd3-114">La chaîne n’apparaît pas dans la liste.</span><span class="sxs-lookup"><span data-stu-id="71fd3-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="71fd3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71fd3-115">E_FAIL</span></span>|<span data-ttu-id="71fd3-116">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="71fd3-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71fd3-117">Une fois que la méthode a retourné E_FAIL, le common language runtime n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="71fd3-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="71fd3-118">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="71fd3-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71fd3-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="71fd3-119">Requirements</span></span>  

 <span data-ttu-id="71fd3-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71fd3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71fd3-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="71fd3-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71fd3-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="71fd3-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71fd3-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71fd3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71fd3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71fd3-124">See also</span></span>

- [<span data-ttu-id="71fd3-125">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="71fd3-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="71fd3-126">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="71fd3-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="71fd3-127">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="71fd3-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="71fd3-128">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="71fd3-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
