---
title: IMetaDataTables::GetColumnInfo, méthode
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0755cb2a91d61725338562cb1fe249a9cfacc38
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781514"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="3c15a-102">IMetaDataTables::GetColumnInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="3c15a-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="3c15a-103">Obtient les données relatives à la colonne spécifiée dans la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3c15a-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c15a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c15a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3c15a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3c15a-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="3c15a-106">[in] Index de la table souhaitée.</span><span class="sxs-lookup"><span data-stu-id="3c15a-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="3c15a-107">[in] Index de la colonne souhaitée.</span><span class="sxs-lookup"><span data-stu-id="3c15a-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="3c15a-108">[out] Pointeur vers l’offset de la colonne dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="3c15a-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="3c15a-109">[out] Pointeur vers la taille, en octets, de la colonne.</span><span class="sxs-lookup"><span data-stu-id="3c15a-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="3c15a-110">[out] Un pointeur vers le type des valeurs dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="3c15a-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="3c15a-111">[out] Pointeur vers un pointeur vers le nom de colonne.</span><span class="sxs-lookup"><span data-stu-id="3c15a-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c15a-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3c15a-112">Requirements</span></span>  
 <span data-ttu-id="3c15a-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c15a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c15a-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3c15a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c15a-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c15a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c15a-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c15a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c15a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c15a-117">See also</span></span>

- [<span data-ttu-id="3c15a-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="3c15a-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="3c15a-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="3c15a-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
