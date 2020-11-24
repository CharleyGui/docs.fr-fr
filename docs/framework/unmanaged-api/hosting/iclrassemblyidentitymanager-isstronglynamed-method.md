---
title: ICLRAssemblyIdentityManager::IsStronglyNamed, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
ms.openlocfilehash: 9ac3b2ae349a696ba0cea1bad3e3484bb1c113fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679241"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="44550-102">ICLRAssemblyIdentityManager::IsStronglyNamed, méthode</span><span class="sxs-lookup"><span data-stu-id="44550-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>

<span data-ttu-id="44550-103">Obtient une valeur qui indique si l’assembly spécifié porte un nom fort.</span><span class="sxs-lookup"><span data-stu-id="44550-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44550-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44550-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44550-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="44550-105">Parameters</span></span>  

 `pwzAssemblyIdentity`  
 <span data-ttu-id="44550-106">dans Données d’identité de l’assembly canonique opaque de l’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="44550-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="44550-107">[out] `true` , si l’assembly référencé par le `pwzAssemblyIdentity` paramètre porte un nom fort ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="44550-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44550-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="44550-108">Return Value</span></span>  
  
|<span data-ttu-id="44550-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44550-109">HRESULT</span></span>|<span data-ttu-id="44550-110">Description</span><span class="sxs-lookup"><span data-stu-id="44550-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44550-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="44550-111">S_OK</span></span>|<span data-ttu-id="44550-112">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="44550-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="44550-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44550-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44550-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="44550-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44550-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44550-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44550-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="44550-116">The call timed out.</span></span>|  
|<span data-ttu-id="44550-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44550-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44550-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="44550-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44550-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44550-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44550-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="44550-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44550-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44550-121">E_FAIL</span></span>|<span data-ttu-id="44550-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="44550-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44550-123">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="44550-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44550-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44550-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44550-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="44550-125">Requirements</span></span>  

 <span data-ttu-id="44550-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44550-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44550-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="44550-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44550-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44550-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44550-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44550-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44550-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44550-130">See also</span></span>

- [<span data-ttu-id="44550-131">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="44550-131">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
