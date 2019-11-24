---
title: IMetaDataDispenser::OpenScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5ce1af82631531f8f7105fbf92ba78db3cca437b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442329"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="17b57-102">IMetaDataDispenser::OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="17b57-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="17b57-103">Opens an existing, on-disk file and maps its metadata into memory.</span><span class="sxs-lookup"><span data-stu-id="17b57-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17b57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17b57-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17b57-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17b57-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="17b57-106">[in] The name of the file to be opened.</span><span class="sxs-lookup"><span data-stu-id="17b57-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="17b57-107">The file must contain common language runtime (CLR) metadata.</span><span class="sxs-lookup"><span data-stu-id="17b57-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="17b57-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span><span class="sxs-lookup"><span data-stu-id="17b57-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="17b57-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span><span class="sxs-lookup"><span data-stu-id="17b57-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="17b57-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span><span class="sxs-lookup"><span data-stu-id="17b57-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="17b57-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="17b57-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="17b57-112">[out] The pointer to the returned interface.</span><span class="sxs-lookup"><span data-stu-id="17b57-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17b57-113">Notes</span><span class="sxs-lookup"><span data-stu-id="17b57-113">Remarks</span></span>  
 <span data-ttu-id="17b57-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span><span class="sxs-lookup"><span data-stu-id="17b57-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="17b57-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span><span class="sxs-lookup"><span data-stu-id="17b57-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="17b57-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span><span class="sxs-lookup"><span data-stu-id="17b57-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="17b57-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span><span class="sxs-lookup"><span data-stu-id="17b57-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="17b57-118">However, problems can arise due to this sharing.</span><span class="sxs-lookup"><span data-stu-id="17b57-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="17b57-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span><span class="sxs-lookup"><span data-stu-id="17b57-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="17b57-120">Use the ofReadOnly value to allow the scope to be shared.</span><span class="sxs-lookup"><span data-stu-id="17b57-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="17b57-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span><span class="sxs-lookup"><span data-stu-id="17b57-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17b57-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="17b57-122">Requirements</span></span>  
 <span data-ttu-id="17b57-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17b57-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17b57-124">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="17b57-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17b57-125">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17b57-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17b57-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17b57-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b57-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17b57-127">See also</span></span>

- [<span data-ttu-id="17b57-128">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="17b57-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="17b57-129">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="17b57-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="17b57-130">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="17b57-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="17b57-131">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="17b57-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="17b57-132">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="17b57-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="17b57-133">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="17b57-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="17b57-134">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="17b57-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="17b57-135">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="17b57-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
