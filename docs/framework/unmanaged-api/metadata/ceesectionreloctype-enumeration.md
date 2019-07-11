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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1218ee76a3b7a2f501f87adf1e0bc8133d5329b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781351"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="57ce2-102">CeeSectionRelocType, énumération</span><span class="sxs-lookup"><span data-stu-id="57ce2-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="57ce2-103">Fournit des valeurs pour influencer le type de `reloc` instruction émise dans un appel à [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="57ce2-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ce2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57ce2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="57ce2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="57ce2-105">Members</span></span>  
  
|<span data-ttu-id="57ce2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="57ce2-106">Member</span></span>|<span data-ttu-id="57ce2-107">Description</span><span class="sxs-lookup"><span data-stu-id="57ce2-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="57ce2-108">Génère uniquement une section relatifs à `reloc`, envoyant rien dans une section .reloc.</span><span class="sxs-lookup"><span data-stu-id="57ce2-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="57ce2-109">Génère un `reloc` pour un emplacement de la taille du pointeur.</span><span class="sxs-lookup"><span data-stu-id="57ce2-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="57ce2-110">Il est transformé en BASED_HIGHLOW ou en BASED_DIR64 selon la plateforme.</span><span class="sxs-lookup"><span data-stu-id="57ce2-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="57ce2-111">Génère un `reloc` pour les 16 bits supérieurs d’un nombre 32 bits, où les 16 bits inférieurs sont inclus dans le mot suivant dans la table .reloc.</span><span class="sxs-lookup"><span data-stu-id="57ce2-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="57ce2-112">Génère un déplacement de la table de jetons, en n’envoyant rien dans une section .reloc.</span><span class="sxs-lookup"><span data-stu-id="57ce2-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="57ce2-113">Indique que la valeur est une correction de l’adresse relative.</span><span class="sxs-lookup"><span data-stu-id="57ce2-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="57ce2-114">Génère uniquement une section relatifs à `reloc`, envoyant rien dans une section .reloc.</span><span class="sxs-lookup"><span data-stu-id="57ce2-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="57ce2-115">Cela `reloc` est relatif à la position de fichier de la section, pas une adresse virtuelle de la section.</span><span class="sxs-lookup"><span data-stu-id="57ce2-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="57ce2-116">Spécifie une correction de l’adresse relative du code.</span><span class="sxs-lookup"><span data-stu-id="57ce2-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="57ce2-117">Génère un `reloc` pour une adresse 64 bits dans un ia64 `movl` instruction.</span><span class="sxs-lookup"><span data-stu-id="57ce2-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="57ce2-118">Génère un `reloc` pour une adresse 64 bits.</span><span class="sxs-lookup"><span data-stu-id="57ce2-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="57ce2-119">Générer un `reloc` pour chaque adresse relative PC 25 bits dans un ia64 `br.call` instruction.</span><span class="sxs-lookup"><span data-stu-id="57ce2-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="57ce2-120">Génère un `reloc` pour chaque adresse relative PC 64 bits dans un ia64 `brl.call` instruction.</span><span class="sxs-lookup"><span data-stu-id="57ce2-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="57ce2-121">Génère une section de 30 bits-relative `reloc`, utilisé pour les valeurs de pointeur avec balises.</span><span class="sxs-lookup"><span data-stu-id="57ce2-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="57ce2-122">Valeur de sentinelle pour garantir des ajouts à cet enum sont reflétées dans le texte interne `reloc` tableau de noms.</span><span class="sxs-lookup"><span data-stu-id="57ce2-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="57ce2-123">Spécifie de ne pas émettre une base `reloc`.</span><span class="sxs-lookup"><span data-stu-id="57ce2-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="57ce2-124">Une valeur qui indique que le contenu de pre-correction de la mémoire est un pointeur plutôt qu’une section décalage.</span><span class="sxs-lookup"><span data-stu-id="57ce2-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57ce2-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="57ce2-125">Requirements</span></span>  
 <span data-ttu-id="57ce2-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57ce2-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57ce2-127">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="57ce2-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57ce2-128">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57ce2-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57ce2-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57ce2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ce2-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57ce2-130">See also</span></span>

- [<span data-ttu-id="57ce2-131">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="57ce2-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="57ce2-132">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="57ce2-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="57ce2-133">AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="57ce2-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
