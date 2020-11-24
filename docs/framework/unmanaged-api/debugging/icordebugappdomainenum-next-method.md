---
title: ICorDebugAppDomainEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: b315f38dc306727e33b52b84d17951a91ccdc39f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684471"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="fd91a-102">ICorDebugAppDomainEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="fd91a-102">ICorDebugAppDomainEnum::Next Method</span></span>

<span data-ttu-id="fd91a-103">Obtient le nombre spécifié de domaines d’application à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="fd91a-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd91a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd91a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd91a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fd91a-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="fd91a-106">dans Nombre de domaines d’application à récupérer.</span><span class="sxs-lookup"><span data-stu-id="fd91a-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="fd91a-107">à Tableau de pointeurs, chacun pointant vers un objet ICorDebugAppDomain qui représente un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="fd91a-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fd91a-108">à Pointeur vers le nombre de domaines d’application réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="fd91a-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="fd91a-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="fd91a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd91a-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fd91a-110">Requirements</span></span>  

 <span data-ttu-id="fd91a-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd91a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd91a-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd91a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd91a-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd91a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd91a-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd91a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
