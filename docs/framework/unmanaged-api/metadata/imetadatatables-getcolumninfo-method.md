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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177122"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="20e1d-102">IMetaDataTables::GetColumnInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="20e1d-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="20e1d-103">Obtient des données sur la colonne spécifiée dans le tableau spécifié.</span><span class="sxs-lookup"><span data-stu-id="20e1d-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20e1d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="20e1d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20e1d-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="20e1d-106">[dans] L’index du tableau souhaité.</span><span class="sxs-lookup"><span data-stu-id="20e1d-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="20e1d-107">[dans] L’index de la colonne souhaitée.</span><span class="sxs-lookup"><span data-stu-id="20e1d-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="20e1d-108">[out] Un pointeur à la compensation de la colonne dans la rangée.</span><span class="sxs-lookup"><span data-stu-id="20e1d-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="20e1d-109">[out] Un pointeur sur la taille, dans les octets, de la colonne.</span><span class="sxs-lookup"><span data-stu-id="20e1d-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="20e1d-110">[out] Un pointeur sur le type de valeurs de la colonne.</span><span class="sxs-lookup"><span data-stu-id="20e1d-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="20e1d-111">[out] Un pointeur à un pointeur au nom de la colonne.</span><span class="sxs-lookup"><span data-stu-id="20e1d-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="20e1d-112">Notes </span><span class="sxs-lookup"><span data-stu-id="20e1d-112">Remarks</span></span>

<span data-ttu-id="20e1d-113">Le type de colonne retournée se situe dans une gamme de valeurs :</span><span class="sxs-lookup"><span data-stu-id="20e1d-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="20e1d-114">pType (en)</span><span class="sxs-lookup"><span data-stu-id="20e1d-114">pType</span></span>                    | <span data-ttu-id="20e1d-115">Description</span><span class="sxs-lookup"><span data-stu-id="20e1d-115">Description</span></span>   | <span data-ttu-id="20e1d-116">Fonction d’aide</span><span class="sxs-lookup"><span data-stu-id="20e1d-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="20e1d-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="20e1d-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="20e1d-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="20e1d-118">(0..63)</span></span>   | <span data-ttu-id="20e1d-119">Débarrasser</span><span class="sxs-lookup"><span data-stu-id="20e1d-119">Rid</span></span>           | <span data-ttu-id="20e1d-120">**IsRidType (isRidType)**</span><span class="sxs-lookup"><span data-stu-id="20e1d-120">**IsRidType**</span></span><br><span data-ttu-id="20e1d-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="20e1d-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="20e1d-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="20e1d-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="20e1d-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="20e1d-123">(64..95)</span></span> | <span data-ttu-id="20e1d-124">Jeton codé</span><span class="sxs-lookup"><span data-stu-id="20e1d-124">Coded token</span></span> | <span data-ttu-id="20e1d-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="20e1d-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="20e1d-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="20e1d-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="20e1d-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="20e1d-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="20e1d-128">Int16</span><span class="sxs-lookup"><span data-stu-id="20e1d-128">Int16</span></span>         | <span data-ttu-id="20e1d-129">**IsFixedType (en)**</span><span class="sxs-lookup"><span data-stu-id="20e1d-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="20e1d-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="20e1d-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="20e1d-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="20e1d-131">UInt16</span></span>        | <span data-ttu-id="20e1d-132">**IsFixedType (en)**</span><span class="sxs-lookup"><span data-stu-id="20e1d-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="20e1d-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="20e1d-133">`iLONG` (98)</span></span>             | <span data-ttu-id="20e1d-134">Int32</span><span class="sxs-lookup"><span data-stu-id="20e1d-134">Int32</span></span>         | <span data-ttu-id="20e1d-135">**IsFixedType (en)**</span><span class="sxs-lookup"><span data-stu-id="20e1d-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="20e1d-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="20e1d-136">`iULONG` (99)</span></span>            | <span data-ttu-id="20e1d-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="20e1d-137">UInt32</span></span>        | <span data-ttu-id="20e1d-138">**IsFixedType (en)**</span><span class="sxs-lookup"><span data-stu-id="20e1d-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="20e1d-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="20e1d-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="20e1d-140">Byte</span><span class="sxs-lookup"><span data-stu-id="20e1d-140">Byte</span></span>          | <span data-ttu-id="20e1d-141">**IsFixedType (en)**</span><span class="sxs-lookup"><span data-stu-id="20e1d-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="20e1d-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="20e1d-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="20e1d-143">String</span><span class="sxs-lookup"><span data-stu-id="20e1d-143">String</span></span>        | <span data-ttu-id="20e1d-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="20e1d-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="20e1d-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="20e1d-145">`iGUID` (102)</span></span>            | <span data-ttu-id="20e1d-146">Guid</span><span class="sxs-lookup"><span data-stu-id="20e1d-146">Guid</span></span>          | <span data-ttu-id="20e1d-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="20e1d-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="20e1d-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="20e1d-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="20e1d-149">Objet blob</span><span class="sxs-lookup"><span data-stu-id="20e1d-149">Blob</span></span>          | <span data-ttu-id="20e1d-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="20e1d-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="20e1d-151">Les valeurs qui *heap* sont stockées dans `IsHeapType == true`le tas (c’est-à-dire) peuvent être lues à l’aide de :</span><span class="sxs-lookup"><span data-stu-id="20e1d-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="20e1d-152">`iSTRING`: **IMetadataTables.GetString**</span><span class="sxs-lookup"><span data-stu-id="20e1d-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="20e1d-153">`iGUID`: **IMetadataTables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="20e1d-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="20e1d-154">`iBLOB`: **IMetadataTables.GetBlob**</span><span class="sxs-lookup"><span data-stu-id="20e1d-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20e1d-155">Pour utiliser les constantes définies dans `#define _DEFINE_META_DATA_META_CONSTANTS` le tableau ci-dessus, inclure la directive fournie par le fichier d’en-tête *cor.h.*</span><span class="sxs-lookup"><span data-stu-id="20e1d-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="20e1d-156">Spécifications</span><span class="sxs-lookup"><span data-stu-id="20e1d-156">Requirements</span></span>  
 <span data-ttu-id="20e1d-157">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20e1d-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e1d-158">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="20e1d-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20e1d-159">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20e1d-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="20e1d-160">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e1d-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e1d-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20e1d-161">See also</span></span>

- [<span data-ttu-id="20e1d-162">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="20e1d-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="20e1d-163">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="20e1d-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
