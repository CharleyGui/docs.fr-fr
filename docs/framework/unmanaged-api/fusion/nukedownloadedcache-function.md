---
title: NukeDownloadedCache, fonction
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29f492173a7fd22ab497d6e0096798e164fccf26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796306"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="1c8ee-102">NukeDownloadedCache, fonction</span><span class="sxs-lookup"><span data-stu-id="1c8ee-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="1c8ee-103">Supprime le cache de téléchargement common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1c8ee-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c8ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c8ee-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1c8ee-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1c8ee-105">Return Value</span></span>  
 <span data-ttu-id="1c8ee-106">Cette méthode retourne les codes d’erreur COM standard, tels que définis dans WinError. h.</span><span class="sxs-lookup"><span data-stu-id="1c8ee-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c8ee-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1c8ee-107">Remarks</span></span>  
 <span data-ttu-id="1c8ee-108">Le cache de téléchargement CLR est la zone dans laquelle les assemblys avec nom fort téléchargés à partir d’une URL sont stockés pour une éventuelle réutilisation.</span><span class="sxs-lookup"><span data-stu-id="1c8ee-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c8ee-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1c8ee-109">Requirements</span></span>  
 <span data-ttu-id="1c8ee-110">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c8ee-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c8ee-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1c8ee-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1c8ee-112">**Bibliothèque** Fusion. dll et mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="1c8ee-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="1c8ee-113">Utilisez fusion. dll au lieu de Mscorwks. dll pour vous assurer que vous ciblez la version correcte du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c8ee-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="1c8ee-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c8ee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8ee-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c8ee-115">See also</span></span>

- [<span data-ttu-id="1c8ee-116">CreateHistoryReader, fonction</span><span class="sxs-lookup"><span data-stu-id="1c8ee-116">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="1c8ee-117">GetHistoryFileDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="1c8ee-117">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="1c8ee-118">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="1c8ee-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
