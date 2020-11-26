---
title: Création d'activités asynchrones dans WF
description: Découvrez comment créer des activités asynchrones personnalisées à l’aide de AsyncCodeActivity, ce qui permet aux activités dérivées d’implémenter une logique d’exécution asynchrone.
ms.date: 03/30/2017
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
ms.openlocfilehash: a03fbde1ff27084cc36dffc3a1912220d9bbca7e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242082"
---
# <a name="creating-asynchronous-activities-in-wf"></a>Création d'activités asynchrones dans WF

<xref:System.Activities.AsyncCodeActivity> fournit aux auteurs d'activités une classe de base qui permet aux activités dérivées d'implémenter la logique d'exécution asynchrone. Les activités personnalisées peuvent ainsi effectuer un travail asynchrone sans maintenir le thread du service de planification de workflow. Elles peuvent également bloquer toute activité qui peut s'exécuter en parallèle. Cette rubrique fournit une vue d'ensemble de la méthode de création des activités asynchrones personnalisées à l'aide de l'objet <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="using-asynccodeactivity"></a>Utilisation d'AsyncCodeActivity  

 L'objet <xref:System.Activities?displayProperty=nameWithType> fournit aux auteurs d'activités personnalisées différentes classes de base pour différentes spécifications de création d'activité. Chacune possède une sémantique particulière et fournit à un auteur de workflow (et au runtime d'activité) un contrat correspondant. Une activité basée sur l'objet <xref:System.Activities.AsyncCodeActivity> est une activité qui effectue le travail de façon asynchrone par rapport au thread du service de planification et dont la logique d'exécution est exprimée en code managé. Du fait qu'il devienne asynchrone, un objet <xref:System.Activities.AsyncCodeActivity> peut induire un point inactif lors de l'exécution. En raison de la nature volatile du travail asynchrone, un objet <xref:System.Activities.AsyncCodeActivity> crée toujours un bloc sans persistance pour la durée d'exécution de l'activité. Cela empêche le runtime du workflow de rendre persistante l'instance de workflow au milieu du travail asynchrone, et empêche également l'instance de workflow de se décharger lors de l'exécution du code asynchrone.  
  
