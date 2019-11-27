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
ms.openlocfilehash: 6737275fb77e6f177832eb1d96214c37942bcd22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442154"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="afd80-102">IMetaDataEmit::SetHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="afd80-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="afd80-103">Définit la méthode référencée par le pointeur de `IUnknown` spécifié comme un rappel de notification pour les remappages de jetons.</span><span class="sxs-lookup"><span data-stu-id="afd80-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afd80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afd80-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afd80-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="afd80-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="afd80-106">dans Gestionnaire à inscrire.</span><span class="sxs-lookup"><span data-stu-id="afd80-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afd80-107">Notes</span><span class="sxs-lookup"><span data-stu-id="afd80-107">Remarks</span></span>  
 <span data-ttu-id="afd80-108">Le moteur de métadonnées envoie une notification à l’aide de la méthode fournie par `SetHandler`, aux compilateurs qui ne génèrent pas d’enregistrements de manière optimisée et qui souhaitent optimiser les enregistrements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="afd80-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="afd80-109">Si la méthode de rappel n’est pas fournie par `SetHandler`, aucune optimisation n’est effectuée lors de l’enregistrement, sauf si plusieurs étendues d’importation ont été fusionnées à l’aide de `IMapToken` lors de la fusion pour chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="afd80-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afd80-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="afd80-110">Requirements</span></span>  
 <span data-ttu-id="afd80-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afd80-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afd80-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="afd80-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afd80-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="afd80-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afd80-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afd80-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd80-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afd80-115">See also</span></span>

- [<span data-ttu-id="afd80-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="afd80-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="afd80-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="afd80-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
