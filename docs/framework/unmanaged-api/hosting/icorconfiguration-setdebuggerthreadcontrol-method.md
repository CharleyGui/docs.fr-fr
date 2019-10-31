---
title: ICorConfiguration::SetDebuggerThreadControl, méthode
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
ms.openlocfilehash: 0f6a369691ab2e4e9fd2e5d9731fb1dc0a42ba11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127795"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="f4527-102">ICorConfiguration::SetDebuggerThreadControl, méthode</span><span class="sxs-lookup"><span data-stu-id="f4527-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="f4527-103">Définit l’interface de rappel que les services de débogage appellera en tant que threads common language runtime (CLR) sont bloqués et débloqués pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="f4527-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4527-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4527-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4527-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f4527-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="f4527-106">dans Pointeur vers un objet [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) qui avertit l’hôte du blocage et du déblocage des threads par les services de débogage.</span><span class="sxs-lookup"><span data-stu-id="f4527-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4527-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="f4527-107">Requirements</span></span>  
 <span data-ttu-id="f4527-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4527-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4527-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f4527-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4527-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f4527-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4527-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4527-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4527-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4527-112">See also</span></span>

- [<span data-ttu-id="f4527-113">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="f4527-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
