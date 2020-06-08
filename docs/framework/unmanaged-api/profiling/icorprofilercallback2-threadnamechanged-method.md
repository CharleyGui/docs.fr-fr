---
title: ICorProfilerCallback2::ThreadNameChanged, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 3eb108ed20d0fd1287cb82eb4d552206aeae15d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499725"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="87a69-102">ICorProfilerCallback2::ThreadNameChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="87a69-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="87a69-103">Notifie le profileur de code que le nom d’un thread a changé.</span><span class="sxs-lookup"><span data-stu-id="87a69-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87a69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87a69-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87a69-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="87a69-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="87a69-106">dans ID du thread.</span><span class="sxs-lookup"><span data-stu-id="87a69-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="87a69-107">dans Longueur du nouveau nom du thread.</span><span class="sxs-lookup"><span data-stu-id="87a69-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="87a69-108">dans Nouveau nom du thread.</span><span class="sxs-lookup"><span data-stu-id="87a69-108">[in] The new name of the thread.</span></span> <span data-ttu-id="87a69-109">Le nom ne se termine pas par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="87a69-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87a69-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="87a69-110">Requirements</span></span>  
 <span data-ttu-id="87a69-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87a69-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87a69-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87a69-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87a69-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87a69-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87a69-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87a69-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a69-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87a69-115">See also</span></span>

- [<span data-ttu-id="87a69-116">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="87a69-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="87a69-117">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="87a69-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
