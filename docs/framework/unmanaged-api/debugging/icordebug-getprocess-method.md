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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e77046745381d3ecc35c24d5af3f9181b9132e9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738161"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="d541a-102">ICorDebug::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="d541a-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="d541a-103">Obtient un pointeur vers l’instance « ICorDebugProcess » pour le processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="d541a-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d541a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d541a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d541a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d541a-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="d541a-106">[in] ID du processus.</span><span class="sxs-lookup"><span data-stu-id="d541a-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="d541a-107">[out] Un pointeur vers l’adresse d’un `ICorDebugProcess` instance pour le processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="d541a-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d541a-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d541a-108">Requirements</span></span>  
 <span data-ttu-id="d541a-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d541a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d541a-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d541a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d541a-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d541a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d541a-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d541a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d541a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d541a-113">See also</span></span>

- [<span data-ttu-id="d541a-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="d541a-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
