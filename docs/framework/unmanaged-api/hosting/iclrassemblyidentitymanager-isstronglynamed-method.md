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
ms.openlocfilehash: 288620eba867160e13a5ebee501a9afcf5623cce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126649"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="bf019-102">ICLRAssemblyIdentityManager::IsStronglyNamed, méthode</span><span class="sxs-lookup"><span data-stu-id="bf019-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="bf019-103">Obtient une valeur qui indique si l’assembly spécifié porte un nom fort.</span><span class="sxs-lookup"><span data-stu-id="bf019-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf019-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf019-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf019-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf019-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="bf019-106">dans Données d’identité de l’assembly canonique opaque de l’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="bf019-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="bf019-107">[out] `true`, si l’assembly référencé par le paramètre `pwzAssemblyIdentity` porte un nom fort ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="bf019-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf019-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bf019-108">Return Value</span></span>  
  
|<span data-ttu-id="bf019-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf019-109">HRESULT</span></span>|<span data-ttu-id="bf019-110">Description</span><span class="sxs-lookup"><span data-stu-id="bf019-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf019-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf019-111">S_OK</span></span>|<span data-ttu-id="bf019-112">La méthode a été retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="bf019-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="bf019-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bf019-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf019-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="bf019-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bf019-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf019-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf019-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="bf019-116">The call timed out.</span></span>|  
|<span data-ttu-id="bf019-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf019-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf019-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="bf019-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf019-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf019-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf019-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="bf019-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf019-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf019-121">E_FAIL</span></span>|<span data-ttu-id="bf019-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="bf019-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf019-123">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="bf019-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf019-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bf019-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf019-125">spécifications</span><span class="sxs-lookup"><span data-stu-id="bf019-125">Requirements</span></span>  
 <span data-ttu-id="bf019-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf019-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf019-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bf019-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf019-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bf019-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf019-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf019-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf019-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf019-130">See also</span></span>

- [<span data-ttu-id="bf019-131">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="bf019-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
