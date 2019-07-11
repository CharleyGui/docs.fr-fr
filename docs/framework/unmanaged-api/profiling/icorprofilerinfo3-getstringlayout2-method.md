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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ac724db000f84e37995a34e808d3df4b1e7a960
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765406"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="5d38f-102">ICorProfilerInfo3::GetStringLayout2, méthode</span><span class="sxs-lookup"><span data-stu-id="5d38f-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="5d38f-103">Obtient des informations sur la disposition d'un objet string.</span><span class="sxs-lookup"><span data-stu-id="5d38f-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="5d38f-104">Cette méthode remplace la [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5d38f-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d38f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d38f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d38f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5d38f-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="5d38f-107">[out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne elle-même.</span><span class="sxs-lookup"><span data-stu-id="5d38f-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="5d38f-108">La longueur est stockée comme un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="5d38f-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="5d38f-109">[out] Un pointeur vers l’offset de la mémoire tampon, relative à la `ObjectID` pointeur, qui stocke la chaîne de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="5d38f-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d38f-110">Notes</span><span class="sxs-lookup"><span data-stu-id="5d38f-110">Remarks</span></span>  
 <span data-ttu-id="5d38f-111">Les chaînes peuvent ou ne peuvent pas être nul.</span><span class="sxs-lookup"><span data-stu-id="5d38f-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d38f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5d38f-112">Requirements</span></span>  
 <span data-ttu-id="5d38f-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d38f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d38f-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d38f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d38f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d38f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d38f-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d38f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d38f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d38f-117">See also</span></span>

- [<span data-ttu-id="5d38f-118">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="5d38f-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="5d38f-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="5d38f-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
