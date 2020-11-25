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
ms.openlocfilehash: a45f613b7547e2e80abdbd8ac85cb0b2b6a499e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716887"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess, méthode

Obtient une instance de [ICorPublishProcess](icorpublishprocess-interface.md) qui représente le processus avec l’identificateur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pid`  
 dans Identificateur du processus.  
  
 `ppProcess`  
 à Pointeur vers l’adresse d’une `ICorPublishProcess` instance de qui représente le processus.  
  
## <a name="remarks"></a>Remarques  

 `GetProcess` échoue si le processus n’existe pas ou s’il ne s’agit pas d’un processus managé pouvant être débogué par l’utilisateur actuel.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublish, interface](icorpublish-interface.md)
