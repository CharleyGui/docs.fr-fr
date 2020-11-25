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
ms.openlocfilehash: f7aa9699e9929608c90020c6b2d66c301fc11955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732708"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType, énumération

Fournit des valeurs pour influencer le type d' `reloc` instruction émis dans un appel à [ICeeGen :: AddSectionReloc,](iceegen-addsectionreloc-method.md).  
  
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
|`srRelocAbsolute`|Génère uniquement une section relative `reloc` , en n’envoyant rien dans une section. reloc.|  
|`srRelocHighLow`|Génère un `reloc` pour un emplacement au format pointeur. Elle est transformée en BASED_HIGHLOW ou BASED_DIR64 en fonction de la plateforme.|  
|`srRelocHighAdj`|Génère un `reloc` pour les 16 bits supérieurs d’un nombre de 32 bits, où les 16 bits inférieurs sont inclus dans le mot suivant de la table. reloc.|  
|`srRelocMapToken`|Génère un réadressage de la carte de jetons, en n’envoyant rien à une section. reloc.|  
|`srRelocRelative`|Indique que la valeur est une correction d’adresse relative.|  
|`srRelocFilePos`|Génère uniquement une section relative `reloc` , en n’envoyant rien dans une section. reloc. Cela `reloc` est relatif à la position de fichier de la section, et non à l’adresse virtuelle de la section.|  
|`srRelocCodeRelative`|Spécifie une correction d’adresse relative au code.|  
|`srRelocIA64Imm64`|Génère une `reloc` pour une adresse de 64 bits dans une `movl` instruction ia64.|  
|`srRelocDir64`|Génère une `reloc` pour une adresse de 64 bits.|  
|`srRelocIA64PcRel25`|Génère une `reloc` pour une adresse relative à un PC 25 bits dans une `br.call` instruction ia64.|  
|`srRelocIA64PcRel64`|Génère un `reloc` pour une adresse relative à un PC 64 bits dans une `brl.call` instruction ia64.|  
|`srRelocAbsoluteTagged`|Génère un relatif à une section de 30 bits `reloc` , utilisé pour les valeurs de pointeur avec balises.|  
|`srRelocSentinel`|Une valeur de sentinelle pour aider à garantir que les ajouts à cette énumération sont reflétés dans le `reloc` tableau de noms interne.|  
|`srNoBaseReloc`|Spécifie de ne pas émettre de base `reloc` .|  
|`srRelocPtr`|Valeur indiquant que le contenu de la précorrection de la mémoire est un pointeur plutôt qu’un décalage de section.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
- [ICeeGen, interface](iceegen-interface.md)
- [AddSectionReloc, méthode](iceegen-addsectionreloc-method.md)
