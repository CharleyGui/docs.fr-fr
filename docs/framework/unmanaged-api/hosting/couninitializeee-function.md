---
title: CoUninitializeEE, fonction
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: 3531cfc0815c3f8a9479e35b2df60b2825801b39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136852"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="041d9-102">CoUninitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="041d9-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="041d9-103">`CoUninitializeEE` est obsolète et ne fournit aucune fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="041d9-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="041d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="041d9-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="041d9-105">Notes</span><span class="sxs-lookup"><span data-stu-id="041d9-105">Remarks</span></span>  
 <span data-ttu-id="041d9-106">Le moteur d’exécution de common language runtime ne peut pas être déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="041d9-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="041d9-107">Pour arrêter l’appel du moteur d’exécution [CorExitProcess,](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="041d9-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="041d9-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="041d9-108">See also</span></span>

- [<span data-ttu-id="041d9-109">CoInitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="041d9-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="041d9-110">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="041d9-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
