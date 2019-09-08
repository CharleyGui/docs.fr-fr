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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d8827f46a12bd090fa27e71072d833607d34677
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777351"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="ea96a-102">EnumCustomAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="ea96a-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="ea96a-103">Récupère des attributs personnalisés au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ea96a-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea96a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea96a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea96a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea96a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ea96a-106">Handle de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="ea96a-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="ea96a-107">Type des attributs à énumérer.</span><span class="sxs-lookup"><span data-stu-id="ea96a-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="ea96a-108">Utilisez `mdTokenNill` pour tous les attributs.</span><span class="sxs-lookup"><span data-stu-id="ea96a-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="ea96a-109">Reçoit des jetons d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="ea96a-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ea96a-110">Spécifie la `rCustomValues` taille du tableau.</span><span class="sxs-lookup"><span data-stu-id="ea96a-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="ea96a-111">Reçoit éventuellement le nombre de valeurs de jeton.</span><span class="sxs-lookup"><span data-stu-id="ea96a-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea96a-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ea96a-112">Return Value</span></span>  
 <span data-ttu-id="ea96a-113">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="ea96a-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea96a-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ea96a-114">Requirements</span></span>  
 <span data-ttu-id="ea96a-115">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="ea96a-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea96a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea96a-116">See also</span></span>

- [<span data-ttu-id="ea96a-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="ea96a-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ea96a-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="ea96a-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ea96a-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="ea96a-119">ALink API</span></span>](index.md)
