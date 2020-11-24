---
title: IMetaDataTables::GetString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 8ecaa003084064be1071a85aa726c38d773ec0b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672576"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="9ceb6-102">IMetaDataTables::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="9ceb6-102">IMetaDataTables::GetString Method</span></span>

<span data-ttu-id="9ceb6-103">Obtient la chaîne à l’index spécifié à partir de la colonne de table dans la portée de référence actuelle.</span><span class="sxs-lookup"><span data-stu-id="9ceb6-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ceb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ceb6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ceb6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ceb6-105">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="9ceb6-106">dans Index à partir duquel commencer la recherche de la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="9ceb6-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="9ceb6-107">à Pointeur vers un pointeur vers la valeur de chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="9ceb6-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ceb6-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ceb6-108">Requirements</span></span>  

 <span data-ttu-id="9ceb6-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ceb6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ceb6-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9ceb6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ceb6-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ceb6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ceb6-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ceb6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ceb6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ceb6-113">See also</span></span>

- [<span data-ttu-id="9ceb6-114">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="9ceb6-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9ceb6-115">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="9ceb6-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
