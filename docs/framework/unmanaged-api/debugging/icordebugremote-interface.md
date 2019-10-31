---
title: ICorDebugRemote, interface
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
ms.openlocfilehash: a7eb2796de060b3a5dc8e8c08d07e6aeeb3daecb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131264"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="8acce-102">ICorDebugRemote, interface</span><span class="sxs-lookup"><span data-stu-id="8acce-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="8acce-103">Fournit la possibilité de lancer ou de joindre un débogueur managé à un processus distant cible.</span><span class="sxs-lookup"><span data-stu-id="8acce-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8acce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8acce-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8acce-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8acce-105">Methods</span></span>  
  
|<span data-ttu-id="8acce-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="8acce-106">Method</span></span>|<span data-ttu-id="8acce-107">Description</span><span class="sxs-lookup"><span data-stu-id="8acce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8acce-108">ICorDebugRemote::CreateProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="8acce-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="8acce-109">Crée un processus sur un ordinateur distant pour le débogage managé.</span><span class="sxs-lookup"><span data-stu-id="8acce-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="8acce-110">ICorDebugRemote::DebugActiveProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="8acce-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="8acce-111">Lance un processus sur un ordinateur distant sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="8acce-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8acce-112">Notes</span><span class="sxs-lookup"><span data-stu-id="8acce-112">Remarks</span></span>  
 <span data-ttu-id="8acce-113">Actuellement, cette fonctionnalité est prise en charge uniquement pour le débogage d’une cible d’application Silverlight qui s’exécute sur un ordinateur Macintosh distant.</span><span class="sxs-lookup"><span data-stu-id="8acce-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8acce-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="8acce-114">Requirements</span></span>  
 <span data-ttu-id="8acce-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8acce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8acce-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8acce-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8acce-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8acce-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8acce-118">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="8acce-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8acce-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8acce-119">See also</span></span>

- [<span data-ttu-id="8acce-120">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="8acce-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="8acce-121">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="8acce-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="8acce-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8acce-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
