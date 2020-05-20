---
title: INotifySink2::OnSyncCallExit, méthode
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: f81ef3f5959e279b3fbbd94d6c5e8a2d86a38e7f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442018"
---
# <a name="inotifysink2onsynccallexit-method"></a>INotifySink2::OnSyncCallExit, méthode
Est appelé lors de la sortie d’un appel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `in_CallID`  
 dans ID de l’appel en cours de sortie. Consultez [call_id structure](call-id-structure.md).  
  
 `out_ppBuffer`  
 à Mémoire tampon d’appel.  
  
 `out_pBufferSize`  
 à Taille de la mémoire tampon d’appel, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifySink2, interface](inotifysink2-interface.md)
- [INotifySource2, interface](inotifysource2-interface.md)
- [INotifyConnection2, interface](inotifyconnection2-interface.md)
