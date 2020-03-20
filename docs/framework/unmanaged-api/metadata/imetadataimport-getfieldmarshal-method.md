---
title: IMetaDataImport::GetFieldMarshal, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: 91a19e5e15dddd446208dfa3b2c32826282067eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175393"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="ac89b-102">IMetaDataImport::GetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="ac89b-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="ac89b-103">Obtient un pointeur pour le natif, type non gestion du champ représenté par les métadonnées de champ spécifiées jeton.</span><span class="sxs-lookup"><span data-stu-id="ac89b-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac89b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac89b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac89b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac89b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ac89b-106">[dans] Le jeton des métadonnées qui représente le champ pour obtenir des informations interop marshaling pour.</span><span class="sxs-lookup"><span data-stu-id="ac89b-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="ac89b-107">[out] Un pointeur à la signature des métadonnées du type natif du champ.</span><span class="sxs-lookup"><span data-stu-id="ac89b-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="ac89b-108">[out] La taille dans `ppvNativeType`les octets de .</span><span class="sxs-lookup"><span data-stu-id="ac89b-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac89b-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ac89b-109">Requirements</span></span>  
 <span data-ttu-id="ac89b-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac89b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac89b-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ac89b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac89b-112">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac89b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac89b-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac89b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac89b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac89b-114">See also</span></span>

- [<span data-ttu-id="ac89b-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ac89b-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ac89b-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="ac89b-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
