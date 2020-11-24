---
title: EnumCustomAttributes, méthode
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
ms.openlocfilehash: 445c833d10631341ef7ad579eaff8ddd96be3428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684848"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="bb6ee-102">EnumCustomAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="bb6ee-102">EnumCustomAttributes Method</span></span>

<span data-ttu-id="bb6ee-103">Récupère des attributs personnalisés au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bb6ee-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb6ee-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb6ee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bb6ee-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="bb6ee-106">Handle de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="bb6ee-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="bb6ee-107">Type des attributs à énumérer.</span><span class="sxs-lookup"><span data-stu-id="bb6ee-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="bb6ee-108">Utilisez `mdTokenNill` pour tous les attributs.</span><span class="sxs-lookup"><span data-stu-id="bb6ee-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="bb6ee-109">Reçoit des jetons d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="bb6ee-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bb6ee-110">Spécifie la taille du `rCustomValues` tableau.</span><span class="sxs-lookup"><span data-stu-id="bb6ee-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="bb6ee-111">Reçoit éventuellement le nombre de valeurs de jeton.</span><span class="sxs-lookup"><span data-stu-id="bb6ee-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb6ee-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bb6ee-112">Return Value</span></span>  

 <span data-ttu-id="bb6ee-113">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="bb6ee-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6ee-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bb6ee-114">Requirements</span></span>  

 <span data-ttu-id="bb6ee-115">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="bb6ee-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6ee-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb6ee-116">See also</span></span>

- [<span data-ttu-id="bb6ee-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="bb6ee-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="bb6ee-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="bb6ee-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="bb6ee-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="bb6ee-119">ALink API</span></span>](index.md)
