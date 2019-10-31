---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: 90474a61b16d65565889bd69ef75616804d8bc60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140880"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="8cfa3-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding, méthode</span><span class="sxs-lookup"><span data-stu-id="8cfa3-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="8cfa3-103">Retourne une interface qui représente un runtime auquel une stratégie d’activation héritée a été liée, par exemple à l’aide de l’attribut `useLegacyV2RuntimeActivationPolicy` sur l’entrée du fichier de configuration de l' [élément de > de démarrage\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , en utilisant directement les API d’activation héritées, ou en appelant la méthode [ICLRRuntimeInfo :: BindAsLegacyV2Runtime,](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8cfa3-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfa3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cfa3-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cfa3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8cfa3-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="8cfa3-106">dans Obligatoire. actuellement, la seule valeur valide pour ce paramètre est `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="8cfa3-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="8cfa3-107">[out] Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8cfa3-107">[out] Required.</span></span> <span data-ttu-id="8cfa3-108">Lorsque cette méthode est retournée, contient un pointeur vers l’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) qui représente un Runtime lié à une stratégie d’activation héritée.</span><span class="sxs-lookup"><span data-stu-id="8cfa3-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cfa3-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8cfa3-109">Return Value</span></span>  
 <span data-ttu-id="8cfa3-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8cfa3-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8cfa3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cfa3-111">HRESULT</span></span>|<span data-ttu-id="8cfa3-112">Description</span><span class="sxs-lookup"><span data-stu-id="8cfa3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cfa3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cfa3-113">S_OK</span></span>|<span data-ttu-id="8cfa3-114">La méthode s'est terminée correctement et a retourné un runtime lié à une stratégie d'activation héritée.</span><span class="sxs-lookup"><span data-stu-id="8cfa3-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="8cfa3-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8cfa3-115">S_FALSE</span></span>|<span data-ttu-id="8cfa3-116">La méthode s'est terminée correctement, mais un runtime hérité n'a pas encore été lié.</span><span class="sxs-lookup"><span data-stu-id="8cfa3-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="8cfa3-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="8cfa3-117">E_NOINTERFACE</span></span>|<span data-ttu-id="8cfa3-118">La méthode a trouvé un runtime lié à une stratégie d'activation héritée, mais `riid` n'est pas pris en charge par ce runtime.</span><span class="sxs-lookup"><span data-stu-id="8cfa3-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cfa3-119">Notes</span><span class="sxs-lookup"><span data-stu-id="8cfa3-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cfa3-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="8cfa3-120">Requirements</span></span>  
 <span data-ttu-id="8cfa3-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cfa3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cfa3-122">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="8cfa3-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8cfa3-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8cfa3-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cfa3-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cfa3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfa3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cfa3-125">See also</span></span>

- [<span data-ttu-id="8cfa3-126">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="8cfa3-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="8cfa3-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="8cfa3-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
