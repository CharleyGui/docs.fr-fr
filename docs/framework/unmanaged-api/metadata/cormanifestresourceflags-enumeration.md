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
ms.openlocfilehash: ebdff88e9fdf499b809d56c4c29a906dbef9ec40
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008974"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="12118-102">CorManifestResourceFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="12118-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="12118-103">Indique la visibilité des ressources encodées dans un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="12118-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12118-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12118-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="12118-105">Membres</span><span class="sxs-lookup"><span data-stu-id="12118-105">Members</span></span>  
  
|<span data-ttu-id="12118-106">Membre</span><span class="sxs-lookup"><span data-stu-id="12118-106">Member</span></span>|<span data-ttu-id="12118-107">Description</span><span class="sxs-lookup"><span data-stu-id="12118-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="12118-108">Réservé.</span><span class="sxs-lookup"><span data-stu-id="12118-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="12118-109">Les ressources sont publiques.</span><span class="sxs-lookup"><span data-stu-id="12118-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="12118-110">Les ressources sont privées.</span><span class="sxs-lookup"><span data-stu-id="12118-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12118-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="12118-111">Requirements</span></span>  
 <span data-ttu-id="12118-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12118-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12118-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="12118-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="12118-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12118-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12118-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12118-115">See also</span></span>

- [<span data-ttu-id="12118-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="12118-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
