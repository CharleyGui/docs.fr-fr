---
title: ICorProfilerInfo::GetCodeInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: eb6efc738b270f8f76d7130a12af4927fb6220ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498360"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="f0c05-102">ICorProfilerInfo::GetCodeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="f0c05-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="f0c05-103">Obtient l'étendue de code natif associée à l'ID de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f0c05-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="f0c05-104">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="f0c05-104">This method is obsolete.</span></span> <span data-ttu-id="f0c05-105">Utilisez la méthode [ICorProfilerInfo2 :: GetCodeInfo2,](icorprofilerinfo2-getcodeinfo2-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="f0c05-105">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0c05-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0c05-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0c05-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0c05-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f0c05-108">[in] ID de la fonction à laquelle le code natif est associé.</span><span class="sxs-lookup"><span data-stu-id="f0c05-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="f0c05-109">[out] Pointeur vers un tableau d'octets qui composent le code natif de la fonction.</span><span class="sxs-lookup"><span data-stu-id="f0c05-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="f0c05-110">[out] Pointeur vers un entier qui spécifie la taille, en octets, du code natif.</span><span class="sxs-lookup"><span data-stu-id="f0c05-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0c05-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0c05-111">Remarks</span></span>  
 <span data-ttu-id="f0c05-112">Pour optimiser la performance, le runtime dans la version 2.0 du .NET Framework fractionne le code natif précompilé d'une fonction en plusieurs régions.</span><span class="sxs-lookup"><span data-stu-id="f0c05-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="f0c05-113">Par conséquent, la méthode `GetCodeInfo` est obsolète dans .NET Framework 2.0, car elle ne peut pas gérer l'étendue du code natif d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="f0c05-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="f0c05-114">Les profileurs doivent utiliser la méthode `ICorProfilerInfo2::GetCodeInfo2` plus générale à la place.</span><span class="sxs-lookup"><span data-stu-id="f0c05-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="f0c05-115">Cette fonction utilise des mémoires tampons allouées par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="f0c05-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c05-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f0c05-116">Requirements</span></span>  
 <span data-ttu-id="f0c05-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0c05-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c05-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0c05-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0c05-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0c05-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0c05-120">**Versions de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="f0c05-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c05-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0c05-121">See also</span></span>

- [<span data-ttu-id="f0c05-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="f0c05-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f0c05-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="f0c05-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f0c05-124">Profilage</span><span class="sxs-lookup"><span data-stu-id="f0c05-124">Profiling</span></span>](index.md)
