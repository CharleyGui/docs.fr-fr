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
ms.openlocfilehash: 585287f63f57f55e877c94684820833b6d1add60
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616536"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="16662-102">_CorImageUnloading, fonction</span><span class="sxs-lookup"><span data-stu-id="16662-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="16662-103">Notifie le chargeur lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="16662-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="16662-104">Cette fonction n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="16662-104">This function is not implemented.</span></span> <span data-ttu-id="16662-105">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="16662-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16662-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16662-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16662-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="16662-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="16662-108">dans Pointeur vers l’emplacement de départ de l’image à décharger.</span><span class="sxs-lookup"><span data-stu-id="16662-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16662-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="16662-109">Requirements</span></span>  
 <span data-ttu-id="16662-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16662-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16662-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="16662-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16662-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="16662-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16662-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16662-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16662-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16662-114">See also</span></span>

- [<span data-ttu-id="16662-115">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="16662-115">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
