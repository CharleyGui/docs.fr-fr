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
ms.openlocfilehash: 78b30f624bd71234e8f1b56600b3a23d15fdf517
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006028"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="6ba94-102">CeeSectionRelocType, énumération</span><span class="sxs-lookup"><span data-stu-id="6ba94-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="6ba94-103">Fournit des valeurs pour influencer le type d' `reloc` instruction émis dans un appel à [ICeeGen :: AddSectionReloc,](iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="6ba94-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ba94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ba94-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6ba94-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6ba94-105">Members</span></span>  
  
|<span data-ttu-id="6ba94-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6ba94-106">Member</span></span>|<span data-ttu-id="6ba94-107">Description</span><span class="sxs-lookup"><span data-stu-id="6ba94-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="6ba94-108">Génère uniquement une section relative `reloc` , en n’envoyant rien dans une section. reloc.</span><span class="sxs-lookup"><span data-stu-id="6ba94-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="6ba94-109">Génère un `reloc` pour un emplacement au format pointeur.</span><span class="sxs-lookup"><span data-stu-id="6ba94-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="6ba94-110">Elle est transformée en BASED_HIGHLOW ou BASED_DIR64 en fonction de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="6ba94-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="6ba94-111">Génère un `reloc` pour les 16 bits supérieurs d’un nombre de 32 bits, où les 16 bits inférieurs sont inclus dans le mot suivant de la table. reloc.</span><span class="sxs-lookup"><span data-stu-id="6ba94-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="6ba94-112">Génère un réadressage de la carte de jetons, en n’envoyant rien à une section. reloc.</span><span class="sxs-lookup"><span data-stu-id="6ba94-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="6ba94-113">Indique que la valeur est une correction d’adresse relative.</span><span class="sxs-lookup"><span data-stu-id="6ba94-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="6ba94-114">Génère uniquement une section relative `reloc` , en n’envoyant rien dans une section. reloc.</span><span class="sxs-lookup"><span data-stu-id="6ba94-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="6ba94-115">Cela `reloc` est relatif à la position de fichier de la section, et non à l’adresse virtuelle de la section.</span><span class="sxs-lookup"><span data-stu-id="6ba94-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="6ba94-116">Spécifie une correction d’adresse relative au code.</span><span class="sxs-lookup"><span data-stu-id="6ba94-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="6ba94-117">Génère une `reloc` pour une adresse de 64 bits dans une `movl` instruction ia64.</span><span class="sxs-lookup"><span data-stu-id="6ba94-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="6ba94-118">Génère une `reloc` pour une adresse de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6ba94-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="6ba94-119">Génère une `reloc` pour une adresse relative à un PC 25 bits dans une `br.call` instruction ia64.</span><span class="sxs-lookup"><span data-stu-id="6ba94-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="6ba94-120">Génère un `reloc` pour une adresse relative à un PC 64 bits dans une `brl.call` instruction ia64.</span><span class="sxs-lookup"><span data-stu-id="6ba94-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="6ba94-121">Génère un relatif à une section de 30 bits `reloc` , utilisé pour les valeurs de pointeur avec balises.</span><span class="sxs-lookup"><span data-stu-id="6ba94-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="6ba94-122">Une valeur de sentinelle pour aider à garantir que les ajouts à cette énumération sont reflétés dans le `reloc` tableau de noms interne.</span><span class="sxs-lookup"><span data-stu-id="6ba94-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="6ba94-123">Spécifie de ne pas émettre de base `reloc` .</span><span class="sxs-lookup"><span data-stu-id="6ba94-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="6ba94-124">Valeur indiquant que le contenu de la précorrection de la mémoire est un pointeur plutôt qu’un décalage de section.</span><span class="sxs-lookup"><span data-stu-id="6ba94-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ba94-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6ba94-125">Requirements</span></span>  
 <span data-ttu-id="6ba94-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ba94-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ba94-127">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6ba94-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ba94-128">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ba94-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ba94-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ba94-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba94-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ba94-130">See also</span></span>

- [<span data-ttu-id="6ba94-131">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="6ba94-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="6ba94-132">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="6ba94-132">ICeeGen Interface</span></span>](iceegen-interface.md)
- [<span data-ttu-id="6ba94-133">AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="6ba94-133">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)
