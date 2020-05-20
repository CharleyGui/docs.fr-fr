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
ms.openlocfilehash: 8a8c2764398d737192190f91646d45f4edf3a0e4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616476"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="fae66-102">CoUninitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="fae66-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="fae66-103">`CoUninitializeCor` est obsolète.</span><span class="sxs-lookup"><span data-stu-id="fae66-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fae66-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="fae66-105">Notes</span><span class="sxs-lookup"><span data-stu-id="fae66-105">Remarks</span></span>  
 <span data-ttu-id="fae66-106">La common language runtime ne peut pas être déchargée d’un processus.</span><span class="sxs-lookup"><span data-stu-id="fae66-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="fae66-107">Pour supprimer complètement le runtime d’un processus en cours d’exécution, vous devez arrêter ce processus.</span><span class="sxs-lookup"><span data-stu-id="fae66-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae66-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fae66-108">See also</span></span>

- [<span data-ttu-id="fae66-109">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="fae66-109">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
