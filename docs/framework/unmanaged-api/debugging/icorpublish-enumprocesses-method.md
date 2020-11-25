---
title: ICorPublish::EnumProcesses, méthode
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 297f672097dd6561a971608f368369c623532907
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716913"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses, méthode

Obtient un énumérateur pour les processus managés qui s’exécutent sur cet ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `Type`  
 Valeur de l’énumération [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) qui spécifie le type de processus à récupérer. Dans la version actuelle, seul COR_PUB_MANAGEDONLY est valide.  
  
 `ppIEnum`  
 Pointeur vers l’adresse d’une instance [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) qui est l’énumérateur des processus.  
  
## <a name="remarks"></a>Remarques  

 La collection de processus de l’énumérateur est basée sur un instantané des processus en cours d’exécution lorsque la `EnumProcesses` méthode est appelée. L’énumérateur n’inclut pas les processus qui se terminent avant ou commençant après l' `EnumProcesses` appel de.  
  
 La `EnumProcesses` méthode peut être appelée plusieurs fois sur cette instance [ICorPublish](icorpublish-interface.md) pour créer une nouvelle collection à jour de processus. Les collections existantes ne seront pas affectées par les appels ultérieurs de la `EnumProcesses` méthode.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublish, interface](icorpublish-interface.md)
