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
ms.openlocfilehash: 0cc79c0a93fa4f05b8c793a8b7fb0b9b3f031b1a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791953"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="a5b34-102">ICorDebugRemote, interface</span><span class="sxs-lookup"><span data-stu-id="a5b34-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="a5b34-103">Fournit la possibilité de lancer ou de joindre un débogueur managé à un processus distant cible.</span><span class="sxs-lookup"><span data-stu-id="a5b34-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5b34-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a5b34-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a5b34-105">Methods</span></span>  
  
|<span data-ttu-id="a5b34-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="a5b34-106">Method</span></span>|<span data-ttu-id="a5b34-107">Description</span><span class="sxs-lookup"><span data-stu-id="a5b34-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5b34-108">ICorDebugRemote::CreateProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="a5b34-108">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="a5b34-109">Crée un processus sur un ordinateur distant pour le débogage managé.</span><span class="sxs-lookup"><span data-stu-id="a5b34-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="a5b34-110">ICorDebugRemote::DebugActiveProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="a5b34-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="a5b34-111">Lance un processus sur un ordinateur distant sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a5b34-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5b34-112">Notes</span><span class="sxs-lookup"><span data-stu-id="a5b34-112">Remarks</span></span>  
 <span data-ttu-id="a5b34-113">Actuellement, cette fonctionnalité est prise en charge uniquement pour le débogage d’une cible d’application Silverlight qui s’exécute sur un ordinateur Macintosh distant.</span><span class="sxs-lookup"><span data-stu-id="a5b34-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b34-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a5b34-114">Requirements</span></span>  
 <span data-ttu-id="a5b34-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5b34-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b34-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5b34-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5b34-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5b34-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5b34-118">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a5b34-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b34-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5b34-119">See also</span></span>

- [<span data-ttu-id="a5b34-120">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="a5b34-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="a5b34-121">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="a5b34-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="a5b34-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a5b34-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
