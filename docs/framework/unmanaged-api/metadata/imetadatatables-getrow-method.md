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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98fc95c618a7a06f5e6c219d7707af291770c06a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781414"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="e9e0a-102">IMetaDataTables::GetRow, méthode</span><span class="sxs-lookup"><span data-stu-id="e9e0a-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="e9e0a-103">Obtient la ligne à l’index de la ligne spécifiée, dans la table à l’index de la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e9e0a-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9e0a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9e0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9e0a-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="e9e0a-106">[in] L’index de la table à partir de laquelle la ligne sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="e9e0a-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="e9e0a-107">[in] L’index de la ligne à obtenir.</span><span class="sxs-lookup"><span data-stu-id="e9e0a-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="e9e0a-108">[out] Pointeur vers un pointeur vers la ligne.</span><span class="sxs-lookup"><span data-stu-id="e9e0a-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9e0a-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e9e0a-109">Remarks</span></span>  
 <span data-ttu-id="e9e0a-110">Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="e9e0a-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e9e0a-111">Pour plus d’informations sur le tableau GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : Metadata Definition and Semantics ».</span><span class="sxs-lookup"><span data-stu-id="e9e0a-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e9e0a-112">La documentation est disponible en ligne. Consultez [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) sur le site web d’Ecma International.</span><span class="sxs-lookup"><span data-stu-id="e9e0a-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9e0a-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e9e0a-113">Requirements</span></span>  
 <span data-ttu-id="e9e0a-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9e0a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9e0a-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e9e0a-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9e0a-116">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9e0a-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9e0a-117">**Versions du .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9e0a-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e0a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9e0a-118">See also</span></span>

- [<span data-ttu-id="e9e0a-119">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="e9e0a-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="e9e0a-120">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="e9e0a-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
