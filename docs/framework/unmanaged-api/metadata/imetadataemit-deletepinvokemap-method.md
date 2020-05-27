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
ms.openlocfilehash: 79af7b5679598ffa82471dcb69adabc2394b13fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009299"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="b950b-102">IMetaDataEmit::DeletePinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="b950b-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="b950b-103">Détruit les métadonnées de mappage PInvoke pour l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="b950b-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b950b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b950b-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b950b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b950b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b950b-106">dans `mdFieldDef`Jeton ou `mdMethodDef` qui représente l’objet pour lequel supprimer les métadonnées de mappage PInvoke.</span><span class="sxs-lookup"><span data-stu-id="b950b-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b950b-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b950b-107">Requirements</span></span>  
 <span data-ttu-id="b950b-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b950b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b950b-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b950b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b950b-110">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b950b-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b950b-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b950b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b950b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b950b-112">See also</span></span>

- [<span data-ttu-id="b950b-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b950b-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b950b-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b950b-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
