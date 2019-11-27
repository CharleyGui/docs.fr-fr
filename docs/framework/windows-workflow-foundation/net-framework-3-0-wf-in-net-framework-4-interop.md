---
title: Utilisation d'activités WF de .NET Framework 3.0 dans .NET Framework 4 avec l'activité d'interopérabilité
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: de0a0474f0a996ce8c781064f56c03b483ca1bb9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283195"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Utilisation d'activités WF de .NET Framework 3.0 dans .NET Framework 4 avec l'activité d'interopérabilité
L’activité <xref:System.Activities.Statements.Interop> est une activité [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (WF 4,5) qui encapsule une activité .NET Framework 3,5 (WF 3,5) au sein d’un flux de travail de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. L’activité WF 3 peut être une activité de feuille unique ou une arborescence entière d’activités. L’exécution (y compris l’annulation et la gestion des exceptions) et la persistance de l’activité .NET Framework 3,5 se produisent dans le contexte de l’instance de workflow [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] en cours d’exécution.  
  
> [!NOTE]
> L’activité <xref:System.Activities.Statements.Interop> n’apparaît pas dans la boîte à outils du concepteur de flux de travail, sauf si le paramètre **Framework cible** du projet du flux de travail est défini sur **.NET Framework 4,5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Critères pour l'Utilisation d'une Activité WF 3 avec une Activité d'interopérabilité  
 Pour qu'une activité WF 3 s'exécute avec succès dans une activité <xref:System.Activities.Statements.Interop>, les critères suivants doivent être remplis :  
  
- L'activité WF 3 doit dériver de <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
- L'activité WF 3 doit être déclarée comme `public` et ne peut pas être `abstract`.  
  
- L’activité WF 3 doit avoir un constructeur sans paramètre public.  
  
- En raison des limitations dans les types d'interface pris en charge par l'activité <xref:System.Activities.Statements.Interop>, <xref:System.Workflow.Activities.HandleExternalEventActivity> et <xref:System.Workflow.Activities.CallExternalMethodActivity> ne peuvent pas être utilisés directement, mais des activités dérivatives créées à l'aide de l'outil WCA.exe (Workflow Communication Activity) peuvent être utilisées. Pour plus d’informations, consultez [Windows Workflow Foundation Tools](https://go.microsoft.com/fwlink/?LinkId=178889) .  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Configuration d'une Activité WF 3 Dans une Activité d'interopérabilité  
 Pour configurer et passer des données dans et hors d'une activité WF 3, sur les limites d'interopérabilité, les propriétés de l'activité WF 3 et les propriétés de métadonnées sont exposées par l'activité <xref:System.Activities.Statements.Interop>. Les propriétés de métadonnées de l'activité WF 3 (tel que <xref:System.Workflow.ComponentModel.Activity.Name%2A>) sont exposées via la collection <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A>. C'est une collection de paires nom-valeur utilisée pour définir les valeurs pour les propriétés de métadonnées de l'activité WF 3. Une propriété de métadonnées est une propriété secondée par une propriété de dépendance pour laquelle l'indicateur <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> est défini.  
  
 Les propriétés de l’activité WF 3 sont exposées via la collection <xref:System.Activities.Statements.Interop.ActivityProperties%2A>. C’est un jeu de paires nom-valeur, où chaque valeur est un objet <xref:System.Activities.Argument>, utilisé pour définir les arguments pour les propriétés de l’activité WF 3. Étant donné que la direction d’une propriété d’activité WF 3 ne peut pas être déduite, chaque propriété est exposée en tant que paire d' <xref:System.Activities.OutArgument> de /<xref:System.Activities.InArgument>. Selon l'utilisation de l'activité de la propriété, vous pouvez fournir une entrée <xref:System.Activities.InArgument>, une entrée <xref:System.Activities.OutArgument>, ou les deux à la fois. Le nom attendu de l’entrée <xref:System.Activities.InArgument> de la collection correspond au nom de la propriété comme défini dans l’activité WF 3. Le nom attendu de l’entrée <xref:System.Activities.OutArgument> dans la collection est une concaténation du nom de la propriété et de la chaîne « out ».  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Limitations de l'utilisation d'une activité WF 3 dans une activité d'interopérabilité  
 Les activités fournies par le système WF 3 ne peuvent pas être directement encapsulées dans une activité <xref:System.Activities.Statements.Interop>. Pour certaines activités WF 3, telles que <xref:System.Workflow.Activities.DelayActivity>, cela s'explique par la présence d'une activité WF 4.5 analogue. Pour d'autres, les fonctionnalités de cette activité ne sont pas prises en charge. De nombreuses activités fournies par le système WF 3 peuvent être utilisées dans les flux de travail encapsulés par l'activité <xref:System.Activities.Statements.Interop>, soumise aux restrictions suivantes :  
  
1. <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> ne peuvent pas être utilisés dans une activité <xref:System.Activities.Statements.Interop>.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>et <xref:System.Workflow.Activities.WebServiceFaultActivity> ne peuvent pas être utilisés dans une activité <xref:System.Activities.Statements.Interop>.  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity> ne peut pas être utilisé dans une activité de <xref:System.Activities.Statements.Interop>.  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity> ne peut pas être utilisé dans une activité de <xref:System.Activities.Statements.Interop>.  
  
5. Les activités liées à la compensation ne peuvent pas être utilisées dans une activité <xref:System.Activities.Statements.Interop>.  
  
 Il y a également des caractéristiques comportementales à comprendre concernant l'utilisation d'activités WF 3 dans l'activité <xref:System.Activities.Statements.Interop> :  
  
1. Les activités WF 3 contenues dans une activité <xref:System.Activities.Statements.Interop> sont initialisées lorsque l'activité <xref:System.Activities.Statements.Interop> est exécutée. Dans WF 4.5 il n'y a pas de phase d'initialisation pour une instance de workflow avant son exécution.  
  
2. L’exécution du WF 4.5 ne contrôle pas l’état de l’instance de workflow lorsqu’une transaction commence, quel que soit le point de contrôle à partir duquel la transaction commence (dans ou en dehors d’une activité <xref:System.Activities.Statements.Interop> ).  
  
3. Les enregistrements de suivi WF 3 pour les activités au sein d'une activité <xref:System.Activities.Statements.Interop> sont fournis aux participants de suivi WF 4.5 comme objets <xref:System.Activities.Tracking.InteropTrackingRecord>. <xref:System.Activities.Tracking.InteropTrackingRecord> est une dérivée de <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4. Una activité personnalisée WF 3 peut accéder aux données à l'aide de files d'attente de workflow dans l'environnement d'interopération de la même façon qu'au sein de l'exécution du workflow WF 3. Aucune modification du code d'activité personnalisé n'est obligatoire. Sur l'hôte, les données sont mises en file d'attente dans un workflow WF 3 en reprenant un <xref:System.Activities.Bookmark>. Le nom du signet correspond à la chaîne du nom de la file d'attente du flux de travail <xref:System.IComparable>.
