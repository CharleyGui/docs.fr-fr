---
title: ICorProfilerInfo3::GetStringLayout2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: f3727343755d7014202f844be28414d31ce55bc1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862254"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="3cc83-102">ICorProfilerInfo3::GetStringLayout2, méthode</span><span class="sxs-lookup"><span data-stu-id="3cc83-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="3cc83-103">Obtient des informations sur la disposition d'un objet string.</span><span class="sxs-lookup"><span data-stu-id="3cc83-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="3cc83-104">Cette méthode remplace la méthode [ICorProfilerInfo2 :: GetStringLayout,](icorprofilerinfo2-getstringlayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3cc83-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc83-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cc83-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc83-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="3cc83-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="3cc83-107">à Pointeur vers le décalage de l’emplacement, relatif au pointeur `ObjectID`, qui stocke la longueur de la chaîne elle-même.</span><span class="sxs-lookup"><span data-stu-id="3cc83-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="3cc83-108">La longueur est stockée sous la forme d’un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="3cc83-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="3cc83-109">à Pointeur vers l’offset de la mémoire tampon, par rapport au pointeur de `ObjectID`, qui stocke la chaîne de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="3cc83-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cc83-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3cc83-110">Remarks</span></span>  
 <span data-ttu-id="3cc83-111">Les chaînes peuvent ou non se terminer par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="3cc83-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc83-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="3cc83-112">Requirements</span></span>  
 <span data-ttu-id="3cc83-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cc83-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc83-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3cc83-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3cc83-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cc83-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cc83-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc83-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc83-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cc83-117">See also</span></span>

- [<span data-ttu-id="3cc83-118">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="3cc83-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3cc83-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="3cc83-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
