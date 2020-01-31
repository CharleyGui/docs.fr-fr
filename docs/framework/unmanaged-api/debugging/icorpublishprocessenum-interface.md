---
title: ICorPublishProcessEnum, interface
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790509"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum, interface
Sous-classe de l’interface [ICorPublishEnum](icorpublishenum-interface.md) qui fournit des méthodes pour parcourir une collection d’objets [ICorPublishProcess](icorpublishprocess-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icorpublishprocessenum-next-method.md)|Obtient le nombre spécifié d’instances de `ICorPublishProcess` de la collection, en commençant à la position actuelle.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorPublishProcessEnum` implémente les méthodes de l’interface abstraite, [ICorPublishEnum](icorpublishenum-interface.md).  
  
 Une instance `ICorPublishProcessEnum` est créée par la méthode [ICorPublish :: EnumProcesses](icorpublish-enumprocesses-method.md) . Le parcours de la collection d’objets `ICorPublishProcess` est basé sur les critères de filtre spécifiés au moment de la création de l’instance de `ICorPublishProcessEnum`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [CorpubPublish, coclasse](corpubpublish-coclass.md)
