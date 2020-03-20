---
title: IMapToken::Map, méthode
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176069"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="cc730-102">IMapToken::Map, méthode</span><span class="sxs-lookup"><span data-stu-id="cc730-102">IMapToken::Map Method</span></span>
<span data-ttu-id="cc730-103">Cartographiez une relation entre les assemblées à l’aide de signatures de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="cc730-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc730-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc730-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc730-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc730-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="cc730-106">[dans] Le jeton des métadonnées qui représente l’objet de code importé.</span><span class="sxs-lookup"><span data-stu-id="cc730-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="cc730-107">[dans] Le jeton des métadonnées qui représente l’objet de code émis.</span><span class="sxs-lookup"><span data-stu-id="cc730-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc730-108">Notes </span><span class="sxs-lookup"><span data-stu-id="cc730-108">Remarks</span></span>  
 <span data-ttu-id="cc730-109">Lorsque la refonte du jeton se produit lors d’une fusion, le jeton d’origine est visé dans la portée des métadonnées importées (source) et le nouveau jeton est visé dans la portée des métadonnées émises (cible).</span><span class="sxs-lookup"><span data-stu-id="cc730-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc730-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cc730-110">Requirements</span></span>  
 <span data-ttu-id="cc730-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc730-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc730-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="cc730-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc730-113">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc730-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc730-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc730-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc730-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc730-115">See also</span></span>

- [<span data-ttu-id="cc730-116">IMapToken, interface</span><span class="sxs-lookup"><span data-stu-id="cc730-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
