---
title: IMetaDataInfo::GetFileMapping, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 0cd2071d4410615a08e774ba30e0e8fe8d1fa7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436174"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="6d093-102">IMetaDataInfo::GetFileMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="6d093-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="6d093-103">Gets the memory region of the mapped file, and the type of mapping.</span><span class="sxs-lookup"><span data-stu-id="6d093-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d093-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d093-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d093-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d093-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="6d093-106">[out] A pointer to the start of the mapped file.</span><span class="sxs-lookup"><span data-stu-id="6d093-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="6d093-107">[out] The size of the mapped region.</span><span class="sxs-lookup"><span data-stu-id="6d093-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="6d093-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span><span class="sxs-lookup"><span data-stu-id="6d093-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="6d093-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span><span class="sxs-lookup"><span data-stu-id="6d093-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="6d093-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="6d093-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="6d093-111">Other values are reserved for future use.</span><span class="sxs-lookup"><span data-stu-id="6d093-111">Other values are reserved for future use.</span></span> <span data-ttu-id="6d093-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span><span class="sxs-lookup"><span data-stu-id="6d093-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d093-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6d093-113">Return Value</span></span>  
  
|<span data-ttu-id="6d093-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d093-114">HRESULT</span></span>|<span data-ttu-id="6d093-115">Description</span><span class="sxs-lookup"><span data-stu-id="6d093-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6d093-116">All outputs are filled.</span><span class="sxs-lookup"><span data-stu-id="6d093-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="6d093-117">NULL was passed as an argument value.</span><span class="sxs-lookup"><span data-stu-id="6d093-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="6d093-118">The CLR implementation cannot provide information about the memory region.</span><span class="sxs-lookup"><span data-stu-id="6d093-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="6d093-119">This can happen for the following reasons:</span><span class="sxs-lookup"><span data-stu-id="6d093-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="6d093-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span><span class="sxs-lookup"><span data-stu-id="6d093-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="6d093-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span><span class="sxs-lookup"><span data-stu-id="6d093-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="6d093-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span><span class="sxs-lookup"><span data-stu-id="6d093-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="6d093-123">-   The file is not a portable executable (PE) file.</span><span class="sxs-lookup"><span data-stu-id="6d093-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="6d093-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span><span class="sxs-lookup"><span data-stu-id="6d093-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d093-125">Notes</span><span class="sxs-lookup"><span data-stu-id="6d093-125">Remarks</span></span>  
 <span data-ttu-id="6d093-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span><span class="sxs-lookup"><span data-stu-id="6d093-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="6d093-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span><span class="sxs-lookup"><span data-stu-id="6d093-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="6d093-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span><span class="sxs-lookup"><span data-stu-id="6d093-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="6d093-129">It cannot be set by the user.</span><span class="sxs-lookup"><span data-stu-id="6d093-129">It cannot be set by the user.</span></span> <span data-ttu-id="6d093-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span><span class="sxs-lookup"><span data-stu-id="6d093-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="6d093-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span><span class="sxs-lookup"><span data-stu-id="6d093-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="6d093-132">Passing NULL for any of the three parameters is not supported.</span><span class="sxs-lookup"><span data-stu-id="6d093-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="6d093-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span><span class="sxs-lookup"><span data-stu-id="6d093-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="6d093-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span><span class="sxs-lookup"><span data-stu-id="6d093-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d093-135">spécifications</span><span class="sxs-lookup"><span data-stu-id="6d093-135">Requirements</span></span>  
 <span data-ttu-id="6d093-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d093-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d093-137">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d093-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d093-138">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d093-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d093-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d093-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d093-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d093-140">See also</span></span>

- [<span data-ttu-id="6d093-141">IMetaDataInfo, interface</span><span class="sxs-lookup"><span data-stu-id="6d093-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="6d093-142">CorFileMapping, énumération</span><span class="sxs-lookup"><span data-stu-id="6d093-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
