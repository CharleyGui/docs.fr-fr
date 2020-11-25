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
ms.openlocfilehash: 4a7e21ae60253c741b57674212e0ecabdd844d2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722555"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="fc4bb-102">ICorProfilerInfo::GetFunctionFromIP, méthode</span><span class="sxs-lookup"><span data-stu-id="fc4bb-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>

<span data-ttu-id="fc4bb-103">Mappe un pointeur d’instruction de code managé à un `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="fc4bb-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc4bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc4bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc4bb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc4bb-105">Parameters</span></span>

- `ip`

  <span data-ttu-id="fc4bb-106">\[in] pointeur d’instruction en code managé.</span><span class="sxs-lookup"><span data-stu-id="fc4bb-106">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="fc4bb-107">\[out] ID de la fonction retournée.</span><span class="sxs-lookup"><span data-stu-id="fc4bb-107">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc4bb-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc4bb-108">Requirements</span></span>  

 <span data-ttu-id="fc4bb-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc4bb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc4bb-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc4bb-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc4bb-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc4bb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc4bb-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc4bb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4bb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc4bb-113">See also</span></span>

- [<span data-ttu-id="fc4bb-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="fc4bb-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
