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
ms.openlocfilehash: 65d9c3688f3a41312a17e6058f73596fc2503dd4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694982"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="b281a-102">ICorDebugProcess::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="b281a-102">ICorDebugProcess::GetID Method</span></span>

<span data-ttu-id="b281a-103">Obtient l’ID (se) du système d’exploitation du processus.</span><span class="sxs-lookup"><span data-stu-id="b281a-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b281a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b281a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b281a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b281a-105">Parameters</span></span>  

 `pdwProcessId`  
 <span data-ttu-id="b281a-106">à ID unique du processus.</span><span class="sxs-lookup"><span data-stu-id="b281a-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b281a-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b281a-107">Requirements</span></span>  

 <span data-ttu-id="b281a-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b281a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b281a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b281a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b281a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b281a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b281a-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b281a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
