---
title: Modèles de suivi
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: ceeb0f5533bb4c637ea7df52249f5b00067d9b3d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551385"
---
# <a name="tracking-profiles"></a>Modèles de suivi

Les profils de suivi contiennent des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution.

## <a name="tracking-profiles"></a>Modèles de suivi

Les modèles de suivi sont utilisés pour indiquer les informations suivi émises pour une instance de workflow. Si aucun profil n'est spécifié, tous les événements de suivi sont émis. Si un profil est spécifié, les événements de suivi spécifiés dans le profil seront émis. Selon vos exigences d’analyse, vous pouvez écrire un profil très général, qui s’abonne à un petit jeu de modifications d’état de haut niveau d’un flux de travail. Inversement, vous pouvez créer un profil très détaillé dont les événements résultants sont assez riches pour reconstruire ultérieurement un flux d'exécution détaillé.

Les profils de suivi se manifestent eux-mêmes en tant qu’éléments XML dans un fichier de configuration .NET Framework standard ou spécifiés dans le code. L'exemple suivant illustre un modèle de suivi [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] dans un fichier de configuration qui permet à un participant au suivi de s'abonner aux événements de flux de travail `Started` et `Completed`.

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

L'exemple suivant illustre le modèle de suivi équivalent créé à l'aide du code.

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

Les enregistrements de suivi sont filtrés en mode de visibilité à l'aide de l'attribut <xref:System.Activities.Tracking.ImplementationVisibility> dans un modèle de suivi. Une activité composite est une activité de niveau supérieur qui contient d'autres activités qui forment son implémentation. Le mode de visibilité spécifie les enregistrements de suivi émis à partir d'activités composites dans une activité de flux de travail, afin de définir si les activités qui forment l'implémentation sont suivies. Le mode de visibilité s'applique au niveau du modèle de suivi. Les requêtes dans le modèle de suivi contrôlent le filtrage des enregistrements de suivi pour chaque activité d'un flux de travail. Pour plus d’informations, consultez la section **types de requêtes** de modèle de suivi dans ce document.

Les deux modes de visibilité spécifiés par l'attribut `implementationVisibility` dans le modèle de suivi sont `RootScope` et `All`. Le mode `RootScope` supprime les enregistrements de suivi pour les activités qui forment l'implémentation d'une activité, dans le cas où une activité composite n'est pas la racine d'un flux de travail. Cela implique que, lorsqu'une activité implémentée à l'aide d'autres activités est ajoutée à un flux de travail et que l'attribut `implementationVisibility` est défini sur RootScope, seule l'activité de niveau supérieur dans cette activité composite est suivie. Si une activité est la racine du flux de travail, l'implémentation de cette activité est le flux de travail lui-même et les enregistrements de suivi sont émis pour les activités qui forment l'implémentation. Le mode All permet d'émettre tous les enregistrements de suivi pour l'activité racine et l'ensemble de ses activités composites.

Par exemple, supposons que *MyActivity* est une activité composite dont l’implémentation contient deux activités, *Activity1* et *Activity2*. Lorsque cette activité est ajoutée à un flux de travail et que le suivi est activé avec un modèle de suivi `implementationVisibility` défini sur `RootScope` , les enregistrements de suivi sont émis uniquement pour *MyActivity*. Toutefois, aucun enregistrement n’est émis pour les activités *Activity1* et *Activity2*.

Toutefois, si l' `implementationVisibility` attribut du modèle de suivi est défini sur `All` , les enregistrements de suivi sont émis non seulement pour *MyActivity*, mais également pour les activités *Activity1* et *Activity2*.

L'indicateur `implementationVisibility` s'applique aux types d'enregistrements de suivi suivants :

- ActivityStateRecord

- FaultPropagationRecord

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> Les enregistrements de suivi CustomTrackingRecord émis à partir de l'implémentation d'une activité ne sont pas éliminés par filtrage par le paramètre implementationVisibility.

Dans le code, la fonctionnalité `implementationVisibility` du modèle de suivi est spécifiée comme suit : <xref:System.Activities.Tracking.ImplementationVisibility.RootScope>.

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

Dans un fichier de configuration, la fonctionnalité `implementationVisibility` du modèle de suivi est spécifiée comme suit : <xref:System.Activities.Tracking.ImplementationVisibility.All>.

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

Le paramètre `ImplementationVisibility` du modèle de suivi est facultatif. Par défaut, sa valeur est définie sur `RootScope`. De plus, les valeurs de cet attribut sont sensibles à la casse.

### <a name="tracking-profile-query-types"></a>Types de requêtes de modèle de suivi

Les modèles de suivi sont structurés comme des abonnements déclaratifs aux enregistrements de suivi qui vous permettent d'interroger le runtime de flux de travail pour rechercher des enregistrements de suivi particuliers. Plusieurs types de requêtes vous permettent de vous abonner à différentes classes d'objets <xref:System.Activities.Tracking.TrackingRecord>. Les profils de suivi peuvent être spécifiés dans la configuration ou via le code. Voici les types de requêtes les plus communs :

- Objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> - Permet de suivre les changements dans le cycle de vie de l'instance de flux de travail comme les événements `Started` et `Completed` montrés précédemment. L'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery> sert à s'abonner aux objets <xref:System.Activities.Tracking.TrackingRecord> suivants :

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  Les états auxquels vous pouvez vous abonner sont spécifiés dans la classe <xref:System.Activities.Tracking.WorkflowInstanceStates>.

  L'exemple suivant indique la configuration ou le code servant à s'abonner aux enregistrements de suivi de flux de travail au niveau de l'instance, pour l'état de l'instance `Started`, à l'aide de l'objet <xref:System.Activities.Tracking.WorkflowInstanceQuery>.

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- Objet <xref:System.Activities.Tracking.ActivityStateQuery> - Permet de suivre les changements dans le cycle de vie des activités qui composent une instance de workflow. Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité « Envoyer un message électronique » se termine dans une instance de Workflow. Cette requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.ActivityStateRecord>. Les états disponibles auxquels s'abonner sont spécifiés dans l'objet <xref:System.Activities.Tracking.ActivityStates>.

  L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements de suivi d'état d'activité qui utilisent l'objet <xref:System.Activities.Tracking.ActivityStateQuery> pour l'activité `SendEmailActivity`.

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > Si plusieurs éléments activityStateQuery ont le même nom, seuls les états dans le dernier élément sont utilisés dans le modèle de suivi.

- Objet <xref:System.Activities.Tracking.ActivityScheduledQuery> - Cette requête vous permet de suivre une activité devant être exécutée par une activité parente. La requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.ActivityScheduledRecord>.

  L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements associés à l'activité enfant `SendEmailActivity` en cours de planification, à l'aide de l'objet <xref:System.Activities.Tracking.ActivityScheduledQuery>.

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- Objet <xref:System.Activities.Tracking.FaultPropagationQuery> - Permet de suivre la gestion des erreurs qui se produisent dans une activité. La requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.FaultPropagationRecord>.

  L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements associés à la propagation d'erreur à l'aide de l'objet <xref:System.Activities.Tracking.FaultPropagationQuery>.

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- Objet <xref:System.Activities.Tracking.CancelRequestedQuery> - Permet de suivre les demandes d'annulation d'une activité enfant par l'activité parente. La requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.CancelRequestedRecord>.

  La configuration et le code utilisés pour s’abonner aux enregistrements liés à l’annulation de l’activité à l’aide de <xref:System.Activities.Tracking.CancelRequestedQuery> sont indiqués dans l’exemple suivant.

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- Objet <xref:System.Activities.Tracking.CustomTrackingQuery> - Permet de suivre les événements que vous définissez dans vos activités de code. La requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.CustomTrackingRecord>.

  L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements associés aux enregistrements de suivi personnalisé à l'aide de l'objet <xref:System.Activities.Tracking.CustomTrackingQuery>.

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- Objet <xref:System.Activities.Tracking.BookmarkResumptionQuery> - Permet de suivre la reprise d'un signet dans une instance de flux de travail. Cette requête est nécessaire pour qu'un objet <xref:System.Activities.Tracking.TrackingParticipant> s'abonne à des objets <xref:System.Activities.Tracking.BookmarkResumptionRecord>.

  L'exemple suivant indique la configuration et le code servant à s'abonner à des enregistrements associés à la reprise de signet à l'aide de l'objet <xref:System.Activities.Tracking.BookmarkResumptionQuery>.

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a>Annotations

Grâce aux annotations, vous pouvez baliser arbitrairement des enregistrements de suivi avec une valeur configurable après la génération. Par exemple, vous pouvez avoir besoin de plusieurs enregistrements de suivi sur plusieurs flux de travail à baliser avec « serveur de messagerie » = = « messagerie Serveur1 ». Lors de l’interrogation ultérieure d’enregistrements de suivi, cela facilite la recherche de tous les enregistrements ayant cette étiquette.

Pour ce faire, une annotation est ajoutée à une requête de suivi comme illustré dans l'exemple suivant.

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a>Création d'un modèle de suivi

Les éléments de requête de suivi sont utilisés pour créer un modèle de suivi à l’aide d’un fichier de configuration ou d’un [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code XML. Voici un exemple de modèle de suivi créé à l'aide d'un fichier de configuration :

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> Pour un WF utilisant l'hôte du service de flux de travail, le modèle de suivi est généralement créé à l'aide d'un fichier de configuration. Mais il peut également être créé avec le code, à l'aide de l'API de modèle de suivi et de requête de suivi.

Un profil configuré en tant que fichier de configuration XML est appliqué à un participant au suivi à l’aide d’une extension de comportement. Elle est ajoutée à un WorkflowServiceHost comme décrit dans la section [configuration du suivi pour un workflow](configuring-tracking-for-a-workflow.md).

Les paramètres de configuration du modèle de suivi déterminent les commentaires des enregistrements de suivi émis par l'hôte. Un participant au suivi s'abonne à des enregistrements de suivi en ajoutant des requêtes à un modèle de suivi. Pour s’abonner à tous les enregistrements de suivi, le modèle de suivi doit spécifier toutes les requêtes de suivi à l’aide \* de «» dans les champs de nom de chacune des requêtes.

Voici quelques exemples communs de profils de suivi :

- Modèle de suivi permettant d'obtenir les enregistrements et les erreurs de l'instance de flux de travail.

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- Modèle de suivi permettant d'obtenir tous les enregistrements de suivi personnalisé.

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a>Voir aussi

- [Suivi SQL](./samples/sql-tracking.md)
- [Analyse Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))
- [Surveillance des applications avec application Fabric](/previous-versions/appfabric/ee677276(v=azure.10))
