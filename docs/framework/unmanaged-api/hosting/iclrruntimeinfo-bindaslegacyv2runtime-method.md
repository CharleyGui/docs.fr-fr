---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: d37ec8e17e62f58212a5f79f4d6b6aa75f57bf7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120259"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="ddb37-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime, méthode</span><span class="sxs-lookup"><span data-stu-id="ddb37-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="ddb37-103">Lie le runtime actuel pour toutes les décisions de stratégie d’activation d’common language runtime (CLR) version 2 héritées.</span><span class="sxs-lookup"><span data-stu-id="ddb37-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddb37-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ddb37-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ddb37-105">Return Value</span></span>  
 <span data-ttu-id="ddb37-106">Cette méthode retourne les HRESULT spécifiques suivants :</span><span class="sxs-lookup"><span data-stu-id="ddb37-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="ddb37-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ddb37-107">HRESULT</span></span>|<span data-ttu-id="ddb37-108">Description</span><span class="sxs-lookup"><span data-stu-id="ddb37-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ddb37-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ddb37-109">S_OK</span></span>|<span data-ttu-id="ddb37-110">La liaison a réussi, ou ce Runtime était déjà lié en tant que Runtime de la stratégie d’activation CLR version 2 héritée.</span><span class="sxs-lookup"><span data-stu-id="ddb37-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="ddb37-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="ddb37-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="ddb37-112">Un Runtime différent était déjà lié à la stratégie d’activation héritée du CLR version 2.</span><span class="sxs-lookup"><span data-stu-id="ddb37-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddb37-113">Notes</span><span class="sxs-lookup"><span data-stu-id="ddb37-113">Remarks</span></span>  
 <span data-ttu-id="ddb37-114">Si le runtime actuel est déjà lié à toutes les décisions de stratégie d’activation CLR version 2 héritées (par exemple, à l’aide de l’attribut `useLegacyV2RuntimeActivationPolicy` sur le [\<élément de > de démarrage](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) dans le fichier de configuration), cette méthode ne retourne pas de résultat d’erreur ; au lieu de cela, le résultat est S_OK, comme c’est le cas si la méthode avait lié avec succès une stratégie d’activation héritée.</span><span class="sxs-lookup"><span data-stu-id="ddb37-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb37-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="ddb37-115">Requirements</span></span>  
 <span data-ttu-id="ddb37-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddb37-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb37-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="ddb37-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ddb37-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ddb37-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ddb37-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb37-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb37-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddb37-120">See also</span></span>

- [<span data-ttu-id="ddb37-121">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="ddb37-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ddb37-122">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="ddb37-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ddb37-123">Hébergement</span><span class="sxs-lookup"><span data-stu-id="ddb37-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="ddb37-124">\<startup>, élément</span><span class="sxs-lookup"><span data-stu-id="ddb37-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
