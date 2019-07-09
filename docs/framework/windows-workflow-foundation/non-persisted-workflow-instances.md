---
title: Instances de workflow non persistantes
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 315d791585ace6ce4adf281abbba0a4c8c72d75a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663042"
---
# <a name="non-persisted-workflow-instances"></a>Instances de workflow non persistantes

Lorsqu'une nouvelle instance de workflow est créée, qui rend son état persistant dans le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, l'hôte de service crée une entrée pour ce service dans le magasin d'instances. Par la suite, lorsque l'instance de workflow est rendue persistante pour la première fois, le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stocke l'état de l'instance actuelle. Si le workflow est hébergé dans le service d'activation des processus Windows, les données de déploiement du service sont aussi écrites dans le magasin d'instances lorsque l'instance est rendue persistante pour la première fois.

Tant que l’instance de workflow n’a pas été rendu persistant, il est dans un **non persistantes** état. Dans cet état, l'instance de workflow ne peut pas être récupérée après un recyclage de domaine d'application, un échec de l'hôte ou un échec de l'ordinateur.

## <a name="the-non-persisted-state"></a>État non persistant

Les instances de workflow durables qui n'ont pas été rendues persistantes restent dans un état non persistant dans les cas suivants :

- L'hôte de service se bloque avant que l'instance de workflow soit persistante pour la première fois. L'instance de workflow reste dans le magasin d'instances et n'est pas récupérée. Si un message corrélé arrive, l'instance de workflow devient à nouveau active.

- L'instance de workflow rencontre une exception avant qu'elle soit rendue persistante pour la première fois. Selon le <xref:System.Activities.UnhandledExceptionAction> retourné, les scénarios suivants se produisent :

  - <xref:System.Activities.UnhandledExceptionAction> a la valeur <xref:System.Activities.UnhandledExceptionAction.Abort>: Lorsqu’une exception se produit, les informations de déploiement de service sont écrites dans le magasin d’instances, et l’instance de workflow est déchargée de la mémoire. L'instance de workflow reste dans un état non persitant et ne peut pas être rechargée.

  - <xref:System.Activities.UnhandledExceptionAction> a la valeur <xref:System.Activities.UnhandledExceptionAction.Cancel> ou <xref:System.Activities.UnhandledExceptionAction.Terminate>: Lorsqu’une exception se produit, informations de déploiement de service sont écrites dans le magasin d’instances, et l’état d’instance activité a la valeur <xref:System.Activities.ActivityInstanceState.Closed>.

Pour réduire le risque de rencontrer des instances de workflow non persistantes déchargées, il est recommandé de rendre le workflow persistant tôt dans son cycle de vie.

## <a name="detection-and-removal-of-non-persisted-instances"></a>Détection et suppression d'instances non persistantes

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ne supprime pas les instances de workflow non persistantes dans le magasin d'instances. Il ne supprime pas non plus les propriétaires des verrous arrivés à expiration auxquels des instances de workflow non persistantes sont associées.

Il est recommandé à l'administrateur de vérifier régulièrement la présence d'instances non persistantes dans le magasin d'instances. Les administrateurs peuvent supprimer ces instances du magasin d'instances s'ils savent que ce workflow ne recevra pas de messages corrélés. Par exemple, si l'instance se trouve dans la base de données depuis plusieurs mois et que vous savez que le workflow a généralement une durée de vie de quelques jours, il est possible de supposer sans risque qu'il s'agit d'une instance non initialisée qui a échoué.

Pour rechercher les instances non persistantes dans le magasin d'instances de workflow SQL, vous pouvez utiliser les requêtes SQL suivantes :

- Cette requête recherche toutes les instances qui n'ont pas été rendues persistantes et retourne l'ID et l'heure de création (stockée en temps UTC) correspondants.

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- Cette requête recherche toutes les instances qui n'ont pas été rendues persistantes et qui ne sont pas chargées et retourne l'ID et l'heure de création (stockée en temps UTC) correspondants.

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- Cette requête recherche toutes les instances suspendues qui n'ont pas été rendues persistantes et retourne l'ID, l'heure de création (stockée en temps UTC), la raison de suspension et le nom de l'exception correspondants.

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

Prenez des précautions lorsque vous supprimez des instances non persistantes. En général, il est possible de supprimer sans risque des instances non persistantes créées par <xref:System.ServiceModel.Activities.WorkflowServiceHost> qui ne sont pas suspendues ou pas chargées. Ces instances spécifiques peuvent être supprimées du magasin en les supprimant de l'affichage `[System.Activities.DurableInstancing].[Instances]` à l'aide de la commande SQL suivante, en remplaçant l'ID d'instance correct.

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> Il est déconseillé de supprimer toutes les instances non persistantes car cet ensemble d'instances inclut des instances qui viennent d'être créées mais qui n'ont pas encore été rendues persistantes.
