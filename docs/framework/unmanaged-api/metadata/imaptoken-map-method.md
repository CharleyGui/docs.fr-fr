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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ac12d5b6bc2911e3bd879285a9a12f65c426f0d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745855"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="096e4-102">IMapToken::Map, méthode</span><span class="sxs-lookup"><span data-stu-id="096e4-102">IMapToken::Map Method</span></span>
<span data-ttu-id="096e4-103">Mappe une relation entre les assemblys à l’aide de signatures de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="096e4-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="096e4-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="096e4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="096e4-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="096e4-106">[in] Le jeton de métadonnées qui représente l’objet de code importé.</span><span class="sxs-lookup"><span data-stu-id="096e4-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="096e4-107">[in] Le jeton de métadonnées qui représente l’objet de code émis.</span><span class="sxs-lookup"><span data-stu-id="096e4-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="096e4-108">Notes</span><span class="sxs-lookup"><span data-stu-id="096e4-108">Remarks</span></span>  
 <span data-ttu-id="096e4-109">Lorsque le jeton remapper se produit pendant une fusion, le jeton d’origine est étendu dans la portée de métadonnées importées (source) et le nouveau jeton est limité dans la portée de métadonnées émise (cible).</span><span class="sxs-lookup"><span data-stu-id="096e4-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096e4-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="096e4-110">Requirements</span></span>  
 <span data-ttu-id="096e4-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="096e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="096e4-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="096e4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="096e4-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="096e4-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="096e4-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="096e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="096e4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="096e4-115">See also</span></span>

- [<span data-ttu-id="096e4-116">IMapToken, interface</span><span class="sxs-lookup"><span data-stu-id="096e4-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
