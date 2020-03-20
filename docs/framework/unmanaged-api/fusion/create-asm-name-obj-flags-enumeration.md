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
ms.openlocfilehash: ee856dbd398d0fa5e3eee7d9b2b2cfc7c7a57ecf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176589"
---
# <a name="create_asm_name_obj_flags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS, énumération
Spécifie les attributs d’un objet [IAssemblyName Interface](iassemblyname-interface.md) lorsqu’il est construit par la fonction [CreateAssemblyNameObject.](createassemblynameobject-function.md)  
  
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
|`CANOF_PARSE_DISPLAY_NAME`|Indique que le paramètre adopté est une identité textuelle.|  
|`CANOF_SET_DEFAULT_VALUES`|Définit quelques valeurs par défaut.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Vérifie la règle de l’assemblée des amis (seulement le nom et la clé publique). Ce membre est pour une utilisation interne seulement.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Une combinaison `CANOF_PARSE_DISPLAY_NAME` de `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` la et des drapeaux. Ce membre est pour une utilisation interne seulement.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** Fusion.h  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyName, interface](iassemblyname-interface.md)
- [CreateAssemblyNameObject, fonction](createassemblynameobject-function.md)
- [Énumérations de fusion](fusion-enumerations.md)
