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
ms.openlocfilehash: 1b8440ed6e878aac3dd08d9f8ed528c93739a724
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686317"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor, énumération

Contient des valeurs qui indiquent les éléments à inclure dans un sous-ensemble personnalisé d’un dump de tas lors du signalement d’erreurs.  
  
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
|`DUMP_FLAVOR_Mini`|Spécifie que le dump du tas personnalisé doit démarrer en tant que Minidump et inclure des données supplémentaires spécifiées par des instances [CustomDumpItem](customdumpitem-structure.md) passées à la même méthode.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Spécifie que le dump du tas personnalisé doit collecter toutes les données d’état d’exécution qui n’ont pas été allouées dynamiquement.|  
  
## <a name="remarks"></a>Remarques  

 Un paramètre de type `ECustomDumpFlavor` est passé à la méthode [ICLRErrorReportingManager :: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ECustomDumpItemKind, énumération](ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager, interface](iclrerrorreportingmanager-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
