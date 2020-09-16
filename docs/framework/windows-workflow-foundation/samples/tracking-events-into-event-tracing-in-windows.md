---
title: Événements de suivi dans Event Tracing for Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 4350287aedae73a7ca9556de7ae3f597950e32ea
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549612"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Événements de suivi dans Event Tracing for Windows

Cet exemple montre comment activer le suivi Windows Workflow Foundation (WF) sur un service de workflow et émettre les événements de suivi dans Suivi d’v nements pour Windows (ETW). Pour émettre des enregistrements de suivi de workflow dans ETW, l'exemple utilise le participant de suivi ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).

Le workflow dans l'exemple reçoit une demande, assigne la réciproque des données d'entrée à la variable d'entrée et retourne la réciproque au client. Lorsque les données d'entrée sont égales à 0, une exception de division par zéro qui n'est pas gérée et provoque l'abandon du workflow se produit. Lorsque le suivi est activé, l'enregistrement de suivi des erreurs est émis dans ETW, ce qui peut aider à corriger l'erreur ultérieurement. Le participant de suivi ETW est configuré avec un modèle de suivi pour s'abonner aux enregistrements de suivi. Le modèle de suivi est défini dans le fichier Web.config et fourni comme paramètre de configuration au participant de suivi ETW. Le participant de suivi ETW est configuré dans le fichier Web.config du service de workflow et appliqué au service comme comportement de service. Dans cet exemple, vous consultez les événements de suivi dans le journal des événements à l'aide de l'observateur d'événements.

## <a name="workflow-tracking-details"></a>Détails de suivi de workflow

Windows Workflow Foundation fournit une infrastructure de suivi pour suivre l’exécution d’une instance de Workflow. Le runtime de suivi crée une instance de workflow pour émettre des événements associés au cycle de vie de workflow, événements des activités de workflow et événements personnalisés. Le tableau suivant détaille les composants principaux de l'infrastructure de suivi.

|Composant|Description|
|---------------|-----------------|
|Runtime de suivi|Fournit l'infrastructure permettant d'émettre des enregistrements de suivi.|
|Participants de suivi|Accède aux enregistrements de suivi. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] est fourni avec un participant de suivi qui écrit les enregistrements de suivi sous la forme d'événements Suivi d'événements pour Windows (ETW, Event Tracing for Windows).|
|Modèle de suivi|Mécanisme de filtrage qui permet à un participant de suivi de s'abonner à un sous-ensemble des enregistrements de suivi émis à partir d'une instance de workflow.|

Le tableau suivant détaille les enregistrements de suivi que l'exécution de workflow émet.

|Enregistrement de suivi|Description|
|---------------------|-----------------|
|Enregistrements de suivi d'instance du workflow.|Décrit le cycle de vie de l'instance de workflow. Par exemple, un enregistrement d'instance est émis lorsque le workflow démarre ou se termine.|
|Enregistrements de suivi d'état d'activité.|Détaille l'exécution de l'activité. Ces enregistrements indiquent l'état d'une activité de workflow, par exemple lorsqu'une activité est planifiée, lorsque l'activité se termine ou lorsqu'une erreur est générée.|
|Enregistrement de reprise de signet.|Émis chaque fois qu'un signet au sein d'une instance de workflow est repris.|
|Enregistrements de suivi personnalisé.|Un auteur de workflow peut créer des enregistrements de suivi personnalisé et les émettre dans l'activité personnalisée.|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Cet enregistrement est émis lorsqu'une activité planifie une autre activité.|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Cet enregistrement est émis lorsqu'une erreur est propagée à partir d'une activité.|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Cet enregistrement est émis lorsqu'une activité est annulée par une autre activité.|

Le participant de suivi s'abonne à un sous-ensemble des enregistrements de suivi émis à l'aide de modèles de suivi. Un modèle de suivi contient des requêtes de suivi qui permettent de s'abonner à un type d'enregistrement de suivi particulier. Les modèles de suivi peuvent être spécifiés dans le code ou dans la configuration.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2010, ouvrez le fichier solution EtwTrackingParticipantSample. sln.

2. Pour générer la solution, appuyez sur Ctrl+Maj+B.

3. Pour exécuter la solution, appuyez sur F5.

    Par défaut, le service écoute sur le port 53797 ( `http://localhost:53797/SampleWorkflowService.xamlx` ).

4. À l’aide de l’Explorateur de fichiers, ouvrez le client test WCF.

    Le client test WCF (WcfTestClient.exe) se trouve dans le \<Visual Studio 2010 installation folder> dossier \Common7\IDE\

    Le dossier d’installation par défaut de Visual Studio 2010 est C:\Program Files\Microsoft Visual Studio 10,0.

