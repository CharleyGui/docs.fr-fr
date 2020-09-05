---
ms.openlocfilehash: 58dbb54d42d89b450134758072e3133ae4e6b13d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497929"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task ne lève plus d’exception ObjectDisposedException après la suppression de l’objet

#### <a name="details"></a>Détails

À l’exception de <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, les méthodes <xref:System.Threading.Tasks.Task?displayProperty=fullName> ne lèvent plus d’exception <xref:System.ObjectDisposedException?displayProperty=fullName> après la suppression de l’objet. Cette modification prend en charge l’utilisation des tâches mises en cache. Par exemple, une méthode peut retourner une tâche mise en cache pour représenter une opération déjà terminée au lieu d'allouer une nouvelle tâche. Cette opération était impossible dans les versions précédentes du .NET Framework, car tout consommateur de la tâche pouvait la supprimer, ce qui la rendait inutilisable.

#### <a name="suggestion"></a>Suggestion

N’oubliez pas que les méthodes Task peuvent ne plus lever d’exceptions <xref:System.ObjectDisposedException?displayProperty=fullName> quand l’objet est supprimé. Si une application dépendait de cette exception pour savoir qu’une tâche avait été supprimée, elle doit être mise à jour pour vérifier explicitement l’état de la tâche à l’aide de <xref:System.Threading.Tasks.Task.Status>.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
