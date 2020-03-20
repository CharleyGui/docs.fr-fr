---
title: IMetaDataTables::GetColumn, méthode
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177142"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="b3291-102">IMetaDataTables::GetColumn, méthode</span><span class="sxs-lookup"><span data-stu-id="b3291-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="b3291-103">Obtient un pointeur à la valeur contenue dans la cellule de la colonne spécifiée et la ligne dans le tableau donné.</span><span class="sxs-lookup"><span data-stu-id="b3291-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3291-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3291-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3291-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b3291-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="b3291-106">[dans] L’index du tableau.</span><span class="sxs-lookup"><span data-stu-id="b3291-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="b3291-107">[dans] L’index de la colonne dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="b3291-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="b3291-108">[dans] L’index de la ligne dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="b3291-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="b3291-109">[out] Un pointeur à la valeur de la cellule.</span><span class="sxs-lookup"><span data-stu-id="b3291-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="b3291-110">Notes </span><span class="sxs-lookup"><span data-stu-id="b3291-110">Remarks</span></span>

<span data-ttu-id="b3291-111">L’interprétation de la `pVal` valeur retournée dépend du type de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b3291-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="b3291-112">Le type de colonne peut être déterminé en appelant [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="b3291-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="b3291-113">La méthode **GetColumn** convertit automatiquement les colonnes de type **Rid** `mdToken` ou **CodedToken** en valeurs 32 bits complètes.</span><span class="sxs-lookup"><span data-stu-id="b3291-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="b3291-114">Il convertit également automatiquement les valeurs 8 ou 16 bits en valeurs 32 bits complètes.</span><span class="sxs-lookup"><span data-stu-id="b3291-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="b3291-115">Pour les colonnes de type *tas,* le *pVal* retourné sera un index dans le tas correspondant.</span><span class="sxs-lookup"><span data-stu-id="b3291-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="b3291-116">Type de colonne</span><span class="sxs-lookup"><span data-stu-id="b3291-116">Column type</span></span>              | <span data-ttu-id="b3291-117">pVal contient</span><span class="sxs-lookup"><span data-stu-id="b3291-117">pVal contains</span></span> | <span data-ttu-id="b3291-118">Commentaire</span><span class="sxs-lookup"><span data-stu-id="b3291-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="b3291-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="b3291-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="b3291-120">(0..63)</span><span class="sxs-lookup"><span data-stu-id="b3291-120">(0..63)</span></span>  | <span data-ttu-id="b3291-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="b3291-121">mdToken</span></span>     | <span data-ttu-id="b3291-122">*pVal* contiendra un jeton complet.</span><span class="sxs-lookup"><span data-stu-id="b3291-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="b3291-123">La fonction convertit automatiquement le Rid en un jeton complet.</span><span class="sxs-lookup"><span data-stu-id="b3291-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="b3291-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="b3291-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="b3291-125">(64..95)</span><span class="sxs-lookup"><span data-stu-id="b3291-125">(64..95)</span></span> | <span data-ttu-id="b3291-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="b3291-126">mdToken</span></span> | <span data-ttu-id="b3291-127">Au retour, *pVal* contiendra un jeton complet.</span><span class="sxs-lookup"><span data-stu-id="b3291-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="b3291-128">La fonction décomprime automatiquement le CodedToken en un jeton complet.</span><span class="sxs-lookup"><span data-stu-id="b3291-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="b3291-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="b3291-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="b3291-130">Int16</span><span class="sxs-lookup"><span data-stu-id="b3291-130">Int16</span></span>         | <span data-ttu-id="b3291-131">Automatiquement signé-étendu à 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b3291-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="b3291-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="b3291-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="b3291-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="b3291-133">UInt16</span></span>        | <span data-ttu-id="b3291-134">Automatiquement signé-étendu à 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b3291-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="b3291-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="b3291-135">`iLONG` (98)</span></span>             | <span data-ttu-id="b3291-136">Int32</span><span class="sxs-lookup"><span data-stu-id="b3291-136">Int32</span></span>         |                                        |
| <span data-ttu-id="b3291-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="b3291-137">`iULONG` (99)</span></span>            | <span data-ttu-id="b3291-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="b3291-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="b3291-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="b3291-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="b3291-140">Byte</span><span class="sxs-lookup"><span data-stu-id="b3291-140">Byte</span></span>          | <span data-ttu-id="b3291-141">Automatiquement signé-étendu à 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b3291-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="b3291-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="b3291-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="b3291-143">Index de tas de cordes</span><span class="sxs-lookup"><span data-stu-id="b3291-143">String heap index</span></span> | <span data-ttu-id="b3291-144">*pVal* est un index dans le tas de cordes.</span><span class="sxs-lookup"><span data-stu-id="b3291-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="b3291-145">Utilisez [IMetadataTables::GetString](imetadatatables-getstring-method.md) pour obtenir la valeur de chaîne de colonne réelle.</span><span class="sxs-lookup"><span data-stu-id="b3291-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="b3291-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="b3291-146">`iGUID` (102)</span></span>            | <span data-ttu-id="b3291-147">Indice de tas Guid</span><span class="sxs-lookup"><span data-stu-id="b3291-147">Guid heap index</span></span> | <span data-ttu-id="b3291-148">*pVal* est un index dans le tas Guid.</span><span class="sxs-lookup"><span data-stu-id="b3291-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="b3291-149">Utilisez [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) pour obtenir la vraie colonne Guid valeur.</span><span class="sxs-lookup"><span data-stu-id="b3291-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="b3291-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="b3291-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="b3291-151">Indice de tas blob</span><span class="sxs-lookup"><span data-stu-id="b3291-151">Blob heap index</span></span> | <span data-ttu-id="b3291-152">*pVal* est un index dans le tas Blob.</span><span class="sxs-lookup"><span data-stu-id="b3291-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="b3291-153">Utilisez [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) pour obtenir la valeur Blob colonne réelle.</span><span class="sxs-lookup"><span data-stu-id="b3291-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="b3291-154">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b3291-154">Requirements</span></span>  
 <span data-ttu-id="b3291-155">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3291-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3291-156">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="b3291-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3291-157">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3291-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3291-158">**Versions cadre .NET**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3291-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3291-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3291-159">See also</span></span>

- [<span data-ttu-id="b3291-160">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="b3291-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="b3291-161">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="b3291-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
