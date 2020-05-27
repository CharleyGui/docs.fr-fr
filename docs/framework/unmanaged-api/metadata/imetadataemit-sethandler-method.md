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
ms.openlocfilehash: 4fa227d18b8cb10936d93fda9bcaf413ce63ca3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003935"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="9cdd7-102">IMetaDataEmit::SetHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="9cdd7-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="9cdd7-103">Définit la méthode référencée par le `IUnknown` pointeur spécifié comme un rappel de notification pour les remappages de jetons.</span><span class="sxs-lookup"><span data-stu-id="9cdd7-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cdd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cdd7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cdd7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9cdd7-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="9cdd7-106">dans Gestionnaire à inscrire.</span><span class="sxs-lookup"><span data-stu-id="9cdd7-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cdd7-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9cdd7-107">Remarks</span></span>  
 <span data-ttu-id="9cdd7-108">Le moteur de métadonnées envoie une notification à l’aide de la méthode fournie par `SetHandler` , aux compilateurs qui ne génèrent pas d’enregistrements de manière optimisée et qui souhaitent optimiser les enregistrements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="9cdd7-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="9cdd7-109">Si la méthode de rappel n’est pas fournie par le biais de `SetHandler` , aucune optimisation n’est effectuée lors de l’enregistrement, sauf si plusieurs étendues d’importation ont été fusionnées à l’aide `IMapToken` de lors de la fusion pour chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="9cdd7-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cdd7-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9cdd7-110">Requirements</span></span>  
 <span data-ttu-id="9cdd7-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cdd7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cdd7-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9cdd7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9cdd7-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9cdd7-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cdd7-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cdd7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdd7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cdd7-115">See also</span></span>

- [<span data-ttu-id="9cdd7-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9cdd7-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9cdd7-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="9cdd7-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
