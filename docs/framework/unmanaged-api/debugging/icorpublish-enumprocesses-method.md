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
ms.openlocfilehash: 5f0dd814ad5adfa1b0dd7199530a3f993634a548
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121793"
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
 Valeur de l’énumération [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) qui spécifie le type de processus à récupérer. Dans la version actuelle, seul COR_PUB_MANAGEDONLY est valide.  
  
 `ppIEnum`  
 Pointeur vers l’adresse d’une instance [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) qui est l’énumérateur des processus.  
  
## <a name="remarks"></a>Notes  
 La collection de processus de l’énumérateur est basée sur un instantané des processus en cours d’exécution lorsque la méthode `EnumProcesses` est appelée. L’énumérateur n’inclut pas les processus qui se terminent avant ou commencent après l’appel de `EnumProcesses`.  
  
 La méthode `EnumProcesses` peut être appelée plusieurs fois sur cette instance [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) pour créer une nouvelle collection à jour de processus. Les collections existantes ne seront pas affectées par les appels ultérieurs de la méthode `EnumProcesses`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublish, interface](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
