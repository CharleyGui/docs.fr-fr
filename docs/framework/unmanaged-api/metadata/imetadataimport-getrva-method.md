---
title: IMetaDataImport::GetRVA, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: a3a5cadc1b5a9df7967aae271ff10296843121dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436958"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="0058d-102">IMetaDataImport::GetRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="0058d-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="0058d-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="0058d-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0058d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0058d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0058d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0058d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0058d-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span><span class="sxs-lookup"><span data-stu-id="0058d-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="0058d-107">If the token is a FieldDef, the field must be a global variable.</span><span class="sxs-lookup"><span data-stu-id="0058d-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="0058d-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span><span class="sxs-lookup"><span data-stu-id="0058d-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="0058d-109">[out] A pointer to the implementation flags for the method.</span><span class="sxs-lookup"><span data-stu-id="0058d-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="0058d-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="0058d-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="0058d-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="0058d-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0058d-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="0058d-112">Requirements</span></span>  
 <span data-ttu-id="0058d-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0058d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0058d-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0058d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0058d-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0058d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0058d-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0058d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0058d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0058d-117">See also</span></span>

- [<span data-ttu-id="0058d-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="0058d-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0058d-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="0058d-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
