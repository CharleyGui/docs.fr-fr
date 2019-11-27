---
title: INotifySink2::OnSyncCallEnter, méthode
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
ms.openlocfilehash: 69c7e6c465de5b8185a86b3de6e5c29f902a1d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440870"
---
# <a name="inotifysink2onsynccallenter-method"></a>INotifySink2::OnSyncCallEnter, méthode
Est appelé lors de l’entrée d’un appel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `in_CallID`  
 dans ID de l’appel entré. Consultez [call_id structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `in_pBuffer`  
 dans Mémoire tampon d’appel.  
  
 `in_BufferSize`  
 dans Taille de la mémoire tampon d’appel, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifySink2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [INotifySource2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
