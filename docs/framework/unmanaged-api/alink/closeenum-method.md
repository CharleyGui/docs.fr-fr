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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b6c839cc664105149f26b0d21d7ba7fb91b3e29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742197"
---
# <a name="closeenum-method"></a><span data-ttu-id="41ff7-102">CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="41ff7-102">CloseEnum Method</span></span>
<span data-ttu-id="41ff7-103">Ferme l’énumération indiquée et libère les ressources associées.</span><span class="sxs-lookup"><span data-stu-id="41ff7-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ff7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41ff7-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="41ff7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41ff7-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="41ff7-106">Handle d’énumération à fermer.</span><span class="sxs-lookup"><span data-stu-id="41ff7-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41ff7-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="41ff7-107">Return Value</span></span>  
 <span data-ttu-id="41ff7-108">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="41ff7-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41ff7-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41ff7-109">Requirements</span></span>  
 <span data-ttu-id="41ff7-110">Nécessite alink.h</span><span class="sxs-lookup"><span data-stu-id="41ff7-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ff7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41ff7-111">See also</span></span>

- [<span data-ttu-id="41ff7-112">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="41ff7-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="41ff7-113">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="41ff7-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="41ff7-114">API ALink</span><span class="sxs-lookup"><span data-stu-id="41ff7-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
