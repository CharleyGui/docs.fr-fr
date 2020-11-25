---
title: INotifyConnection2::RegisterNotifySource, méthode
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: 1286dd970e437af0a8b607ed050ab4838f73a41f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720046"
---
# <a name="inotifyconnection2registernotifysource-method"></a>INotifyConnection2::RegisterNotifySource, méthode

Installe une source de notification spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `in_pNotifySource`  
 dans Spécifie l’objet à utiliser comme source de notification.  
  
 `out_ppNotifySink`  
 à Reçoit l’objet à utiliser en tant que récepteur de notifications.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifyConnection2, interface](inotifyconnection2-interface.md)
- [INotifySource2, interface](inotifysource2-interface.md)
- [INotifySink2, interface](inotifysink2-interface.md)
- [UnregisterNotifySource, méthode](inotifyconnection2-unregisternotifysource-method.md)
