---
title: ICorDebugThread2::GetVolatileOSThreadID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
ms.openlocfilehash: e8d59d617efa7656a3034d5c5e009a46b6121cdb
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377657"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="62b79-102">ICorDebugThread2::GetVolatileOSThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="62b79-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="62b79-103">Obtient l’identificateur de thread de système d’exploitation pour ce ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="62b79-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62b79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62b79-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62b79-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62b79-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="62b79-106">à Identificateur de thread de système d’exploitation pour ce thread.</span><span class="sxs-lookup"><span data-stu-id="62b79-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62b79-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="62b79-107">Requirements</span></span>  
 <span data-ttu-id="62b79-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62b79-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62b79-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62b79-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62b79-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62b79-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62b79-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62b79-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
