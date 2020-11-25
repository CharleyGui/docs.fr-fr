---
title: ICorDebug::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
ms.openlocfilehash: 46c2b444984c5a0062f1cfbc0cd29dbe409b16fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723439"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="4a968-102">ICorDebug::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="4a968-102">ICorDebug::GetProcess Method</span></span>

<span data-ttu-id="4a968-103">Obtient un pointeur vers l’instance « ICorDebugProcess » pour le processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a968-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a968-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a968-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a968-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4a968-105">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="4a968-106">dans ID du processus.</span><span class="sxs-lookup"><span data-stu-id="4a968-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="4a968-107">à Pointeur vers l’adresse d’une `ICorDebugProcess` instance pour le processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a968-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a968-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4a968-108">Requirements</span></span>  

 <span data-ttu-id="4a968-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a968-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a968-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a968-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a968-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a968-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a968-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a968-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a968-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a968-113">See also</span></span>

- [<span data-ttu-id="4a968-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="4a968-114">ICorDebug Interface</span></span>](icordebug-interface.md)
