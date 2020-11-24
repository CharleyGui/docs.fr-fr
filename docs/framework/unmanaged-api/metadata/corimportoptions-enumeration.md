---
title: CorImportOptions, énumération
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
ms.openlocfilehash: 3d5989d43644088403a77f26c02af9ffaae0732b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677215"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions, énumération

Contient des valeurs d'indicateur qui contrôlent le comportement lors de l'importation d'un assembly en dehors de la portée actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDImportOptionDefault`|Indique le comportement par défaut, qui consiste à ignorer les enregistrements supprimés.|  
|`MDImportOptionAll`|Indique que toutes les métadonnées doivent être énumérées.|  
|`MDImportOptionAllTypeDefs`|Indique que tous les TypeDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllMethodDefs`|Indique que tous les MethodDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllFieldDefs`|Indique que tous les FieldDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllProperties`|Indique que tous les PropertyDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllEvents`|Indique que tous les EventDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllCustomAttributes`|Indique que tous les attributs personnalisés, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllExportedTypes`|Indique que tous les types exportés, y compris ceux qui sont supprimés, doivent être énumérés.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
