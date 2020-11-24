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
ms.openlocfilehash: e6616392eaa23f8ba40247c5aabd12e4d530cea1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687845"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="e0bb2-102">CoUninitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="e0bb2-102">CoUninitializeEE Function</span></span>

<span data-ttu-id="e0bb2-103">`CoUninitializeEE` est obsolète et ne fournit aucune fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e0bb2-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0bb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0bb2-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0bb2-105">Notes</span><span class="sxs-lookup"><span data-stu-id="e0bb2-105">Remarks</span></span>  

 <span data-ttu-id="e0bb2-106">Le moteur d’exécution de common language runtime ne peut pas être déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="e0bb2-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="e0bb2-107">Pour arrêter l’appel du moteur d’exécution [CorExitProcess,](corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="e0bb2-107">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bb2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0bb2-108">See also</span></span>

- [<span data-ttu-id="e0bb2-109">CoInitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="e0bb2-109">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="e0bb2-110">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="e0bb2-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
