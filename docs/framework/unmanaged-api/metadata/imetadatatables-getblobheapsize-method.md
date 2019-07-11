---
title: IMetaDataTables::GetBlobHeapSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9a73df0b73eb5043103479b7452fedc84b02819
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781552"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="45fc2-102">IMetaDataTables::GetBlobHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="45fc2-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="45fc2-103">Obtient la taille, en octets, du tas des objets volumineux binaires (BLOB).</span><span class="sxs-lookup"><span data-stu-id="45fc2-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45fc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45fc2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="45fc2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="45fc2-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="45fc2-106">[out] Pointeur vers la taille, en octets, du tas de BLOB.</span><span class="sxs-lookup"><span data-stu-id="45fc2-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45fc2-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="45fc2-107">Requirements</span></span>  
 <span data-ttu-id="45fc2-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45fc2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45fc2-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="45fc2-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45fc2-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45fc2-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45fc2-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45fc2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45fc2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45fc2-112">See also</span></span>

- [<span data-ttu-id="45fc2-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="45fc2-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="45fc2-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="45fc2-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
