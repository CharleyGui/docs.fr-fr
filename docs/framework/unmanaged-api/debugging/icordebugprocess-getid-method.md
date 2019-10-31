---
title: ICorDebugProcess::GetID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
ms.openlocfilehash: ae0c23e3d48df6add8951a6d90029185a99bb323
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128829"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="779e3-102">ICorDebugProcess::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="779e3-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="779e3-103">Obtient l’ID (se) du système d’exploitation du processus.</span><span class="sxs-lookup"><span data-stu-id="779e3-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="779e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="779e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="779e3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="779e3-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="779e3-106">à ID unique du processus.</span><span class="sxs-lookup"><span data-stu-id="779e3-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="779e3-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="779e3-107">Requirements</span></span>  
 <span data-ttu-id="779e3-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="779e3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="779e3-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="779e3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="779e3-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="779e3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="779e3-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="779e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
