---
title: ICorConfiguration::AddDebuggerSpecialThread, méthode
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: 8b6593ad995872f0e0014b1e8bcd8a4b576bbeaf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762424"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="0c257-102">ICorConfiguration::AddDebuggerSpecialThread, méthode</span><span class="sxs-lookup"><span data-stu-id="0c257-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="0c257-103">Indique aux services de débogage qu’un thread particulier doit pouvoir continuer à s’exécuter pendant que le débogueur a une application arrêtée pendant des scénarios de débogage managés ou non managés.</span><span class="sxs-lookup"><span data-stu-id="0c257-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c257-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c257-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c257-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0c257-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="0c257-106">dans ID du thread qui doit être autorisé à continuer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c257-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c257-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0c257-107">Remarks</span></span>  
 <span data-ttu-id="0c257-108">Le thread spécifié n’est pas autorisé à exécuter du code managé ou à entrer le runtime de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="0c257-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="0c257-109">Par exemple, un thread de ce type serait un thread in-process pour prendre en charge les débogueurs de script hérités.</span><span class="sxs-lookup"><span data-stu-id="0c257-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c257-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="0c257-110">Requirements</span></span>  
 <span data-ttu-id="0c257-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c257-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c257-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0c257-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c257-113">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0c257-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c257-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c257-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c257-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c257-115">See also</span></span>

- [<span data-ttu-id="0c257-116">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="0c257-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
