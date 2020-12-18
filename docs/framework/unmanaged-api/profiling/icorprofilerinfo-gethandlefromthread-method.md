---
title: ICorProfilerInfo::GetHandleFromThread, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 94c2c6e01e4188f1fa13c3b6a9f638d4b79a502f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678192"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="0e407-102">ICorProfilerInfo::GetHandleFromThread, méthode</span><span class="sxs-lookup"><span data-stu-id="0e407-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="0e407-103">Mappe l’ID d’un thread à un handle de thread Win32.</span><span class="sxs-lookup"><span data-stu-id="0e407-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e407-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e407-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e407-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e407-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="0e407-106">dans ID de thread à mapper.</span><span class="sxs-lookup"><span data-stu-id="0e407-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="0e407-107">à Pointeur vers un handle de thread Win32.</span><span class="sxs-lookup"><span data-stu-id="0e407-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e407-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="0e407-108">Remarks</span></span>  

 <span data-ttu-id="0e407-109">Le profileur doit appeler la `DuplicateHandle` fonction Win32 sur le descripteur avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="0e407-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  

 <span data-ttu-id="0e407-110">Le handle retourné par cette méthode est détenu par le runtime et le profileur ne doit jamais le fermer.</span><span class="sxs-lookup"><span data-stu-id="0e407-110">The handle returned from this method is owned by the runtime and the profiler should never close it.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="0e407-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e407-111">Requirements</span></span>  

 <span data-ttu-id="0e407-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e407-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e407-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0e407-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0e407-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e407-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e407-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e407-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e407-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e407-116">See also</span></span>

- [<span data-ttu-id="0e407-117">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="0e407-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
