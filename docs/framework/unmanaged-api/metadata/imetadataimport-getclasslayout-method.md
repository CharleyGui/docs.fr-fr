---
title: IMetaDataImport::GetClassLayout, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: e02d7dd4b287d027b633ae9bf2e98e036062bdd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175406"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="7e9d4-102">IMetaDataImport::GetClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="7e9d4-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="7e9d4-103">Obtient les informations de disposition pour la classe référencée par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="7e9d4-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e9d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e9d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e9d4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e9d4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7e9d4-106">[dans] Le jeton TypeDef pour la classe avec la mise en page à revenir.</span><span class="sxs-lookup"><span data-stu-id="7e9d4-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="7e9d4-107">[out] L’une des valeurs 1, 2, 4, 8 ou 16, représentant la taille du pack de la classe.</span><span class="sxs-lookup"><span data-stu-id="7e9d4-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="7e9d4-108">[out] Un éventail de [valeurs COR_FIELD_OFFSET.](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)</span><span class="sxs-lookup"><span data-stu-id="7e9d4-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7e9d4-109">[in] Taille maximale du tableau `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="7e9d4-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="7e9d4-110">[out] Le nombre d’éléments retournés dans `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="7e9d4-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="7e9d4-111">[out] La taille dans les octets `td`de la classe représentée par .</span><span class="sxs-lookup"><span data-stu-id="7e9d4-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e9d4-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7e9d4-112">Requirements</span></span>  
 <span data-ttu-id="7e9d4-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e9d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e9d4-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="7e9d4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e9d4-115">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e9d4-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e9d4-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e9d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e9d4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e9d4-117">See also</span></span>

- [<span data-ttu-id="7e9d4-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="7e9d4-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7e9d4-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="7e9d4-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
