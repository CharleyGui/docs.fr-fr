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
ms.openlocfilehash: 048010f00f6581a29c6b1a3150bf5ae8822b5664
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672459"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="64a97-102">IMetaDataTables::GetUserStringHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="64a97-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>

<span data-ttu-id="64a97-103">Obtient la taille, en octets, du tas de la chaîne utilisateur.</span><span class="sxs-lookup"><span data-stu-id="64a97-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a97-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64a97-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64a97-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="64a97-105">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="64a97-106">à Pointeur vers la taille, en octets, du tas de la chaîne utilisateur.</span><span class="sxs-lookup"><span data-stu-id="64a97-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64a97-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="64a97-107">Requirements</span></span>  

 <span data-ttu-id="64a97-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64a97-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64a97-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="64a97-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64a97-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64a97-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64a97-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64a97-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a97-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64a97-112">See also</span></span>

- [<span data-ttu-id="64a97-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="64a97-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="64a97-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="64a97-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
