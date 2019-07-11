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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ebdf0dd2457cd10e31ff71c32b1c09d0e014431
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765989"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="12cf1-102">ICorDebugProcess::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="12cf1-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="12cf1-103">Obtient l’ID de système d’exploitation (se) du processus.</span><span class="sxs-lookup"><span data-stu-id="12cf1-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12cf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12cf1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12cf1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12cf1-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="12cf1-106">[out] ID unique du processus.</span><span class="sxs-lookup"><span data-stu-id="12cf1-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12cf1-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12cf1-107">Requirements</span></span>  
 <span data-ttu-id="12cf1-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12cf1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12cf1-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12cf1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12cf1-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12cf1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12cf1-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12cf1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
