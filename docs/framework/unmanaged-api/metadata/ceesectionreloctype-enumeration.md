---
title: CeeSectionRelocType, énumération
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: efce0c13944b383c42cbff6a6af4795293ee2989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444160"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="b67c2-102">CeeSectionRelocType, énumération</span><span class="sxs-lookup"><span data-stu-id="b67c2-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="b67c2-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="b67c2-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b67c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b67c2-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="b67c2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b67c2-105">Members</span></span>  
  
|<span data-ttu-id="b67c2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b67c2-106">Member</span></span>|<span data-ttu-id="b67c2-107">Description</span><span class="sxs-lookup"><span data-stu-id="b67c2-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="b67c2-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span><span class="sxs-lookup"><span data-stu-id="b67c2-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="b67c2-109">Generates a `reloc` for a pointer-sized location.</span><span class="sxs-lookup"><span data-stu-id="b67c2-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="b67c2-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span><span class="sxs-lookup"><span data-stu-id="b67c2-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="b67c2-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span><span class="sxs-lookup"><span data-stu-id="b67c2-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="b67c2-112">Generates a token map relocation, sending nothing into a .reloc section.</span><span class="sxs-lookup"><span data-stu-id="b67c2-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="b67c2-113">Indicates that the value is a relative address fixup.</span><span class="sxs-lookup"><span data-stu-id="b67c2-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="b67c2-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span><span class="sxs-lookup"><span data-stu-id="b67c2-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="b67c2-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span><span class="sxs-lookup"><span data-stu-id="b67c2-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="b67c2-116">Specifies a code-relative address fixup.</span><span class="sxs-lookup"><span data-stu-id="b67c2-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="b67c2-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span><span class="sxs-lookup"><span data-stu-id="b67c2-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="b67c2-118">Generates a `reloc` for a 64-bit address.</span><span class="sxs-lookup"><span data-stu-id="b67c2-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="b67c2-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span><span class="sxs-lookup"><span data-stu-id="b67c2-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="b67c2-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span><span class="sxs-lookup"><span data-stu-id="b67c2-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="b67c2-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span><span class="sxs-lookup"><span data-stu-id="b67c2-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="b67c2-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span><span class="sxs-lookup"><span data-stu-id="b67c2-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="b67c2-123">Specifies not to emit a base `reloc`.</span><span class="sxs-lookup"><span data-stu-id="b67c2-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="b67c2-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span><span class="sxs-lookup"><span data-stu-id="b67c2-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b67c2-125">spécifications</span><span class="sxs-lookup"><span data-stu-id="b67c2-125">Requirements</span></span>  
 <span data-ttu-id="b67c2-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b67c2-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b67c2-127">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b67c2-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b67c2-128">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b67c2-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b67c2-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b67c2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67c2-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b67c2-130">See also</span></span>

- [<span data-ttu-id="b67c2-131">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="b67c2-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="b67c2-132">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="b67c2-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="b67c2-133">AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="b67c2-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
