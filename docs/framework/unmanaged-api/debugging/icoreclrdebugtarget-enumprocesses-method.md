---
title: Méthode ICoreClrDebugTarget::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 4d1404e3f7565ee26edd94e059b7f01f8edd4dd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121842"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="efa5f-102">Méthode ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="efa5f-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="efa5f-103">Énumère les processus en cours d'exécution sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="efa5f-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efa5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efa5f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efa5f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="efa5f-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="efa5f-106">[out] Nombre de processus retournés dans `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="efa5f-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="efa5f-107">Cette valeur peut être égale à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="efa5f-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="efa5f-108">à Tableau de structures [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) qui représentent les processus en cours d’exécution sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="efa5f-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efa5f-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="efa5f-109">Return Value</span></span>  
 <span data-ttu-id="efa5f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="efa5f-110">S_OK</span></span>  
 <span data-ttu-id="efa5f-111">Opération réussie.</span><span class="sxs-lookup"><span data-stu-id="efa5f-111">Success.</span></span>  
  
 <span data-ttu-id="efa5f-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="efa5f-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="efa5f-113">Impossible d'allouer suffisamment de mémoire pour `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="efa5f-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="efa5f-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="efa5f-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="efa5f-115">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="efa5f-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efa5f-116">Notes</span><span class="sxs-lookup"><span data-stu-id="efa5f-116">Remarks</span></span>  
 <span data-ttu-id="efa5f-117">Pour libérer la mémoire allouée par cette méthode, appelez la méthode [ICoreClrDebugTarget :: FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="efa5f-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efa5f-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="efa5f-118">Requirements</span></span>  
 <span data-ttu-id="efa5f-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efa5f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efa5f-120">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="efa5f-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="efa5f-121">**Bibliothèque :** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="efa5f-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="efa5f-122">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="efa5f-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa5f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efa5f-123">See also</span></span>

- [<span data-ttu-id="efa5f-124">ICoreClrDebugTarget, interface</span><span class="sxs-lookup"><span data-stu-id="efa5f-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
