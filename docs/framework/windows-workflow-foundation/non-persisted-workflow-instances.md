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
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="24a69-102">Instances de workflow non persistantes</span><span class="sxs-lookup"><span data-stu-id="24a69-102">Non-Persisted Workflow Instances</span></span>

<span data-ttu-id="24a69-103">Lorsqu'une nouvelle instance de workflow est créée, qui rend son état persistant dans le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, l'hôte de service crée une entrée pour ce service dans le magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="24a69-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="24a69-104">Par la suite, lorsque l'instance de workflow est rendue persistante pour la première fois, le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stocke l'état de l'instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="24a69-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="24a69-105">Si le workflow est hébergé dans le service d'activation des processus Windows, les données de déploiement du service sont aussi écrites dans le magasin d'instances lorsque l'instance est rendue persistante pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="24a69-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>

<span data-ttu-id="24a69-106">Tant que l’instance de workflow n’a pas été rendu persistant, il est dans un **non persistantes** état.</span><span class="sxs-lookup"><span data-stu-id="24a69-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="24a69-107">Dans cet état, l'instance de workflow ne peut pas être récupérée après un recyclage de domaine d'application, un échec de l'hôte ou un échec de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="24a69-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>

## <a name="the-non-persisted-state"></a><span data-ttu-id="24a69-108">État non persistant</span><span class="sxs-lookup"><span data-stu-id="24a69-108">The Non-Persisted State</span></span>

<span data-ttu-id="24a69-109">Les instances de workflow durables qui n'ont pas été rendues persistantes restent dans un état non persistant dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="24a69-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>

- <span data-ttu-id="24a69-110">L'hôte de service se bloque avant que l'instance de workflow soit persistante pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="24a69-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="24a69-111">L'instance de workflow reste dans le magasin d'instances et n'est pas récupérée.</span><span class="sxs-lookup"><span data-stu-id="24a69-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="24a69-112">Si un message corrélé arrive, l'instance de workflow devient à nouveau active.</span><span class="sxs-lookup"><span data-stu-id="24a69-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>

- <span data-ttu-id="24a69-113">L'instance de workflow rencontre une exception avant qu'elle soit rendue persistante pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="24a69-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="24a69-114">Selon le <xref:System.Activities.UnhandledExceptionAction> retourné, les scénarios suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="24a69-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>

  - <span data-ttu-id="24a69-115"><xref:System.Activities.UnhandledExceptionAction> a la valeur <xref:System.Activities.UnhandledExceptionAction.Abort>: Lorsqu’une exception se produit, les informations de déploiement de service sont écrites dans le magasin d’instances, et l’instance de workflow est déchargée de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="24a69-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="24a69-116">L'instance de workflow reste dans un état non persitant et ne peut pas être rechargée.</span><span class="sxs-lookup"><span data-stu-id="24a69-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>

  - <span data-ttu-id="24a69-117"><xref:System.Activities.UnhandledExceptionAction> a la valeur <xref:System.Activities.UnhandledExceptionAction.Cancel> ou <xref:System.Activities.UnhandledExceptionAction.Terminate>: Lorsqu’une exception se produit, informations de déploiement de service sont écrites dans le magasin d’instances, et l’état d’instance activité a la valeur <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="24a69-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>

<span data-ttu-id="24a69-118">Pour réduire le risque de rencontrer des instances de workflow non persistantes déchargées, il est recommandé de rendre le workflow persistant tôt dans son cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="24a69-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>

## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="24a69-119">Détection et suppression d'instances non persistantes</span><span class="sxs-lookup"><span data-stu-id="24a69-119">Detection and Removal of Non-Persisted Instances</span></span>

<span data-ttu-id="24a69-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ne supprime pas les instances de workflow non persistantes dans le magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="24a69-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="24a69-121">Il ne supprime pas non plus les propriétaires des verrous arrivés à expiration auxquels des instances de workflow non persistantes sont associées.</span><span class="sxs-lookup"><span data-stu-id="24a69-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>

<span data-ttu-id="24a69-122">Il est recommandé à l'administrateur de vérifier régulièrement la présence d'instances non persistantes dans le magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="24a69-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="24a69-123">Les administrateurs peuvent supprimer ces instances du magasin d'instances s'ils savent que ce workflow ne recevra pas de messages corrélés.</span><span class="sxs-lookup"><span data-stu-id="24a69-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="24a69-124">Par exemple, si l'instance se trouve dans la base de données depuis plusieurs mois et que vous savez que le workflow a généralement une durée de vie de quelques jours, il est possible de supposer sans risque qu'il s'agit d'une instance non initialisée qui a échoué.</span><span class="sxs-lookup"><span data-stu-id="24a69-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>

<span data-ttu-id="24a69-125">Pour rechercher les instances non persistantes dans le magasin d'instances de workflow SQL, vous pouvez utiliser les requêtes SQL suivantes :</span><span class="sxs-lookup"><span data-stu-id="24a69-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>

- <span data-ttu-id="24a69-126">Cette requête recherche toutes les instances qui n'ont pas été rendues persistantes et retourne l'ID et l'heure de création (stockée en temps UTC) correspondants.</span><span class="sxs-lookup"><span data-stu-id="24a69-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- <span data-ttu-id="24a69-127">Cette requête recherche toutes les instances qui n'ont pas été rendues persistantes et qui ne sont pas chargées et retourne l'ID et l'heure de création (stockée en temps UTC) correspondants.</span><span class="sxs-lookup"><span data-stu-id="24a69-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- <span data-ttu-id="24a69-128">Cette requête recherche toutes les instances suspendues qui n'ont pas été rendues persistantes et retourne l'ID, l'heure de création (stockée en temps UTC), la raison de suspension et le nom de l'exception correspondants.</span><span class="sxs-lookup"><span data-stu-id="24a69-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

<span data-ttu-id="24a69-129">Prenez des précautions lorsque vous supprimez des instances non persistantes.</span><span class="sxs-lookup"><span data-stu-id="24a69-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="24a69-130">En général, il est possible de supprimer sans risque des instances non persistantes créées par <xref:System.ServiceModel.Activities.WorkflowServiceHost> qui ne sont pas suspendues ou pas chargées.</span><span class="sxs-lookup"><span data-stu-id="24a69-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="24a69-131">Ces instances spécifiques peuvent être supprimées du magasin en les supprimant de l'affichage `[System.Activities.DurableInstancing].[Instances]` à l'aide de la commande SQL suivante, en remplaçant l'ID d'instance correct.</span><span class="sxs-lookup"><span data-stu-id="24a69-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> <span data-ttu-id="24a69-132">Il est déconseillé de supprimer toutes les instances non persistantes car cet ensemble d'instances inclut des instances qui viennent d'être créées mais qui n'ont pas encore été rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="24a69-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
