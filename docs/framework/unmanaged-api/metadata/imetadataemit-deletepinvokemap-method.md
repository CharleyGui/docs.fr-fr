---
title: IMetaDataEmit::DeletePinvokeMap, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 6fc6cf9b7333dd4caad3c5a4b081fecb060c8f86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722087"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="a6056-102">IMetaDataEmit::DeletePinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="a6056-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>

<span data-ttu-id="a6056-103">Détruit les métadonnées de mappage PInvoke pour l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="a6056-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6056-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6056-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6056-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6056-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="a6056-106">dans `mdFieldDef` Jeton ou `mdMethodDef` qui représente l’objet pour lequel supprimer les métadonnées de mappage PInvoke.</span><span class="sxs-lookup"><span data-stu-id="a6056-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6056-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6056-107">Requirements</span></span>  

 <span data-ttu-id="a6056-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6056-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6056-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a6056-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6056-110">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6056-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6056-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6056-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6056-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6056-112">See also</span></span>

- [<span data-ttu-id="a6056-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a6056-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a6056-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a6056-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
