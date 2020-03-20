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
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176212"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="05a33-102">CeeSectionRelocType, énumération</span><span class="sxs-lookup"><span data-stu-id="05a33-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="05a33-103">Fournit des valeurs pour `reloc` influencer le type d’instruction émise dans un appel à [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="05a33-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05a33-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="05a33-105">Membres</span><span class="sxs-lookup"><span data-stu-id="05a33-105">Members</span></span>  
  
|<span data-ttu-id="05a33-106">Membre</span><span class="sxs-lookup"><span data-stu-id="05a33-106">Member</span></span>|<span data-ttu-id="05a33-107">Description</span><span class="sxs-lookup"><span data-stu-id="05a33-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="05a33-108">Ne génère qu’une `reloc`section relative, n’envoyant rien dans une section .reloc.</span><span class="sxs-lookup"><span data-stu-id="05a33-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="05a33-109">Génère un `reloc` emplacement de la taille d’un pointeur.</span><span class="sxs-lookup"><span data-stu-id="05a33-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="05a33-110">Ceci est transformé en BASED_HIGHLOW ou BASED_DIR64 en fonction de la plate-forme.</span><span class="sxs-lookup"><span data-stu-id="05a33-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="05a33-111">Génère un `reloc` pour le top 16 bits d’un nombre de 32 bits, où les 16 bits inférieurs sont inclus dans le mot suivant dans le tableau .reloc.</span><span class="sxs-lookup"><span data-stu-id="05a33-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="05a33-112">Génère une relocalisation de carte symbolique, n’envoyant rien dans une section .reloc.</span><span class="sxs-lookup"><span data-stu-id="05a33-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="05a33-113">Indique que la valeur est un fixup adresse relative.</span><span class="sxs-lookup"><span data-stu-id="05a33-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="05a33-114">Ne génère qu’une `reloc`section relative, n’envoyant rien dans une section .reloc.</span><span class="sxs-lookup"><span data-stu-id="05a33-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="05a33-115">Ceci `reloc` est relatif à la position de fichier de la section, et non à l’adresse virtuelle de la section.</span><span class="sxs-lookup"><span data-stu-id="05a33-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="05a33-116">Spécifie un correctif d’adresse code-relatif.</span><span class="sxs-lookup"><span data-stu-id="05a33-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="05a33-117">Génère une `reloc` adresse pour 64 bits dans `movl` une instruction ia64.</span><span class="sxs-lookup"><span data-stu-id="05a33-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="05a33-118">Génère une `reloc` adresse 64 bits.</span><span class="sxs-lookup"><span data-stu-id="05a33-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="05a33-119">Générer `reloc` un pour une adresse PC-relative 25 bits dans une instruction ia64. `br.call`</span><span class="sxs-lookup"><span data-stu-id="05a33-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="05a33-120">Génère un `reloc` pour une adresse PC-relative 64 bits `brl.call` dans une instruction ia64.</span><span class="sxs-lookup"><span data-stu-id="05a33-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="05a33-121">Génère une section-relative `reloc`de 30 bits, utilisée pour les valeurs de pointeur marqués.</span><span class="sxs-lookup"><span data-stu-id="05a33-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="05a33-122">Une valeur sentinelle pour aider à s’assurer que `reloc` tous les ajouts à cet enum sont reflétés dans le tableau de nom interne.</span><span class="sxs-lookup"><span data-stu-id="05a33-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="05a33-123">Précise de ne pas `reloc`émettre une base .</span><span class="sxs-lookup"><span data-stu-id="05a33-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="05a33-124">Une valeur indiquant que le contenu pré-fixup de la mémoire est un pointeur plutôt qu’un décalage de section.</span><span class="sxs-lookup"><span data-stu-id="05a33-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05a33-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="05a33-125">Requirements</span></span>  
 <span data-ttu-id="05a33-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05a33-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a33-127">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="05a33-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05a33-128">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05a33-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05a33-129">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a33-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a33-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05a33-130">See also</span></span>

- [<span data-ttu-id="05a33-131">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="05a33-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="05a33-132">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="05a33-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="05a33-133">AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="05a33-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
