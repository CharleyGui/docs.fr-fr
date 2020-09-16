---
title: Configuration du suivi d'un workflow
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 098b295be00b1b8283e26e79ea14e78634fdb504
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557552"
---
# <a name="configuring-tracking-for-a-workflow"></a>Configuration du suivi d'un workflow

Un workflow peut s'exécuter de trois façons :

- Hébergé dans <xref:System.ServiceModel.Activities.WorkflowServiceHost>

- Exécuté en tant que <xref:System.Activities.WorkflowApplication>

- Exécuté directement à l'aide de <xref:System.Activities.WorkflowInvoker>

En fonction de l'option d'hébergement du workflow, un participant de suivi peut être ajouté soit via du code, soit via un fichier de configuration. Cette rubrique explique comment le suivi est configuré en ajoutant un participant de suivi à un <xref:System.Activities.WorkflowApplication> et à un <xref:System.ServiceModel.Activities.WorkflowServiceHost>, et comment activer le suivi lorsque vous utilisez <xref:System.Activities.WorkflowInvoker>.

## <a name="configuring-workflow-application-tracking"></a>Configuration du suivi d'application de workflow

Un workflow peut s'exécuter à l'aide de la classe <xref:System.Activities.WorkflowApplication>. Cette rubrique montre comment le suivi est configuré pour une application de workflow [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] en ajoutant un participant de suivi à l'hôte du workflow <xref:System.Activities.WorkflowApplication>. Dans ce cas, le workflow s'exécute comme une application de workflow. Vous configurez une application de workflow via du code (plutôt qu'à l'aide d'un fichier de configuration), qui est un fichier .exe auto-hébergé à l'aide de la classe <xref:System.Activities.WorkflowApplication>. Le participant de suivi est ajouté sous forme d'extension à l'instance <xref:System.Activities.WorkflowApplication>. Cela est fait en ajoutant le <xref:System.Activities.Tracking.TrackingParticipant> à la collection d’extensions pour l’instance WorkflowApplication.

Pour une application de workflow, vous pouvez ajouter l’extension de comportement <xref:System.Activities.Tracking.EtwTrackingParticipant> comme indiqué dans le code suivant.

```csharp
LogActivity activity = new LogActivity();

WorkflowApplication instance = new WorkflowApplication(activity);
EtwTrackingParticipant trackingParticipant =
    new EtwTrackingParticipant
{

        TrackingProfile = new TrackingProfile
           {
               Name = "SampleTrackingProfile",
               ActivityDefinitionId = "ProcessOrder",
               Queries = new WorkflowInstanceQuery
               {
                  States = { "*" }
              }
          }
       };
instance.Extensions.Add(trackingParticipant);
```

### <a name="configuring-workflow-service-tracking"></a>Configuration du suivi de service de workflow

Un flux de travail peut être exposé en tant que service WCF lorsqu’il est hébergé dans l' <xref:System.ServiceModel.Activities.WorkflowServiceHost> hôte de service. <xref:System.ServiceModel.Activities.WorkflowServiceHost> est une implémentation spécialisée de ServiceHost .NET pour un service basé sur un workflow. Cette section explique comment configurer le suivi pour un service de workflow [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] s'exécutant dans <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Il est configuré via un fichier Web.config (pour un service hébergé sur le Web) ou un fichier App.config (pour un service hébergé dans une application autonome, telle qu’une application console) en spécifiant un comportement de service ou via du code en ajoutant, à la collection <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, un comportement spécifique au suivi pour l’hôte de service.

Pour un service de workflow hébergé dans <xref:System.ServiceModel.WorkflowServiceHost> , vous pouvez ajouter <xref:System.Activities.Tracking.EtwTrackingParticipant> à l’aide de l' `behavior` élément <> dans un fichier de configuration, comme indiqué dans l’exemple suivant.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

Pour un service de workflow hébergé dans <xref:System.ServiceModel.WorkflowServiceHost>, vous pouvez également ajouter l’extension de comportement <xref:System.Activities.Tracking.EtwTrackingParticipant> dans le code. Pour ajouter un participant au suivi personnalisé, créez une extension de comportement et ajoutez-le au <xref:System.ServiceModel.ServiceHost> comme indiqué dans l'exemple de code suivant.

> [!NOTE]
> Si vous souhaitez afficher un exemple de code qui montre comment créer un élément de comportement personnalisé qui ajoute un participant de suivi personnalisé, reportez-vous aux exemples de [suivi](./samples/tracking.md) .

```csharp
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new
                                 Uri("http://localhost:8001/Sample"));
EtwTrackingBehavior trackingBehavior =
    new EtwTrackingBehavior
    {
        ProfileName = "Sample Tracking Profile"
    };
svcHost.Description.Behaviors.Add(trackingBehavior);
svcHost.Open();
```

Le participant au suivi est ajouté à l'hôte du service de workflow comme une extension au comportement.

Cet exemple de code suivant indique comment lire un modèle de suivi de fichier de configuration.

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            profileName ??= "";

            //Find the profile with the specified profile name in the list of profile found in config
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))
                        select p;

            if (match.Count() == 0)
            {
                //return an empty profile
                trackingProfile = new TrackingProfile()
                {
                    ActivityDefinitionId = displayName
                };

            }
            else
            {
                trackingProfile = match.First();
            }

            return trackingProfile;
