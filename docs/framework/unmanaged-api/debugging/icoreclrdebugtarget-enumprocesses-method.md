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
ms.openlocfilehash: 7e0219ae0d7d474812865f01e4e2fcfe2e4da991
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679362"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="ef9a9-102">Méthode ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="ef9a9-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>

<span data-ttu-id="ef9a9-103">Énumère les processus en cours d'exécution sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ef9a9-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef9a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef9a9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef9a9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef9a9-105">Parameters</span></span>  

 `pcProcs`  
 <span data-ttu-id="ef9a9-106">[out] Nombre de processus retournés dans `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="ef9a9-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="ef9a9-107">Cette valeur peut être égale à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="ef9a9-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="ef9a9-108">à Tableau de structures [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) qui représentent les processus en cours d’exécution sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ef9a9-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef9a9-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ef9a9-109">Return Value</span></span>  

 <span data-ttu-id="ef9a9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef9a9-110">S_OK</span></span>  
 <span data-ttu-id="ef9a9-111">Réussite.</span><span class="sxs-lookup"><span data-stu-id="ef9a9-111">Success.</span></span>  
  
 <span data-ttu-id="ef9a9-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ef9a9-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ef9a9-113">Impossible d'allouer suffisamment de mémoire pour `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="ef9a9-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="ef9a9-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="ef9a9-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ef9a9-115">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="ef9a9-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef9a9-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="ef9a9-116">Remarks</span></span>  

 <span data-ttu-id="ef9a9-117">Pour libérer la mémoire allouée par cette méthode, appelez la méthode [ICoreClrDebugTarget :: FreeMemory](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ef9a9-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef9a9-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ef9a9-118">Requirements</span></span>  

 <span data-ttu-id="ef9a9-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef9a9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef9a9-120">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="ef9a9-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ef9a9-121">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="ef9a9-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ef9a9-122">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="ef9a9-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9a9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef9a9-123">See also</span></span>

- [<span data-ttu-id="ef9a9-124">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="ef9a9-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
