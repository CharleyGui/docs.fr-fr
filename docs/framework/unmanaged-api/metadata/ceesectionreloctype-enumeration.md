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
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType, énumération
Fournit des valeurs pour influencer le type d' `reloc` instruction émise dans un appel à [ICeeGen :: AddSectionReloc,](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
|`srRelocAbsolute`|Génère uniquement un `reloc`relatif à une section, en n’envoyant rien à une section. reloc.|  
|`srRelocHighLow`|Génère un `reloc` pour un emplacement au format pointeur. Elle est transformée en BASED_HIGHLOW ou BASED_DIR64 en fonction de la plateforme.|  
|`srRelocHighAdj`|Génère un `reloc` pour les 16 bits supérieurs d’un nombre 32 bits, où les 16 bits inférieurs sont inclus dans le mot suivant de la table. reloc.|  
|`srRelocMapToken`|Génère un réadressage de la carte de jetons, en n’envoyant rien à une section. reloc.|  
|`srRelocRelative`|Indique que la valeur est une correction d’adresse relative.|  
|`srRelocFilePos`|Génère uniquement un `reloc`relatif à une section, en n’envoyant rien à une section. reloc. Cette `reloc` est relative à la position de fichier de la section, et non à l’adresse virtuelle de la section.|  
|`srRelocCodeRelative`|Spécifie une correction d’adresse relative au code.|  
|`srRelocIA64Imm64`|Génère une `reloc` pour une adresse de 64 bits dans une instruction ia64 `movl`.|  
|`srRelocDir64`|Génère une `reloc` pour une adresse de 64 bits.|  
|`srRelocIA64PcRel25`|Génère un `reloc` pour une adresse relative à un PC 25 bits dans une instruction ia64 `br.call`.|  
|`srRelocIA64PcRel64`|Génère un `reloc` pour une adresse relative à un PC 64 bits dans une instruction ia64 `brl.call`.|  
|`srRelocAbsoluteTagged`|Génère un `reloc`relatif à une section de 30 bits, utilisé pour les valeurs de pointeur avec balises.|  
|`srRelocSentinel`|Une valeur de sentinelle pour aider à garantir que les ajouts à cette énumération sont reflétés dans le tableau de noms `reloc` interne.|  
|`srNoBaseReloc`|Spécifie de ne pas émettre de `reloc`de base.|  
|`srRelocPtr`|Valeur indiquant que le contenu de la précorrection de la mémoire est un pointeur plutôt qu’un décalage de section.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen, interface](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
