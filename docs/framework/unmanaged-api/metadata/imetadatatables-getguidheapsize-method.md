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
ms.openlocfilehash: 1b524067ac72dfd3bd19475f11d4ec12a307731d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702418"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="9e727-102">IMetaDataTables::GetGuidHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="9e727-102">IMetaDataTables::GetGuidHeapSize Method</span></span>

<span data-ttu-id="9e727-103">Obtient la taille, en octets, du tas GUID.</span><span class="sxs-lookup"><span data-stu-id="9e727-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e727-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e727-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e727-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9e727-105">Parameters</span></span>  

 `pcbGuids`  
 <span data-ttu-id="9e727-106">à Pointeur vers la taille, en octets, du tas GUID.</span><span class="sxs-lookup"><span data-stu-id="9e727-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e727-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9e727-107">Requirements</span></span>  

 <span data-ttu-id="9e727-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e727-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e727-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9e727-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e727-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e727-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9e727-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e727-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e727-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e727-112">See also</span></span>

- [<span data-ttu-id="9e727-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="9e727-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9e727-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="9e727-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
