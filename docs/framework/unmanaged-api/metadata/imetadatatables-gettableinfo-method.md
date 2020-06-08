---
title: IMetaDataTables::GetTableInfo, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 7e60dd9535809ca13f3bbe6ac76f5ea1209df734
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501166"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="026bf-102">IMetaDataTables::GetTableInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="026bf-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="026bf-103">Obtient le nom, la taille de ligne, le nombre de lignes, le nombre de colonnes et l’index de colonne clé de la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="026bf-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="026bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="026bf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="026bf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="026bf-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="026bf-106">dans Identificateur de la table dont les propriétés doivent être retournées.</span><span class="sxs-lookup"><span data-stu-id="026bf-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="026bf-107">à Pointeur vers la taille, en octets, d’une ligne de table.</span><span class="sxs-lookup"><span data-stu-id="026bf-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="026bf-108">à Pointeur vers le nombre de lignes dans la table.</span><span class="sxs-lookup"><span data-stu-id="026bf-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="026bf-109">à Pointeur vers le nombre de colonnes dans la table.</span><span class="sxs-lookup"><span data-stu-id="026bf-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="026bf-110">à Pointeur vers l’index de la colonne clé, ou-1 si la table n’a pas de colonne clé.</span><span class="sxs-lookup"><span data-stu-id="026bf-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="026bf-111">à Pointeur vers un pointeur vers le nom de la table.</span><span class="sxs-lookup"><span data-stu-id="026bf-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="026bf-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="026bf-112">Requirements</span></span>  
 <span data-ttu-id="026bf-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="026bf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="026bf-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="026bf-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="026bf-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="026bf-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="026bf-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="026bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026bf-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="026bf-117">See also</span></span>

- [<span data-ttu-id="026bf-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="026bf-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="026bf-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="026bf-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
