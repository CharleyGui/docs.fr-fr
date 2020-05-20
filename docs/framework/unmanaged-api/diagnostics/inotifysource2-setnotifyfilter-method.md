---
title: INotifySource2::SetNotifyFilter, méthode
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 7ba9f68e102696da107b5cb782c76cb55ed95ee6
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441966"
---
# <a name="inotifysource2setnotifyfilter-method"></a>INotifySource2::SetNotifyFilter, méthode
Affecte un filtre de notification à utiliser avec cette source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `in_NotifyFilter`  
 dans Combinaison d’opérations de bits des valeurs d’énumération [notify_filter](notify-filter-enumeration.md) qui identifient les rappels pour l’API du débogueur.  
  
 `in_pUserThreadFilter`  
 dans Pointeur vers une structure [USER_THREAD](user-thread-structure.md) qui identifie des threads pour l’API du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifySource2, interface](inotifysource2-interface.md)
- [INotifyConnection2, interface](inotifyconnection2-interface.md)
- [INotifySink2, interface](inotifysink2-interface.md)
