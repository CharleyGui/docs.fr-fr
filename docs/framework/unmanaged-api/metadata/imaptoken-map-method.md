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
ms.openlocfilehash: fd362beb9f8fd7a1f2076eb6490a96c0358520e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432153"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="1b805-102">IMapToken::Map, méthode</span><span class="sxs-lookup"><span data-stu-id="1b805-102">IMapToken::Map Method</span></span>
<span data-ttu-id="1b805-103">Maps a relationship between the assemblies using metadata signatures.</span><span class="sxs-lookup"><span data-stu-id="1b805-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b805-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b805-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b805-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b805-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="1b805-106">[in] The metadata token that represents the imported code object.</span><span class="sxs-lookup"><span data-stu-id="1b805-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="1b805-107">[in] The metadata token that represents the emitted code object.</span><span class="sxs-lookup"><span data-stu-id="1b805-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b805-108">Notes</span><span class="sxs-lookup"><span data-stu-id="1b805-108">Remarks</span></span>  
 <span data-ttu-id="1b805-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span><span class="sxs-lookup"><span data-stu-id="1b805-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b805-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="1b805-110">Requirements</span></span>  
 <span data-ttu-id="1b805-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b805-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b805-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b805-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b805-113">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b805-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b805-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b805-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b805-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b805-115">See also</span></span>

- [<span data-ttu-id="1b805-116">IMapToken, interface</span><span class="sxs-lookup"><span data-stu-id="1b805-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
