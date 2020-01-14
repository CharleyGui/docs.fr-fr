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
ms.openlocfilehash: d3e056bc93c2faf2b1509536b8d8d4df6886dd20
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937380"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="e4fdd-102">IMetaDataTables::GetTableIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="e4fdd-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="e4fdd-103">Obtient l’index de la table référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="e4fdd-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4fdd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4fdd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4fdd-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e4fdd-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="e4fdd-106">dans Jeton qui fait référence à la table.</span><span class="sxs-lookup"><span data-stu-id="e4fdd-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="e4fdd-107">à Pointeur vers l’index retourné pour la table référencée.</span><span class="sxs-lookup"><span data-stu-id="e4fdd-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4fdd-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e4fdd-108">Remarks</span></span>  
 <span data-ttu-id="e4fdd-109">Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="e4fdd-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e4fdd-110">Pour plus d’informations sur la table GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : définition et sémantique des métadonnées ».</span><span class="sxs-lookup"><span data-stu-id="e4fdd-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e4fdd-111">La documentation est disponible en ligne. consultez [les C# normes ECMA et Common Language Infrastructure](../../../standard/components.md#applicable-standards) [standard et ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="e4fdd-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4fdd-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e4fdd-112">Requirements</span></span>  
 <span data-ttu-id="e4fdd-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4fdd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4fdd-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e4fdd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4fdd-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4fdd-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4fdd-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4fdd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4fdd-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4fdd-117">See also</span></span>

- [<span data-ttu-id="e4fdd-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="e4fdd-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="e4fdd-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="e4fdd-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
