---
title: IMetaDataTables::GetGuid, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175276"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="554de-102">IMetaDataTables::GetGuid, méthode</span><span class="sxs-lookup"><span data-stu-id="554de-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="554de-103">Obtient un GUID de la ligne à l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="554de-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="554de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="554de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="554de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="554de-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="554de-106">[dans] L’index de la ligne à partir de laquelle obtenir le GUID.</span><span class="sxs-lookup"><span data-stu-id="554de-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="554de-107">[out] Un pointeur à un pointeur à la GUID.</span><span class="sxs-lookup"><span data-stu-id="554de-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="554de-108">Notes </span><span class="sxs-lookup"><span data-stu-id="554de-108">Remarks</span></span>  

  <span data-ttu-id="554de-109">Nous ne recommandons pas l’utilisation de cette méthode, car elle ne donne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="554de-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="554de-110">Pour plus d’informations sur le tableau GUID, consultez la documentation sur l’infrastructure linguistique commune (CLI), en particulier «Partition II: Metadata Definition and Semantics».</span><span class="sxs-lookup"><span data-stu-id="554de-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="554de-111">La documentation est disponible en ligne; voir [ECMA C et Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and Standard [ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="554de-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="554de-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="554de-112">Requirements</span></span>  
 <span data-ttu-id="554de-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="554de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="554de-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="554de-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="554de-115">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="554de-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="554de-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="554de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554de-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="554de-117">See also</span></span>

- [<span data-ttu-id="554de-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="554de-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="554de-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="554de-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
