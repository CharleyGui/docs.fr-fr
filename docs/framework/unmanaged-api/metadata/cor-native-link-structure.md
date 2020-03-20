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
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177957"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="b821b-102">COR_NATIVE_LINK, structure</span><span class="sxs-lookup"><span data-stu-id="b821b-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="b821b-103">Contient des informations utilisées pour lier du code natif.</span><span class="sxs-lookup"><span data-stu-id="b821b-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b821b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b821b-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="b821b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b821b-105">Members</span></span>  
  
|<span data-ttu-id="b821b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b821b-106">Member</span></span>|<span data-ttu-id="b821b-107">Description</span><span class="sxs-lookup"><span data-stu-id="b821b-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="b821b-108">Le type à être lié dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="b821b-108">The type to be linked in native code.</span></span> <span data-ttu-id="b821b-109">Cette valeur est l’une des valeurs [de CorNativeLinkType.](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="b821b-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="b821b-110">Drapeaux utilisés par le lien lors de la liaison du code indigène.</span><span class="sxs-lookup"><span data-stu-id="b821b-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="b821b-111">Cette valeur est l’une des valeurs [corNativeLinkFlags.](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="b821b-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="b821b-112">Le jeton de métadonnées MemberRef qui représente le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b821b-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="b821b-113">Le format est `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="b821b-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b821b-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b821b-114">Requirements</span></span>  
 <span data-ttu-id="b821b-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b821b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b821b-116">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="b821b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b821b-117">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b821b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b821b-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b821b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b821b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b821b-119">See also</span></span>

- [<span data-ttu-id="b821b-120">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="b821b-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="b821b-121">CorNativeLinkType, énumération</span><span class="sxs-lookup"><span data-stu-id="b821b-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="b821b-122">CorNativeLinkFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="b821b-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
