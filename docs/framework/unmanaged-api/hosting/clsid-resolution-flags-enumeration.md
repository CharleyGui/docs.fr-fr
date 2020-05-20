---
title: CLSID_RESOLUTION_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
ms.openlocfilehash: 5ac015f958d9504bbd14a66ead86548b8df32764
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616773"
---
# <a name="clsid_resolution_flags-enumeration"></a>CLSID_RESOLUTION_FLAGS, énumération
Contient des valeurs qui indiquent comment le common language runtime (CLR) doit résoudre un `CLSID` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|Indique le comportement par défaut.|  
|`CLSID_RESOLUTION_REGISTERED`|Indique que le runtime effectue une recherche dans le registre et applique la stratégie shim.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
