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
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450147"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="14b02-102">CorNotificationForTokenMovement, énumération</span><span class="sxs-lookup"><span data-stu-id="14b02-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="14b02-103">Spécifie les notifications qui seront envoyées au client de l’API de métadonnées lorsqu’un remappage de jeton se produit.</span><span class="sxs-lookup"><span data-stu-id="14b02-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14b02-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="14b02-105">Membres</span><span class="sxs-lookup"><span data-stu-id="14b02-105">Members</span></span>  
  
|<span data-ttu-id="14b02-106">Membre</span><span class="sxs-lookup"><span data-stu-id="14b02-106">Member</span></span>|<span data-ttu-id="14b02-107">Description</span><span class="sxs-lookup"><span data-stu-id="14b02-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="14b02-108">Notifier quand des jetons `mdTypeRef`, `mdMethodDef`, `mdMemberRef`ou `mdFieldDef` se déplacent.</span><span class="sxs-lookup"><span data-stu-id="14b02-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="14b02-109">Notifier quand un jeton est déplacé.</span><span class="sxs-lookup"><span data-stu-id="14b02-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="14b02-110">Ne pas avertir quand les jetons sont déplacés.</span><span class="sxs-lookup"><span data-stu-id="14b02-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="14b02-111">Notifier lorsqu’un jeton `mdMethodDef` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="14b02-112">Notifier lorsqu’un jeton `mdMemberRef` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="14b02-113">Notifier lorsqu’un jeton `mdFieldDef` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="14b02-114">Notifier lorsqu’un jeton `mdTypeRef` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="14b02-115">Notifier lorsqu’un jeton `mdTypeDef` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="14b02-116">Notifier lorsqu’un jeton `mdParamDef` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="14b02-117">Notifier lorsqu’un jeton `mdInterfaceImpl` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="14b02-118">Notifier lorsqu’un jeton `mdProperty` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="14b02-119">Notifier lorsqu’un jeton `mdEvent` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="14b02-120">Notifier lorsqu’un jeton `mdSignature` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="14b02-121">Notifier lorsqu’un jeton `mdTypeSpec` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="14b02-122">Notifier lorsqu’un jeton `mdCustomAttribute` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="14b02-123">Notifier lorsqu’un jeton `mdSecurityValue` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="14b02-124">Notifier lorsqu’un jeton `mdPermission` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="14b02-125">Notifier lorsqu’un jeton `mdModuleRef` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="14b02-126">Notifier lorsqu’un jeton `mdNameSpace` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="14b02-127">Notifier lorsqu’un jeton `mdAssemblyRef` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="14b02-128">Notifier lorsqu’un jeton `mdFile` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="14b02-129">Notifier lorsqu’un jeton `mdExportedType` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="14b02-130">Notifier lorsqu’un jeton `mdManifestResource` se déplace.</span><span class="sxs-lookup"><span data-stu-id="14b02-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14b02-131">Notes</span><span class="sxs-lookup"><span data-stu-id="14b02-131">Remarks</span></span>  
 <span data-ttu-id="14b02-132">Un jeton peut être remappé (c’est-à-dire déplacé) au cours d’une fusion de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="14b02-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14b02-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="14b02-133">Requirements</span></span>  
 <span data-ttu-id="14b02-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14b02-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14b02-135">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="14b02-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="14b02-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14b02-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b02-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14b02-137">See also</span></span>

- [<span data-ttu-id="14b02-138">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="14b02-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
