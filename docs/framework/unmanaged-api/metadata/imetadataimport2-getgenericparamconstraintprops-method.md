---
title: IMetaDataImport2::GetGenericParamConstraintProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
ms.openlocfilehash: 6d7884e896d6a0463639e7ef08b47dced10a27f4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431375"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="2bbaa-102">IMetaDataImport2::GetGenericParamConstraintProps, méthode</span><span class="sxs-lookup"><span data-stu-id="2bbaa-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="2bbaa-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span><span class="sxs-lookup"><span data-stu-id="2bbaa-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bbaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bbaa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bbaa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2bbaa-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="2bbaa-106">[in] The token to the generic parameter constraint for which to return the metadata.</span><span class="sxs-lookup"><span data-stu-id="2bbaa-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="2bbaa-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span><span class="sxs-lookup"><span data-stu-id="2bbaa-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="2bbaa-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="2bbaa-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bbaa-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="2bbaa-109">Requirements</span></span>  
 <span data-ttu-id="2bbaa-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bbaa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bbaa-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2bbaa-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2bbaa-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bbaa-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2bbaa-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bbaa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbaa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bbaa-114">See also</span></span>

- [<span data-ttu-id="2bbaa-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="2bbaa-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="2bbaa-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="2bbaa-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
