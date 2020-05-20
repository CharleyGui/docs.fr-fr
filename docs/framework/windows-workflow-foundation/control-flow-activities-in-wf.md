---
title: Activités de flux de contrôle dans WF
description: Cet article résume les activités .NET Framework 4.6.1 pour contrôler le flux d’exécution au sein d’un Workflow.
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: 18ff982d3f215e3fd46108eb2411f3d1a5ab9745
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420069"
---
# <a name="control-flow-activities-in-wf"></a>Activités de flux de contrôle dans WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] fournit plusieurs activités pour le contrôle de flux d'exécution dans un workflow. Certaines de ces activités (telles que `Switch` et `If` ) implémentent des structures de contrôle de Flow similaires à celles des environnements de programmation tels que Visual C#, tandis que d’autres (comme `Pick` ) modélisent de nouvelles structures de programmation.  
  
 Notez que lorsque les activités telles que les activités `Parallel` et `ParallelForEach` planifient plusieurs activités enfants pour qu'elles s'exécutent simultanément, seul un thread unique est utilisé pour un workflow. Chaque activité enfant de ces activités s'exécute séquentiellement et les activités consécutives ne s'exécutent pas tant que d'anciennes activités ne soient terminées ou ne deviennent inactives. Par conséquent, ces activités sont très utiles pour les applications dans lesquelles plusieurs activités potentielles de blocage doivent s'exécuter de façon entrelacée. Si aucune des activités enfants de ces activités n'est inactive, une activité `Parallel` s'exécute juste comme une activité `Sequence`, et une activité `ParallelForEach` s'exécute juste comme une activité `ForEach`. Si, toutefois, des activités asynchrones (telles que des activités qui dérivent de <xref:System.Activities.AsyncCodeActivity>) ou des activités de messagerie sont utilisées, le contrôle passe à la branche suivante alors que l’activité enfant attend son message à accepter ou son travail asynchrone à exécuter.  
  
## <a name="flow-control-activities"></a>Activités de contrôle de flux  
  
|Activité|Description|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Exécute une fois les activités contenues et continue de le faire jusqu'à ce qu'une condition soit `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Exécute une instruction incorporée en séquence pour chaque élément d’une collection. <xref:System.Activities.Statements.ForEach%601> est semblable au mot clé `foreach`, mais est implémenté comme une activité et non comme une instruction de langage.|  
|<xref:System.Activities.Statements.If>|Exécute des activités contenues si une condition est `true`, et peut exécuter des activités contenues dans la propriété <xref:System.Activities.Statements.If.Else%2A> si la condition est `false`.|  
|<xref:System.Activities.Statements.Parallel>|Exécute des activités contenues en parallèle.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Exécute une instruction incorporée en parallèle pour chaque élément d'une collection.|  
|<xref:System.Activities.Statements.Pick>|Fournit une modélisation de flux de contrôle reposant sur des événements.|  
|<xref:System.Activities.Statements.PickBranch>|Représente un chemin d'exécution potentiel dans une activité <xref:System.Activities.Statements.Pick>.|  
|<xref:System.Activities.Statements.Sequence>|Exécute des activités contenues dans l'ordre.|  
|<xref:System.Activities.Statements.Switch%601>|Choisit de traiter une activité parmi un certain nombre d'activités, en fonction de la valeur de l'expression donnée.|  
|<xref:System.Activities.Statements.While>|Exécute des activités contenues tant qu'une condition est `true`.|
