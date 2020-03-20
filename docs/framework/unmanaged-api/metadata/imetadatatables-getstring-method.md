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
ms.openlocfilehash: 216a1f7bd2ff5a596fa7abf7874b5e603d5a9f7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175237"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="bd61c-102">IMetaDataTables::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="bd61c-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="bd61c-103">Obtient la chaîne à l’index spécifié à partir de la colonne de table dans la portée de référence actuelle.</span><span class="sxs-lookup"><span data-stu-id="bd61c-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd61c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd61c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd61c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd61c-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="bd61c-106">[dans] L’indice auquel commencer à chercher la prochaine valeur.</span><span class="sxs-lookup"><span data-stu-id="bd61c-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="bd61c-107">[out] Un pointeur à un pointeur à la valeur de la chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="bd61c-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd61c-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bd61c-108">Requirements</span></span>  
 <span data-ttu-id="bd61c-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd61c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd61c-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="bd61c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd61c-111">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd61c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd61c-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd61c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd61c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd61c-113">See also</span></span>

- [<span data-ttu-id="bd61c-114">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="bd61c-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="bd61c-115">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="bd61c-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
