---
title: INotifySink2, interface
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
ms.openlocfilehash: 255fe51f86157842a5807145bf7c58ae1ff5ba8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720020"
---
# <a name="inotifysink2-interface"></a>INotifySink2, interface

Déclare des méthodes pour la notification du récepteur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnSyncCallEnter, méthode](inotifysink2-onsynccallenter-method.md)|Est appelé lors de l’entrée d’un appel.|  
|[OnSyncCallExit, méthode](inotifysink2-onsynccallexit-method.md)|Est appelé lors de la sortie d’un appel.|  
|[OnSyncCallOut, méthode](inotifysink2-onsynccallout-method.md)|Est appelé quand un appel est en sortie.|  
|[OnSyncCallReturn, méthode](inotifysink2-onsynccallreturn-method.md)|Est appelé quand un appel est retourné.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifyConnection2, interface](inotifyconnection2-interface.md)
- [INotifySource2, interface](inotifysource2-interface.md)
- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
