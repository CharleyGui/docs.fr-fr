---
title: CREATE_ASM_NAME_OBJ_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: 52d5ad3a18c102422e90621c7d1e23b2692c0000
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683228"
---
# <a name="create_asm_name_obj_flags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS, énumération

Spécifie les attributs d’un objet d' [interface IAssemblyName](iassemblyname-interface.md) lorsqu’il est construit par la fonction [CreateAssemblyNameObject,](createassemblynameobject-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|Indique que le paramètre passé est une identité textuelle.|  
|`CANOF_SET_DEFAULT_VALUES`|Définit quelques valeurs par défaut.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Vérifie la règle d’assembly friend (nom et clé publique uniquement). Ce membre est destiné à un usage interne uniquement.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Combinaison des `CANOF_PARSE_DISPLAY_NAME` `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` indicateurs et. Ce membre est destiné à un usage interne uniquement.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyName, interface](iassemblyname-interface.md)
- [CreateAssemblyNameObject, fonction](createassemblynameobject-function.md)
- [Énumérations de fusion](fusion-enumerations.md)
