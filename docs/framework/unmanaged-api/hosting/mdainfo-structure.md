---
title: MDAInfo, structure
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 198141545119976cb9107bc9c09b913572e266ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781125"
---
# <a name="mdainfo-structure"></a>MDAInfo, structure
Fournit des détails sur la `Event_MDAFired` événement qui déclenche la création d’un assistant débogage managé (MDA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`lpMDACaption`|Le titre de l’Assistant Débogage MANAGÉ actuel. Le titre décrit le genre d’échec qui a déclenché le `Event_MDAFired` événement.|  
|`lpMDAMessage`|Le message de sortie fourni par l’Assistant Débogage MANAGÉ actuel.|  
  
## <a name="remarks"></a>Notes  
 Les Assistants Débogage managé (MDA) sont outils de débogage qui fonctionnent conjointement avec le common language runtime (CLR) pour effectuer des tâches telles que l’identification des conditions non valides dans le moteur d’exécution ou d’immersion des informations supplémentaires sur l’état de la moteur. Les MDA génèrent des messages XML sur les événements qui sont difficiles à intercepter. Ils sont particulièrement utiles pour déboguer des transitions entre code managé et non managé.  
  
 Le runtime entreprend les actions suivantes lorsqu’un événement qui déclenche la création d’un Assistant Débogage MANAGÉ est déclenché :  
  
- Si l’hôte n’a pas inscrit un [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance en appelant [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) recevoir les notifications d’un `Event_MDAFired` événement, le runtime continue avec son comportement par défaut, non hébergé.  
  
- Si l’hôte a inscrit un gestionnaire pour cet événement, le runtime vérifie si un débogueur est attaché au processus. Dans le cas, le runtime arrête le débogueur. Lorsque le débogueur continue, il appelle l’hôte. Si aucun débogueur n’est attaché, le runtime appelle `IActionOnCLREvent::OnEvent` et passe un pointeur vers un `MDAInfo` instance en tant que le `data` paramètre.  
  
 L’hôte peut choisir d’activer les MDA et d’être notifié lorsqu’un MDA est activé. Cela donne la possibilité de substituer le comportement par défaut et d’abandonner le thread managé qui a déclenché l’événement, pour empêcher d’endommager l’état du processus de l’hôte. Pour plus d’informations sur l’utilisation des Assistants Débogage managé, consultez [diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
