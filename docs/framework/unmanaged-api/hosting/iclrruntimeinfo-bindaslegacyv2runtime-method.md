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
ms.openlocfilehash: f0a03ecce49bbc3c1c03d037c9be31a8e994259d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732089"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="42978-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime, méthode</span><span class="sxs-lookup"><span data-stu-id="42978-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>

<span data-ttu-id="42978-103">Lie le runtime actuel pour toutes les décisions de stratégie d’activation d’common language runtime (CLR) version 2 héritées.</span><span class="sxs-lookup"><span data-stu-id="42978-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42978-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42978-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="42978-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="42978-105">Return Value</span></span>  

 <span data-ttu-id="42978-106">Cette méthode retourne les HRESULT spécifiques suivants :</span><span class="sxs-lookup"><span data-stu-id="42978-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="42978-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42978-107">HRESULT</span></span>|<span data-ttu-id="42978-108">Description</span><span class="sxs-lookup"><span data-stu-id="42978-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42978-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="42978-109">S_OK</span></span>|<span data-ttu-id="42978-110">La liaison a réussi, ou ce Runtime était déjà lié en tant que Runtime de la stratégie d’activation CLR version 2 héritée.</span><span class="sxs-lookup"><span data-stu-id="42978-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="42978-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="42978-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="42978-112">Un Runtime différent était déjà lié à la stratégie d’activation héritée du CLR version 2.</span><span class="sxs-lookup"><span data-stu-id="42978-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42978-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="42978-113">Remarks</span></span>  

 <span data-ttu-id="42978-114">Si le runtime actuel est déjà lié à toutes les décisions de stratégie d’activation héritées de CLR version 2 (par exemple, en utilisant l' `useLegacyV2RuntimeActivationPolicy` attribut sur l' [ \<startup> élément](../../configure-apps/file-schema/startup/startup-element.md) dans le fichier de configuration), cette méthode ne retourne pas de résultat d’erreur ; à la place, le résultat est S_OK, comme c’est le cas si la méthode avait lié avec succès une stratégie d’activation héritée.</span><span class="sxs-lookup"><span data-stu-id="42978-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42978-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="42978-115">Requirements</span></span>  

 <span data-ttu-id="42978-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42978-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42978-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="42978-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="42978-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42978-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42978-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42978-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42978-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42978-120">See also</span></span>

- [<span data-ttu-id="42978-121">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="42978-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="42978-122">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="42978-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="42978-123">Hébergement</span><span class="sxs-lookup"><span data-stu-id="42978-123">Hosting</span></span>](index.md)
- [<span data-ttu-id="42978-124">\<startup> Appartient</span><span class="sxs-lookup"><span data-stu-id="42978-124">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