### <a name="asynccodeactivity-methods"></a>Méthodes AsyncCodeActivity  

 Les activités qui dérivent de l'objet <xref:System.Activities.AsyncCodeActivity> peuvent créer la logique d'exécution asynchrone en substituant le code personnalisé aux méthodes <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> et <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Une fois appelées par le runtime, un <xref:System.Activities.AsyncCodeActivityContext> est passé à ces méthodes. <xref:System.Activities.AsyncCodeActivityContext>permet à l’auteur de l’activité de fournir un état partagé <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> dans la propriété du contexte <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> . Dans l'exemple suivant, une activité `GenerateRandom` génère un nombre aléatoire de façon asynchrone.  
  
 [!code-csharp[CFX_ActivityExample#8](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 L'exemple d'activité précédent dérive d'<xref:System.Activities.AsyncCodeActivity%601>, et comprend un `OutArgument<int>` élevé nommé `Result`. La valeur retournée par la méthode `GetRandom` est extraite et retournée par la substitution <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> et cette valeur est définie comme valeur `Result`. Les activités asynchrones qui ne retournent pas de résultat doivent dériver d'<xref:System.Activities.AsyncCodeActivity>. Dans l'exemple suivant, une activité `DisplayRandom` qui dérive d'<xref:System.Activities.AsyncCodeActivity> est définie. Cette activité est semblable à l'activité `GetRandom`, mais au lieu de retourner un résultat, elle affiche un message sur la console.  
  
 [!code-csharp[CFX_ActivityExample#11](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Notez qu'étant donné qu'il n'y a pas de valeur de retour, `DisplayRandom` utilise un <xref:System.Action> au lieu d'un <xref:System.Func%602> pour appeler son délégué, et que le délégué ne retourne aucune valeur.  
  
 <xref:System.Activities.AsyncCodeActivity> fournit également une substitution <xref:System.Activities.AsyncCodeActivity.Cancel%2A>. Tandis que <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> et <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> sont des substitutions obligatoires, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> est facultative et peut être substituée de sorte que l'activité puisse nettoyer son état asynchrone en attente lors de son annulation ou de son abandon. Si le nettoyage est possible et `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` est `true`, l'activité doit appeler la méthode <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>. Toute exception levée à partir de cette méthode est critique pour l'instance de workflow.  
  
 [!code-csharp[CFX_ActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Appel de méthodes asynchrones sur une classe  

 La plupart des classes de la .NET Framework fournissent des fonctionnalités asynchrones, et cette fonctionnalité peut être appelée de manière asynchrone à l’aide d’une <xref:System.Activities.AsyncCodeActivity> activité basée sur. Dans l’exemple suivant, une activité créée de façon asynchrone crée un fichier à l’aide de la <xref:System.IO.FileStream> classe.  
  
 [!code-csharp[CFX_ActivityExample#12](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>Partager l'état entre les méthodes BeginExecute et EndExecute  

 Dans l'exemple précédent, l'objet <xref:System.IO.FileStream> créé dans <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> était accessible dans le <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Cela s'avère possible, car la variable `file` a été passée dans la propriété <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> dans <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Il s'agit de la méthode correcte pour partager l'état entre <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> et <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Il est incorrect d'utiliser une variable membre dans la classe dérivée (`FileWriter` dans ce cas) pour partager l'état entre <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> et <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>, car l'objet activité peut être référencé par plusieurs instances d'activité. Toute tentative d'utilisation d'une variable membre pour partager l'état peut générer des valeurs d'un <xref:System.Activities.ActivityInstance> qui remplacent ou consomment des valeurs d'un autre <xref:System.Activities.ActivityInstance>.  
  
### <a name="accessing-argument-values"></a>Accès aux valeurs des arguments  

 L’environnement d’un objet <xref:System.Activities.AsyncCodeActivity> se compose d’arguments définis sur l’activité. Ces arguments sont accessibles à partir des <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> substitutions à l’aide du <xref:System.Activities.AsyncCodeActivityContext> paramètre. Il est impossible d’accéder aux arguments dans le délégué, mais les valeurs d’argument ou toutes autres données peuvent être passées dans celui-ci à l’aide de ses paramètres. L'exemple suivant consiste à définir une activité générant un nombre aléatoire qui obtient la limite supérieure inclusive de son argument `Max`. La valeur de l’argument est passée dans le code asynchrone lors de l’appel du délégué.  
  
 [!code-csharp[CFX_ActivityExample#9](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Planifier des actions ou des activités enfants à l'aide d'AsyncCodeActivity  

 Les activités personnalisées dérivées <xref:System.Activities.AsyncCodeActivity> fournissent une méthode pour effectuer des tâches de façon asynchrone concernant le thread de workflow, mais ne permettent pas de planifier des activités enfants ou des actions. Toutefois, le comportement asynchrone peut être incorporé à la planification des activités enfants via la composition. Une activité asynchrone peut être créée, puis être composée d'une activité dérivée <xref:System.Activities.Activity> ou <xref:System.Activities.NativeActivity> pour fournir le comportement asynchrone et planifier des activités ou actions enfants. Par exemple, une activité peut être créée qui dérive de <xref:System.Activities.Activity>, et qui a comme implémentation un <xref:System.Activities.Statements.Sequence> contenant l'activité asynchrone, ainsi que les autres activités qui implémentent la logique de l'activité. Pour obtenir plus d’exemples de composition d’activités à l’aide de <xref:System.Activities.Activity> et de <xref:System.Activities.NativeActivity> , consultez [procédure : créer une activité](how-to-create-an-activity.md) et des [options de création d’activité](activity-authoring-options-in-wf.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Action>
- <xref:System.Func%602>
