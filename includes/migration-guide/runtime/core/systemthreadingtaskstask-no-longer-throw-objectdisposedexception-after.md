---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619992"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task ne lève plus d’exception ObjectDisposedException après la suppression de l’objet

#### <a name="details"></a>Détails

À l’exception de <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, les méthodes <xref:System.Threading.Tasks.Task?displayProperty=fullName> ne lèvent plus d’exception <xref:System.ObjectDisposedException?displayProperty=fullName> après la suppression de l’objet. Cette modification prend en charge l’utilisation des tâches mises en cache. Par exemple, une méthode peut retourner une tâche mise en cache pour représenter une opération déjà terminée au lieu d'allouer une nouvelle tâche. Cette opération était impossible dans les versions précédentes du .NET Framework, car tout consommateur de la tâche pouvait la supprimer, ce qui la rendait inutilisable.

#### <a name="suggestion"></a>Suggestion

N’oubliez pas que les méthodes Task peuvent ne plus lever d’exceptions <xref:System.ObjectDisposedException?displayProperty=fullName> quand l’objet est supprimé. Si une application dépendait de cette exception pour savoir qu’une tâche avait été supprimée, elle doit être mise à jour pour vérifier explicitement l’état de la tâche à l’aide de <xref:System.Threading.Tasks.Task.Status>.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|
