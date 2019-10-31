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
ms.openlocfilehash: 8f97614412eb2d49b202e86bdabc727159deb5d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131696"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="9972b-102">NukeDownloadedCache, fonction</span><span class="sxs-lookup"><span data-stu-id="9972b-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="9972b-103">Supprime le cache de téléchargement common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9972b-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9972b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9972b-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9972b-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9972b-105">Return Value</span></span>  
 <span data-ttu-id="9972b-106">Cette méthode retourne les codes d’erreur COM standard, tels que définis dans WinError. h.</span><span class="sxs-lookup"><span data-stu-id="9972b-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9972b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9972b-107">Remarks</span></span>  
 <span data-ttu-id="9972b-108">Le cache de téléchargement CLR est la zone dans laquelle les assemblys avec nom fort téléchargés à partir d’une URL sont stockés pour une éventuelle réutilisation.</span><span class="sxs-lookup"><span data-stu-id="9972b-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9972b-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="9972b-109">Requirements</span></span>  
 <span data-ttu-id="9972b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9972b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9972b-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9972b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9972b-112">**Bibliothèque :** Fusion. dll et mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="9972b-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="9972b-113">Utilisez fusion. dll au lieu de Mscorwks. dll pour vous assurer que vous ciblez la version correcte du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9972b-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="9972b-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9972b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9972b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9972b-115">See also</span></span>

- [<span data-ttu-id="9972b-116">CreateHistoryReader, fonction</span><span class="sxs-lookup"><span data-stu-id="9972b-116">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="9972b-117">GetHistoryFileDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="9972b-117">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="9972b-118">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="9972b-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
