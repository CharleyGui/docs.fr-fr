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
ms.openlocfilehash: d03c22c455f0e44ce32d4593d9eee50ceef94a22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443949"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="5144d-102">COR_NATIVE_LINK, structure</span><span class="sxs-lookup"><span data-stu-id="5144d-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="5144d-103">Contient des informations utilisées pour lier du code natif.</span><span class="sxs-lookup"><span data-stu-id="5144d-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5144d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5144d-104">Syntax</span></span>  
  
```cpp  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="5144d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5144d-105">Members</span></span>  
  
|<span data-ttu-id="5144d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5144d-106">Member</span></span>|<span data-ttu-id="5144d-107">Description</span><span class="sxs-lookup"><span data-stu-id="5144d-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="5144d-108">Type à lier en code natif.</span><span class="sxs-lookup"><span data-stu-id="5144d-108">The type to be linked in native code.</span></span> <span data-ttu-id="5144d-109">Cette valeur est l’une des valeurs [CorNativeLinkType,](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="5144d-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="5144d-110">Indicateurs utilisés par l’éditeur de liens lors de la liaison de code natif.</span><span class="sxs-lookup"><span data-stu-id="5144d-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="5144d-111">Cette valeur est l’une des valeurs [CorNativeLinkFlags,](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="5144d-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="5144d-112">Jeton de métadonnées MemberRef qui représente le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5144d-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="5144d-113">Le format est `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="5144d-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5144d-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5144d-114">Requirements</span></span>  
 <span data-ttu-id="5144d-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5144d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5144d-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5144d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5144d-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5144d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5144d-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5144d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5144d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5144d-119">See also</span></span>

- [<span data-ttu-id="5144d-120">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="5144d-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="5144d-121">CorNativeLinkType, énumération</span><span class="sxs-lookup"><span data-stu-id="5144d-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="5144d-122">CorNativeLinkFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="5144d-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
