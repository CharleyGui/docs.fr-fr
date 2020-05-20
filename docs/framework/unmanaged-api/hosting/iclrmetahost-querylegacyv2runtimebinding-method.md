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
ms.openlocfilehash: b9a51a85bd17e527d4c04b69ca65100a7069607f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703715"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="8c66d-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding, méthode</span><span class="sxs-lookup"><span data-stu-id="8c66d-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="8c66d-103">Retourne une interface qui représente un runtime auquel une stratégie d’activation héritée a été liée, par exemple, en utilisant l' `useLegacyV2RuntimeActivationPolicy` attribut sur l’entrée du fichier de configuration de l' [ \< élément de démarrage>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , en utilisant directement les API d’activation héritées ou en appelant la méthode [ICLRRuntimeInfo :: BindAsLegacyV2Runtime,](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8c66d-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c66d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c66d-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c66d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c66d-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="8c66d-106">dans Obligatoire. actuellement, la seule valeur valide pour ce paramètre est `IID_ICLRRuntimeInfo` .</span><span class="sxs-lookup"><span data-stu-id="8c66d-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="8c66d-107">[out] Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8c66d-107">[out] Required.</span></span> <span data-ttu-id="8c66d-108">Lorsque cette méthode est retournée, contient un pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui représente un Runtime lié à une stratégie d’activation héritée.</span><span class="sxs-lookup"><span data-stu-id="8c66d-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c66d-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8c66d-109">Return Value</span></span>  
 <span data-ttu-id="8c66d-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8c66d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8c66d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c66d-111">HRESULT</span></span>|<span data-ttu-id="8c66d-112">Description</span><span class="sxs-lookup"><span data-stu-id="8c66d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c66d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c66d-113">S_OK</span></span>|<span data-ttu-id="8c66d-114">La méthode s'est terminée correctement et a retourné un runtime lié à une stratégie d'activation héritée.</span><span class="sxs-lookup"><span data-stu-id="8c66d-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="8c66d-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8c66d-115">S_FALSE</span></span>|<span data-ttu-id="8c66d-116">La méthode s'est terminée correctement, mais un runtime hérité n'a pas encore été lié.</span><span class="sxs-lookup"><span data-stu-id="8c66d-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="8c66d-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="8c66d-117">E_NOINTERFACE</span></span>|<span data-ttu-id="8c66d-118">La méthode a trouvé un runtime lié à une stratégie d'activation héritée, mais `riid` n'est pas pris en charge par ce runtime.</span><span class="sxs-lookup"><span data-stu-id="8c66d-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c66d-119">Notes</span><span class="sxs-lookup"><span data-stu-id="8c66d-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c66d-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8c66d-120">Requirements</span></span>  
 <span data-ttu-id="8c66d-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c66d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c66d-122">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="8c66d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8c66d-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c66d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c66d-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c66d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c66d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c66d-125">See also</span></span>

- [<span data-ttu-id="8c66d-126">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="8c66d-126">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="8c66d-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="8c66d-127">Hosting</span></span>](index.md)
