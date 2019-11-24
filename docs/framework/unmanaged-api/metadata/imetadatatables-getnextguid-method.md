---
title: IMetaDataTables::GetNextGuid, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: 32edbb6a0eeaf636338983c5cc2e032ddf8b5854
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443732"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="a135a-102">IMetaDataTables::GetNextGuid, méthode</span><span class="sxs-lookup"><span data-stu-id="a135a-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="a135a-103">Gets the index of the next GUID value in the current table column.</span><span class="sxs-lookup"><span data-stu-id="a135a-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a135a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a135a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a135a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a135a-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="a135a-106">[in] The index value from a GUID table column.</span><span class="sxs-lookup"><span data-stu-id="a135a-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="a135a-107">[out] A pointer to the index of the next GUID value.</span><span class="sxs-lookup"><span data-stu-id="a135a-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a135a-108">Notes</span><span class="sxs-lookup"><span data-stu-id="a135a-108">Remarks</span></span>  
 <span data-ttu-id="a135a-109">We do not recommend the use of this method, because it does not return consistent results.</span><span class="sxs-lookup"><span data-stu-id="a135a-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="a135a-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span><span class="sxs-lookup"><span data-stu-id="a135a-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="a135a-111">La documentation est disponible en ligne. Consultez [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) sur le site web d’Ecma International.</span><span class="sxs-lookup"><span data-stu-id="a135a-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a135a-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="a135a-112">Requirements</span></span>  
 <span data-ttu-id="a135a-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a135a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a135a-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a135a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a135a-115">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a135a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a135a-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a135a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a135a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a135a-117">See also</span></span>

- [<span data-ttu-id="a135a-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="a135a-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a135a-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="a135a-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
