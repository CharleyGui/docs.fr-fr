---
title: IMetaDataImport::FindMember, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: 7a46fa5319a1badc0cf28dcdbf535a6ed017c9c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437919"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="39d86-102">IMetaDataImport::FindMember, méthode</span><span class="sxs-lookup"><span data-stu-id="39d86-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="39d86-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span><span class="sxs-lookup"><span data-stu-id="39d86-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39d86-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39d86-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="39d86-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="39d86-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span><span class="sxs-lookup"><span data-stu-id="39d86-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="39d86-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span><span class="sxs-lookup"><span data-stu-id="39d86-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="39d86-108">[in] The name of the member to search for.</span><span class="sxs-lookup"><span data-stu-id="39d86-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="39d86-109">[in] A pointer to the binary metadata signature of the member.</span><span class="sxs-lookup"><span data-stu-id="39d86-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="39d86-110">[in] The size in bytes of `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="39d86-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="39d86-111">[out] A pointer to the matching MemberDef token.</span><span class="sxs-lookup"><span data-stu-id="39d86-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39d86-112">Notes</span><span class="sxs-lookup"><span data-stu-id="39d86-112">Remarks</span></span>  
 <span data-ttu-id="39d86-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="39d86-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="39d86-114">There might be multiple members with the same name in a class or interface.</span><span class="sxs-lookup"><span data-stu-id="39d86-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="39d86-115">In that case, pass the member's signature to find the unique match.</span><span class="sxs-lookup"><span data-stu-id="39d86-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="39d86-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span><span class="sxs-lookup"><span data-stu-id="39d86-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="39d86-117">A signature can embed a token that identifies the enclosing class or value type.</span><span class="sxs-lookup"><span data-stu-id="39d86-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="39d86-118">The token is an index into the local TypeDef table.</span><span class="sxs-lookup"><span data-stu-id="39d86-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="39d86-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="39d86-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="39d86-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span><span class="sxs-lookup"><span data-stu-id="39d86-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39d86-121">`FindMember` is a helper method.</span><span class="sxs-lookup"><span data-stu-id="39d86-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="39d86-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="39d86-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39d86-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="39d86-123">Requirements</span></span>  
 <span data-ttu-id="39d86-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39d86-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39d86-125">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="39d86-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39d86-126">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39d86-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39d86-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39d86-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d86-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39d86-128">See also</span></span>

- [<span data-ttu-id="39d86-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="39d86-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="39d86-130">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="39d86-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
