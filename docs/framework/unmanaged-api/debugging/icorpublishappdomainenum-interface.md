---
title: ICorPublishAppDomainEnum, interface
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: 61cac0922423acabef3d47618d98ddf082d071da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790676"
---
# <a name="icorpublishappdomainenum-interface"></a>ICorPublishAppDomainEnum, interface
Sous-classe de l’interface [ICorPublishEnum](icorpublishenum-interface.md) qui fournit des méthodes pour parcourir une collection d’objets [ICorPublishAppDomain](icorpublishappdomain-interface.md) qui existent actuellement dans un processus.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icorpublishappdomainenum-next-method.md)|Obtient le nombre spécifié d’instances de `ICorPublishAppDomain` de la collection, en commençant à la position actuelle.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorPublishAppDomainEnum` implémente les méthodes de l’interface abstraite, [ICorPublishEnum](icorpublishenum-interface.md).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [CorpubPublish, coclasse](corpubpublish-coclass.md)
