---
title: INotifySink2::OnSyncCallOut, méthode
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: e7b3d5bd53bb9e4d6b897bfbf109c1f7307224cd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442507"
---
# <a name="inotifysink2onsynccallout-method"></a>INotifySink2::OnSyncCallOut, méthode
Est appelé quand un appel est en sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `in_CallID`  
 dans ID de l’appel sortant. Consultez [call_id structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `out_ppBuffer`  
 à Mémoire tampon d’appel.  
  
 `out_pBufferSize`  
 à Taille de la mémoire tampon d’appel, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifySink2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [INotifySource2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
