---
title: COR_NATIVE_LINK, structure
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 15f573ebc07bcf08a1ab8f5a5bbb88e940c5c8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724167"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="ed818-102">COR_NATIVE_LINK, structure</span><span class="sxs-lookup"><span data-stu-id="ed818-102">COR_NATIVE_LINK Structure</span></span>

<span data-ttu-id="ed818-103">Contient des informations utilisées pour lier du code natif.</span><span class="sxs-lookup"><span data-stu-id="ed818-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed818-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed818-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="ed818-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ed818-105">Members</span></span>  
  
|<span data-ttu-id="ed818-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ed818-106">Member</span></span>|<span data-ttu-id="ed818-107">Description</span><span class="sxs-lookup"><span data-stu-id="ed818-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="ed818-108">Type à lier en code natif.</span><span class="sxs-lookup"><span data-stu-id="ed818-108">The type to be linked in native code.</span></span> <span data-ttu-id="ed818-109">Cette valeur est l’une des valeurs [CorNativeLinkType,](cornativelinktype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ed818-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="ed818-110">Indicateurs utilisés par l’éditeur de liens lors de la liaison de code natif.</span><span class="sxs-lookup"><span data-stu-id="ed818-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="ed818-111">Cette valeur est l’une des valeurs [CorNativeLinkFlags,](cornativelinkflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ed818-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="ed818-112">Jeton de métadonnées MemberRef qui représente le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ed818-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="ed818-113">Le format est `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="ed818-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed818-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ed818-114">Requirements</span></span>  

 <span data-ttu-id="ed818-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed818-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed818-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ed818-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed818-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed818-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed818-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed818-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed818-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed818-119">See also</span></span>

- [<span data-ttu-id="ed818-120">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="ed818-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="ed818-121">CorNativeLinkType, énumération</span><span class="sxs-lookup"><span data-stu-id="ed818-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="ed818-122">CorNativeLinkFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="ed818-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
