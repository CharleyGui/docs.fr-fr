---
title: ICorDebugRemoteTarget, interface
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
ms.openlocfilehash: 4883c208468db0096bed3ff8cf4a8ed50a5d7cc6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379227"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="3feeb-102">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="3feeb-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="3feeb-103">Fournit des méthodes qui permettent aux développeurs de déboguer des applications Silverlight dans l’environnement common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3feeb-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3feeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3feeb-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3feeb-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3feeb-105">Methods</span></span>  
  
|<span data-ttu-id="3feeb-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="3feeb-106">Method</span></span>|<span data-ttu-id="3feeb-107">Description</span><span class="sxs-lookup"><span data-stu-id="3feeb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3feeb-108">ICorDebugRemoteTarget::GetHostName, méthode</span><span class="sxs-lookup"><span data-stu-id="3feeb-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="3feeb-109">Retourne le nom d’hôte ou l’adresse IP d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="3feeb-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3feeb-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="3feeb-110">Remarks</span></span>  
 <span data-ttu-id="3feeb-111">Le débogage en mode mixte (autrement dit, le code managé et le code natif) n’est pas pris en charge sur Windows 95, Windows 98 ou Windows ME, ni sur les plateformes autres que x86 (comme IA-64 et AMD64).</span><span class="sxs-lookup"><span data-stu-id="3feeb-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3feeb-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3feeb-112">Requirements</span></span>  
 <span data-ttu-id="3feeb-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3feeb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3feeb-114">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="3feeb-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="3feeb-115">**Bibliothèque :** : CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3feeb-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="3feeb-116">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="3feeb-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3feeb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3feeb-117">See also</span></span>

- [<span data-ttu-id="3feeb-118">ICorDebugRemote, interface</span><span class="sxs-lookup"><span data-stu-id="3feeb-118">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="3feeb-119">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="3feeb-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="3feeb-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3feeb-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
