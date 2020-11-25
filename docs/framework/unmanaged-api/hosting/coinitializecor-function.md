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
ms.openlocfilehash: 9d077d5c5a414568b5643cad0171e101d7bb06f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731707"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="cc26a-102">CoInitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="cc26a-102">CoInitializeCor Function</span></span>

<span data-ttu-id="cc26a-103">`CoInitializeCor` est obsolète.</span><span class="sxs-lookup"><span data-stu-id="cc26a-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc26a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc26a-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="cc26a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="cc26a-105">Remarks</span></span>  

 <span data-ttu-id="cc26a-106">Pour initialiser le common language runtime, utilisez [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="cc26a-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc26a-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cc26a-107">Requirements</span></span>  

 <span data-ttu-id="cc26a-108">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cc26a-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc26a-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc26a-109">See also</span></span>

- [<span data-ttu-id="cc26a-110">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="cc26a-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
