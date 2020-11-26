---
title: Meilleures pratiques de persistance
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: 950a5d5c742b7882db93d71f3e7f205009f2a863
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246145"
---
# <a name="persistence-best-practices"></a>Meilleures pratiques de persistance

Ce document traite des meilleures pratiques de conception et configuration de workflow associées à la persistance de workflow.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Conception et implémentation de workflow durables  

 En règle générale, les workflows fonctionnent pendant de courtes périodes entrelacées avec des périodes d'inactivité au cours desquelles ils sont attente d'un événement. Cet événement peut être un message ou un minuteur d'expiration. Pour pouvoir décharger l'instance de workflow lorsqu'elle devient inactive, l'hôte de service doit rendre cette instance persistante. Cela s’avère possible uniquement si l’instance de workflow n’est pas dans une zone de non-persistance (par exemple, en attente d’une transaction ou d’un rappel asynchrone). Pour permettre le déchargement d’une instance de workflow inactive, l’auteur du workflow doit utiliser les portées de transaction et les activités asynchrones uniquement pour des actions de courte durée. Plus particulièrement, il doit conserver les activités de délai dans ces zones de non-persistance aussi brèves que possible.  
  
 Un workflow peut uniquement être rendu persistant si tous les types de données qu'il utilise sont sérialisables. En outre, les types personnalisés utilisés dans les workflows persistants doivent être sérialisables avec <xref:System.Runtime.Serialization.NetDataContractSerializer> pour pouvoir être rendus persistants par <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Une instance de workflow ne peut pas être récupérée en cas d'échec de l'hôte ou de l'ordinateur, si elle n'est pas persistante. En règle générale, il est recommandé de rendre persistante une instance de workflow tôt dans son cycle de vie.  
  
 Si le workflow est occupé pendant longtemps, il est recommandé de rendre persistante l'instance de workflow régulièrement pendant toute cette période. Pour ce faire, vous pouvez ajouter des activités <xref:System.Activities.Statements.Persist> dans l'ensemble de la séquence des activités qui maintiennent l'instance de workflow occupée. De cette façon, un recyclage de domaine d'application, un échec de l'hôte ou de l'ordinateur n'entraîne pas la restauration au début de la période d'occupation. Soyez conscient que l'ajout d'activités <xref:System.Activities.Statements.Persist> à votre workflow peut provoquer une diminution des performances.  
  
 Windows Server AppFabric simplifie grandement la configuration et l'utilisation de la persistance. Pour plus d’informations, consultez [persistance de l’infrastructure d’applications Windows Server](/previous-versions/appfabric/ee677272(v=azure.10))  
  
## <a name="configuration-of-scalability-parameters"></a>Configuration des paramètres d'évolutivité  

 Les conditions requises en termes d'évolutivité et de performance déterminent la configuration des paramètres suivants :  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Ces paramètres doivent être définis comme suit, en fonction du scénario actuel.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Scénario : petit nombre d'instances de workflow qui nécessitent un temps de réponse optimal  

 Dans ce scénario, toutes les instances de workflow doivent rester chargées lorsqu'elles deviennent inactives. Affectez une valeur élevée à <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>. L'utilisation de ce paramètre empêche une instance de workflow de se déplacer entre les ordinateurs. Utilisez ce paramètre uniquement si une ou plusieurs des conditions suivantes sont remplies :  
  
- Une instance de workflow reçoit un seul message durant toute sa durée de vie.  
  
- Toutes les instances de workflow s'exécutent sur un seul ordinateur.  
  
