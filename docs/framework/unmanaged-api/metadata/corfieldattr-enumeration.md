---
title: CorFieldAttr, énumération
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: 4e40f684cc1578672cb8ff474972ce9cdc39efb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718824"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr, énumération

Contient des valeurs qui décrivent les métadonnées concernant un champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`fdFieldAccessMask`|Spécifie les informations d’accessibilité.|  
|`fdPrivateScope`|Spécifie que le champ ne peut pas être référencé.|  
|`fdPrivate`|Spécifie que le champ est accessible uniquement par son type parent.|  
|`fdFamANDAssem`|Spécifie que le champ est accessible par les classes dérivées dans son assembly.|  
|`fdAssembly`|Spécifie que le champ est accessible par tous les types de son assembly.|  
|`fdFamily`|Spécifie que le champ est accessible uniquement par son type et ses classes dérivées.|  
|`fdFamORAssem`|Spécifie que le champ est accessible par les classes dérivées et par tous les types de son assembly.|  
|`fdPublic`|Spécifie que le champ est accessible par tous les types ayant une visibilité de cette portée.|  
|`fdStatic`|Spécifie que le champ est un membre de son type plutôt qu’un membre d’instance.|  
|`fdInitOnly`|Spécifie que le champ ne peut pas être modifié une fois qu’il a été initialisé.|  
|`fdLiteral`|Spécifie que la valeur de champ est une constante au moment de la compilation.|  
|`fdNotSerialized`|Spécifie que le champ n’est pas sérialisé quand son type est distant.|  
|`fdSpecialName`|Spécifie que le champ est spécial et que son nom décrit comment.|  
|`fdPinvokeImpl`|Spécifie que l’implémentation de champ est transférée par le biais de PInvoke.|  
|`fdReservedMask`|Réservé à un usage interne par la common language runtime.|  
|`fdRTSpecialName`|Spécifie que l’common language runtime les API internes de métadonnées doivent vérifier l’encodage du nom.|  
|`fdHasFieldMarshal`|Spécifie que le champ contient des informations de marshaling.|  
|`fdHasDefault`|Spécifie que le champ a une valeur par défaut.|  
|`fdHasFieldRVA`|Spécifie que le champ a une adresse virtuelle relative.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
