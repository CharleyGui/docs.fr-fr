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
ms.openlocfilehash: c32407c3fc0bc5a045b80ec48937699826d981af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177166"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="555da-102">IMetaDataTables::GetBlobHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="555da-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="555da-103">Obtient la taille, dans les octets, du tas binaire grand objet (BLOB).</span><span class="sxs-lookup"><span data-stu-id="555da-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="555da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="555da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="555da-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="555da-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="555da-106">[out] Un pointeur sur la taille, dans les octets, du tas BLOB.</span><span class="sxs-lookup"><span data-stu-id="555da-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="555da-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="555da-107">Requirements</span></span>  
 <span data-ttu-id="555da-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="555da-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="555da-109">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="555da-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="555da-110">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="555da-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="555da-111">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="555da-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="555da-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="555da-112">See also</span></span>

- [<span data-ttu-id="555da-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="555da-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="555da-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="555da-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
