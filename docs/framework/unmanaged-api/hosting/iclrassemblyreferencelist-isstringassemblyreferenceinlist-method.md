---
title: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
ms.openlocfilehash: 74d47b3f55c10f65d47f726a2b96ba5e0b18b749
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679141"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="98888-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList, méthode</span><span class="sxs-lookup"><span data-stu-id="98888-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>

<span data-ttu-id="98888-103">Obtient une valeur qui indique si le nom fourni correspond au nom d’un assembly dans la liste.</span><span class="sxs-lookup"><span data-stu-id="98888-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98888-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98888-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98888-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="98888-105">Parameters</span></span>  

 `pwzAssemblyName`  
 <span data-ttu-id="98888-106">dans Nom de l’assembly à rechercher.</span><span class="sxs-lookup"><span data-stu-id="98888-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98888-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="98888-107">Return Value</span></span>  
  
|<span data-ttu-id="98888-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98888-108">HRESULT</span></span>|<span data-ttu-id="98888-109">Description</span><span class="sxs-lookup"><span data-stu-id="98888-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98888-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="98888-110">S_OK</span></span>|<span data-ttu-id="98888-111">La chaîne apparaît dans la liste.</span><span class="sxs-lookup"><span data-stu-id="98888-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="98888-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="98888-112">S_FALSE</span></span>|<span data-ttu-id="98888-113">La chaîne n’apparaît pas dans la liste.</span><span class="sxs-lookup"><span data-stu-id="98888-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="98888-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98888-114">E_FAIL</span></span>|<span data-ttu-id="98888-115">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="98888-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98888-116">Une fois que la méthode a retourné E_FAIL, le common language runtime n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="98888-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="98888-117">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="98888-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98888-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="98888-118">Requirements</span></span>  

 <span data-ttu-id="98888-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98888-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98888-120">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98888-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98888-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98888-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98888-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98888-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98888-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98888-123">See also</span></span>

- [<span data-ttu-id="98888-124">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="98888-124">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="98888-125">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="98888-125">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="98888-126">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="98888-126">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="98888-127">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="98888-127">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
