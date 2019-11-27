---
title: CorUnmanagedCallingConvention, énumération
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: 58d30e71929d314ee36adb9f83270858ff8a161b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442438"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="b9189-102">CorUnmanagedCallingConvention, énumération</span><span class="sxs-lookup"><span data-stu-id="b9189-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="b9189-103">Spécifie les conventions d’appel pour le code non managé.</span><span class="sxs-lookup"><span data-stu-id="b9189-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9189-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9189-104">Syntax</span></span>  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="b9189-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b9189-105">Members</span></span>  
  
|<span data-ttu-id="b9189-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b9189-106">Member</span></span>|<span data-ttu-id="b9189-107">Description</span><span class="sxs-lookup"><span data-stu-id="b9189-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="b9189-108">Convention d’appel du langage C.</span><span class="sxs-lookup"><span data-stu-id="b9189-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="b9189-109">Convention d’appel standard.</span><span class="sxs-lookup"><span data-stu-id="b9189-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="b9189-110">Convention d’appel « This ».</span><span class="sxs-lookup"><span data-stu-id="b9189-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="b9189-111">Convention d’appel « Fast ».</span><span class="sxs-lookup"><span data-stu-id="b9189-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="b9189-112">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="b9189-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="b9189-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="b9189-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="b9189-114">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="b9189-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="b9189-115">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="b9189-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9189-116">Notes</span><span class="sxs-lookup"><span data-stu-id="b9189-116">Remarks</span></span>  
 <span data-ttu-id="b9189-117">Le CLR ne prend pas en charge la Convention d’appel « Fast » dans le .NET Framework version 1,0.</span><span class="sxs-lookup"><span data-stu-id="b9189-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9189-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9189-118">Requirements</span></span>  
 <span data-ttu-id="b9189-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9189-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9189-120">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b9189-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b9189-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9189-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9189-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9189-122">See also</span></span>

- [<span data-ttu-id="b9189-123">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="b9189-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
