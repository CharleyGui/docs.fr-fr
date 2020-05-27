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
ms.openlocfilehash: a11b7d5939c4c20504b1ff3dfb4613f85bca0db4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007973"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="96de6-102">COR_NATIVE_LINK, structure</span><span class="sxs-lookup"><span data-stu-id="96de6-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="96de6-103">Contient des informations utilisées pour lier du code natif.</span><span class="sxs-lookup"><span data-stu-id="96de6-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96de6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96de6-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="96de6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="96de6-105">Members</span></span>  
  
|<span data-ttu-id="96de6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="96de6-106">Member</span></span>|<span data-ttu-id="96de6-107">Description</span><span class="sxs-lookup"><span data-stu-id="96de6-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="96de6-108">Type à lier en code natif.</span><span class="sxs-lookup"><span data-stu-id="96de6-108">The type to be linked in native code.</span></span> <span data-ttu-id="96de6-109">Cette valeur est l’une des valeurs [CorNativeLinkType,](cornativelinktype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="96de6-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="96de6-110">Indicateurs utilisés par l’éditeur de liens lors de la liaison de code natif.</span><span class="sxs-lookup"><span data-stu-id="96de6-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="96de6-111">Cette valeur est l’une des valeurs [CorNativeLinkFlags,](cornativelinkflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="96de6-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="96de6-112">Jeton de métadonnées MemberRef qui représente le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="96de6-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="96de6-113">Le format est `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="96de6-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96de6-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="96de6-114">Requirements</span></span>  
 <span data-ttu-id="96de6-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96de6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96de6-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="96de6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96de6-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="96de6-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96de6-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96de6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96de6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96de6-119">See also</span></span>

- [<span data-ttu-id="96de6-120">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="96de6-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="96de6-121">CorNativeLinkType, énumération</span><span class="sxs-lookup"><span data-stu-id="96de6-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="96de6-122">CorNativeLinkFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="96de6-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
