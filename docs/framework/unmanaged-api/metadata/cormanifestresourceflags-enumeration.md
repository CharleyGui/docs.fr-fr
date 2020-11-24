---
title: CorManifestResourceFlags, énumération
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
ms.openlocfilehash: f8334cb44042e21c086bc05c723e99b0c079fa2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677061"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="c1e69-102">CorManifestResourceFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="c1e69-102">CorManifestResourceFlags Enumeration</span></span>

<span data-ttu-id="c1e69-103">Indique la visibilité des ressources encodées dans un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="c1e69-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1e69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1e69-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c1e69-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c1e69-105">Members</span></span>  
  
|<span data-ttu-id="c1e69-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c1e69-106">Member</span></span>|<span data-ttu-id="c1e69-107">Description</span><span class="sxs-lookup"><span data-stu-id="c1e69-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="c1e69-108">Réservé.</span><span class="sxs-lookup"><span data-stu-id="c1e69-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="c1e69-109">Les ressources sont publiques.</span><span class="sxs-lookup"><span data-stu-id="c1e69-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="c1e69-110">Les ressources sont privées.</span><span class="sxs-lookup"><span data-stu-id="c1e69-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1e69-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1e69-111">Requirements</span></span>  

 <span data-ttu-id="c1e69-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1e69-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1e69-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c1e69-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c1e69-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1e69-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e69-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1e69-115">See also</span></span>

- [<span data-ttu-id="c1e69-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="c1e69-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
