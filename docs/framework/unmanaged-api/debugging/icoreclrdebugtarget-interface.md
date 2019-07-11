---
title: Interface ICorDebugDataTarget
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5a3d06f72ed7163a414ef12e9bec650d8b20783
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774283"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="b9f45-102">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="b9f45-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="b9f45-103">Fournit des méthodes qui contrôlent les nombres de références, énumérer des processus et libèrent la mémoire associée à un débogueur est attaché à une cible distante Macintosh Silverlight.</span><span class="sxs-lookup"><span data-stu-id="b9f45-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9f45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9f45-104">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b9f45-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b9f45-105">Methods</span></span>  
  
|<span data-ttu-id="b9f45-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="b9f45-106">Method</span></span>|<span data-ttu-id="b9f45-107">Description</span><span class="sxs-lookup"><span data-stu-id="b9f45-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9f45-108">ICoreClrDebugTarget::EnumProcesses, méthode</span><span class="sxs-lookup"><span data-stu-id="b9f45-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="b9f45-109">Énumère les processus en cours d'exécution sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b9f45-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="b9f45-110">ICoreClrDebugTarget::EnumRuntimes, méthode</span><span class="sxs-lookup"><span data-stu-id="b9f45-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="b9f45-111">Énumère le common language runtime (CLR) dans le processus spécifié sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b9f45-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="b9f45-112">ICoreClrDebugTarget::FreeMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="b9f45-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="b9f45-113">Libère la mémoire est allouée par les méthodes d’énumération dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="b9f45-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9f45-114">Notes</span><span class="sxs-lookup"><span data-stu-id="b9f45-114">Remarks</span></span>  
 <span data-ttu-id="b9f45-115">Actuellement, cette fonctionnalité est prise en charge uniquement pour le débogage d’une cible de l’application basée sur Silverlight qui s’exécute sur un ordinateur Macintosh distant.</span><span class="sxs-lookup"><span data-stu-id="b9f45-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9f45-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9f45-116">Requirements</span></span>  
 <span data-ttu-id="b9f45-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9f45-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9f45-118">**En-tête :** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b9f45-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b9f45-119">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b9f45-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b9f45-120">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b9f45-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f45-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9f45-121">See also</span></span>

- [<span data-ttu-id="b9f45-122">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="b9f45-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="b9f45-123">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="b9f45-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="b9f45-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b9f45-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
