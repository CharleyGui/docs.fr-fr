---
title: IMetaDataTables::GetUserStringHeapSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 1aea017f17e29544e9288e1f57e6f84f9a2f6dae
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501103"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="4d5cb-102">IMetaDataTables::GetUserStringHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="4d5cb-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="4d5cb-103">Obtient la taille, en octets, du tas de la chaîne utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d5cb-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d5cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d5cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d5cb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4d5cb-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="4d5cb-106">à Pointeur vers la taille, en octets, du tas de la chaîne utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d5cb-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d5cb-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4d5cb-107">Requirements</span></span>  
 <span data-ttu-id="4d5cb-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d5cb-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d5cb-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4d5cb-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d5cb-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d5cb-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d5cb-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d5cb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d5cb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d5cb-112">See also</span></span>

- [<span data-ttu-id="4d5cb-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="4d5cb-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="4d5cb-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="4d5cb-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
