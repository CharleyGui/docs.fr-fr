---
title: IMetaDataEmit::SetFieldMarshal, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 1037cd4210605192870d43d88979b89af6536380
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175653"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="2601f-102">IMetaDataEmit::SetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="2601f-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="2601f-103">Définit les informations de marshaling PInvoke pour le champ, le retour de méthode, ou le paramètre de méthode référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="2601f-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2601f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2601f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2601f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2601f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2601f-106">[dans] Le jeton pour l’élément de données cible.</span><span class="sxs-lookup"><span data-stu-id="2601f-106">[in] The token for target data item.</span></span> <span data-ttu-id="2601f-107">C’est `mdFieldDef` soit `mdParamDef` un ou un jeton.</span><span class="sxs-lookup"><span data-stu-id="2601f-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="2601f-108">[dans] La signature pour type non-gestion.</span><span class="sxs-lookup"><span data-stu-id="2601f-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="2601f-109">[dans] Le compte d’octets dans `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="2601f-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2601f-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2601f-110">Requirements</span></span>  
 <span data-ttu-id="2601f-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2601f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2601f-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="2601f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2601f-113">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2601f-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2601f-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2601f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2601f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2601f-115">See also</span></span>

- [<span data-ttu-id="2601f-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="2601f-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2601f-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="2601f-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
