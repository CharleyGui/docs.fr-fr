---
title: 'Procédure : activer la persistance pour les workflows et les services de workflow'
description: Découvrez comment configurer le magasin d’instances de workflow SQL pour activer la persistance pour les workflows et les services de workflow par programme et à l’aide d’un fichier de configuration.
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 31fe6e3f06989e9a42254747565342cf97e4b9f1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421512"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="f98f7-103">Procédure : activer la persistance pour les workflows et les services de workflow</span><span class="sxs-lookup"><span data-stu-id="f98f7-103">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="f98f7-104">Cette rubrique décrit la procédure d'activation de la persistance pour les flux de travail et les services de workflow.</span><span class="sxs-lookup"><span data-stu-id="f98f7-104">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="f98f7-105">Activation de la persistance pour les flux de travail</span><span class="sxs-lookup"><span data-stu-id="f98f7-105">Enable Persistence for Workflows</span></span>

<span data-ttu-id="f98f7-106">Vous pouvez associer un magasin d’instances à un **WorkflowApplication** à l’aide <xref:System.Activities.WorkflowApplication.InstanceStore%2A> de la propriété de la <xref:System.Activities.WorkflowApplication> classe.</span><span class="sxs-lookup"><span data-stu-id="f98f7-106">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="f98f7-107">La méthode <xref:System.Activities.WorkflowApplication.Persist%2A> enregistre ou rend persistant un flux de travail dans le magasin d'instances associé à l'application.</span><span class="sxs-lookup"><span data-stu-id="f98f7-107">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="f98f7-108">La méthode <xref:System.Activities.WorkflowApplication.Unload%2A> rend persistant un flux de travail dans le magasin d'instances, puis décharge l'instance de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="f98f7-108">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="f98f7-109">La méthode **Load** charge un flux de travail en mémoire à l’aide des données de workflow stockées dans le magasin de persistance d’instance.</span><span class="sxs-lookup"><span data-stu-id="f98f7-109">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="f98f7-110">La méthode **persiste** effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f98f7-110">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="f98f7-111">Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.</span><span class="sxs-lookup"><span data-stu-id="f98f7-111">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="f98f7-112">Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="f98f7-112">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="f98f7-113">Reprend le service de planification de workflow.</span><span class="sxs-lookup"><span data-stu-id="f98f7-113">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="f98f7-114">La méthode **Unload** effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f98f7-114">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="f98f7-115">Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.</span><span class="sxs-lookup"><span data-stu-id="f98f7-115">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="f98f7-116">Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="f98f7-116">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="f98f7-117">Supprime l'instance de workflow en mémoire.</span><span class="sxs-lookup"><span data-stu-id="f98f7-117">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="f98f7-118">Les méthodes de **persistance** et de **déchargement** sont bloquées lorsqu’un flux de travail se trouve dans une zone de non-persistance jusqu’à ce que le flux de travail quitte la zone de non-persistance.</span><span class="sxs-lookup"><span data-stu-id="f98f7-118">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="f98f7-119">La méthode poursuit les opérations de persistance ou de déchargement une fois la zone sans persistance fermée.</span><span class="sxs-lookup"><span data-stu-id="f98f7-119">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="f98f7-120">Si la zone sans persistance ne se ferme pas avant que le délai d'attente ne s'écoule ou si le processus de persistance prend trop de temps, une TimeoutException est levée.</span><span class="sxs-lookup"><span data-stu-id="f98f7-120">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="f98f7-121">Activation de la persistance pour les services de workflow dans le code</span><span class="sxs-lookup"><span data-stu-id="f98f7-121">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="f98f7-122">Le membre **DurableInstancingOptions** de la <xref:System.ServiceModel.WorkflowServiceHost> classe a une propriété nommée **InstanceStore** que vous pouvez utiliser pour associer un magasin d’instances à **WorkflowServiceHost**.</span><span class="sxs-lookup"><span data-stu-id="f98f7-122">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="f98f7-123">Lorsque le **WorkflowServiceHost** est ouvert, la persistance est automatiquement activée si **DurableInstancingOptions. InstanceStore** n’est pas null.</span><span class="sxs-lookup"><span data-stu-id="f98f7-123">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="f98f7-124">En règle générale, un comportement de service fournit le magasin d’instances concrètes à utiliser avec un hôte de service de workflow à l’aide de la propriété **InstanceStore** .</span><span class="sxs-lookup"><span data-stu-id="f98f7-124">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="f98f7-125">Par exemple, le SqlWorkflowInstanceStoreBehavior crée une instance du **SqlWorkflowInstanceStore**, le configure et l’assigne à **DurableInstancingOptions. InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="f98f7-125">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="f98f7-126">Activation de la persistance pour les services de workflow à l'aide d'un fichier de configuration d'application</span><span class="sxs-lookup"><span data-stu-id="f98f7-126">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="f98f7-127">La persistance peut être activée à l'aide d'un fichier de configuration de l'application en ajoutant le code suivant à votre fichier app.config ou web.config :</span><span class="sxs-lookup"><span data-stu-id="f98f7-127">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
