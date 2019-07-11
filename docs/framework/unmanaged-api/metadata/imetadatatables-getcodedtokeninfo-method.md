---
title: IMetaDataTables::GetCodedTokenInfo, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b89409a08ed2dff0111b3b6e552960ac78a5882e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781530"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="ff904-102">IMetaDataTables::GetCodedTokenInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="ff904-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="ff904-103">Obtient un pointeur vers un tableau de jetons associé à l’index de ligne spécifié.</span><span class="sxs-lookup"><span data-stu-id="ff904-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff904-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff904-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff904-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff904-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="ff904-106">[in] Le type de jeton codé à retourner.</span><span class="sxs-lookup"><span data-stu-id="ff904-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ff904-107">[out] Un pointeur vers la longueur de `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="ff904-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="ff904-108">[out] Pointeur vers un pointeur vers un tableau qui contient la liste des jetons retournés.</span><span class="sxs-lookup"><span data-stu-id="ff904-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="ff904-109">[out] Un pointeur vers un pointeur vers le nom du jeton à `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="ff904-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff904-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ff904-110">Requirements</span></span>  
 <span data-ttu-id="ff904-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff904-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff904-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff904-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff904-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff904-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff904-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff904-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff904-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff904-115">See also</span></span>

- [<span data-ttu-id="ff904-116">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="ff904-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ff904-117">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="ff904-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
