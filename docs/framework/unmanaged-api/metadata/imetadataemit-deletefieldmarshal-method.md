---
title: IMetaDataEmit::DeleteFieldMarshal, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 6d0f9a8c5c3baf7594e098a3d5544bad55fdc917
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009286"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="32377-102">IMetaDataEmit::DeleteFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="32377-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="32377-103">Détruit la signature de métadonnées de marshaling PInvoke pour l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="32377-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32377-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32377-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32377-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="32377-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="32377-106">dans `mdFieldDef`Jeton ou `mdParamDef` qui représente le champ ou le paramètre pour lequel la signature des métadonnées de marshaling doit être supprimée.</span><span class="sxs-lookup"><span data-stu-id="32377-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32377-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="32377-107">Requirements</span></span>  
 <span data-ttu-id="32377-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32377-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32377-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="32377-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32377-110">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="32377-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32377-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32377-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32377-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32377-112">See also</span></span>

- [<span data-ttu-id="32377-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="32377-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="32377-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="32377-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
