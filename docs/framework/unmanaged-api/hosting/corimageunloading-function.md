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
ms.openlocfilehash: 30e3a88140c8a438001e8428df4c5ee879c83376
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136920"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="10630-102">_CorImageUnloading, fonction</span><span class="sxs-lookup"><span data-stu-id="10630-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="10630-103">Notifie le chargeur lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="10630-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="10630-104">Cette fonction n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="10630-104">This function is not implemented.</span></span> <span data-ttu-id="10630-105">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="10630-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10630-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10630-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10630-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="10630-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="10630-108">dans Pointeur vers l’emplacement de départ de l’image à décharger.</span><span class="sxs-lookup"><span data-stu-id="10630-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10630-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="10630-109">Requirements</span></span>  
 <span data-ttu-id="10630-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10630-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10630-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="10630-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10630-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="10630-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="10630-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10630-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10630-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10630-114">See also</span></span>

- [<span data-ttu-id="10630-115">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="10630-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
