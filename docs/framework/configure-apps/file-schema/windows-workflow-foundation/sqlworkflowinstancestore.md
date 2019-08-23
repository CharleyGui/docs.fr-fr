---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 7a6f9fb5b2b98d2951343b5a529507b3fcd88dc8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947525"
---
# <a name="sqlworkflowinstancestore"></a>\<sqlWorkflowInstanceStore>
Comportement de service qui vous permet de configurer la <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> fonctionnalité, qui prend en charge la persistance des informations d’État pour les instances de service de workflow dans une base de données SQL Server 2005 ou SQL Server 2008. Pour plus d’informations sur cette fonctionnalité, consultez [magasin d’instances de workflow SQL](../../../windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<> de comportement  
\<sqlWorkflowInstanceStore>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String" 
                                hostLockRenewalPeriod="TimeSpan" 
                                instanceCompletionAction="DeleteNothing/DeleteAll" 
                                instanceEncodingAction="None/GZip" 
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|connectionString|Chaîne qui contient une chaîne de connexion utilisée pour se connecter à une base de données de persistance sous-jacente.|  
|connectionStringName|Chaîne qui contient une chaîne de connexion nommée au serveur de base de données. «DefaultConnectionString» est un exemple de chaîne de connexion nommée.|  
|hostLockRenewalPeriod|Valeur Timespan qui spécifie la période pendant laquelle l'hôte doit renouveler le verrou sur une instance. Si l'hôte ne renouvelle pas le verrou pendant la période spécifiée, l'instance est déverrouillée et peut être choisie par un autre hôte.<br /><br /> Le déchargement d'un flux de travail implique qu'il soit également rendu persistant. Si cet attribut a la valeur zéro, l’instance de workflow est persistante et déchargée immédiatement après que le flux de travail devient inactif. L’affectation de la valeur TimeSpan. MaxValue à cet attribut désactive efficacement l’opération de déchargement. Les instances de flux de travail inactives ne sont jamais déchargées.|  
|instanceCompletionAction|Valeur indiquant si les données de l'instance du flux de travail sont conservées dans le magasin de persistance une fois l'instance du flux de travail terminée ou si elles sont supprimées à ce stade. Cette valeur est de type <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Les actions énumérées consistent en la suppression ou la non-suppression des données de l'instance du magasin de persistance, lorsque l'instance a terminé son opération.<br /><br /> La conservation des instances après leur achèvement engendre une croissance rapide de la base de données de persistance, ce qui en affecte les performances. Vous devez configurer une stratégie de vidage de la base de données pour supprimer régulièrement ces enregistrements afin de veiller à ce que les performances de la base de données soient à un niveau satisfaisant pour vos besoins.|  
|instanceEncodingOption|Valeur facultative qui indique si les informations d'état de l'instance sont compressées à l'aide de l'algorithme Gzip avant l'enregistrement des informations dans le magasin de persistance. Cette valeur est de type <xref:System.Activities.DurableInstancing.InstanceEncodingOption>. Les valeurs possibles de cette propriété <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>sont, qui ne spécifient aucune <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>compression, et, qui spécifie que les données d’instance sont compressées et utilise l’algorithme gzip.|  
|instanceLockedExceptionAction|Valeur qui spécifie l'action qui se produit en réponse à une exception levée lorsque l'hôte essaie de verrouiller une instance déjà verrouillée par un autre hôte. Cette valeur est de type <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Les options autorisées pour ce champ sont les suivantes: Aucune, nouvelle tentative de base et nouvelle tentative agressive. La valeur par défaut est Aucun. La liste suivante fournit les descriptions de ces trois options :<br /><br /> - Aucun. L'hôte de service n'essaie pas de verrouiller l'instance et passe l'objet <xref:System.Runtime.DurableInstancing.InstanceLockedException> à l'appelant.<br />-Nouvelle tentative de base. L'hôte de service réessaie de verrouiller l'instance avec un intervalle de tentative linéaire et passe l'exception à l'appelant à la fin de la séquence.<br />-Nouvelle tentative agressive. L'hôte de service réessaie de verrouiller l'instance avec un délai exponentiellement croissant et passe l'objet <xref:System.Runtime.DurableInstancing.InstanceLockedException> à l'appelant à la fin de la séquence.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<> de comportement \<de la > serviceBehaviors](behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [Magasin d’instances de workflow SQL](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
