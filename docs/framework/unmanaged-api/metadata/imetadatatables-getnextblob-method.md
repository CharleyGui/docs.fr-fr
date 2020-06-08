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
ms.openlocfilehash: 086448248364403b718408ad8bd32e48447742d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490379"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="1c21c-102">IMetaDataTables::GetNextBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="1c21c-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="1c21c-103">Obtient l’index de l’objet BLOB (Binary Large Object) suivant dans la table.</span><span class="sxs-lookup"><span data-stu-id="1c21c-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c21c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c21c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c21c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c21c-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="1c21c-106">dans Index, tel qu’il est retourné par une colonne d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="1c21c-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="1c21c-107">à Pointeur vers l’index de l’objet BLOB suivant.</span><span class="sxs-lookup"><span data-stu-id="1c21c-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c21c-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1c21c-108">Requirements</span></span>  
 <span data-ttu-id="1c21c-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c21c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c21c-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1c21c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c21c-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1c21c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c21c-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c21c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c21c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c21c-113">See also</span></span>

- [<span data-ttu-id="1c21c-114">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="1c21c-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="1c21c-115">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="1c21c-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
