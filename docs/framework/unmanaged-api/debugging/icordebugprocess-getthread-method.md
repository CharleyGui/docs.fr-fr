---
title: ICorDebugProcess::GetThread, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
ms.openlocfilehash: e70204aa555ed9411d1d2cd5ad8cde7e0c53de2a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694995"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="59162-102">ICorDebugProcess::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="59162-102">ICorDebugProcess::GetThread Method</span></span>

<span data-ttu-id="59162-103">Obtient le thread de ce processus qui a l’ID de thread du système d’exploitation spécifié.</span><span class="sxs-lookup"><span data-stu-id="59162-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59162-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59162-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59162-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59162-105">Parameters</span></span>  

 `dwThreadId`  
 <span data-ttu-id="59162-106">dans ID de thread de système d’exploitation du thread à récupérer.</span><span class="sxs-lookup"><span data-stu-id="59162-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="59162-107">à Pointeur vers l’adresse d’un objet ICorDebugThread qui représente le thread.</span><span class="sxs-lookup"><span data-stu-id="59162-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59162-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="59162-108">Requirements</span></span>  

 <span data-ttu-id="59162-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59162-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59162-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59162-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59162-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59162-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59162-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59162-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
