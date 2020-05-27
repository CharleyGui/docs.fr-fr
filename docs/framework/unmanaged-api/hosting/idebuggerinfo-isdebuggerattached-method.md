---
title: IDebuggerInfo::IsDebuggerAttached, méthode
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
ms.openlocfilehash: 95b7a2f6d35104c3353853549dacc783355feb5b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805335"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="01fca-102">IDebuggerInfo::IsDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="01fca-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="01fca-103">Obtient une valeur qui indique si un débogueur managé est attaché à ce processus.</span><span class="sxs-lookup"><span data-stu-id="01fca-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01fca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01fca-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01fca-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01fca-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="01fca-106">à Pointeur vers une valeur qui est `true` si un débogueur managé est attaché au processus ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="01fca-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01fca-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="01fca-107">Requirements</span></span>  
 <span data-ttu-id="01fca-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01fca-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01fca-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01fca-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01fca-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01fca-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01fca-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01fca-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01fca-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01fca-112">See also</span></span>

- [<span data-ttu-id="01fca-113">IDebuggerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="01fca-113">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)
