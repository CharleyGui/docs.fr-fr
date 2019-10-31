---
title: CoInitializeCor, fonction
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: e8d65e739504e01a7d11b37d1b34d7313b13a5e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138337"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="5ed45-102">CoInitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="5ed45-102">CoInitializeCor Function</span></span>
<span data-ttu-id="5ed45-103">`CoInitializeCor` est obsolète.</span><span class="sxs-lookup"><span data-stu-id="5ed45-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ed45-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="5ed45-105">Notes</span><span class="sxs-lookup"><span data-stu-id="5ed45-105">Remarks</span></span>  
 <span data-ttu-id="5ed45-106">Pour initialiser le common language runtime, utilisez [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="5ed45-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed45-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="5ed45-107">Requirements</span></span>  
 <span data-ttu-id="5ed45-108">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5ed45-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed45-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ed45-109">See also</span></span>

- [<span data-ttu-id="5ed45-110">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="5ed45-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
