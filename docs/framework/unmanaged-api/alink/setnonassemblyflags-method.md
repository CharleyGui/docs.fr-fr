---
title: SetNonAssemblyFlags, méthode
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8a22e958740b69ba0e09bf062bf4d86075c3ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777009"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="1ec21-102">SetNonAssemblyFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="1ec21-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="1ec21-103">Définit des indicateurs qui ne sont pas spécifiques à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1ec21-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ec21-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ec21-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ec21-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="1ec21-106">Indicateurs ALink.</span><span class="sxs-lookup"><span data-stu-id="1ec21-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ec21-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1ec21-107">Return Value</span></span>  
 <span data-ttu-id="1ec21-108">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="1ec21-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ec21-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1ec21-109">Requirements</span></span>  
 <span data-ttu-id="1ec21-110">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="1ec21-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec21-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ec21-111">See also</span></span>

- [<span data-ttu-id="1ec21-112">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="1ec21-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1ec21-113">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="1ec21-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1ec21-114">API ALink</span><span class="sxs-lookup"><span data-stu-id="1ec21-114">ALink API</span></span>](index.md)
