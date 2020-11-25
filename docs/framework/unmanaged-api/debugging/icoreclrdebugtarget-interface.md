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
ms.openlocfilehash: 791bd2754a96b97a38e2509c0c61a644324857cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716952"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="1d3bc-102">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="1d3bc-102">ICoreClrDebugTarget Interface</span></span>

<span data-ttu-id="1d3bc-103">Fournit des méthodes qui contrôlent les décomptes de références, énumèrent les processus et libèrent la mémoire associée à un débogueur attaché à une cible Silverlight Macintosh à distance.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d3bc-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1d3bc-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1d3bc-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1d3bc-105">Methods</span></span>  
  
|<span data-ttu-id="1d3bc-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="1d3bc-106">Method</span></span>|<span data-ttu-id="1d3bc-107">Description</span><span class="sxs-lookup"><span data-stu-id="1d3bc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d3bc-108">Méthode ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="1d3bc-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="1d3bc-109">Énumère les processus en cours d'exécution sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="1d3bc-110">Méthode ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="1d3bc-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="1d3bc-111">Énumère les CLR (Common Language Runtime) dans le processus spécifié sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="1d3bc-112">Méthode ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="1d3bc-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="1d3bc-113">Libère la mémoire allouée par les méthodes d’énumération de cette classe.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d3bc-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d3bc-114">Remarks</span></span>  

 <span data-ttu-id="1d3bc-115">Actuellement, cette fonctionnalité est prise en charge uniquement pour le débogage d’une cible d’application Silverlight qui s’exécute sur un ordinateur Macintosh distant.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d3bc-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1d3bc-116">Requirements</span></span>  

 <span data-ttu-id="1d3bc-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d3bc-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d3bc-118">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="1d3bc-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="1d3bc-119">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="1d3bc-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="1d3bc-120">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="1d3bc-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d3bc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d3bc-121">See also</span></span>

- [<span data-ttu-id="1d3bc-122">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="1d3bc-122">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="1d3bc-123">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="1d3bc-123">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="1d3bc-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1d3bc-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
