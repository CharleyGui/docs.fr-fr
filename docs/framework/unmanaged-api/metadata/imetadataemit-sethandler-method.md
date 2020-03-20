---
title: IMetaDataEmit::SetHandler, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177540"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="f5b74-102">IMetaDataEmit::SetHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="f5b74-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="f5b74-103">Définit la méthode référencée par le pointeur spécifié `IUnknown` comme un rappel de notification pour les remaps symboliques.</span><span class="sxs-lookup"><span data-stu-id="f5b74-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5b74-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5b74-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5b74-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="f5b74-106">[dans] Le gestionnaire de s’inscrire.</span><span class="sxs-lookup"><span data-stu-id="f5b74-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5b74-107">Notes </span><span class="sxs-lookup"><span data-stu-id="f5b74-107">Remarks</span></span>  
 <span data-ttu-id="f5b74-108">Le moteur de métadonnées envoie la `SetHandler`notification en utilisant la méthode qui est fournie par , pour les compilateurs qui ne génèrent pas d’enregistrements d’une manière optimisée et qui voudraient optimiser les enregistrements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="f5b74-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="f5b74-109">Si la méthode de rappel `SetHandler`n’est pas fournie par le biais, aucune optimisation `IMapToken` ne sera effectuée sur enregistrer, sauf lorsque plusieurs portées d’importation ont été fusionnées en utilisant sur la fusion pour chaque portée.</span><span class="sxs-lookup"><span data-stu-id="f5b74-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5b74-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f5b74-110">Requirements</span></span>  
 <span data-ttu-id="f5b74-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5b74-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b74-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="f5b74-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5b74-113">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5b74-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5b74-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b74-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5b74-115">See also</span></span>

- [<span data-ttu-id="f5b74-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f5b74-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f5b74-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f5b74-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
