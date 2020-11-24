---
title: CorNotificationForTokenMovement, énumération
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: 0f9cb8db35a1669cead6f9f26c9a89e063628dd8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687669"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="8658c-102">CorNotificationForTokenMovement, énumération</span><span class="sxs-lookup"><span data-stu-id="8658c-102">CorNotificationForTokenMovement Enumeration</span></span>

<span data-ttu-id="8658c-103">Spécifie les notifications qui seront envoyées au client de l’API de métadonnées lorsqu’un remappage de jeton se produit.</span><span class="sxs-lookup"><span data-stu-id="8658c-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8658c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8658c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="8658c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="8658c-105">Members</span></span>  
  
|<span data-ttu-id="8658c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="8658c-106">Member</span></span>|<span data-ttu-id="8658c-107">Description</span><span class="sxs-lookup"><span data-stu-id="8658c-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="8658c-108">Notifier quand les jetons,, `mdTypeRef` `mdMethodDef` `mdMemberRef` ou `mdFieldDef` se déplacent.</span><span class="sxs-lookup"><span data-stu-id="8658c-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="8658c-109">Notifier quand un jeton est déplacé.</span><span class="sxs-lookup"><span data-stu-id="8658c-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="8658c-110">Ne pas avertir quand les jetons sont déplacés.</span><span class="sxs-lookup"><span data-stu-id="8658c-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="8658c-111">Notifier en cas de déplacement d’un `mdMethodDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="8658c-112">Notifier en cas de déplacement d’un `mdMemberRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="8658c-113">Notifier en cas de déplacement d’un `mdFieldDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="8658c-114">Notifier en cas de déplacement d’un `mdTypeRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="8658c-115">Notifier en cas de déplacement d’un `mdTypeDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="8658c-116">Notifier en cas de déplacement d’un `mdParamDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="8658c-117">Notifier en cas de déplacement d’un `mdInterfaceImpl` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="8658c-118">Notifier en cas de déplacement d’un `mdProperty` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="8658c-119">Notifier en cas de déplacement d’un `mdEvent` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="8658c-120">Notifier en cas de déplacement d’un `mdSignature` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="8658c-121">Notifier en cas de déplacement d’un `mdTypeSpec` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="8658c-122">Notifier en cas de déplacement d’un `mdCustomAttribute` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="8658c-123">Notifier en cas de déplacement d’un `mdSecurityValue` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="8658c-124">Notifier en cas de déplacement d’un `mdPermission` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="8658c-125">Notifier en cas de déplacement d’un `mdModuleRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="8658c-126">Notifier en cas de déplacement d’un `mdNameSpace` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="8658c-127">Notifier en cas de déplacement d’un `mdAssemblyRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="8658c-128">Notifier en cas de déplacement d’un `mdFile` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="8658c-129">Notifier en cas de déplacement d’un `mdExportedType` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="8658c-130">Notifier en cas de déplacement d’un `mdManifestResource` jeton.</span><span class="sxs-lookup"><span data-stu-id="8658c-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8658c-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="8658c-131">Remarks</span></span>  

 <span data-ttu-id="8658c-132">Un jeton peut être remappé (c’est-à-dire déplacé) au cours d’une fusion de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8658c-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8658c-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8658c-133">Requirements</span></span>  

 <span data-ttu-id="8658c-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8658c-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8658c-135">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8658c-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8658c-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8658c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8658c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8658c-137">See also</span></span>

- [<span data-ttu-id="8658c-138">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="8658c-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
