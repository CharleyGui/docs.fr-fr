---
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
ms.openlocfilehash: cfc384a71ac7e91181bdec09f0d385bacbe31753
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716666"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="5e4f3-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList, méthode</span><span class="sxs-lookup"><span data-stu-id="5e4f3-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>

<span data-ttu-id="5e4f3-103">Obtient un pointeur d’interface vers une instance [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) à partir de la liste d’identités d’assembly partielle fournie.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e4f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e4f3-104">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e4f3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e4f3-105">Parameters</span></span>  

 `ppwzAssemblyReferences`  
 <span data-ttu-id="5e4f3-106">dans Tableau de chaînes terminées par le caractère null sous la forme « name, Property = value... » qui spécifient une liste d’identités d’assembly partielles.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="5e4f3-107">dans Nombre d’éléments dans `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="5e4f3-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="5e4f3-108">à Pointeur d’interface vers un `ICLRAssemblyReferenceList` objet qui contient les données d’identité de l’assembly pour la liste d’assemblys spécifiée dans `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="5e4f3-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e4f3-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5e4f3-109">Return Value</span></span>  
  
|<span data-ttu-id="5e4f3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e4f3-110">HRESULT</span></span>|<span data-ttu-id="5e4f3-111">Description</span><span class="sxs-lookup"><span data-stu-id="5e4f3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e4f3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e4f3-112">S_OK</span></span>|<span data-ttu-id="5e4f3-113">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="5e4f3-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e4f3-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e4f3-115">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e4f3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e4f3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e4f3-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-117">The call timed out.</span></span>|  
|<span data-ttu-id="5e4f3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e4f3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e4f3-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e4f3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e4f3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e4f3-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e4f3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e4f3-122">E_FAIL</span></span>|<span data-ttu-id="5e4f3-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e4f3-124">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e4f3-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5e4f3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e4f3-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5e4f3-126">Requirements</span></span>  

 <span data-ttu-id="5e4f3-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f3-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e4f3-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5e4f3-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e4f3-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e4f3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e4f3-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e4f3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4f3-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e4f3-131">See also</span></span>

- [<span data-ttu-id="5e4f3-132">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="5e4f3-132">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="5e4f3-133">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="5e4f3-133">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
