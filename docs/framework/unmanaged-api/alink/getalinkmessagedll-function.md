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
ms.openlocfilehash: 554bd32ae965b21a88a09577749bbd7975f5ec7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684744"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="15a2d-102">GetALinkMessageDll, fonction</span><span class="sxs-lookup"><span data-stu-id="15a2d-102">GetALinkMessageDll Function</span></span>

<span data-ttu-id="15a2d-103">Recherche et charge la DLL du message.</span><span class="sxs-lookup"><span data-stu-id="15a2d-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="15a2d-104">Retourne 0 si la DLL du message est introuvable ou n’a pas pu être chargée.</span><span class="sxs-lookup"><span data-stu-id="15a2d-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="15a2d-105">La DLL du message doit se trouver dans un sous-répertoire dont le nom est un ID de langue ou dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="15a2d-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a2d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="15a2d-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="15a2d-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="15a2d-107">Requirements</span></span>  

 <span data-ttu-id="15a2d-108">**En-tête :** ALink. h</span><span class="sxs-lookup"><span data-stu-id="15a2d-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="15a2d-109">**Bibliothèque**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="15a2d-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a2d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15a2d-110">See also</span></span>

- [<span data-ttu-id="15a2d-111">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="15a2d-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
