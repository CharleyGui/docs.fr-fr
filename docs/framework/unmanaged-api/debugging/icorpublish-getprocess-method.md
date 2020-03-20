---
title: ICorPublish::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: 46f047dbec7ff008873540806b76ffe7085086b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178421"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess, méthode
Obtient une instance [ICorPublishProcess](icorpublishprocess-interface.md) qui représente le processus avec l’identifiant spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pid`  
 [dans] L’identifiant du processus.  
  
 `ppProcess`  
 [out] Un pointeur à `ICorPublishProcess` l’adresse d’une instance qui représente le processus.  
  
## <a name="remarks"></a>Notes   
 `GetProcess`échoue si le processus n’existe pas, ou n’est pas un processus géré qui peut être débogé par l’utilisateur actuel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorPub.idl, CorPub.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublish, interface](icorpublish-interface.md)
