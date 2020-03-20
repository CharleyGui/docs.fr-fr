---
title: IMetaDataEmit::SetMethodImplFlags, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: 7ed7770f26ea4620d79f3be3f67e72f73c75057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175627"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="63ae7-102">IMetaDataEmit::SetMethodImplFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="63ae7-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="63ae7-103">Définit ou met à jour la signature des métadonnées de la mise en œuvre de la méthode héritée qui est référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="63ae7-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63ae7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63ae7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63ae7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63ae7-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="63ae7-106">[dans] Le jeton pour la méthode à changer.</span><span class="sxs-lookup"><span data-stu-id="63ae7-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="63ae7-107">[dans] Une combinaison des valeurs de l’énumération [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) qui spécifie les fonctionnalités de mise en œuvre de la méthode.</span><span class="sxs-lookup"><span data-stu-id="63ae7-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63ae7-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="63ae7-108">Requirements</span></span>  
 <span data-ttu-id="63ae7-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63ae7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63ae7-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="63ae7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63ae7-111">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63ae7-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63ae7-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63ae7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63ae7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63ae7-113">See also</span></span>

- [<span data-ttu-id="63ae7-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="63ae7-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="63ae7-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="63ae7-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
