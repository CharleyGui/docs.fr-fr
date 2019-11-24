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
ms.openlocfilehash: 1a4f7703536bcfdae75b0bcffae8dca0734e9e0f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437563"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="cd3c3-102">IMetaDataImport::GetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="cd3c3-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="cd3c3-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span><span class="sxs-lookup"><span data-stu-id="cd3c3-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd3c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd3c3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd3c3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cd3c3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="cd3c3-106">[in] The metadata token that represents the field to get interop marshaling information for.</span><span class="sxs-lookup"><span data-stu-id="cd3c3-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="cd3c3-107">[out] A pointer to the metadata signature of the field's native type.</span><span class="sxs-lookup"><span data-stu-id="cd3c3-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="cd3c3-108">[out] The size in bytes of `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="cd3c3-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd3c3-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="cd3c3-109">Requirements</span></span>  
 <span data-ttu-id="cd3c3-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd3c3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd3c3-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd3c3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd3c3-112">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd3c3-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd3c3-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd3c3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3c3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd3c3-114">See also</span></span>

- [<span data-ttu-id="cd3c3-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="cd3c3-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cd3c3-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="cd3c3-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
