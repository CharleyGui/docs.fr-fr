---
title: CorCheckDuplicatesFor, énumération
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176186"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="f2ad6-102">CorCheckDuplicatesFor, énumération</span><span class="sxs-lookup"><span data-stu-id="f2ad6-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="f2ad6-103">Spécifie les jetons de métadonnées qui seront vérifiés pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ad6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2ad6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="f2ad6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f2ad6-105">Members</span></span>  
  
|<span data-ttu-id="f2ad6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f2ad6-106">Member</span></span>|<span data-ttu-id="f2ad6-107">Description</span><span class="sxs-lookup"><span data-stu-id="f2ad6-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="f2ad6-108">Vérifiez tous les jetons de métadonnées pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="f2ad6-109">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="f2ad6-110">Ne vérifiez pas les jetons de métadonnées pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="f2ad6-111">Vérifiez s’il `mdTypeDef` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="f2ad6-112">Vérifiez s’il `mdInterfaceImpl` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="f2ad6-113">Vérifiez s’il `mdMethodDef` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="f2ad6-114">Vérifiez s’il `mdTypeRef` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="f2ad6-115">Vérifiez s’il `mdMemberRef` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="f2ad6-116">Vérifiez s’il `mdCustomAttribute` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="f2ad6-117">Vérifiez s’il `mdParamDef` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="f2ad6-118">Vérifiez s’il `mdPermission` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="f2ad6-119">Vérifiez s’il `mdProperty` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="f2ad6-120">Vérifiez s’il `mdEvent` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="f2ad6-121">Vérifiez s’il `mdFieldDef` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="f2ad6-122">Vérifiez s’il `mdSignature` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="f2ad6-123">Vérifiez s’il `mdModuleRef` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="f2ad6-124">Vérifiez s’il `mdTypeSpec` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="f2ad6-125">Vérifiez s’il `mdImplMap` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="f2ad6-126">Vérifiez s’il `mdAssemblyRef` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="f2ad6-127">Vérifiez s’il `mdFile` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="f2ad6-128">Vérifiez s’il `mdExportedType` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="f2ad6-129">Vérifiez s’il `mdManifestResource` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="f2ad6-130">Vérifiez s’il `mdGenericParam` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="f2ad6-131">Vérifiez s’il `mdMethodSpec` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="f2ad6-132">Vérifiez s’il `mdGenericParamConstraint` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="f2ad6-133">Vérifiez s’il `mdAssembly` y a des doublons de jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="f2ad6-134">Vérifiez les doublons `mdSignature` `mdTypeSpec`de `mdMemberRef`, `mdTypeRef`, , et `mdMethodSpec` les jetons.</span><span class="sxs-lookup"><span data-stu-id="f2ad6-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2ad6-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f2ad6-135">Requirements</span></span>  
 <span data-ttu-id="f2ad6-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2ad6-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2ad6-137">**En-tête:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f2ad6-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f2ad6-138">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2ad6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ad6-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2ad6-139">See also</span></span>

- [<span data-ttu-id="f2ad6-140">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="f2ad6-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
