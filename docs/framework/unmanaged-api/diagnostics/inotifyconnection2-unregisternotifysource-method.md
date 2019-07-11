---
title: INotifyConnection2::UnregisterNotifySource, méthode
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b8a8c3dbfb7b9949811025846484ab233ed3741
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776623"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a>INotifyConnection2::UnregisterNotifySource, méthode
Supprime un objet de source de notification spécifié à partir de la connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `in_pNotifySource`  
 [in] Objet de notification doit être annulée.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifyConnection2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySource2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifySink2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [RegisterNotifySource, méthode](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