5. Dans le client test WCF, sélectionnez **Ajouter un service** dans le menu **fichier** .

    Ajoutez l'adresse du point de terminaison dans la zone d'entrée. La valeur par défaut est `http://localhost:53797/SampleWorkflowService.xamlx`.

6. Ouvrez l'application Observateur d'événements.

    Avant d’appeler le service, démarrez observateur d’événements à partir du menu **Démarrer** , sélectionnez **exécuter** et tapez `eventvwr.exe` . Vérifiez que le journal des événements écoute les événements de suivi émis à partir du service de workflow.

7. Dans l’arborescence de la observateur d’événements, accédez à **Observateur d’événements**, **journaux des applications et des services**et **Microsoft**. Cliquez avec le bouton droit sur **Microsoft** et sélectionnez **Afficher** , puis **afficher les journaux d’analyse et de débogage** pour activer les journaux d’analyse et de débogage

    Assurez-vous que l’option **afficher les journaux d’analyse et de débogage** est activée.

8. Dans l’arborescence de observateur d’événements, accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, serveur d’applications **-applications**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **activer le journal** pour activer le journal d' **analyse** .

9. Testez le service à l'aide du client test WCF en double-cliquant sur `GetData`.

    Vous ouvrez ainsi la méthode `GetData`. La demande accepte un paramètre et vérifie que la valeur est égale à 0, qui est la valeur par défaut.

     Cliquez sur **appeler**.

10. Observez les événements émis à partir du workflow.

    Revenez à observateur d’événements et accédez à **Observateur d’événements** **journaux des applications et des services**, **Microsoft**, **Windows**, serveur d’applications **-applications**. Cliquez avec le bouton droit sur **analyse** , puis sélectionnez **Actualiser**.

    Les événements de workflow sont affichés dans l'observateur d'événements. Notez que les événements d'exécution du workflow sont affichés et que l'un d'eux est une exception non gérée qui correspond à l'erreur dans le workflow. Par ailleurs, un événement d'avertissement est émis à partir de l'activité de workflow, qui indique que l'activité génère une erreur.

11. Répétez les étapes 9 et 10 avec une entrée de données autre que 0, afin qu'aucune erreur ne soit générée.

Les modèles de suivi vous permettent de vous abonner à des événements émis par l'exécution lorsque l'état d'une instance de workflow est modifié. Selon vos exigences d’analyse, vous pouvez créer un profil très général, qui s’abonne à un petit jeu de modifications d’état de haut niveau d’un workflow. En revanche, vous pouvez créer un profil très précis dont la sortie est assez riche pour reconstruire l'exécution ultérieurement. L'exemple illustre les événements émis à partir de l'exécution du workflow dans ETW à l'aide du `HealthMonitoring Tracking Profile`, qui émet un petit jeu d'événements. Un profil différent qui émet d'autres événements de suivi de workflow est également fourni dans le fichier Web.config nommé `Troubleshooting Tracking Profile`. Lorsque le [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] est installé, un profil par défaut avec un nom vide est configuré dans le fichier Machine.config. Ce profil est utilisé par la configuration de comportement de suivi ETW lorsque aucun nom de profil n'est spécifié ou lorsqu'un nom de profil vide est spécifié.

Le modèle de suivi de contrôle d'état émet des enregistrements d'instance de workflow et des enregistrements de propagation d'erreur de l'activité. Ce profil est créé en ajoutant le modèle de suivi suivant à un fichier de configuration Web.config.

```xml
<tracking>
  <profiles>
    <trackingProfile name="HealthMonitoring Tracking Profile">
      <workflow activityDefinitionId="*">
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Started"/>
              <state name="Completed"/>
              <state name="Aborted"/>
              <state name="UnhandledException"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

 Le profil peut être modifié en changeant la configuration `EtwTrackingParticipant` comme suit.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a>Pour nettoyer (facultatif)

1. Ouvrez l'observateur d'événements.

2. Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, serveur d’applications **-applications**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **désactiver le journal**.

3. Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, serveur d’applications **-applications**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **effacer le journal**.

4. Choisissez l’option **Effacer** pour effacer les événements.

## <a name="known-issue"></a>Problème connu

> [!NOTE]
> Un problème connu de l'observateur d'événements est qu'il lui arrive de ne pas parvenir à décoder des événements ETW. Un message d'erreur semblable au suivant s'affiche éventuellement.
>
> La description de l’ID \<id> d’événement de la source Microsoft-Windows-serveur d’applications-applications est introuvable. Le composant qui déclenche cet événement n’est pas installé sur votre ordinateur local, ou l’installation est endommagée. Vous pouvez installer ou réparer le composant sur l’ordinateur local.
>
> Si vous rencontrez cette erreur, cliquez sur Actualiser dans le volet Actions. Le décodage de l'événement doit maintenant s'effectuer correctement.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))
