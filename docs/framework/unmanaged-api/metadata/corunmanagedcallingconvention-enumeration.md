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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9206fbde13f457d4b2e2941ee744d645c6df9774
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781995"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="06efa-102">CorUnmanagedCallingConvention, énumération</span><span class="sxs-lookup"><span data-stu-id="06efa-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="06efa-103">Spécifie les conventions d’appel du code non managé.</span><span class="sxs-lookup"><span data-stu-id="06efa-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06efa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06efa-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="06efa-105">Membres</span><span class="sxs-lookup"><span data-stu-id="06efa-105">Members</span></span>  
  
|<span data-ttu-id="06efa-106">Membre</span><span class="sxs-lookup"><span data-stu-id="06efa-106">Member</span></span>|<span data-ttu-id="06efa-107">Description</span><span class="sxs-lookup"><span data-stu-id="06efa-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="06efa-108">La convention d’appel langage C.</span><span class="sxs-lookup"><span data-stu-id="06efa-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="06efa-109">La convention d’appel standard.</span><span class="sxs-lookup"><span data-stu-id="06efa-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="06efa-110">« Thie » convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="06efa-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="06efa-111">La convention d’appel « rapide ».</span><span class="sxs-lookup"><span data-stu-id="06efa-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="06efa-112">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="06efa-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="06efa-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="06efa-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="06efa-114">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="06efa-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="06efa-115">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="06efa-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06efa-116">Notes</span><span class="sxs-lookup"><span data-stu-id="06efa-116">Remarks</span></span>  
 <span data-ttu-id="06efa-117">Le CLR ne prend pas en charge la convention d’appel « rapide » dans le .NET Framework version 1.0.</span><span class="sxs-lookup"><span data-stu-id="06efa-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06efa-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="06efa-118">Requirements</span></span>  
 <span data-ttu-id="06efa-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06efa-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06efa-120">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="06efa-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="06efa-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06efa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06efa-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06efa-122">See also</span></span>

- [<span data-ttu-id="06efa-123">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="06efa-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
