---
title: ICorProfilerInfo::GetThreadInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 532288364b2db1e6be49b9e6f87019b1e41e6866
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497918"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="da67c-102">ICorProfilerInfo::GetThreadInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="da67c-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="da67c-103">Obtient l’identité de thread Win32 actuelle pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="da67c-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da67c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da67c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da67c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da67c-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="da67c-106">dans ID du thread pour lequel obtenir l’ID Win32 actuel.</span><span class="sxs-lookup"><span data-stu-id="da67c-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="da67c-107">à Pointeur vers l’ID de thread Win32 actuel du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="da67c-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da67c-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="da67c-108">Requirements</span></span>  
 <span data-ttu-id="da67c-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da67c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da67c-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da67c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da67c-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da67c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da67c-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da67c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da67c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da67c-113">See also</span></span>

- [<span data-ttu-id="da67c-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="da67c-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