```

Cet exemple de code indique comment ajouter un modèle de suivi à un hôte de workflow.

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> Pour plus d’informations sur les profils de suivi, consultez la rubrique [profils de suivi](tracking-profiles.md).

### <a name="configuring-tracking-using-workflowinvoker"></a>Configuration du suivi à l'aide de WorkflowInvoker

Pour configurer le suivi pour un workflow exécuté à l’aide de <xref:System.Activities.WorkflowInvoker>, ajoutez le fournisseur de suivi en tant qu’extension à une instance <xref:System.Activities.WorkflowInvoker>. L’exemple de code suivant provient de l’exemple de [suivi personnalisé](./samples/custom-tracking.md) .

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Affichage des enregistrements de suivi dans l'observateur d'événements

Il existe deux journaux de l'Observateur d'événements particulièrement intéressants à consulter lors de l'exécution de WF : le journal d'analyse et le journal de débogage. Les deux se trouvent sous le nœud Microsoft&#124;Windows&#124;Application Server-applications. Les journaux de cette section contiennent des événements d'une application unique plutôt que des événements qui ont un impact sur le système entier.

Les événements de trace de débogage sont écrits dans le journal de débogage. Pour collecter les événements de trace de débogage WF dans l'Observateur d'événements, activez le journal de débogage.

1. Pour ouvrir observateur d’événements, cliquez sur **Démarrer**, puis sur **exécuter.** Dans la boîte de dialogue Exécuter, tapez `eventvwr` .

2. Dans la boîte de dialogue observateur d’événements, développez le nœud **journaux des applications et des services** .

3. Développez les nœuds **Microsoft**, **Windows**et serveur d’applications **-applications** .

4. Cliquez avec le bouton droit sur le nœud **débogage** sous le nœud serveur d’applications **-applications** , puis sélectionnez **activer le journal**.

5. Exécutez votre application avec le suivi activé pour générer des événements de suivi.

6. Cliquez avec le bouton droit sur le nœud **débogage** , puis sélectionnez **Actualiser.** Les événements de suivi doivent être visibles dans le volet central.

WF 4 fournit un participant de suivi qui écrit des enregistrements de suivi dans une session ETW (suivi d'événements pour Windows). Le participant de suivi ETW est configuré avec un modèle de suivi pour s'abonner aux enregistrements de suivi. Lorsque le suivi est activé, les enregistrements de suivi des erreurs sont émis dans ETW. Les événements de suivi ETW (entre la plage 100-113) correspondant aux événements de suivi émis par le participant de suivi ETW sont écrits dans le journal analytique.

Pour afficher des enregistrements de suivi, procédez comme suit :

1. Pour ouvrir observateur d’événements, cliquez sur **Démarrer**, puis sur **exécuter.** Dans la boîte de dialogue Exécuter, tapez `eventvwr` .

2. Dans la boîte de dialogue observateur d’événements, développez le nœud **journaux des applications et des services** .

3. Développez les nœuds **Microsoft**, **Windows**et serveur d’applications **-applications** .

4. Cliquez avec le bouton droit sur le nœud **analyse** sous le nœud serveur d’applications **-applications** , puis sélectionnez **activer le journal**.

5. Exécutez votre application avec le suivi activé pour générer des enregistrements de suivi.

6. Cliquez avec le bouton droit sur le nœud **analyse** et sélectionnez **Actualiser.** Les enregistrements de suivi doivent être visibles dans le volet central.

L’illustration suivante montre les événements de suivi dans l’observateur d’événements :

![Capture d’écran de l’observateur d’événements montrant des enregistrements de suivi.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a>Enregistrement d'un ID de fournisseur spécifique à l'application

Si des événements doivent être écrits dans un journal des applications spécifique, procédez comme suit pour enregistrer le nouveau manifeste du fournisseur.

1. Déclarez l'ID de fournisseur dans le fichier de configuration de l'application.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Copiez le fichier manifeste de%windir%\Microsoft.NET\Framework \\ \<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.applications.Man dans un emplacement temporaire, puis renommez-le Microsoft. Windows. ApplicationServer. Applications_Provider1. Man

3. Remplacez le GUID dans le fichier manifeste par le nouveau GUID.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. Modifiez le nom du fournisseur si vous ne voulez pas désinstaller le fournisseur par défaut.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. Si vous avez modifié le nom du fournisseur à l'étape précédente, remplacez les noms des canaux dans le fichier manifeste par le nouveau nom de fournisseur.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Générez la DLL de ressource en procédant comme suit.

    1. Installez le Kit de développement logiciel (SDK) Windows. Le SDK Windows comprend le compilateur de messages ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) et le compilateur de ressources ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).

    2. Dans une invite de commandes du Kit de développement logiciel (SDK) Windows, exécutez mc.exe sur le nouveau fichier manifeste.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Exécutez rc.exe sur le fichier de ressources généré à l'étape précédente.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. Créez un fichier .cs vide appelé NewProviderReg.cs.

    5. Créez une DLL de ressource à l'aide du compilateur C#.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Remplacez la ressource et le nom de la dll de message dans le fichier manifeste par `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` le nouveau nom de la dll.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. Utilisez [wevtutil](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) pour inscrire le manifeste.

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Voir aussi

- [Analyse Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))
- [Surveillance des applications avec application Fabric](/previous-versions/appfabric/ee677276(v=azure.10))
