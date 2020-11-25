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
ms.openlocfilehash: f776ac59ff9bd665dc3bfde74e8a8bb0f8acc89e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702457"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="3b118-102">IMetaDataTables::GetGuid, méthode</span><span class="sxs-lookup"><span data-stu-id="3b118-102">IMetaDataTables::GetGuid Method</span></span>

<span data-ttu-id="3b118-103">Obtient un GUID à partir de la ligne à l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="3b118-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b118-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b118-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b118-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b118-105">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="3b118-106">dans Index de la ligne à partir de laquelle le GUID doit être obtenu.</span><span class="sxs-lookup"><span data-stu-id="3b118-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="3b118-107">à Pointeur vers un pointeur vers le GUID.</span><span class="sxs-lookup"><span data-stu-id="3b118-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b118-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="3b118-108">Remarks</span></span>  

  <span data-ttu-id="3b118-109">Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="3b118-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="3b118-110">Pour plus d’informations sur la table GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : définition et sémantique des métadonnées ».</span><span class="sxs-lookup"><span data-stu-id="3b118-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="3b118-111">La documentation est disponible en ligne. consultez [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="3b118-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b118-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3b118-112">Requirements</span></span>  

 <span data-ttu-id="3b118-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b118-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b118-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3b118-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b118-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b118-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b118-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b118-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b118-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b118-117">See also</span></span>

- [<span data-ttu-id="3b118-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="3b118-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="3b118-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="3b118-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
