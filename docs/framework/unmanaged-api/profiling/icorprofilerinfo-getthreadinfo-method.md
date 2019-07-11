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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 405d5ff49ba7bc2e5204f00cf50c30822354e56d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775588"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="af00f-102">ICorProfilerInfo::GetThreadInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="af00f-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="af00f-103">Obtient l’identité de thread Win32 actuelle pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="af00f-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af00f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af00f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af00f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="af00f-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="af00f-106">[in] L’ID du thread pour lequel obtenir l’ID Win32 actuel.</span><span class="sxs-lookup"><span data-stu-id="af00f-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="af00f-107">[out] ID un pointeur vers le thread de Win32 actuel du thread spécifié d'.</span><span class="sxs-lookup"><span data-stu-id="af00f-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af00f-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="af00f-108">Requirements</span></span>  
 <span data-ttu-id="af00f-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af00f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af00f-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af00f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af00f-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af00f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af00f-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af00f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af00f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af00f-113">See also</span></span>

- [<span data-ttu-id="af00f-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="af00f-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
