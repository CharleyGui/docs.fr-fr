---
title: _CorImageUnloading, fonction
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
ms.openlocfilehash: 4932e1fd6294f4a01264e982835dd0707324082a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178234"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="716aa-102">_CorImageUnloading, fonction</span><span class="sxs-lookup"><span data-stu-id="716aa-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="716aa-103">Informe la chargeuse lorsque les images du module géré sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="716aa-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="716aa-104">Cette fonction n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="716aa-104">This function is not implemented.</span></span> <span data-ttu-id="716aa-105">S’il est appelé, il revient E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="716aa-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="716aa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="716aa-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="716aa-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="716aa-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="716aa-108">[dans] Un pointeur à l’emplacement de départ de l’image à décharger.</span><span class="sxs-lookup"><span data-stu-id="716aa-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="716aa-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="716aa-109">Requirements</span></span>  
 <span data-ttu-id="716aa-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="716aa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="716aa-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="716aa-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="716aa-112">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="716aa-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="716aa-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="716aa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716aa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="716aa-114">See also</span></span>

- [<span data-ttu-id="716aa-115">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="716aa-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
