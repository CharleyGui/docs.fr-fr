---
title: ICorDebugProcess::ReadMemory, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: ef9e339c74b2d2785d758ed9c4adfc1901073253
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139361"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="afbce-102">ICorDebugProcess::ReadMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="afbce-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="afbce-103">Reads a specified area of memory for this process.</span><span class="sxs-lookup"><span data-stu-id="afbce-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afbce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afbce-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afbce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="afbce-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="afbce-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span><span class="sxs-lookup"><span data-stu-id="afbce-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="afbce-107">[in] The number of bytes to be read from memory.</span><span class="sxs-lookup"><span data-stu-id="afbce-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="afbce-108">[out] A buffer that receives the contents of the memory.</span><span class="sxs-lookup"><span data-stu-id="afbce-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="afbce-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span><span class="sxs-lookup"><span data-stu-id="afbce-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afbce-110">Notes</span><span class="sxs-lookup"><span data-stu-id="afbce-110">Remarks</span></span>  
 <span data-ttu-id="afbce-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span><span class="sxs-lookup"><span data-stu-id="afbce-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="afbce-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span><span class="sxs-lookup"><span data-stu-id="afbce-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="afbce-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span><span class="sxs-lookup"><span data-stu-id="afbce-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="afbce-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="afbce-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="afbce-115">No caching of process memory is performed.</span><span class="sxs-lookup"><span data-stu-id="afbce-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afbce-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="afbce-116">Requirements</span></span>  
 <span data-ttu-id="afbce-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afbce-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afbce-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afbce-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afbce-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afbce-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afbce-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afbce-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
