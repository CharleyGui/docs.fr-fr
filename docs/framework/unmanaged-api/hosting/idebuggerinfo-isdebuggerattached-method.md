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
ms.openlocfilehash: cbd6fa5f7935a57799d695c3ebb617d856e6dbd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133178"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="ba148-102">IDebuggerInfo::IsDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="ba148-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="ba148-103">Obtient une valeur qui indique si un débogueur managé est attaché à ce processus.</span><span class="sxs-lookup"><span data-stu-id="ba148-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba148-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba148-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba148-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba148-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="ba148-106">à Pointeur vers une valeur `true` si un débogueur managé est attaché au processus ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ba148-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba148-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="ba148-107">Requirements</span></span>  
 <span data-ttu-id="ba148-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba148-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba148-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ba148-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba148-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ba148-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba148-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba148-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba148-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba148-112">See also</span></span>

- [<span data-ttu-id="ba148-113">IDebuggerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="ba148-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
