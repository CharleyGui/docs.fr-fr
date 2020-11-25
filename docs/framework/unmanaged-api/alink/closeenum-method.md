---
title: CloseEnum, méthode
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
ms.openlocfilehash: 59b1ec3f9ca382ef13680e3aad4d0c0c0e175f1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716965"
---
# <a name="closeenum-method"></a><span data-ttu-id="79321-102">CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="79321-102">CloseEnum Method</span></span>

<span data-ttu-id="79321-103">Ferme l’énumération indiquée et libère les ressources associées.</span><span class="sxs-lookup"><span data-stu-id="79321-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79321-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79321-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="79321-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79321-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="79321-106">Handle d’énumération à fermer.</span><span class="sxs-lookup"><span data-stu-id="79321-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79321-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="79321-107">Return Value</span></span>  

 <span data-ttu-id="79321-108">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="79321-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79321-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="79321-109">Requirements</span></span>  

 <span data-ttu-id="79321-110">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="79321-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79321-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79321-111">See also</span></span>

- [<span data-ttu-id="79321-112">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="79321-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="79321-113">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="79321-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="79321-114">API ALink</span><span class="sxs-lookup"><span data-stu-id="79321-114">ALink API</span></span>](index.md)
