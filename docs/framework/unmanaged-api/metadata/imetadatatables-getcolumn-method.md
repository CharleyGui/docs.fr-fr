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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 853f137d91e1b3eb4f3f65a06522618f8441dcb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053676"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="a5007-102">IMetaDataTables::GetColumn, méthode</span><span class="sxs-lookup"><span data-stu-id="a5007-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="a5007-103">Obtient un pointeur vers la valeur contenue dans la cellule de la colonne et de la ligne spécifiées dans la table donnée.</span><span class="sxs-lookup"><span data-stu-id="a5007-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5007-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5007-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5007-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5007-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="a5007-106">dans Index de la table.</span><span class="sxs-lookup"><span data-stu-id="a5007-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="a5007-107">dans Index de la colonne dans la table.</span><span class="sxs-lookup"><span data-stu-id="a5007-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="a5007-108">dans Index de la ligne dans la table.</span><span class="sxs-lookup"><span data-stu-id="a5007-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="a5007-109">à Pointeur vers la valeur dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="a5007-109">[out] A pointer to the value in the cell.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="a5007-110">Notes</span><span class="sxs-lookup"><span data-stu-id="a5007-110">Remarks</span></span>

<span data-ttu-id="a5007-111">L’interprétation de la valeur retournée par `pVal` dépend du type de la colonne.</span><span class="sxs-lookup"><span data-stu-id="a5007-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="a5007-112">Le type de colonne peut être déterminé en appelant [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="a5007-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="a5007-113">La méthode **GetColumn** convertit automatiquement les colonnes de type **RID** ou **CodedToken** en valeurs 32 `mdToken` bits complètes.</span><span class="sxs-lookup"><span data-stu-id="a5007-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="a5007-114">Il convertit également automatiquement les valeurs de 8 ou 16 bits en valeurs 32 bits complètes.</span><span class="sxs-lookup"><span data-stu-id="a5007-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span> 
- <span data-ttu-id="a5007-115">Pour les colonnes de type *Heap* , le *pval* retourné est un index dans le tas correspondant.</span><span class="sxs-lookup"><span data-stu-id="a5007-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="a5007-116">Type de colonne</span><span class="sxs-lookup"><span data-stu-id="a5007-116">Column type</span></span>              | <span data-ttu-id="a5007-117">pVal contient</span><span class="sxs-lookup"><span data-stu-id="a5007-117">pVal contains</span></span> | <span data-ttu-id="a5007-118">Commentaire</span><span class="sxs-lookup"><span data-stu-id="a5007-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="a5007-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="a5007-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="a5007-120">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="a5007-120">(0..63)</span></span>  | <span data-ttu-id="a5007-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="a5007-121">mdToken</span></span>     | <span data-ttu-id="a5007-122">*pval* contient un jeton complet.</span><span class="sxs-lookup"><span data-stu-id="a5007-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="a5007-123">La fonction convertit automatiquement le RID en jeton complet.</span><span class="sxs-lookup"><span data-stu-id="a5007-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="a5007-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="a5007-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="a5007-125">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="a5007-125">(64..95)</span></span> | <span data-ttu-id="a5007-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="a5007-126">mdToken</span></span> | <span data-ttu-id="a5007-127">Lors du retour, *pval* contient un jeton complet.</span><span class="sxs-lookup"><span data-stu-id="a5007-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="a5007-128">La fonction décompresse automatiquement le CodedToken en jeton complet.</span><span class="sxs-lookup"><span data-stu-id="a5007-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="a5007-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="a5007-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="a5007-130">Int16</span><span class="sxs-lookup"><span data-stu-id="a5007-130">Int16</span></span>         | <span data-ttu-id="a5007-131">Signature automatique-étendu à 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a5007-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a5007-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="a5007-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="a5007-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="a5007-133">UInt16</span></span>        | <span data-ttu-id="a5007-134">Signature automatique-étendu à 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a5007-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a5007-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="a5007-135">`iLONG` (98)</span></span>             | <span data-ttu-id="a5007-136">Int32</span><span class="sxs-lookup"><span data-stu-id="a5007-136">Int32</span></span>         |                                        | 
| <span data-ttu-id="a5007-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="a5007-137">`iULONG` (99)</span></span>            | <span data-ttu-id="a5007-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="a5007-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="a5007-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="a5007-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="a5007-140">Byte</span><span class="sxs-lookup"><span data-stu-id="a5007-140">Byte</span></span>          | <span data-ttu-id="a5007-141">Signature automatique-étendu à 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a5007-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a5007-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="a5007-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="a5007-143">Index du tas de chaîne</span><span class="sxs-lookup"><span data-stu-id="a5007-143">String heap index</span></span> | <span data-ttu-id="a5007-144">*pval* est un index dans le tas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="a5007-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="a5007-145">Utilisez [IMetadataTables :: GetString](imetadatatables-getstring-method.md) pour récupérer la valeur de la chaîne de colonne réelle.</span><span class="sxs-lookup"><span data-stu-id="a5007-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="a5007-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="a5007-146">`iGUID` (102)</span></span>            | <span data-ttu-id="a5007-147">Index du tas GUID</span><span class="sxs-lookup"><span data-stu-id="a5007-147">Guid heap index</span></span> | <span data-ttu-id="a5007-148">*pval* est un index dans le tas GUID.</span><span class="sxs-lookup"><span data-stu-id="a5007-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="a5007-149">Utilisez [IMetadataTables :: GetGuid](imetadatatables-getguid-method.md) pour récupérer la valeur du GUID de colonne réel.</span><span class="sxs-lookup"><span data-stu-id="a5007-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="a5007-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="a5007-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="a5007-151">Index du tas d’objets BLOB</span><span class="sxs-lookup"><span data-stu-id="a5007-151">Blob heap index</span></span> | <span data-ttu-id="a5007-152">*pval* est un index dans le tas d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="a5007-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="a5007-153">Utilisez [IMetadataTables :: GetBlob](imetadatatables-getblob-method.md) pour récupérer la valeur réelle de l’objet blob de colonne.</span><span class="sxs-lookup"><span data-stu-id="a5007-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="a5007-154">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a5007-154">Requirements</span></span>  
 <span data-ttu-id="a5007-155">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5007-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5007-156">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a5007-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5007-157">**Bibliothèque** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a5007-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5007-158">**Versions de .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5007-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5007-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5007-159">See also</span></span>

- [<span data-ttu-id="a5007-160">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="a5007-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a5007-161">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="a5007-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
