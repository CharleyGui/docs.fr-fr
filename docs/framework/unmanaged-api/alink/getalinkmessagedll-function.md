---
title: GetALinkMessageDll, fonction
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 41e79a4c9587e3e738039cbf6a84087a2e7fc9b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741956"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="96652-102">GetALinkMessageDll, fonction</span><span class="sxs-lookup"><span data-stu-id="96652-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="96652-103">Recherche et charge la DLL de message.</span><span class="sxs-lookup"><span data-stu-id="96652-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="96652-104">Retourne 0 si Impossible de trouver ou de charger la DLL de message.</span><span class="sxs-lookup"><span data-stu-id="96652-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="96652-105">La DLL de message doit être dans un sous-répertoire dont le nom est un ID de langue, ou dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="96652-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96652-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96652-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="96652-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="96652-107">Requirements</span></span>  
 <span data-ttu-id="96652-108">**En-tête :** alink.h</span><span class="sxs-lookup"><span data-stu-id="96652-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="96652-109">**Bibliothèque**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="96652-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96652-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96652-110">See also</span></span>

- [<span data-ttu-id="96652-111">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="96652-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
