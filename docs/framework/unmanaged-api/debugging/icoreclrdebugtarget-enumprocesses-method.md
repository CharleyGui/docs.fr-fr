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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 301e6cc153f905bc5c15e1b526e6fb1a492a76d6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774439"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="66b1c-102">Méthode ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="66b1c-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="66b1c-103">Énumère les processus en cours d'exécution sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="66b1c-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66b1c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66b1c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66b1c-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="66b1c-106">[out] Nombre de processus retournés dans `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="66b1c-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="66b1c-107">Cette valeur peut être égale à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="66b1c-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="66b1c-108">[out] Un tableau de [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures représentant les processus en cours d’exécution sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="66b1c-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66b1c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="66b1c-109">Return Value</span></span>  
 <span data-ttu-id="66b1c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="66b1c-110">S_OK</span></span>  
 <span data-ttu-id="66b1c-111">Opération réussie.</span><span class="sxs-lookup"><span data-stu-id="66b1c-111">Success.</span></span>  
  
 <span data-ttu-id="66b1c-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="66b1c-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="66b1c-113">Impossible d'allouer suffisamment de mémoire pour `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="66b1c-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="66b1c-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="66b1c-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="66b1c-115">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="66b1c-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66b1c-116">Notes</span><span class="sxs-lookup"><span data-stu-id="66b1c-116">Remarks</span></span>  
 <span data-ttu-id="66b1c-117">Pour libérer la mémoire allouée par cette méthode, appelez le [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="66b1c-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66b1c-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66b1c-118">Requirements</span></span>  
 <span data-ttu-id="66b1c-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66b1c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66b1c-120">**En-tête :** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="66b1c-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="66b1c-121">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="66b1c-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="66b1c-122">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="66b1c-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b1c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66b1c-123">See also</span></span>

- [<span data-ttu-id="66b1c-124">ICoreClrDebugTarget, interface</span><span class="sxs-lookup"><span data-stu-id="66b1c-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
