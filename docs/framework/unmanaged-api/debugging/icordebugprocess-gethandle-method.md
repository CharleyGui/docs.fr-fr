---
title: ICorDebugProcess::GetHandle, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: e4061580d59b0cf2a6e6e481d5242005e9452caf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128870"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="62585-102">ICorDebugProcess::GetHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="62585-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="62585-103">Obtient un handle pour le processus.</span><span class="sxs-lookup"><span data-stu-id="62585-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62585-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62585-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62585-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62585-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="62585-106">à Pointeur vers un `HPROCESS` qui est le handle du processus.</span><span class="sxs-lookup"><span data-stu-id="62585-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62585-107">Notes</span><span class="sxs-lookup"><span data-stu-id="62585-107">Remarks</span></span>  
 <span data-ttu-id="62585-108">Le handle récupéré appartient à l’interface de débogage.</span><span class="sxs-lookup"><span data-stu-id="62585-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="62585-109">Le débogueur doit dupliquer le handle avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="62585-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62585-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="62585-110">Requirements</span></span>  
 <span data-ttu-id="62585-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62585-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62585-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62585-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62585-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62585-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62585-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62585-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
