---
title: IMetaDataTables::GetTableIndex, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 195642d9186016417db310402b664a1043d09e71
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781368"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="fd6e2-102">IMetaDataTables::GetTableIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="fd6e2-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="fd6e2-103">Obtient l’index pour la table référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="fd6e2-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd6e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd6e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd6e2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fd6e2-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="fd6e2-106">[in] Le jeton qui fait référence à la table.</span><span class="sxs-lookup"><span data-stu-id="fd6e2-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="fd6e2-107">[out] Pointeur vers l’index retourné pour la table référencée.</span><span class="sxs-lookup"><span data-stu-id="fd6e2-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd6e2-108">Notes</span><span class="sxs-lookup"><span data-stu-id="fd6e2-108">Remarks</span></span>  
 <span data-ttu-id="fd6e2-109">Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="fd6e2-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="fd6e2-110">Pour plus d’informations sur le tableau GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : Metadata Definition and Semantics ».</span><span class="sxs-lookup"><span data-stu-id="fd6e2-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="fd6e2-111">La documentation est disponible en ligne. Consultez [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) sur le site web d’Ecma International.</span><span class="sxs-lookup"><span data-stu-id="fd6e2-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd6e2-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fd6e2-112">Requirements</span></span>  
 <span data-ttu-id="fd6e2-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd6e2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd6e2-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fd6e2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd6e2-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd6e2-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd6e2-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd6e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6e2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd6e2-117">See also</span></span>

- [<span data-ttu-id="fd6e2-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="fd6e2-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="fd6e2-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="fd6e2-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
