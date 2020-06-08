---
title: ICorProfilerCallback::ExceptionCLRCatcherFound, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: 4f4d53b086453adce38902518f2de3dde1f2812f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500245"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="06ff9-102">ICorProfilerCallback::ExceptionCLRCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="06ff9-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="06ff9-103">Appelée lorsqu’un `catch` bloc pour une exception est trouvé à l’intérieur du Common Language Runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="06ff9-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="06ff9-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06ff9-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06ff9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06ff9-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="06ff9-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="06ff9-106">Requirements</span></span>  
 <span data-ttu-id="06ff9-107">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06ff9-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06ff9-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06ff9-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06ff9-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06ff9-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06ff9-110">**Version de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="06ff9-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ff9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06ff9-111">See also</span></span>

- [<span data-ttu-id="06ff9-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="06ff9-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="06ff9-113">ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="06ff9-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
