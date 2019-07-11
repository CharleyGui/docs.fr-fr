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
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType, énumération
Fournit des valeurs pour influencer le type de `reloc` instruction émise dans un appel à [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
|`srRelocAbsolute`|Génère uniquement une section relatifs à `reloc`, envoyant rien dans une section .reloc.|  
|`srRelocHighLow`|Génère un `reloc` pour un emplacement de la taille du pointeur. Il est transformé en BASED_HIGHLOW ou en BASED_DIR64 selon la plateforme.|  
|`srRelocHighAdj`|Génère un `reloc` pour les 16 bits supérieurs d’un nombre 32 bits, où les 16 bits inférieurs sont inclus dans le mot suivant dans la table .reloc.|  
|`srRelocMapToken`|Génère un déplacement de la table de jetons, en n’envoyant rien dans une section .reloc.|  
|`srRelocRelative`|Indique que la valeur est une correction de l’adresse relative.|  
|`srRelocFilePos`|Génère uniquement une section relatifs à `reloc`, envoyant rien dans une section .reloc. Cela `reloc` est relatif à la position de fichier de la section, pas une adresse virtuelle de la section.|  
|`srRelocCodeRelative`|Spécifie une correction de l’adresse relative du code.|  
|`srRelocIA64Imm64`|Génère un `reloc` pour une adresse 64 bits dans un ia64 `movl` instruction.|  
|`srRelocDir64`|Génère un `reloc` pour une adresse 64 bits.|  
|`srRelocIA64PcRel25`|Générer un `reloc` pour chaque adresse relative PC 25 bits dans un ia64 `br.call` instruction.|  
|`srRelocIA64PcRel64`|Génère un `reloc` pour chaque adresse relative PC 64 bits dans un ia64 `brl.call` instruction.|  
|`srRelocAbsoluteTagged`|Génère une section de 30 bits-relative `reloc`, utilisé pour les valeurs de pointeur avec balises.|  
|`srRelocSentinel`|Valeur de sentinelle pour garantir des ajouts à cet enum sont reflétées dans le texte interne `reloc` tableau de noms.|  
|`srNoBaseReloc`|Spécifie de ne pas émettre une base `reloc`.|  
|`srRelocPtr`|Une valeur qui indique que le contenu de pre-correction de la mémoire est un pointeur plutôt qu’une section décalage.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen, interface](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
