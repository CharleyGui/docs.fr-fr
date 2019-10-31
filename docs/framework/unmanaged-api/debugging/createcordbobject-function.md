---
title: Fonction CreateCordbObject
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: d21e0d3d0370ec7c1b223be29099f6b99822463b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132104"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="c2a7d-102">Fonction CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="c2a7d-102">CreateCordbObject Function</span></span>
<span data-ttu-id="c2a7d-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2a7d-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2a7d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c2a7d-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="c2a7d-106">[in] Version de débogage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="c2a7d-107">Ce paramètre doit être CorDebugVersion_2_0 pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="c2a7d-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2a7d-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c2a7d-109">Return Value</span></span>  
 <span data-ttu-id="c2a7d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2a7d-110">S_OK</span></span>  
 <span data-ttu-id="c2a7d-111">Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="c2a7d-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c2a7d-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="c2a7d-113">`ppCordb` est null ou `iDebuggerVersion` n'est pas CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="c2a7d-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c2a7d-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="c2a7d-115">Impossible d'allouer suffisamment de mémoire pour `ppCordb`.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="c2a7d-116">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="c2a7d-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c2a7d-117">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2a7d-118">Notes</span><span class="sxs-lookup"><span data-stu-id="c2a7d-118">Remarks</span></span>  
 <span data-ttu-id="c2a7d-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span><span class="sxs-lookup"><span data-stu-id="c2a7d-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2a7d-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="c2a7d-120">Requirements</span></span>  
 <span data-ttu-id="c2a7d-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2a7d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2a7d-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="c2a7d-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c2a7d-123">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="c2a7d-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c2a7d-124">**.NET Framework Versions:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c2a7d-124">**.NET Framework Versions:** 3.5 SP1</span></span>
