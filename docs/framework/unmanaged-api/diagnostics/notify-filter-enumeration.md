---
title: NOTIFY_FILTER, énumération
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: 92e40dbe8892d48dba1c54d9cd16faa409440b24
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438118"
---
# <a name="notify_filter-enumeration"></a>NOTIFY_FILTER, énumération
Identifie les rappels pour les fonctions du débogueur. Pour plus d’informations, consultez la méthode [INotifySource2 :: SetNotifyFilter,](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|Indique que la méthode [INotifySink2 :: OnSyncCallOut,](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) doit être appelée.|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|Indique que la méthode [INotifySink2 :: OnSyncCallEnter,](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) doit être appelée.|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|Indique que la méthode [INotifySink2 :: OnSyncCallExit,](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) doit être appelée.|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|Indique que la méthode [INotifySink2 :: OnSyncCallReturn,](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) doit être appelée.|  
|`NOTIFY_FILTER_ALLSYNC`|Indique que toutes les méthodes [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) doivent être appelées.|  
|`NOTIFY_FILTER_ALL`|Active toutes les notifications existantes et futures.|  
|`NOTIFY_FILTER_NONE`|Indique qu’aucune méthode de notification ne doit être appelée.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
