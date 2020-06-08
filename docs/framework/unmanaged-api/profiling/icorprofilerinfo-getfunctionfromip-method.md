---
title: ICorProfilerInfo::GetFunctionFromIP, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
ms.openlocfilehash: 339c5db1610a3cf087085ce19fc663436d9c4ec1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498308"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="5bbe6-102">ICorProfilerInfo::GetFunctionFromIP, méthode</span><span class="sxs-lookup"><span data-stu-id="5bbe6-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="5bbe6-103">Mappe un pointeur d’instruction de code managé à un `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="5bbe6-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bbe6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bbe6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bbe6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5bbe6-105">Parameters</span></span>

- `ip`

  <span data-ttu-id="5bbe6-106">\[in] pointeur d’instruction en code managé.</span><span class="sxs-lookup"><span data-stu-id="5bbe6-106">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="5bbe6-107">\[out] ID de la fonction retournée.</span><span class="sxs-lookup"><span data-stu-id="5bbe6-107">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="5bbe6-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5bbe6-108">Requirements</span></span>  
 <span data-ttu-id="5bbe6-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bbe6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bbe6-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5bbe6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5bbe6-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bbe6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bbe6-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bbe6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bbe6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bbe6-113">See also</span></span>

- [<span data-ttu-id="5bbe6-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="5bbe6-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
