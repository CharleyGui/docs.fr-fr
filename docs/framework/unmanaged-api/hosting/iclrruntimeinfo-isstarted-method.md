---
title: ICLRRuntimeInfo::IsStarted, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 432de909e1b8166f6d8923889382d9408fb6c62d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490260"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="55f9a-102">ICLRRuntimeInfo::IsStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="55f9a-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="55f9a-103">Indique si le runtime a été démarré (autrement dit, si le [méthode ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) a été appelé et a réussi).</span><span class="sxs-lookup"><span data-stu-id="55f9a-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55f9a-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55f9a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="55f9a-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="55f9a-106">[out] `true` si cette exécution est démarrée ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="55f9a-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="55f9a-107">[out] Retourne les indicateurs qui ont été utilisés pour démarrer le runtime.</span><span class="sxs-lookup"><span data-stu-id="55f9a-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f9a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="55f9a-108">Return Value</span></span>  
 <span data-ttu-id="55f9a-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="55f9a-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="55f9a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55f9a-110">HRESULT</span></span>|<span data-ttu-id="55f9a-111">Description</span><span class="sxs-lookup"><span data-stu-id="55f9a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55f9a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="55f9a-112">S_OK</span></span>|<span data-ttu-id="55f9a-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="55f9a-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="55f9a-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="55f9a-114">E_NOTIMPL</span></span>|<span data-ttu-id="55f9a-115">La version du common language runtime (CLR) est antérieure à la version du CLR dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55f9a-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55f9a-116">Notes</span><span class="sxs-lookup"><span data-stu-id="55f9a-116">Remarks</span></span>  
 <span data-ttu-id="55f9a-117">Cette méthode ne fonctionne pas avec les versions CLR antérieures à la version du CLR dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55f9a-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f9a-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="55f9a-118">Requirements</span></span>  
 <span data-ttu-id="55f9a-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55f9a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f9a-120">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="55f9a-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="55f9a-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55f9a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55f9a-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f9a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f9a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55f9a-123">See also</span></span>

- [<span data-ttu-id="55f9a-124">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="55f9a-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="55f9a-125">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="55f9a-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="55f9a-126">Hébergement</span><span class="sxs-lookup"><span data-stu-id="55f9a-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
