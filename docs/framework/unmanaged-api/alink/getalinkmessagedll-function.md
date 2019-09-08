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
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787482"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="eafc6-102">GetALinkMessageDll, fonction</span><span class="sxs-lookup"><span data-stu-id="eafc6-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="eafc6-103">Recherche et charge la DLL du message.</span><span class="sxs-lookup"><span data-stu-id="eafc6-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="eafc6-104">Retourne 0 si la DLL du message est introuvable ou n’a pas pu être chargée.</span><span class="sxs-lookup"><span data-stu-id="eafc6-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="eafc6-105">La DLL du message doit se trouver dans un sous-répertoire dont le nom est un ID de langue ou dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="eafc6-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eafc6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eafc6-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="eafc6-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eafc6-107">Requirements</span></span>  
 <span data-ttu-id="eafc6-108">**En-tête :** ALink. h</span><span class="sxs-lookup"><span data-stu-id="eafc6-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="eafc6-109">**Bibliothèque**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="eafc6-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eafc6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eafc6-110">See also</span></span>

- [<span data-ttu-id="eafc6-111">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="eafc6-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
