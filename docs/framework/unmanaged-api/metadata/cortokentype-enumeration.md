---
title: CorTokenType, énumération
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 629e18b6cd2fd7910804ecc608a45d2406dddea1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007492"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="c400d-102">CorTokenType, énumération</span><span class="sxs-lookup"><span data-stu-id="c400d-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="c400d-103">Indique le type d’un jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c400d-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c400d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c400d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="c400d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c400d-105">Members</span></span>  
  
|<span data-ttu-id="c400d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c400d-106">Member</span></span>|<span data-ttu-id="c400d-107">Description</span><span class="sxs-lookup"><span data-stu-id="c400d-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="c400d-108">`mdModule`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="c400d-109">`mdTypeRef`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="c400d-110">`mdTypeDef`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="c400d-111">`mdFieldDef`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="c400d-112">`mdMethodDef`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="c400d-113">`mdParamDef`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="c400d-114">`mdInterfaceImpl`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="c400d-115">`mdMemberRef`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="c400d-116">`mdCustomAttribute`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="c400d-117">`mdPermission`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="c400d-118">`mdSignature`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="c400d-119">`mdEvent`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="c400d-120">`mdProperty`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="c400d-121">`mdModuleRef`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="c400d-122">`mdTypeSpec`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="c400d-123">`mdAssembly`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="c400d-124">`mdAssemblyRef`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="c400d-125">`mdFile`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="c400d-126">`mdExportedType`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="c400d-127">`mdManifestResource`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="c400d-128">`mdGenericParam`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="c400d-129">`mdMethodSpec`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="c400d-130">`mdGenericParamConstraint`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="c400d-131">`mdString`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="c400d-132">`mdName`Jeton.</span><span class="sxs-lookup"><span data-stu-id="c400d-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="c400d-133">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="c400d-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c400d-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="c400d-134">Remarks</span></span>  
 <span data-ttu-id="c400d-135">Chaque valeur est égale à la valeur de l’octet de poids le plus élevé dans le jeton de métadonnées correspondant.</span><span class="sxs-lookup"><span data-stu-id="c400d-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c400d-136">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c400d-136">Requirements</span></span>  
 <span data-ttu-id="c400d-137">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c400d-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c400d-138">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c400d-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c400d-139">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c400d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c400d-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c400d-140">See also</span></span>

- [<span data-ttu-id="c400d-141">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="c400d-141">Metadata Enumerations</span></span>](metadata-enumerations.md)
