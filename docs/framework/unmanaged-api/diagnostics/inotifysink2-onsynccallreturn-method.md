---
title: INotifySink2::OnSyncCallReturn, méthode
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
ms.openlocfilehash: fe2db3df688f91ec6e1aadd8cc3bb43726e5c30f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719955"
---
# <a name="inotifysink2onsynccallreturn-method"></a>INotifySink2::OnSyncCallReturn, méthode

Est appelé quand un appel est retourné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `in_CallID`  
 dans ID de l’appel retourné par. Consultez [call_id structure](call-id-structure.md).  
  
 `in_pBuffer`  
 dans Mémoire tampon d’appel.  
  
 `in_BufferSize`  
 dans Taille de la mémoire tampon d’appel, en octets.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifySink2, interface](inotifysink2-interface.md)
- [INotifySource2, interface](inotifysource2-interface.md)
- [INotifyConnection2, interface](inotifyconnection2-interface.md)
