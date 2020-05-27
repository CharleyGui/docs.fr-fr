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
ms.openlocfilehash: a15c912cdf0eef1b8f131e8425ad9b5b01289982
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006725"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="648f3-102">METAHOST_CONFIG_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="648f3-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="648f3-103">Décrit les indicateurs possibles retournés dans le `pdwConfigFlags` paramètre de la méthode [ICLRMetaHostPolicy :: GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) , indiquant la présence et le paramétrage de l' `useLegacyV2RuntimeActivationPolicy` attribut dans l' [ \<startup> élément](../../configure-apps/file-schema/startup/startup-element.md) du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="648f3-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="648f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="648f3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="648f3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="648f3-105">Members</span></span>  
  
|<span data-ttu-id="648f3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="648f3-106">Member</span></span>|<span data-ttu-id="648f3-107">Description</span><span class="sxs-lookup"><span data-stu-id="648f3-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="648f3-108">L' `useLegacyV2RuntimeActivationPolicy` attribut n’était pas présent dans l' [ \<startup> élément](../../configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="648f3-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="648f3-109">L' `useLegacyV2RuntimeActivationPolicy` attribut était présent et a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="648f3-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="648f3-110">L' `useLegacyV2RuntimeActivationPolicy` attribut était présent et a la valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="648f3-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="648f3-111">Appliquez ce masque à la valeur retournée dans `pdwConfigFlags` pour récupérer les valeurs correspondant à `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="648f3-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="648f3-112">Notes</span><span class="sxs-lookup"><span data-stu-id="648f3-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="648f3-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="648f3-113">Requirements</span></span>  
 <span data-ttu-id="648f3-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="648f3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="648f3-115">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="648f3-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="648f3-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="648f3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="648f3-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="648f3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="648f3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="648f3-118">See also</span></span>

- [<span data-ttu-id="648f3-119">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="648f3-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="648f3-120">GetRequestedRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="648f3-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="648f3-121">\<startup>Appartient</span><span class="sxs-lookup"><span data-stu-id="648f3-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
