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
ms.openlocfilehash: cdbcdb9359d295ad9bed2050ed36499feba74d9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442275"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="e74df-102">IMetaDataEmit::SetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="e74df-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="e74df-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="e74df-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e74df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e74df-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e74df-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e74df-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e74df-106">[in] The token for target data item.</span><span class="sxs-lookup"><span data-stu-id="e74df-106">[in] The token for target data item.</span></span> <span data-ttu-id="e74df-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="e74df-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="e74df-108">[in] The signature for unmanaged type.</span><span class="sxs-lookup"><span data-stu-id="e74df-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="e74df-109">[in] The count of bytes in `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="e74df-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e74df-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="e74df-110">Requirements</span></span>  
 <span data-ttu-id="e74df-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e74df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e74df-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e74df-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e74df-113">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e74df-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e74df-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e74df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74df-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e74df-115">See also</span></span>

- [<span data-ttu-id="e74df-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e74df-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e74df-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e74df-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
