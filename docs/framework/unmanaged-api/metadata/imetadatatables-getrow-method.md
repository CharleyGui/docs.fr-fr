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
ms.openlocfilehash: 9ac6eba18ae23dc80a8dc90383aa67cfe41b39ff
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937406"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="7c9d5-102">IMetaDataTables::GetRow, méthode</span><span class="sxs-lookup"><span data-stu-id="7c9d5-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="7c9d5-103">Obtient la ligne à l’index de ligne spécifié dans la table au niveau de l’index de table spécifié.</span><span class="sxs-lookup"><span data-stu-id="7c9d5-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c9d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c9d5-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="7c9d5-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="7c9d5-106">dans Index de la table à partir de laquelle la ligne sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="7c9d5-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="7c9d5-107">dans Index de la ligne à récupérer.</span><span class="sxs-lookup"><span data-stu-id="7c9d5-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="7c9d5-108">à Pointeur vers un pointeur vers la ligne.</span><span class="sxs-lookup"><span data-stu-id="7c9d5-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c9d5-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7c9d5-109">Remarks</span></span>  

  <span data-ttu-id="7c9d5-110">Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="7c9d5-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="7c9d5-111">Pour plus d’informations sur la table GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : définition et sémantique des métadonnées ».</span><span class="sxs-lookup"><span data-stu-id="7c9d5-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="7c9d5-112">La documentation est disponible en ligne. consultez [les C# normes ECMA et Common Language Infrastructure](../../../standard/components.md#applicable-standards) [standard et ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="7c9d5-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9d5-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7c9d5-113">Requirements</span></span>  
 <span data-ttu-id="7c9d5-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9d5-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7c9d5-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c9d5-116">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c9d5-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c9d5-117">**Versions de .NET Framework**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9d5-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9d5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c9d5-118">See also</span></span>

- [<span data-ttu-id="7c9d5-119">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="7c9d5-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="7c9d5-120">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="7c9d5-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
