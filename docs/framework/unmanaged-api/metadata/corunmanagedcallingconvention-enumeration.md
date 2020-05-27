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
ms.openlocfilehash: b4c521489f38360d45c2cf8ff3780e057299f0b4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008948"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="16a2d-102">CorUnmanagedCallingConvention, énumération</span><span class="sxs-lookup"><span data-stu-id="16a2d-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="16a2d-103">Spécifie les conventions d’appel pour le code non managé.</span><span class="sxs-lookup"><span data-stu-id="16a2d-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16a2d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="16a2d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="16a2d-105">Members</span></span>  
  
|<span data-ttu-id="16a2d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="16a2d-106">Member</span></span>|<span data-ttu-id="16a2d-107">Description</span><span class="sxs-lookup"><span data-stu-id="16a2d-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="16a2d-108">Convention d’appel du langage C.</span><span class="sxs-lookup"><span data-stu-id="16a2d-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="16a2d-109">Convention d’appel standard.</span><span class="sxs-lookup"><span data-stu-id="16a2d-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="16a2d-110">Convention d’appel « This ».</span><span class="sxs-lookup"><span data-stu-id="16a2d-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="16a2d-111">Convention d’appel « Fast ».</span><span class="sxs-lookup"><span data-stu-id="16a2d-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="16a2d-112">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="16a2d-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="16a2d-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="16a2d-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="16a2d-114">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="16a2d-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="16a2d-115">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="16a2d-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16a2d-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="16a2d-116">Remarks</span></span>  
 <span data-ttu-id="16a2d-117">Le CLR ne prend pas en charge la Convention d’appel « Fast » dans le .NET Framework version 1,0.</span><span class="sxs-lookup"><span data-stu-id="16a2d-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16a2d-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="16a2d-118">Requirements</span></span>  
 <span data-ttu-id="16a2d-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16a2d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16a2d-120">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="16a2d-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="16a2d-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16a2d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a2d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16a2d-122">See also</span></span>

- [<span data-ttu-id="16a2d-123">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="16a2d-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
