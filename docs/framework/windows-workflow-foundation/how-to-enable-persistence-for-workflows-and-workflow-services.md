---
title: 'Procédure : activer la persistance pour les workflows et les services de workflow'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460890"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Procédure : activer la persistance pour les workflows et les services de workflow

Cette rubrique décrit la procédure d'activation de la persistance pour les flux de travail et les services de workflow.

## <a name="enable-persistence-for-workflows"></a>Activation de la persistance pour les flux de travail

Vous pouvez associer un magasin d’instances à un **WorkflowApplication** à l’aide de la propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> de la classe <xref:System.Activities.WorkflowApplication>. La méthode <xref:System.Activities.WorkflowApplication.Persist%2A> enregistre ou rend persistant un flux de travail dans le magasin d'instances associé à l'application. La méthode <xref:System.Activities.WorkflowApplication.Unload%2A> rend persistant un flux de travail dans le magasin d'instances, puis décharge l'instance de la mémoire. La méthode **Load** charge un flux de travail en mémoire à l’aide des données de workflow stockées dans le magasin de persistance d’instance.

La méthode **persiste** effectue les étapes suivantes :

1. Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.

2. Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.

3. Reprend le service de planification de workflow.

 La méthode **Unload** effectue les étapes suivantes :

1. Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.

2. Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.

3. Supprime l'instance de workflow en mémoire.

Les méthodes de **persistance** et de **déchargement** sont bloquées lorsqu’un flux de travail se trouve dans une zone de non-persistance jusqu’à ce que le flux de travail quitte la zone de non-persistance. La méthode poursuit les opérations de persistance ou de déchargement une fois la zone sans persistance fermée. Si la zone sans persistance ne se ferme pas avant que le délai d'attente ne s'écoule ou si le processus de persistance prend trop de temps, une TimeoutException est levée.

## <a name="enable-persistence-for-workflow-services-in-code"></a>Activation de la persistance pour les services de workflow dans le code

Le membre **DurableInstancingOptions** de la classe <xref:System.ServiceModel.WorkflowServiceHost> a une propriété nommée **InstanceStore** que vous pouvez utiliser pour associer un magasin d’instances à **WorkflowServiceHost**.

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

Lorsque le **WorkflowServiceHost** est ouvert, la persistance est automatiquement activée si **DurableInstancingOptions. InstanceStore** n’est pas null.

En règle générale, un comportement de service fournit le magasin d’instances concrètes à utiliser avec un hôte de service de workflow à l’aide de la propriété **InstanceStore** . Par exemple, le SqlWorkflowInstanceStoreBehavior crée une instance du **SqlWorkflowInstanceStore**, le configure et l’assigne à **DurableInstancingOptions. InstanceStore**.

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Activation de la persistance pour les services de workflow à l'aide d'un fichier de configuration d'application

La persistance peut être activée à l'aide d'un fichier de configuration de l'application en ajoutant le code suivant à votre fichier app.config ou web.config :

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
