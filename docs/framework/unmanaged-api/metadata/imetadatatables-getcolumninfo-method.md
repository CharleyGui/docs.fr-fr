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
ms.openlocfilehash: a044924810016eea60682b8765aeee448b552f0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501194"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="6e9dd-102">IMetaDataTables::GetColumnInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="6e9dd-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="6e9dd-103">Obtient les données relatives à la colonne spécifiée dans la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6e9dd-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e9dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e9dd-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6e9dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e9dd-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="6e9dd-106">dans Index de la table souhaitée.</span><span class="sxs-lookup"><span data-stu-id="6e9dd-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="6e9dd-107">dans Index de la colonne souhaitée.</span><span class="sxs-lookup"><span data-stu-id="6e9dd-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="6e9dd-108">à Pointeur vers le décalage de la colonne dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="6e9dd-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="6e9dd-109">à Pointeur vers la taille, en octets, de la colonne.</span><span class="sxs-lookup"><span data-stu-id="6e9dd-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="6e9dd-110">à Pointeur vers le type des valeurs de la colonne.</span><span class="sxs-lookup"><span data-stu-id="6e9dd-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="6e9dd-111">à Pointeur vers un pointeur vers le nom de la colonne.</span><span class="sxs-lookup"><span data-stu-id="6e9dd-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="6e9dd-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="6e9dd-112">Remarks</span></span>

<span data-ttu-id="6e9dd-113">Le type de colonne retourné est compris dans une plage de valeurs :</span><span class="sxs-lookup"><span data-stu-id="6e9dd-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="6e9dd-114">pType</span><span class="sxs-lookup"><span data-stu-id="6e9dd-114">pType</span></span>                    | <span data-ttu-id="6e9dd-115">Description</span><span class="sxs-lookup"><span data-stu-id="6e9dd-115">Description</span></span>   | <span data-ttu-id="6e9dd-116">Fonction d’assistance</span><span class="sxs-lookup"><span data-stu-id="6e9dd-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="6e9dd-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="6e9dd-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="6e9dd-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-118">(0..63)</span></span>   | <span data-ttu-id="6e9dd-119">RID</span><span class="sxs-lookup"><span data-stu-id="6e9dd-119">Rid</span></span>           | <span data-ttu-id="6e9dd-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-120">**IsRidType**</span></span><br><span data-ttu-id="6e9dd-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="6e9dd-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="6e9dd-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="6e9dd-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-123">(64..95)</span></span> | <span data-ttu-id="6e9dd-124">Jeton codé</span><span class="sxs-lookup"><span data-stu-id="6e9dd-124">Coded token</span></span> | <span data-ttu-id="6e9dd-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="6e9dd-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="6e9dd-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="6e9dd-128">Int16</span><span class="sxs-lookup"><span data-stu-id="6e9dd-128">Int16</span></span>         | <span data-ttu-id="6e9dd-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6e9dd-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="6e9dd-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="6e9dd-131">UInt16</span></span>        | <span data-ttu-id="6e9dd-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6e9dd-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-133">`iLONG` (98)</span></span>             | <span data-ttu-id="6e9dd-134">Int32</span><span class="sxs-lookup"><span data-stu-id="6e9dd-134">Int32</span></span>         | <span data-ttu-id="6e9dd-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6e9dd-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-136">`iULONG` (99)</span></span>            | <span data-ttu-id="6e9dd-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="6e9dd-137">UInt32</span></span>        | <span data-ttu-id="6e9dd-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6e9dd-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="6e9dd-140">Byte</span><span class="sxs-lookup"><span data-stu-id="6e9dd-140">Byte</span></span>          | <span data-ttu-id="6e9dd-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6e9dd-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="6e9dd-143">String</span><span class="sxs-lookup"><span data-stu-id="6e9dd-143">String</span></span>        | <span data-ttu-id="6e9dd-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="6e9dd-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-145">`iGUID` (102)</span></span>            | <span data-ttu-id="6e9dd-146">Guid</span><span class="sxs-lookup"><span data-stu-id="6e9dd-146">Guid</span></span>          | <span data-ttu-id="6e9dd-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="6e9dd-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="6e9dd-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="6e9dd-149">Objet blob</span><span class="sxs-lookup"><span data-stu-id="6e9dd-149">Blob</span></span>          | <span data-ttu-id="6e9dd-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="6e9dd-151">Les valeurs stockées dans le *tas* (autrement dit, `IsHeapType == true` ) peuvent être lues à l’aide de :</span><span class="sxs-lookup"><span data-stu-id="6e9dd-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="6e9dd-152">`iSTRING`: **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="6e9dd-153">`iGUID`: **IMetadataTables. GetGuid**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="6e9dd-154">`iBLOB`: **IMetadataTables. getBlob**</span><span class="sxs-lookup"><span data-stu-id="6e9dd-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e9dd-155">Pour utiliser les constantes définies dans le tableau ci-dessus, incluez la directive `#define _DEFINE_META_DATA_META_CONSTANTS` fournie par le fichier d’en-tête *Cor. h* .</span><span class="sxs-lookup"><span data-stu-id="6e9dd-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e9dd-156">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6e9dd-156">Requirements</span></span>  
 <span data-ttu-id="6e9dd-157">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e9dd-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e9dd-158">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6e9dd-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e9dd-159">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6e9dd-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e9dd-160">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e9dd-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e9dd-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e9dd-161">See also</span></span>

- [<span data-ttu-id="6e9dd-162">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="6e9dd-162">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="6e9dd-163">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="6e9dd-163">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
