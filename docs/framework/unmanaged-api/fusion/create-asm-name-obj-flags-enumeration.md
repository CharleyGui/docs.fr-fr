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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 871ad81cd83c40d7299f39ede404e274b95b2ac0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778459"
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS, énumération
Spécifie les attributs d’un [IAssemblyName, Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) de l’objet lorsqu’il est construit par la [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) (fonction).  
  
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
|`CANOF_SET_DEFAULT_VALUES`|Définit le nombre de valeurs par défaut.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Vérifie la règle d’assembly friend (uniquement un nom et clé publique). Ce membre est à usage interne uniquement.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Une combinaison de la `CANOF_PARSE_DISPLAY_NAME` et `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` indicateurs. Ce membre est à usage interne uniquement.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyName, interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [CreateAssemblyNameObject, fonction](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [Énumérations de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
