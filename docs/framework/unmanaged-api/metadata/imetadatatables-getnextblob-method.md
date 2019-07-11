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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1e7181f50d94fa417bf9d00c3531747cefca82c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781477"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="d5c71-102">IMetaDataTables::GetNextBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="d5c71-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="d5c71-103">Obtient l’index de l’objet binaire volumineux (BLOB) de suivant dans la table.</span><span class="sxs-lookup"><span data-stu-id="d5c71-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5c71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5c71-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d5c71-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="d5c71-106">[in] L’index, tel que retourné par une colonne d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="d5c71-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="d5c71-107">[out] Pointeur vers l’index de l’objet BLOB suivant.</span><span class="sxs-lookup"><span data-stu-id="d5c71-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c71-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d5c71-108">Requirements</span></span>  
 <span data-ttu-id="d5c71-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5c71-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c71-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d5c71-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5c71-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5c71-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5c71-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c71-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c71-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5c71-113">See also</span></span>

- [<span data-ttu-id="d5c71-114">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="d5c71-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d5c71-115">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="d5c71-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
