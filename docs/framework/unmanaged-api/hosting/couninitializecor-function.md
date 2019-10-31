---
title: CoUninitializeCor, fonction
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
ms.openlocfilehash: eddc2f29da0efd9e56df710203b1d7621ffc27a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136867"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="bd834-102">CoUninitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="bd834-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="bd834-103">`CoUninitializeCor` est obsolète.</span><span class="sxs-lookup"><span data-stu-id="bd834-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd834-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd834-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd834-105">Notes</span><span class="sxs-lookup"><span data-stu-id="bd834-105">Remarks</span></span>  
 <span data-ttu-id="bd834-106">La common language runtime ne peut pas être déchargée d’un processus.</span><span class="sxs-lookup"><span data-stu-id="bd834-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="bd834-107">Pour supprimer complètement le runtime d’un processus en cours d’exécution, vous devez arrêter ce processus.</span><span class="sxs-lookup"><span data-stu-id="bd834-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd834-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd834-108">See also</span></span>

- [<span data-ttu-id="bd834-109">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="bd834-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
