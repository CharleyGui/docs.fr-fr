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
ms.openlocfilehash: 64c70fe0b657047ae35dccb763fa57120403deef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177149"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="d5736-102">IMetaDataTables::GetCodedTokenInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="d5736-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="d5736-103">Obtient un pointeur à un tableau de jetons associés à l’index de ligne spécifié.</span><span class="sxs-lookup"><span data-stu-id="d5736-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5736-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5736-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5736-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d5736-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="d5736-106">[dans] Le genre de jeton codé pour revenir.</span><span class="sxs-lookup"><span data-stu-id="d5736-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d5736-107">[out] Un pointeur à `ppTokens`la longueur de .</span><span class="sxs-lookup"><span data-stu-id="d5736-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="d5736-108">[out] Un pointeur à un pointeur à un tableau qui contient la liste des jetons retournés.</span><span class="sxs-lookup"><span data-stu-id="d5736-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="d5736-109">[out] Un pointeur à un pointeur au `ixCdTkn`nom du jeton à .</span><span class="sxs-lookup"><span data-stu-id="d5736-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5736-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d5736-110">Requirements</span></span>  
 <span data-ttu-id="d5736-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5736-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5736-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="d5736-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5736-113">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5736-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5736-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5736-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5736-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5736-115">See also</span></span>

- [<span data-ttu-id="d5736-116">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="d5736-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d5736-117">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="d5736-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
