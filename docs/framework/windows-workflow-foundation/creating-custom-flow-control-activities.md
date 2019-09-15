---
title: Création d'activités de contrôle de flux personnalisées
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: 8e7d4caad197631509fe80a5b5a08eff4d228c1c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989729"
---
# <a name="creating-custom-flow-control-activities"></a>Création d'activités de contrôle de flux personnalisées
Le .NET Framework contient diverses activités de contrôle de Flow qui fonctionnent de la même façon que des structures de programmation abstraites (telles que <xref:System.Activities.Statements.Flowchart>) ou des instructions de programmation standard (telles que <xref:System.Activities.Statements.If>). Cette rubrique décrit l’architecture de l’un des exemples de projets, [foreach non générique](./samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Création de la classe personnalisée  
 Étant donné que la classe ForEach non générique devra planifier des activités enfants, elle devra dériver de <xref:System.Activities.NativeActivity>, puisque les activités qui dérivent de <xref:System.Workflow.Activities.CodeActivity> ne disposent pas de cette fonctionnalité.  
  
```csharp  
public sealed class ForEach : NativeActivity  
{
}
```  
  
 La classe personnalisée requiert que plusieurs membres stockent les données utilisées par l'activité et fournissent des fonctionnalités permettant d'exécuter les activités enfants de l'activité. Ces membres incluent :  
  
- `valueEnumerator`: Non public <xref:System.Activities.Variable%601> de type <xref:System.Collections.IEnumerator> utilisé pour itérer au sein de la collection d’éléments. Ce membre est de type <xref:System.Activities.Variable%601>, car il est utilisé en interne dans l'activité, plutôt qu'un argument ou une propriété publique, qui serait utilisé si cet objet avait une origine externe à l'activité.  
  
- `OnChildComplete`: Propriété publique <xref:System.Activities.CompletionCallback> qui s’exécute lorsque chaque enfant termine l’exécution. Ce membre est défini comme une propriété CLR, puisque sa valeur ne changera pas dans les différentes instances de l'activité.  
  
- `Values`: Collection d’entrées utilisées pour les itérations de l’activité enfant. Ce membre est de type <xref:System.Activities.InArgument%601>, puisque l'origine des données est extérieure à l'activité, mais le contenu des collection n'est pas supposé changer au cours de l'exécution de l'activité. Si l’activité nécessitait que la fonctionnalité modifie le contenu de cette collection au cours de l’exécution de l’activité (pour ajouter ou supprimer des activités, par exemple), ce membre aurait été défini comme <xref:System.Activities.ActivityAction>, qui aurait ensuite été évalué lors de chaque accès, de sorte que l’activité ait accès aux modifications.  
  
- `Body`: Ce membre définit l’activité à exécuter pour chaque élément de la `Values` collection. Ce membre est défini comme <xref:System.Activities.ActivityAction> de sorte qu'il est évalué chaque fois qu'on y accède.  
  
- `Execute`: Cette méthode utilise les `InternalExecute`membres `OnForEachComplete`, et `GetStateAndExecute` non publics pour planifier l’exécution et assigner le gestionnaire d’achèvement de l’activité enfant définie dans le membre Body.  
  
- `CacheMetadata`: Ce membre fournit au runtime les informations dont il a besoin pour exécuter l’activité. Par défaut, la méthode `CacheMetadata` d'une activité indique au runtime tous les membres publics de l'activité, mais puisque cette activité utilise des membres privés pour certaines fonctionnalités, elle doit signaler leur existence au runtime de telle sorte qu'il en soit informé. Dans ce cas, la fonction `CacheMetadata` est remplacée afin que le membre `valueEnumerator` soit accessible. Ce membre crée également un argument pour les valeurs de l'activité afin qu'elles puissent être passées dans l'activité au cours de l'exécution.
