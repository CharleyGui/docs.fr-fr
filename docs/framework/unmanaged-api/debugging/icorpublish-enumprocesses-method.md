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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1804a14c1197148afbffb5ec2cb4f29cb9ff019e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774553"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses, méthode
Obtient un énumérateur pour les processus gérés en cours d’exécution sur cet ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `Type`  
 Une valeur de la [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) énumération qui spécifie le type de processus à récupérer. Dans la version actuelle, seul COR_PUB_MANAGEDONLY est valide.  
  
 `ppIEnum`  
 Un pointeur vers l’adresse d’un [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance qui est l’énumérateur des processus.  
  
## <a name="remarks"></a>Notes  
 Collection de l’énumérateur de processus est basée sur un instantané des processus en cours d’exécution lorsque le `EnumProcesses` méthode est appelée. L’énumérateur n’inclut pas tous les processus qui termine avant ou démarrent après `EnumProcesses` est appelée.  
  
 Le `EnumProcesses` méthode peut être appelée plusieurs fois sur ce [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance pour créer une nouvelle collection à jour de processus. Les collections existantes ne seront pas affectées par les appels ultérieurs de le `EnumProcesses` (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub.idl, CorPub.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublish, interface](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
