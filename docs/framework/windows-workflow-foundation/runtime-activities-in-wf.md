---
title: Activités d'exécution dans WF
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: b0472c669d69d9397843a004bee1bb2c15e139c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245697"
---
# <a name="runtime-activities-in-wf"></a>Activités d'exécution dans WF

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] offre plusieurs activités fournies par le système pour l'accès aux fonctionnalités de l'exécution du workflow, telles que la persistance et l'arrêt de workflow.  
  
|Activité|Description|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|Demande de façon explicite à ce que le workflow rende son état persistant.|  
|<xref:System.Activities.Statements.TerminateWorkflow>|Arrête l'instance de workflow en cours d'exécution.|  
|<xref:System.Activities.Statements.NoPersistScope>|Activité de conteneur qui empêche la persistance des activités enfants.|
