---
title: IMetaDataTables::GetGuidHeapSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
ms.openlocfilehash: cf455b3fb34d8eed78ffaadffad621062c2b9b22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443494"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="dddaa-102">IMetaDataTables::GetGuidHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="dddaa-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="dddaa-103">Obtient la taille, en octets, du tas GUID.</span><span class="sxs-lookup"><span data-stu-id="dddaa-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dddaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dddaa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dddaa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dddaa-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="dddaa-106">à Pointeur vers la taille, en octets, du tas GUID.</span><span class="sxs-lookup"><span data-stu-id="dddaa-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dddaa-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dddaa-107">Requirements</span></span>  
 <span data-ttu-id="dddaa-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dddaa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dddaa-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dddaa-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dddaa-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dddaa-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dddaa-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dddaa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dddaa-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dddaa-112">See also</span></span>

- [<span data-ttu-id="dddaa-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="dddaa-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="dddaa-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="dddaa-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
