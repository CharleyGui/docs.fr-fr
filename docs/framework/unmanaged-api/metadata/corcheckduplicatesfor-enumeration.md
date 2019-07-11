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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a82ce9709e008e092c5f31372a89bf9a16e1f88b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767018"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="cf328-102">CorCheckDuplicatesFor, énumération</span><span class="sxs-lookup"><span data-stu-id="cf328-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="cf328-103">Spécifie les jetons de métadonnées qui seront vérifiés pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="cf328-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf328-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf328-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cf328-105">Membres</span><span class="sxs-lookup"><span data-stu-id="cf328-105">Members</span></span>  
  
|<span data-ttu-id="cf328-106">Membre</span><span class="sxs-lookup"><span data-stu-id="cf328-106">Member</span></span>|<span data-ttu-id="cf328-107">Description</span><span class="sxs-lookup"><span data-stu-id="cf328-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="cf328-108">Vérifiez tous les jetons de métadonnées pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="cf328-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="cf328-109">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="cf328-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="cf328-110">Ne pas vérifier les jetons de métadonnées pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="cf328-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="cf328-111">Vérifier les doublons de `mdTypeDef` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="cf328-112">Vérifier les doublons de `mdInterfaceImpl` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="cf328-113">Vérifier les doublons de `mdMethodDef` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="cf328-114">Vérifier les doublons de `mdTypeRef` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="cf328-115">Vérifier les doublons de `mdMemberRef` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="cf328-116">Vérifier les doublons de `mdCustomAttribute` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="cf328-117">Vérifier les doublons de `mdParamDef` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="cf328-118">Vérifier les doublons de `mdPermission` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="cf328-119">Vérifier les doublons de `mdProperty` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="cf328-120">Vérifier les doublons de `mdEvent` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="cf328-121">Vérifier les doublons de `mdFieldDef` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="cf328-122">Vérifier les doublons de `mdSignature` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="cf328-123">Vérifier les doublons de `mdModuleRef` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="cf328-124">Vérifier les doublons de `mdTypeSpec` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="cf328-125">Vérifier les doublons de `mdImplMap` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="cf328-126">Vérifier les doublons de `mdAssemblyRef` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="cf328-127">Vérifier les doublons de `mdFile` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="cf328-128">Vérifier les doublons de `mdExportedType` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="cf328-129">Vérifier les doublons de `mdManifestResource` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="cf328-130">Vérifier les doublons de `mdGenericParam` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="cf328-131">Vérifier les doublons de `mdMethodSpec` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="cf328-132">Vérifier les doublons de `mdGenericParamConstraint` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="cf328-133">Vérifier les doublons de `mdAssembly` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="cf328-134">Vérifier les doublons de `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, et `mdMethodSpec` jetons.</span><span class="sxs-lookup"><span data-stu-id="cf328-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf328-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf328-135">Requirements</span></span>  
 <span data-ttu-id="cf328-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf328-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf328-137">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cf328-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cf328-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf328-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf328-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf328-139">See also</span></span>

- [<span data-ttu-id="cf328-140">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="cf328-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
