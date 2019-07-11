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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b488b6a887b0c66d8c17f8ea78f48f7d2ea31011
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758398"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="e78cb-102">_CorImageUnloading, fonction</span><span class="sxs-lookup"><span data-stu-id="e78cb-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="e78cb-103">Notifie le chargeur lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="e78cb-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="e78cb-104">Cette fonction n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="e78cb-104">This function is not implemented.</span></span> <span data-ttu-id="e78cb-105">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="e78cb-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78cb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e78cb-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e78cb-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e78cb-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="e78cb-108">[in] Pointeur vers l’emplacement de départ de l’image à décharger.</span><span class="sxs-lookup"><span data-stu-id="e78cb-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e78cb-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e78cb-109">Requirements</span></span>  
 <span data-ttu-id="e78cb-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e78cb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e78cb-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e78cb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e78cb-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e78cb-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e78cb-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e78cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78cb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e78cb-114">See also</span></span>

- [<span data-ttu-id="e78cb-115">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="e78cb-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
