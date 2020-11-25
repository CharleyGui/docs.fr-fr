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
ms.openlocfilehash: 8e88d90e3291d21888fae7aa162f84b6377658c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730017"
---
# <a name="mdainfo-structure"></a>MDAInfo, structure

Fournit des détails sur l' `Event_MDAFired` événement, qui déclenche la création d’un Assistant Débogage managé (MDA).  
  
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
|`lpMDACaption`|Titre de l’Assistant Débogage managé actuel. Le titre décrit le type d’échec qui a déclenché l' `Event_MDAFired` événement.|  
|`lpMDAMessage`|Message de sortie fourni par l’Assistant Débogage managé actuel.|  
  
## <a name="remarks"></a>Remarques  

 Les Assistants Débogage managé (MDA) sont des aides au débogage qui fonctionnent conjointement avec le common language runtime (CLR) pour effectuer des tâches telles que l’identification de conditions non valides dans le moteur d’exécution du runtime ou le vidage d’informations supplémentaires sur l’état du moteur. Les MDA génèrent des messages XML sur les événements qui, sinon, sont difficiles à intercepter. Ils sont particulièrement utiles pour déboguer des transitions entre du code managé et du code non managé.  
  
 Le Runtime effectue les étapes suivantes lorsqu’un événement qui déclenche la création d’un Assistant Débogage managé est déclenché :  
  
- Si l’hôte n’a pas inscrit une instance [IActionOnCLREvent](iactiononclrevent-interface.md) en appelant [ICLROnEventManager :: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) pour être averti d’un `Event_MDAFired` événement, le runtime continue avec son comportement par défaut, non hébergé.  
  
- Si l’hôte a inscrit un gestionnaire pour cet événement, le runtime vérifie si un débogueur est attaché au processus. Si c’est le cas, le runtime s’arrête dans le débogueur. Quand le débogueur continue, il appelle l’hôte. Si aucun débogueur n’est attaché, le runtime appelle `IActionOnCLREvent::OnEvent` et passe un pointeur vers une `MDAInfo` instance en tant que `data` paramètre.  
  
 L’hôte peut choisir d’activer les MDA et de recevoir une notification lorsqu’un Assistant Débogage managé est activé. Cela donne à l’hôte la possibilité de substituer le comportement par défaut et d’abandonner le thread managé qui a déclenché l’événement, afin de l’empêcher de corrompre l’état du processus. Pour plus d’informations sur l’utilisation des MDA, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d'hébergement](hosting-structures.md)
- [Diagnostic d'erreurs avec les Assistants de débogage managés](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
