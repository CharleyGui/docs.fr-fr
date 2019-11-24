---
title: IMetaDataImport::ResolveTypeRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431473"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="20ffc-102">IMetaDataImport::ResolveTypeRef, méthode</span><span class="sxs-lookup"><span data-stu-id="20ffc-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="20ffc-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span><span class="sxs-lookup"><span data-stu-id="20ffc-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ffc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20ffc-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20ffc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20ffc-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="20ffc-106">[in] The TypeRef metadata token to return the referenced type information for.</span><span class="sxs-lookup"><span data-stu-id="20ffc-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="20ffc-107">[in] The IID of the interface to return in `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="20ffc-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="20ffc-108">Typically, this would be IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="20ffc-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="20ffc-109">[out] An interface to the module scope in which the referenced type is defined.</span><span class="sxs-lookup"><span data-stu-id="20ffc-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="20ffc-110">[out] A pointer to a TypeDef token that represents the referenced type.</span><span class="sxs-lookup"><span data-stu-id="20ffc-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20ffc-111">Notes</span><span class="sxs-lookup"><span data-stu-id="20ffc-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="20ffc-112">Do not use this method if multiple application domains are loaded.</span><span class="sxs-lookup"><span data-stu-id="20ffc-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="20ffc-113">The method does not respect application domain boundaries.</span><span class="sxs-lookup"><span data-stu-id="20ffc-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="20ffc-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span><span class="sxs-lookup"><span data-stu-id="20ffc-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="20ffc-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span><span class="sxs-lookup"><span data-stu-id="20ffc-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="20ffc-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span><span class="sxs-lookup"><span data-stu-id="20ffc-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="20ffc-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="20ffc-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="20ffc-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span><span class="sxs-lookup"><span data-stu-id="20ffc-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20ffc-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="20ffc-119">Requirements</span></span>  
 <span data-ttu-id="20ffc-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20ffc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20ffc-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="20ffc-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20ffc-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20ffc-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="20ffc-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20ffc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ffc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20ffc-124">See also</span></span>

- [<span data-ttu-id="20ffc-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="20ffc-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="20ffc-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="20ffc-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
