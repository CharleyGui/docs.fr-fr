---
title: ECustomDumpFlavor, énumération
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a416a51f5121f29d373fcfdfa6b0597d9b10ded5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779383"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor, énumération
Contient des valeurs qui indiquent les éléments à inclure dans un sous-ensemble personnalisé d’un segment de mémoire de vidage lors du signalement des erreurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|Spécifie que le dump du tas personnalisé doit démarrer en tant qu’un minidump et inclure les données supplémentaires spécifiées par les [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passées à la même méthode.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Spécifie que le dump du tas personnalisé doit rassembler toutes les données d’état d’exécution qui ne sont pas allouées dynamiquement.|  
  
## <a name="remarks"></a>Notes  
 Un paramètre de type `ECustomDumpFlavor` est passé à la [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ECustomDumpItemKind, énumération](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
