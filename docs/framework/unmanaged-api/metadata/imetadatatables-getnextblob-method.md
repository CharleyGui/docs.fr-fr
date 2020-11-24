---
title: IMetaDataTables::GetNextBlob, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: ba694f485d5a51870a1283b6ccbcb7b042a14501
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685641"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="fe196-102">IMetaDataTables::GetNextBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="fe196-102">IMetaDataTables::GetNextBlob Method</span></span>

<span data-ttu-id="fe196-103">Obtient l’index de l’objet BLOB (Binary Large Object) suivant dans la table.</span><span class="sxs-lookup"><span data-stu-id="fe196-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe196-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe196-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe196-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe196-105">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="fe196-106">dans Index, tel qu’il est retourné par une colonne d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="fe196-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="fe196-107">à Pointeur vers l’index de l’objet BLOB suivant.</span><span class="sxs-lookup"><span data-stu-id="fe196-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe196-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fe196-108">Requirements</span></span>  

 <span data-ttu-id="fe196-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe196-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe196-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fe196-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe196-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe196-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe196-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe196-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe196-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe196-113">See also</span></span>

- [<span data-ttu-id="fe196-114">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="fe196-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="fe196-115">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="fe196-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
