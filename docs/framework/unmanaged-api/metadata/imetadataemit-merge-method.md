---
title: IMetaDataEmit::Merge, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 06894f238f9fda3111d5484bb1b2add183a5abb2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448057"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="9fb3c-102">IMetaDataEmit::Merge, méthode</span><span class="sxs-lookup"><span data-stu-id="9fb3c-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="9fb3c-103">Adds the specified imported scope to the list of scopes to be merged.</span><span class="sxs-lookup"><span data-stu-id="9fb3c-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fb3c-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fb3c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fb3c-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="9fb3c-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span><span class="sxs-lookup"><span data-stu-id="9fb3c-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="9fb3c-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span><span class="sxs-lookup"><span data-stu-id="9fb3c-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="9fb3c-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span><span class="sxs-lookup"><span data-stu-id="9fb3c-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fb3c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="9fb3c-109">Remarks</span></span>  
 <span data-ttu-id="9fb3c-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span><span class="sxs-lookup"><span data-stu-id="9fb3c-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fb3c-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="9fb3c-111">Requirements</span></span>  
 <span data-ttu-id="9fb3c-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fb3c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb3c-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fb3c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fb3c-114">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fb3c-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fb3c-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb3c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb3c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fb3c-116">See also</span></span>

- [<span data-ttu-id="9fb3c-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9fb3c-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9fb3c-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="9fb3c-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
