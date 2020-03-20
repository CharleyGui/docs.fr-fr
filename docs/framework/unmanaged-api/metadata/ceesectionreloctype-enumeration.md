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
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType, énumération
Fournit des valeurs pour `reloc` influencer le type d’instruction émise dans un appel à [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`srRelocAbsolute`|Ne génère qu’une `reloc`section relative, n’envoyant rien dans une section .reloc.|  
|`srRelocHighLow`|Génère un `reloc` emplacement de la taille d’un pointeur. Ceci est transformé en BASED_HIGHLOW ou BASED_DIR64 en fonction de la plate-forme.|  
|`srRelocHighAdj`|Génère un `reloc` pour le top 16 bits d’un nombre de 32 bits, où les 16 bits inférieurs sont inclus dans le mot suivant dans le tableau .reloc.|  
|`srRelocMapToken`|Génère une relocalisation de carte symbolique, n’envoyant rien dans une section .reloc.|  
|`srRelocRelative`|Indique que la valeur est un fixup adresse relative.|  
|`srRelocFilePos`|Ne génère qu’une `reloc`section relative, n’envoyant rien dans une section .reloc. Ceci `reloc` est relatif à la position de fichier de la section, et non à l’adresse virtuelle de la section.|  
|`srRelocCodeRelative`|Spécifie un correctif d’adresse code-relatif.|  
|`srRelocIA64Imm64`|Génère une `reloc` adresse pour 64 bits dans `movl` une instruction ia64.|  
|`srRelocDir64`|Génère une `reloc` adresse 64 bits.|  
|`srRelocIA64PcRel25`|Générer `reloc` un pour une adresse PC-relative 25 bits dans une instruction ia64. `br.call`|  
|`srRelocIA64PcRel64`|Génère un `reloc` pour une adresse PC-relative 64 bits `brl.call` dans une instruction ia64.|  
|`srRelocAbsoluteTagged`|Génère une section-relative `reloc`de 30 bits, utilisée pour les valeurs de pointeur marqués.|  
|`srRelocSentinel`|Une valeur sentinelle pour aider à s’assurer que `reloc` tous les ajouts à cet enum sont reflétés dans le tableau de nom interne.|  
|`srNoBaseReloc`|Précise de ne pas `reloc`émettre une base .|  
|`srRelocPtr`|Une valeur indiquant que le contenu pré-fixup de la mémoire est un pointeur plutôt qu’un décalage de section.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen, interface](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
