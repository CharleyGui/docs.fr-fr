---
title: Propriétés et Arguments
ms.date: 03/30/2017
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
ms.openlocfilehash: 2ed443b962e6cccb8a0f670f1dbd744bfa8ed354
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245924"
---
# <a name="properties-vs-arguments"></a>Propriétés et Arguments

Plusieurs options sont disponibles pour passer des données dans une activité. En plus d'utiliser <xref:System.Activities.InArgument>, il est également possible de développer des activités qui reçoivent des données à l'aide des propriétés CLR standard ou des propriétés <xref:System.Activities.ActivityAction> publiques. Cette rubrique explique comment sélectionner le type de méthode approprié.  
  
## <a name="using-clr-properties"></a>Utilisation des propriétés CLR  

 Lors du passage des données dans une activité, les propriétés CLR (c'est-à-dire, les méthodes publiques qui utilisent des routines Get et Set pour exposer des données) sont l'option qui a le plus de restrictions. La valeur d'un paramètre passé dans une propriété CLR doit être connue lorsque la solution est compilée ; cette valeur sera la même pour chaque instance du workflow. Ainsi, une valeur passée dans une propriété CLR est semblable à une constante définie dans le code ; cette valeur ne peut pas changer pendant la durée de vie de l'activité, et ne peut pas être modifiée pour plusieurs instances de l'activité. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> est un exemple de propriété CLR exposée par une activité ; le nom de méthode que l'activité appelle ne peut pas être modifié en fonction de conditions d'exécution, et sera identique pour toutes les instances de l'activité.  
  
## <a name="using-arguments"></a>Utilisation des arguments  

 Les arguments doivent être utilisés lorsque les données ne sont évaluées qu’une fois pendant la durée de vie de l’activité ; c’est-à-dire que sa valeur ne changera pas pendant la durée de vie de l’activité, mais la valeur peut être différente pour différentes instances de l’activité. <xref:System.Activities.Statements.If.Condition%2A> est un exemple de valeur qui est évaluée une seule fois ; par conséquent, elle est définie comme argument. <xref:System.Activities.Statements.WriteLine.Text%2A> est un autre exemple d'une méthode qui doit être définie comme argument, car elle n'est évaluée qu'une seule fois pendant l'exécution de l'activité, mais elle peut être différente pour plusieurs instances de l'activité.  
  
## <a name="using-activityaction"></a>Utilisation d'ActivityAction  

 Lorsque des données doivent être évaluées plusieurs fois au cours de la durée de vie de l'exécution d'une activité, une <xref:System.Activities.ActivityAction> doit être utilisée. Par exemple, la propriété <xref:System.Activities.Statements.While.Condition%2A> est évaluée pour chaque itération de la boucle <xref:System.Activities.Statements.While> . Si un <xref:System.Activities.InArgument> était utilisé dans ce but, la boucle ne se terminerait jamais, puisque l’argument ne serait pas réévalué pour chaque itération et retournerait toujours le même résultat.
