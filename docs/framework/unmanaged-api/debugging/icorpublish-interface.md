---
title: ICorPublish, interface
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: c4a24d879ebd9e8813ea0ac4597818569f4ae6fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790727"
---
# <a name="icorpublish-interface"></a>ICorPublish, interface
Sert d’interface générale pour la publication d’informations sur les processus et les informations sur les domaines d’application de ces processus.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumProcesses, méthode](icorpublish-enumprocesses-method.md)|Obtient une instance [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) qui contient les processus managés en cours d’exécution sur cet ordinateur.|  
|[GetProcess, méthode](icorpublish-getprocess-method.md)|Obtient une instance de [ICorPublishProcess](icorpublishprocess-interface.md) qui représente le processus avec l’identificateur spécifié.|  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [CorpubPublish, coclasse](corpubpublish-coclass.md)
