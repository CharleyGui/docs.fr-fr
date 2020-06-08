---
title: IMetaDataTables, interface
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 2105033e684ec172e24adfb14bcab7668b388af3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501119"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="b1676-102">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="b1676-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="b1676-103">Fournit des méthodes pour le stockage et la récupération d'informations de métadonnées dans des tables.</span><span class="sxs-lookup"><span data-stu-id="b1676-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1676-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b1676-104">Methods</span></span>  
  
|<span data-ttu-id="b1676-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-105">Method</span></span>|<span data-ttu-id="b1676-106">Description</span><span class="sxs-lookup"><span data-stu-id="b1676-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1676-107">GetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-107">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="b1676-108">Obtient un pointeur vers l’objet BLOB (Binary Large Object) situé à l’index de colonne spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1676-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="b1676-109">GetBlobHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-109">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="b1676-110">Obtient la taille, en octets, du tas d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="b1676-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="b1676-111">GetCodedTokenInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-111">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="b1676-112">Obtient un pointeur vers un tableau de jetons associé à l’index de ligne spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1676-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="b1676-113">GetColumn, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-113">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="b1676-114">Obtient un pointeur vers les valeurs contenues dans la colonne à l’index de colonne spécifié, dans la table au niveau de l’index de table spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1676-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="b1676-115">GetColumnInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-115">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="b1676-116">Obtient les données relatives à la colonne spécifiée dans la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b1676-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="b1676-117">GetGuid, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-117">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="b1676-118">Obtient un GUID à partir de la ligne à l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1676-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="b1676-119">GetGuidHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-119">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="b1676-120">Obtient la taille, en octets, du tas GUID.</span><span class="sxs-lookup"><span data-stu-id="b1676-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="b1676-121">GetNextBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-121">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="b1676-122">Obtient l’index de l’objet BLOB suivant dans la table.</span><span class="sxs-lookup"><span data-stu-id="b1676-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="b1676-123">GetNextGuid, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-123">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="b1676-124">Obtient l’index de la valeur GUID suivante dans la colonne de table actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1676-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="b1676-125">GetNextString, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-125">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="b1676-126">Obtient l’index de la chaîne suivante dans la colonne de table actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1676-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="b1676-127">GetNextUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-127">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="b1676-128">Obtient l’index de la ligne qui contient la chaîne codée en dur suivante dans la colonne de table actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1676-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="b1676-129">GetNumTables, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-129">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="b1676-130">Obtient le nombre de tables dans la portée de l' `IMetaDataTables` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1676-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="b1676-131">GetRow, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-131">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="b1676-132">Obtient la ligne à l’index de ligne spécifié dans la table au niveau de l’index de table spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1676-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="b1676-133">GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-133">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="b1676-134">Obtient la chaîne à l’index spécifié à partir de la colonne de table dans la portée de référence actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1676-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="b1676-135">GetStringHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-135">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="b1676-136">Obtient la taille, en octets, du tas de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="b1676-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="b1676-137">GetTableIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-137">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="b1676-138">Obtient l’index de la table référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1676-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="b1676-139">GetTableInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-139">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="b1676-140">Obtient le nom, la taille de ligne, le nombre de lignes, le nombre de colonnes et l’index de colonne clé de la table au niveau de l’index de table spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1676-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="b1676-141">GetUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-141">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="b1676-142">Obtient la chaîne codée en dur à l’index spécifié dans la colonne de chaîne de l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1676-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="b1676-143">GetUserStringHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b1676-143">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="b1676-144">Obtient la taille, en octets, du tas de la chaîne utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b1676-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1676-145">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b1676-145">Requirements</span></span>  
 <span data-ttu-id="b1676-146">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1676-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1676-147">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b1676-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1676-148">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1676-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1676-149">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1676-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1676-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1676-150">See also</span></span>

- [<span data-ttu-id="b1676-151">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="b1676-151">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="b1676-152">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="b1676-152">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
