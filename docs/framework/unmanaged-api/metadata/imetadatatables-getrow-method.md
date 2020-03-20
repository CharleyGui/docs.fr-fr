---
title: IMetaDataTables::GetRow, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177115"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="e8abb-102">IMetaDataTables::GetRow, méthode</span><span class="sxs-lookup"><span data-stu-id="e8abb-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="e8abb-103">Obtient la ligne à l’indice de ligne spécifié, dans le tableau à l’indice de table spécifié.</span><span class="sxs-lookup"><span data-stu-id="e8abb-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8abb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8abb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8abb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8abb-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="e8abb-106">[dans] L’index de la table à partir de laquelle la ligne sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="e8abb-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="e8abb-107">[dans] L’index de la ligne à obtenir.</span><span class="sxs-lookup"><span data-stu-id="e8abb-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="e8abb-108">[out] Un pointeur à un pointeur de la ligne.</span><span class="sxs-lookup"><span data-stu-id="e8abb-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8abb-109">Notes </span><span class="sxs-lookup"><span data-stu-id="e8abb-109">Remarks</span></span>  

  <span data-ttu-id="e8abb-110">Nous ne recommandons pas l’utilisation de cette méthode, car elle ne donne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="e8abb-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e8abb-111">Pour plus d’informations sur le tableau GUID, consultez la documentation sur l’infrastructure linguistique commune (CLI), en particulier «Partition II: Metadata Definition and Semantics».</span><span class="sxs-lookup"><span data-stu-id="e8abb-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e8abb-112">La documentation est disponible en ligne; voir [ECMA C et Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and Standard [ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="e8abb-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8abb-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8abb-113">Requirements</span></span>  
 <span data-ttu-id="e8abb-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8abb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8abb-115">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="e8abb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8abb-116">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8abb-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8abb-117">**Versions cadre .NET**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8abb-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8abb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8abb-118">See also</span></span>

- [<span data-ttu-id="e8abb-119">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="e8abb-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="e8abb-120">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="e8abb-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
