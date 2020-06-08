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
ms.openlocfilehash: 6b37fcfc04e3ec880c67f102ec12d7f3e4b06a43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493160"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="1612f-102">METAHOST_CONFIG_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="1612f-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="1612f-103">Décrit les indicateurs possibles retournés dans le `pdwConfigFlags` paramètre de la méthode [ICLRMetaHostPolicy :: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , indiquant la présence et le paramétrage de l' `useLegacyV2RuntimeActivationPolicy` attribut dans l' [ \<startup> élément](../../configure-apps/file-schema/startup/startup-element.md) du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1612f-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1612f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1612f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="1612f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1612f-105">Members</span></span>  
  
|<span data-ttu-id="1612f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1612f-106">Member</span></span>|<span data-ttu-id="1612f-107">Description</span><span class="sxs-lookup"><span data-stu-id="1612f-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="1612f-108">L' `useLegacyV2RuntimeActivationPolicy` attribut n’était pas présent dans l' [ \<startup> élément](../../configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="1612f-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="1612f-109">L' `useLegacyV2RuntimeActivationPolicy` attribut était présent et a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="1612f-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="1612f-110">L' `useLegacyV2RuntimeActivationPolicy` attribut était présent et a la valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="1612f-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="1612f-111">Appliquez ce masque à la valeur retournée dans `pdwConfigFlags` pour récupérer les valeurs correspondant à `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="1612f-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1612f-112">Notes</span><span class="sxs-lookup"><span data-stu-id="1612f-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1612f-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1612f-113">Requirements</span></span>  
 <span data-ttu-id="1612f-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1612f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1612f-115">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="1612f-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="1612f-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1612f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1612f-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1612f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1612f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1612f-118">See also</span></span>

- [<span data-ttu-id="1612f-119">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="1612f-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="1612f-120">GetRequestedRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="1612f-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="1612f-121">\<startup>Appartient</span><span class="sxs-lookup"><span data-stu-id="1612f-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
