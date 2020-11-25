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
ms.openlocfilehash: e508bcae15e72ce592529cf4b68af5d75ea49038
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721957"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="2dda6-102">IMetaDataTables::GetBlobHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="2dda6-102">IMetaDataTables::GetBlobHeapSize Method</span></span>

<span data-ttu-id="2dda6-103">Obtient la taille, en octets, du tas d’objets BLOB (Binary Large Object).</span><span class="sxs-lookup"><span data-stu-id="2dda6-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dda6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dda6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2dda6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2dda6-105">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="2dda6-106">à Pointeur vers la taille, en octets, du tas d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="2dda6-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dda6-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2dda6-107">Requirements</span></span>  

 <span data-ttu-id="2dda6-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dda6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dda6-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2dda6-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2dda6-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2dda6-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2dda6-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dda6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dda6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dda6-112">See also</span></span>

- [<span data-ttu-id="2dda6-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="2dda6-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="2dda6-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="2dda6-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
