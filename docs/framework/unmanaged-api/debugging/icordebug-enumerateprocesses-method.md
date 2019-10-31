---
title: ICorDebug::EnumerateProcesses, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
ms.openlocfilehash: 09a8a2bb38378f5d4a32d7b00b68d02f1aa4c054
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110714"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="c2e48-102">ICorDebug::EnumerateProcesses, méthode</span><span class="sxs-lookup"><span data-stu-id="c2e48-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="c2e48-103">Obtient un énumérateur pour les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="c2e48-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2e48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2e48-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2e48-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c2e48-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="c2e48-106">Pointeur vers l’adresse d’un objet ICorDebugProcessEnum qui est l’énumérateur pour les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="c2e48-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2e48-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="c2e48-107">Requirements</span></span>  
 <span data-ttu-id="c2e48-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2e48-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2e48-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2e48-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2e48-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2e48-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2e48-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2e48-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e48-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2e48-112">See also</span></span>

- [<span data-ttu-id="c2e48-113">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="c2e48-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
