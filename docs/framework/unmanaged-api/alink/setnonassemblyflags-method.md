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
ms.openlocfilehash: b7bcf530947c161decc9c01c07df310550d69738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733761"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="43812-102">SetNonAssemblyFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="43812-102">SetNonAssemblyFlags Method</span></span>

<span data-ttu-id="43812-103">Définit des indicateurs qui ne sont pas spécifiques à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="43812-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43812-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43812-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="43812-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="43812-105">Parameters</span></span>  

 `afFlags`  
 <span data-ttu-id="43812-106">Indicateurs ALink.</span><span class="sxs-lookup"><span data-stu-id="43812-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43812-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="43812-107">Return Value</span></span>  

 <span data-ttu-id="43812-108">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="43812-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43812-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="43812-109">Requirements</span></span>  

 <span data-ttu-id="43812-110">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="43812-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43812-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43812-111">See also</span></span>

- [<span data-ttu-id="43812-112">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="43812-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="43812-113">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="43812-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="43812-114">API ALink</span><span class="sxs-lookup"><span data-stu-id="43812-114">ALink API</span></span>](index.md)
