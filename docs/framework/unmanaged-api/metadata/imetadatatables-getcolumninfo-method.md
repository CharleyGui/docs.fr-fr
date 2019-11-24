---
title: IMetaDataTables::GetColumnInfo, méthode
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: 854d3ad28cc00c03e903b9e1d2ce3863e3ceef17
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436095"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="66b40-102">IMetaDataTables::GetColumnInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="66b40-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="66b40-103">Gets data about the specified column in the specified table.</span><span class="sxs-lookup"><span data-stu-id="66b40-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66b40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66b40-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66b40-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="66b40-106">[in] The index of the desired table.</span><span class="sxs-lookup"><span data-stu-id="66b40-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="66b40-107">[in] The index of the desired column.</span><span class="sxs-lookup"><span data-stu-id="66b40-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="66b40-108">[out] A pointer to the offset of the column in the row.</span><span class="sxs-lookup"><span data-stu-id="66b40-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="66b40-109">[out] A pointer to the size, in bytes, of the column.</span><span class="sxs-lookup"><span data-stu-id="66b40-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="66b40-110">[out] A pointer to the type of the values in the column.</span><span class="sxs-lookup"><span data-stu-id="66b40-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="66b40-111">[out] A pointer to a pointer to the column name.</span><span class="sxs-lookup"><span data-stu-id="66b40-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="66b40-112">Notes</span><span class="sxs-lookup"><span data-stu-id="66b40-112">Remarks</span></span>

<span data-ttu-id="66b40-113">The returned column type falls within a range of values:</span><span class="sxs-lookup"><span data-stu-id="66b40-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="66b40-114">pType</span><span class="sxs-lookup"><span data-stu-id="66b40-114">pType</span></span>                    | <span data-ttu-id="66b40-115">Description</span><span class="sxs-lookup"><span data-stu-id="66b40-115">Description</span></span>   | <span data-ttu-id="66b40-116">Helper function</span><span class="sxs-lookup"><span data-stu-id="66b40-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="66b40-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="66b40-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="66b40-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="66b40-118">(0..63)</span></span>   | <span data-ttu-id="66b40-119">Rid</span><span class="sxs-lookup"><span data-stu-id="66b40-119">Rid</span></span>           | <span data-ttu-id="66b40-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="66b40-120">**IsRidType**</span></span><br><span data-ttu-id="66b40-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="66b40-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="66b40-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="66b40-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="66b40-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="66b40-123">(64..95)</span></span> | <span data-ttu-id="66b40-124">Coded token</span><span class="sxs-lookup"><span data-stu-id="66b40-124">Coded token</span></span> | <span data-ttu-id="66b40-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="66b40-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="66b40-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="66b40-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="66b40-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="66b40-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="66b40-128">Int16</span><span class="sxs-lookup"><span data-stu-id="66b40-128">Int16</span></span>         | <span data-ttu-id="66b40-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="66b40-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="66b40-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="66b40-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="66b40-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="66b40-131">UInt16</span></span>        | <span data-ttu-id="66b40-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="66b40-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="66b40-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="66b40-133">`iLONG` (98)</span></span>             | <span data-ttu-id="66b40-134">Int32</span><span class="sxs-lookup"><span data-stu-id="66b40-134">Int32</span></span>         | <span data-ttu-id="66b40-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="66b40-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="66b40-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="66b40-136">`iULONG` (99)</span></span>            | <span data-ttu-id="66b40-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="66b40-137">UInt32</span></span>        | <span data-ttu-id="66b40-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="66b40-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="66b40-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="66b40-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="66b40-140">Byte</span><span class="sxs-lookup"><span data-stu-id="66b40-140">Byte</span></span>          | <span data-ttu-id="66b40-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="66b40-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="66b40-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="66b40-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="66b40-143">Chaîne</span><span class="sxs-lookup"><span data-stu-id="66b40-143">String</span></span>        | <span data-ttu-id="66b40-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="66b40-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="66b40-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="66b40-145">`iGUID` (102)</span></span>            | <span data-ttu-id="66b40-146">GUID</span><span class="sxs-lookup"><span data-stu-id="66b40-146">Guid</span></span>          | <span data-ttu-id="66b40-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="66b40-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="66b40-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="66b40-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="66b40-149">Blob</span><span class="sxs-lookup"><span data-stu-id="66b40-149">Blob</span></span>          | <span data-ttu-id="66b40-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="66b40-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="66b40-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span><span class="sxs-lookup"><span data-stu-id="66b40-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="66b40-152">`iSTRING`: **IMetadataTables.GetString**</span><span class="sxs-lookup"><span data-stu-id="66b40-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="66b40-153">`iGUID`: **IMetadataTables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="66b40-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="66b40-154">`iBLOB`: **IMetadataTables.GetBlob**</span><span class="sxs-lookup"><span data-stu-id="66b40-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66b40-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span><span class="sxs-lookup"><span data-stu-id="66b40-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="66b40-156">spécifications</span><span class="sxs-lookup"><span data-stu-id="66b40-156">Requirements</span></span>  
 <span data-ttu-id="66b40-157">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66b40-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66b40-158">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66b40-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66b40-159">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66b40-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66b40-160">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66b40-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b40-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66b40-161">See also</span></span>

- [<span data-ttu-id="66b40-162">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="66b40-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="66b40-163">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="66b40-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