- Tous les messages reçus par une instance de workflow sont reçus par le même ordinateur.  
  
 Utilisez des activités <xref:System.Activities.Statements.Persist> ou affectez la valeur 0 à <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> pour permettre la récupération de votre instance de workflow après un échec de l'ordinateur ou de l'hôte de service.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Scénario : les instances de workflow sont inactives pendant de longues périodes  

 Dans ce scénario, affectez la valeur 0 à la propriété <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> pour libérer les ressources dès que possible.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Scénario : les instances de workflow reçoivent plusieurs messages dans une courte période  

 Dans ce scénario, affectez la valeur 60 à la propriété <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> si ces messages sont reçus par le même ordinateur. Cela empêche une séquence rapide de déchargement et chargement d'une instance de workflow. Par ailleurs, l'instance n'est pas conservée trop longtemps en mémoire.  
  
 Affectez la valeur 0 à la propriété <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>, et BasicRetry ou AggressiveRetry à la propriété <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> si ces messages peuvent être reçus par des ordinateurs distincts. Cela permet à l'instance de workflow d'être chargée par un autre ordinateur.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Scénario : le workflow utilise des activités de délai avec des durées courtes  

 Dans ce scénario, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> vérifie régulièrement dans la base de données de persistance la présence d'instances qui doivent être chargées en raison d'une activité <xref:System.Activities.Statements.Delay> arrivée à expiration. Si <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> trouve un minuteur qui va expirer au cours de la fréquence d'interrogation suivante, le magasin d'instances de workflow SQL réduit la fréquence. L'interrogation suivante aura lieu dès que le minuteur aura expiré. De cette façon, le magasin d'instances de workflow SQL obtient une haute précision des minuteurs qui s'exécutent plus longtemps que la fréquence définie par la propriété <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Pour permettre le traitement en temps voulu de délais plus courts, l'instance de workflow doit rester en mémoire pendant au moins une fréquence d'interrogation.  
  
 Affectez la valeur 0 à la propriété <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> pour écrire le délai d'expiration dans la base de données de persistance.  
  
 Affectez une valeur supérieure ou égale à <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> à <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> pour conserver l'instance en mémoire pendant au moins une fréquence d'interrogation.  
  
 Il est déconseillé de réduire <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> car cela provoque une charge accrue sur la base de données de persistance. Chaque hôte de service qui utilise <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> interroge la base de données une seule fois par période de détection. Affecter un intervalle de temps trop court à <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> peut provoquer une diminution des performances du système si le nombre d'hôtes de service est trop élevé.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>Configuration du magasin d'instances de workflow SQL  

 Les paramètres de configuration du magasin d'instances de workflow SQL sont les suivants :  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Ce paramètre fait en sorte que <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> compresse l'état de l'instance de workflow. La compression réduit la quantité de données stockées dans la base de données de persistance et le trafic réseau si la base de données de persistance réside sur un serveur de base de données dédié. Si la compression est utilisée, des ressources de calcul sont nécessaires pour compresser et extraire l'état de l'instance. Dans la plupart des cas, la compression améliore les performances.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Ce paramètre fait en sorte que <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> conserve ou supprime les instances terminées. La conservation des instances terminées augmente la capacité de stockage requise de la base de données de persistance et la taille des tables, ce qui allonge les temps de recherche dans les tables. Sauf si les instances terminées sont nécessaires pour le débogage ou l'audit, il est préférable de faire en sorte que <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> supprime ces instances. Les instances supprimées ne doivent être conservées que si l'utilisateur établit un processus permettant éventuellement de les supprimer. Notez que les clés de corrélation ne peuvent pas être réutilisées tant que l'instance de workflow terminée réside dans le magasin d'instances.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Ce paramètre définit l'intervalle maximal dans lequel <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> vérifie dans la base de données de persistance la présence d'instances qui doivent être chargées si une activité <xref:System.Activities.Statements.Delay> arrive à expiration. Si <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> trouve un minuteur qui va expirer au cours de la fréquence d'interrogation suivante, il réduit l'intervalle d'interrogation de façon à ce que l'interrogation suivante se produise après l'expiration du minuteur. De cette façon, le magasin d'instances de workflow SQL obtient une haute précision des minuteurs qui s'exécutent plus longtemps que la fréquence définie par la propriété <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Il est déconseillé de réduire <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, car cela provoque une charge accrue sur la base de données de persistance. Chaque hôte de service qui utilise <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> interroge la base de données une seule fois par période de détection. Affecter un intervalle trop court à <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> peut provoquer une diminution des performances du système si le nombre d'hôtes de service est trop élevé.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Ce paramètre définit l'intervalle dans lequel l'hôte renouvelle son verrou dans la base de données de persistance. Réduire cet intervalle permettra la récupération plus rapide de l'instance de workflow après un échec de l'ordinateur ou de l'hôte. Par contre, une période de renouvellement de verrou courte augmente la charge sur la base de données de persistance. Chaque hôte de service qui utilise <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> mettra à jour ses verrous dans la base de données une seule fois par période de renouvellement. Si un ordinateur exécute plusieurs hôtes de service, assurez-vous que la charge provoquée par le renouvellement de verrou n'altère pas les performances du système. Le cas échéant, envisagez d'augmenter le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 S'il est activé, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> effectue une nouvelle tentative de chargement d'une instance verrouillée au cours des trente secondes suivantes. Affectez BasicRetry ou AggressiveRetry à la propriété <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> si le workflow reçoit plusieurs messages dans une courte période et ces messages sont reçus par des ordinateurs distincts.  
  
 Étant donné que le mécanisme de tentative de chargement n'entraîne pas une surcharge de performance tant que les tentatives de chargement ne sont pas exécutées, la propriété <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> doit toujours être activée.
