---
ms.openlocfilehash: ab2907b05bff409fed9a370d5cbebbf3d1575d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379689"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task ne lève plus d’exception ObjectDisposedException après la suppression de l’objet

|   |   |
|---|---|
|Détails|À l’exception de <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, les méthodes <xref:System.Threading.Tasks.Task?displayProperty=name> ne lèvent plus d’exception <xref:System.ObjectDisposedException?displayProperty=name> après la suppression de l’objet. Cette modification prend en charge l’utilisation des tâches mises en cache. Par exemple, une méthode peut retourner une tâche mise en cache pour représenter une opération déjà terminée au lieu d'allouer une nouvelle tâche. Cette opération était impossible dans les versions précédentes du .NET Framework, car tout consommateur de la tâche pouvait la supprimer, ce qui la rendait inutilisable.|
|Suggestion|N’oubliez pas que les méthodes Task peuvent ne plus lever d’exceptions <xref:System.ObjectDisposedException?displayProperty=name> quand l’objet est supprimé. Si une application dépendait de cette exception pour savoir qu’une tâche avait été supprimée, elle doit être mise à jour pour vérifier explicitement l’état de la tâche à l’aide de <xref:System.Threading.Tasks.Task.Status>.|
|Portée|Mineur|
|Version|4.5|
|Type|Runtime|
