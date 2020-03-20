---
title: CorAttributeTargets, énumération
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 51741aa3a6d965c1e9743081628d8ad62e8fb04e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176199"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets, énumération
Spécifie les éléments de l'application auxquels un attribut peut être appliqué.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`catAssembly`|L'attribut peut être appliqué à un assembly.|  
|`catModule`|L’attribut peut être appliqué à un module portable exécutable (.dll ou .exe).|  
|`catClass`|L'attribut peut être appliqué à une classe.|  
|`catStruct`|L'attribut peut être appliqué à une structure, c'est-à-dire à un type valeur.|  
|`catEnum`|L'attribut peut être appliqué à une énumération.|  
|`catConstructor`|L'attribut peut être appliqué à un constructeur.|  
|`catMethod`|L'attribut peut être appliqué à une méthode.|  
|`catProperty`|L'attribut peut être appliqué à une propriété.|  
|`catField`|L'attribut peut être appliqué à un champ.|  
|`catEvent`|L'attribut peut être appliqué à un événement.|  
|`catInterface`|L'attribut peut être appliqué à une interface.|  
|`catParameter`|L'attribut peut être appliqué à un paramètre.|  
|`catDelegate`|L'attribut peut être appliqué à un délégué.|  
|`catGenericParameter`|L'attribut peut être appliqué à un paramètre générique.|  
|`catAll`|L'attribut peut être appliqué à n'importe quel élément de l'application.|  
|`catClassMembers`|L’attribut peut être appliqué à un membre d’une classe.|  
  
## <a name="remarks"></a>Notes   
 Les `CorAttributeTargets` valeurs de recensement peuvent être combinées avec une opération PEU sage OU pour obtenir la combinaison préférée.  
  
 Les `CorAttributeTargets` parallèles <xref:System.AttributeTargets?displayProperty=nameWithType> de l’énumération gérée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorHdr.h  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
