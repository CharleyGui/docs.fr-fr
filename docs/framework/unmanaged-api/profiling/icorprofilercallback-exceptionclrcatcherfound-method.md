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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 683cec06cd4c2fdef310126adc2921c858ca5687
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776030"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="5f1d0-102">ICorProfilerCallback::ExceptionCLRCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="5f1d0-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="5f1d0-103">Appelé lorsqu’un `catch` block pour une exception se trouve dans le common language runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="5f1d0-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="5f1d0-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="5f1d0-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f1d0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f1d0-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="5f1d0-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5f1d0-106">Requirements</span></span>  
 <span data-ttu-id="5f1d0-107">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f1d0-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f1d0-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f1d0-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f1d0-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f1d0-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f1d0-110">**Version du .NET framework :** 1.0</span><span class="sxs-lookup"><span data-stu-id="5f1d0-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f1d0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f1d0-111">See also</span></span>

- [<span data-ttu-id="5f1d0-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="5f1d0-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="5f1d0-113">ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="5f1d0-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
