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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05bc472711838236ed18b00ce808d022d9581dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758204"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="b8a1c-102">CoUninitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="b8a1c-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="b8a1c-103">`CoUninitializeEE` est obsolète et n’offre aucune fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="b8a1c-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8a1c-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b8a1c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="b8a1c-105">Remarks</span></span>  
 <span data-ttu-id="b8a1c-106">Le moteur d’exécution du common language runtime ne peut pas être déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="b8a1c-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="b8a1c-107">Pour arrêter le moteur d’exécution, appelez [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="b8a1c-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a1c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8a1c-108">See also</span></span>

- [<span data-ttu-id="b8a1c-109">CoInitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="b8a1c-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="b8a1c-110">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="b8a1c-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
