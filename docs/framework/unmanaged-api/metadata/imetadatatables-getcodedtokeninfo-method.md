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
ms.openlocfilehash: 8ab16ad5b2b2838125e07511ef47be737f40671c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501207"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="7451f-102">IMetaDataTables::GetCodedTokenInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="7451f-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="7451f-103">Obtient un pointeur vers un tableau de jetons associé à l’index de ligne spécifié.</span><span class="sxs-lookup"><span data-stu-id="7451f-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7451f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7451f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7451f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7451f-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="7451f-106">dans Type de jeton codé à retourner.</span><span class="sxs-lookup"><span data-stu-id="7451f-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7451f-107">à Pointeur vers la longueur de `ppTokens` .</span><span class="sxs-lookup"><span data-stu-id="7451f-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="7451f-108">à Pointeur vers un pointeur vers un tableau qui contient la liste des jetons retournés.</span><span class="sxs-lookup"><span data-stu-id="7451f-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="7451f-109">à Pointeur vers un pointeur vers le nom du jeton à `ixCdTkn` .</span><span class="sxs-lookup"><span data-stu-id="7451f-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7451f-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7451f-110">Requirements</span></span>  
 <span data-ttu-id="7451f-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7451f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7451f-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7451f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7451f-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7451f-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7451f-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7451f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7451f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7451f-115">See also</span></span>

- [<span data-ttu-id="7451f-116">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="7451f-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="7451f-117">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="7451f-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
