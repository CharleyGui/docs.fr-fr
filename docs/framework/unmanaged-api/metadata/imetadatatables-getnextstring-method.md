---
title: IMetaDataTables::GetNextString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
ms.openlocfilehash: 6f4764f016360a2ec0ab054b7a89ccb3f86aeb43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490222"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="fe45e-102">IMetaDataTables::GetNextString, méthode</span><span class="sxs-lookup"><span data-stu-id="fe45e-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="fe45e-103">Obtient l’index de la chaîne suivante dans la colonne de table actuelle.</span><span class="sxs-lookup"><span data-stu-id="fe45e-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe45e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe45e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe45e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe45e-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="fe45e-106">dans Valeur d’index d’une colonne de table de chaînes.</span><span class="sxs-lookup"><span data-stu-id="fe45e-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="fe45e-107">à Pointeur vers l’index de la chaîne suivante dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="fe45e-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe45e-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fe45e-108">Requirements</span></span>  
 <span data-ttu-id="fe45e-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe45e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe45e-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fe45e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe45e-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fe45e-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe45e-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe45e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe45e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe45e-113">See also</span></span>

- [<span data-ttu-id="fe45e-114">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="fe45e-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="fe45e-115">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="fe45e-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
