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
ms.openlocfilehash: 41e7b8193ce3288d526db8d7d8c289b0a053ee4e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489754"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="74095-102">IMetaDataTables::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="74095-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="74095-103">Obtient la chaîne à l’index spécifié à partir de la colonne de table dans la portée de référence actuelle.</span><span class="sxs-lookup"><span data-stu-id="74095-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74095-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74095-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74095-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74095-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="74095-106">dans Index à partir duquel commencer la recherche de la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="74095-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="74095-107">à Pointeur vers un pointeur vers la valeur de chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="74095-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74095-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="74095-108">Requirements</span></span>  
 <span data-ttu-id="74095-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74095-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74095-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="74095-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74095-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="74095-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74095-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74095-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74095-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74095-113">See also</span></span>

- [<span data-ttu-id="74095-114">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="74095-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="74095-115">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="74095-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
