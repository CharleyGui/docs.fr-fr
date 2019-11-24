---
title: IMethodMalloc::Alloc, méthode
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447571"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="19885-102">IMethodMalloc::Alloc, méthode</span><span class="sxs-lookup"><span data-stu-id="19885-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="19885-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span><span class="sxs-lookup"><span data-stu-id="19885-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="19885-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19885-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="19885-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19885-105">Parameters</span></span>

`cb`\
<span data-ttu-id="19885-106">[in] The number of bytes to allocate for the method body.</span><span class="sxs-lookup"><span data-stu-id="19885-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="19885-107">Notes</span><span class="sxs-lookup"><span data-stu-id="19885-107">Remarks</span></span>

 <span data-ttu-id="19885-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span><span class="sxs-lookup"><span data-stu-id="19885-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="19885-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span><span class="sxs-lookup"><span data-stu-id="19885-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="19885-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span><span class="sxs-lookup"><span data-stu-id="19885-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="19885-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="19885-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="19885-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="19885-112">Requirements</span></span>
 <span data-ttu-id="19885-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19885-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="19885-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19885-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="19885-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19885-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="19885-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19885-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="19885-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19885-117">See also</span></span>

- [<span data-ttu-id="19885-118">IMethodMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="19885-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
