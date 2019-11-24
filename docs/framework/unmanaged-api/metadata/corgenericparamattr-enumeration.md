---
title: CorGenericParamAttr, énumération
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450280"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="97c28-102">CorGenericParamAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="97c28-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="97c28-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="97c28-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97c28-104">Syntax</span></span>  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="97c28-105">Membres</span><span class="sxs-lookup"><span data-stu-id="97c28-105">Members</span></span>  
  
|<span data-ttu-id="97c28-106">Membre</span><span class="sxs-lookup"><span data-stu-id="97c28-106">Member</span></span>|<span data-ttu-id="97c28-107">Description</span><span class="sxs-lookup"><span data-stu-id="97c28-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="97c28-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span><span class="sxs-lookup"><span data-stu-id="97c28-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="97c28-109">Indicates the absence of variance.</span><span class="sxs-lookup"><span data-stu-id="97c28-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="97c28-110">Indicates covariance.</span><span class="sxs-lookup"><span data-stu-id="97c28-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="97c28-111">Indicates contravariance.</span><span class="sxs-lookup"><span data-stu-id="97c28-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="97c28-112">Special constraints can apply to any <xref:System.Type> parameter.</span><span class="sxs-lookup"><span data-stu-id="97c28-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="97c28-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span><span class="sxs-lookup"><span data-stu-id="97c28-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="97c28-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span><span class="sxs-lookup"><span data-stu-id="97c28-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="97c28-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span><span class="sxs-lookup"><span data-stu-id="97c28-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="97c28-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span><span class="sxs-lookup"><span data-stu-id="97c28-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97c28-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="97c28-117">Requirements</span></span>  
 <span data-ttu-id="97c28-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97c28-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97c28-119">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="97c28-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="97c28-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97c28-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c28-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97c28-121">See also</span></span>

- [<span data-ttu-id="97c28-122">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="97c28-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
