---
title: METAHOST_CONFIG_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 07cab119810c4da25d16a4ad7c13f2d2bda16455
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140309"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="59c61-102">METAHOST_CONFIG_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="59c61-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="59c61-103">Décrit les indicateurs possibles retournés dans le paramètre `pdwConfigFlags` de la méthode [ICLRMetaHostPolicy :: GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) , indiquant la présence et le paramétrage de l’attribut `useLegacyV2RuntimeActivationPolicy` dans la [\<élément > de démarrage](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) de l’élément fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="59c61-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59c61-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="59c61-105">Membres</span><span class="sxs-lookup"><span data-stu-id="59c61-105">Members</span></span>  
  
|<span data-ttu-id="59c61-106">Membre</span><span class="sxs-lookup"><span data-stu-id="59c61-106">Member</span></span>|<span data-ttu-id="59c61-107">Description</span><span class="sxs-lookup"><span data-stu-id="59c61-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="59c61-108">L’attribut `useLegacyV2RuntimeActivationPolicy` n’était pas présent dans l' [élément > startup\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="59c61-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="59c61-109">L’attribut `useLegacyV2RuntimeActivationPolicy` était présent et défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="59c61-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="59c61-110">L’attribut `useLegacyV2RuntimeActivationPolicy` était présent et défini sur `false`.</span><span class="sxs-lookup"><span data-stu-id="59c61-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="59c61-111">Appliquez ce masque à la valeur retournée dans `pdwConfigFlags` pour récupérer les valeurs correspondant à `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="59c61-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59c61-112">Notes</span><span class="sxs-lookup"><span data-stu-id="59c61-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c61-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="59c61-113">Requirements</span></span>  
 <span data-ttu-id="59c61-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59c61-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59c61-115">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="59c61-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="59c61-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="59c61-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59c61-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59c61-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c61-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59c61-118">See also</span></span>

- [<span data-ttu-id="59c61-119">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="59c61-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="59c61-120">GetRequestedRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="59c61-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="59c61-121">\<startup>, élément</span><span class="sxs-lookup"><span data-stu-id="59c61-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
