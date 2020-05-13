---
title: ICorDebugProcessEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: d00a5f71ac7e47d78deebca0e46350e465964c72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210096"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="96d93-102">ICorDebugProcessEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="96d93-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="96d93-103">Obtient le nombre spécifié d’instances ICorDebugProcess de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="96d93-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96d93-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96d93-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96d93-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="96d93-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="96d93-106">dans Nombre d' `ICorDebugProcess` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="96d93-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="96d93-107">à Tableau de pointeurs, chacun pointant vers un `ICorDebugProcess` objet qui représente un processus.</span><span class="sxs-lookup"><span data-stu-id="96d93-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="96d93-108">à Pointeur vers le nombre d' `ICorDebugProcess` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="96d93-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="96d93-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="96d93-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96d93-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="96d93-110">Requirements</span></span>  
 <span data-ttu-id="96d93-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96d93-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96d93-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96d93-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96d93-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96d93-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96d93-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96d93-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
