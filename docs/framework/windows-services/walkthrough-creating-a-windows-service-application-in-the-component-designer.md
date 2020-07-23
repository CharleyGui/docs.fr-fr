---
title: 'Didacticiel : créer une application de service Windows'
description: Dans ce didacticiel, créez une application de service Windows dans Visual Studio qui écrit des messages dans un journal des événements. Ajoutez des fonctionnalités, définissez l’État, ajoutez des programmes d’installation, et bien plus encore.
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 487a974af2280a02b83fe685324c9464df705585
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925629"
---
# <a name="tutorial-create-a-windows-service-app"></a>Didacticiel : créer une application de service Windows

Cet article explique comment créer, dans Visual Studio, une application de service Windows qui écrit des messages dans un journal des événements.

## <a name="create-a-service"></a>Créer un service

Pour commencer, créez le projet et définissez les valeurs nécessaires au fonctionnement correct du service.

1. Dans le menu **Fichier** de Visual Studio, sélectionnez **Nouveau** > **Projet** (ou appuyez sur **Ctrl**+**Maj**+**N**) pour ouvrir la fenêtre **Nouveau projet**.

2. Accédez au modèle de projet **Service Windows (.NET Framework)** et sélectionnez-le. Pour le trouver, développez **Installé** et **Visual C# ** ou **Visual Basic**, puis sélectionnez **Windows Desktop**. Ou entrez *Service Windows* dans la zone de recherche en haut à droite et appuyez sur **Entrée**.

   ![Modèle Windows Service dans la boîte de dialogue Nouveau projet de Visual Studio](./media/new-project-dialog.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle de **service Windows** , vous devrez peut-être installer la charge de travail **développement .net Desktop** :
   >
   > Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Ouvrir Visual Studio Installer** dans l’angle inférieur gauche. Sélectionnez la charge de travail **Développement .NET Desktop**, puis sélectionnez **Modifier**.

3. Dans **Nom**, entrez *MyNewService*, puis sélectionnez **OK**.

   L’onglet **Conception** apparaît (**Service1.cs [Conception]** ou **Service1.vb [Conception]**).

   Le modèle de projet inclut une classe Component appelée `Service1` qui hérite de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Elle contient une grande partie du code de service de base, comme le code pour démarrer le service.

## <a name="rename-the-service"></a>Renommer le service

Renommez le service **Service1** en **MyNewService**.

1. Dans l’**Explorateur de solutions**, sélectionnez **Service1.cs** ou **Service1.vb**, puis choisissez **Renommer** dans le menu contextuel. Renommez le fichier **MyNewService.cs** ou **MyNewService.vb**, puis appuyez sur **Entrée**.

    Une fenêtre contextuelle vous invite à indiquer si vous voulez renommer toutes les références à l’élément de code *Service1*.

2. Dans la fenêtre contextuelle, sélectionnez **Oui**.

    ![Renommer l’invite](./media/windows-service-rename.png "Invite de changement de nom du service Windows")

3. Sous l’onglet **Conception**, sélectionnez **Propriétés** dans le menu contextuel. Dans la fenêtre **Propriétés**, remplacez la valeur **ServiceName** par *MyNewService*.

    ![Propriétés du service](./media/windows-service-properties.png "Propriétés du service Windows")

4. Sélectionnez **Enregistrer tout** dans le menu **Fichier**.

## <a name="add-features-to-the-service"></a>Ajouter des fonctionnalités au service

Dans cette section, vous ajoutez un journal des événements personnalisé au service Windows. Le composant <xref:System.Diagnostics.EventLog> est un exemple du type de composant que vous pouvez ajouter à un service Windows.

### <a name="add-custom-event-log-functionality"></a>Ajouter une fonctionnalité de journal des événements personnalisé

1. Dans l’**Explorateur de solutions**, dans le menu contextuel de **MyNewService.cs** ou **MyNewService.vb**, choisissez **Concepteur de vues**.

2. Dans **Boîte à outils**, développez **Composants**, puis faites glisser le composant **EventLog** vers l’onglet **Service1.cs [Conception]** ou ** Service1.vb [Conception]**.

3. Dans l’**Explorateur de solutions**, dans le menu contextuel de **MyNewService.cs** ou **MyNewService.vb**, choisissez **Afficher le code**.

4. Définissez un journal des événements personnalisé. Pour C#, modifiez le constructeur `MyNewService()` existant ; pour Visual Basic, ajoutez le constructeur `New()` :

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. Ajoutez une instruction `using` à **MyNewService.cs** (si elle n’existe pas déjà) ou une instruction `Imports` à **MyNewService.vb**, pour l’espace de noms <xref:System.Diagnostics?displayProperty=nameWithType> :

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. Sélectionnez **Enregistrer tout** dans le menu **Fichier**.

### <a name="define-what-occurs-when-the-service-starts"></a>Définir les actions à effectuer lors du démarrage du service

Dans l’éditeur de code pour **MyNewService.cs** ou **MyNewService.vb**, localisez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ; Visual Studio a automatiquement créé une définition de méthode vide quand vous avez créé le projet. Ajoutez du code qui écrit une entrée dans le journal des événements lorsque le service démarre :

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a>Interrogation

Étant donné qu’une application de service est conçue pour être durable, elle interroge ou supervise généralement le système, que vous configurez dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>. La méthode `OnStart` doit retourner au système d’exploitation une fois que le service a commencé à fonctionner pour que le système ne soit pas bloqué.

Pour configurer un mécanisme d’interrogation simple, utilisez le composant <xref:System.Timers.Timer?displayProperty=nameWithType>. Le minuteur déclenche un événement <xref:System.Timers.Timer.Elapsed> à intervalles réguliers, moment auquel votre service peut effectuer sa supervision. Vous utilisez le composant <xref:System.Timers.Timer> comme suit :

- Définissez les propriétés du composant <xref:System.Timers.Timer> dans la méthode `MyNewService.OnStart`.
- Démarrez le minuteur en appelant la méthode <xref:System.Timers.Timer.Start%2A>.

##### <a name="set-up-the-polling-mechanism"></a>Configurez le mécanisme d’interrogation.

1. Ajoutez le code suivant dans l’événement `MyNewService.OnStart` pour configurer le mécanisme d’interrogation :

   ```csharp
   // Set up a timer that triggers every minute.
   Timer timer = new Timer();
   timer.Interval = 60000; // 60 seconds
   timer.Elapsed += new ElapsedEventHandler(this.OnTimer);
   timer.Start();
   ```

   ```vb
   ' Set up a timer that triggers every minute.
   Dim timer As Timer = New Timer()
   timer.Interval = 60000 ' 60 seconds
   AddHandler timer.Elapsed, AddressOf Me.OnTimer
   timer.Start()
   ```

2. Ajoutez une instruction `using` à **MyNewService.cs** ou une instruction `Imports` à **MyNewService.vb** pour l’espace de noms <xref:System.Timers?displayProperty=nameWithType> :

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. Dans la classe `MyNewService`, ajoutez la méthode `OnTimer` pour gérer l’événement <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> :

   ```csharp
   public void OnTimer(object sender, ElapsedEventArgs args)
   {
       // TODO: Insert monitoring activities here.
       eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);
   }
   ```

   ```vb
   Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)
      ' TODO: Insert monitoring activities here.
      eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)
      eventId = eventId + 1
   End Sub
   ```

4. Dans la classe `MyNewService`, ajoutez une variable membre. Celle-ci contient l’identificateur de l’événement suivant à écrire dans le journal des événements :

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

Au lieu d’exécuter tout votre travail sur le thread principal, vous pouvez exécuter des tâches à l’aide de threads de travail en arrière-plan. Pour plus d’informations, consultez <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Définir les actions à effectuer lors de l'arrêt du service

Insérez une ligne de code dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStop%2A> qui ajoute une entrée dans le journal des événements lorsque le service est arrêté :

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Définir d'autres actions du service

Vous pouvez substituer les méthodes <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> et <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> afin de définir d'autres types de traitement pour votre composant.

Le code suivant montre comment substituer la méthode <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> dans la classe `MyNewService` :

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a>Définir l’état du service

Les services indiquent leur état au [Gestionnaire de contrôle des services](/windows/desktop/Services/service-control-manager). Les utilisateurs peuvent ainsi déterminer si un service fonctionne correctement. Par défaut, un service qui hérite de <xref:System.ServiceProcess.ServiceBase> signale un ensemble limité de paramètres d’état, qui incluent SERVICE_STOPPED, SERVICE_PAUSED et SERVICE_RUNNING. Si un service prend du temps à démarrer, il s’avère utile de signaler un état SERVICE_START_PENDING.

Vous pouvez implémenter les paramètres d’état SERVICE_START_PENDING et SERVICE_STOP_PENDING en ajoutant du code qui appelle la fonction [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) Windows.

### <a name="implement-service-pending-status"></a>Implémenter l’état de service en attente

1. Ajoutez une instruction `using` à **MyNewService.cs** ou une instruction `Imports` à **MyNewService.vb** pour l’espace de noms <xref:System.Runtime.InteropServices?displayProperty=nameWithType> :

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Ajoutez le code suivant à **MyNewService.cs** ou **MyNewService.vb** pour déclarer les valeurs `ServiceState` et ajouter une structure pour l’état. Vous utiliserez cette structure dans un appel de code non managé :

    ```csharp
    public enum ServiceState
    {
        SERVICE_STOPPED = 0x00000001,
        SERVICE_START_PENDING = 0x00000002,
        SERVICE_STOP_PENDING = 0x00000003,
        SERVICE_RUNNING = 0x00000004,
        SERVICE_CONTINUE_PENDING = 0x00000005,
        SERVICE_PAUSE_PENDING = 0x00000006,
        SERVICE_PAUSED = 0x00000007,
    }

    [StructLayout(LayoutKind.Sequential)]
    public struct ServiceStatus
    {
        public int dwServiceType;
        public ServiceState dwCurrentState;
        public int dwControlsAccepted;
        public int dwWin32ExitCode;
        public int dwServiceSpecificExitCode;
        public int dwCheckPoint;
        public int dwWaitHint;
    };
    ```

    ```vb
    Public Enum ServiceState
        SERVICE_STOPPED = 1
        SERVICE_START_PENDING = 2
        SERVICE_STOP_PENDING = 3
        SERVICE_RUNNING = 4
        SERVICE_CONTINUE_PENDING = 5
        SERVICE_PAUSE_PENDING = 6
        SERVICE_PAUSED = 7
    End Enum

    <StructLayout(LayoutKind.Sequential)>
    Public Structure ServiceStatus
        Public dwServiceType As Long
        Public dwCurrentState As ServiceState
        Public dwControlsAccepted As Long
        Public dwWin32ExitCode As Long
        Public dwServiceSpecificExitCode As Long
        Public dwCheckPoint As Long
        Public dwWaitHint As Long
    End Structure
    ```

    > [!NOTE]
    > La boîte de dialogue Gestionnaire de contrôle des services utilise les membres `dwWaitHint` et `dwCheckpoint` de la [structure SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) pour déterminer le délai d’attente avant le démarrage ou l’arrêt d’un service Windows. Si l’exécution de vos méthodes `OnStart` et `OnStop` est longue, votre service peut demander plus de temps en appelant à nouveau `SetServiceStatus` avec une valeur `dwCheckPoint` incrémentée.

3. Dans la classe `MyNewService`, déclarez la fonction [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) à l’aide d’un [appel de code non managé](../interop/consuming-unmanaged-dll-functions.md) :

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. Pour implémenter l’état SERVICE_START_PENDING, ajoutez le code suivant au début de la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> :

    ```csharp
    // Update the service state to Start Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Start Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

5. Ajoutez du code à la fin de la méthode `OnStart` pour affecter à l’état la valeur SERVICE_RUNNING :

    ```csharp
    // Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

6. (Facultatif) Si <xref:System.ServiceProcess.ServiceBase.OnStop%2A> est une méthode durable, répétez cette procédure dans la méthode `OnStop`. Implémentez l’état SERVICE_STOP_PENDING et retournez l’état SERVICE_STOPPED avant la fin de la méthode `OnStop`.

   Par exemple :

    ```csharp
    // Update the service state to Stop Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);

    // Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Stop Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)

    ' Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

## <a name="add-installers-to-the-service"></a>Ajouter des programmes d'installation pour le service

Avant d’exécuter un service Windows, vous devez l’installer, ce qui ’inscrit auprès du Gestionnaire de contrôle des services. Ajoutez à votre projet des programmes d’installation pour gérer les détails de l’inscription.

1. Dans l’**Explorateur de solutions**, dans le menu contextuel de **MyNewService.cs** ou **MyNewService.vb**, choisissez **Concepteur de vues**.

2. En mode **Conception**, sélectionnez la zone d’arrière-plan, puis choisissez **Ajouter le programme d’installation** dans le menu contextuel.

     Par défaut, Visual Studio ajoute une classe Component nommée `ProjectInstaller`, qui contient deux programmes d’installation, à votre projet. Ces programmes d’installation sont destinés à votre service et au processus associé du service.

3. En mode **Conception** pour **ProjectInstaller**, sélectionnez **serviceInstaller1** pour un projet Visual C# ou **ServiceInstaller1** pour un projet Visual Basic, puis choisissez **Propriétés** dans le menu contextuel.

4. Dans la fenêtre **Propriétés**, vérifiez que la propriété <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> a la valeur **MyNewService**.

5. Ajoutez du texte à la propriété <xref:System.ServiceProcess.ServiceInstaller.Description%2A>, comme *Un exemple de service*.

     Ce texte apparaît dans la colonne **Description** de la fenêtre **Services** et explique le service à l’utilisateur.

    ![Description du service dans la fenêtre Services.](./media/windows-service-description.png "Description du service")

6. Ajoutez du texte à la propriété <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A>. Par exemple, *Nom complet de MyNewService*.

     Ce texte apparaît dans la colonne **Nom complet** de la fenêtre **Services**. Ce nom peut être différent de la propriété <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, qui est le nom utilisé par le système (par exemple, le nom que vous utilisez pour la commande `net start` pour démarrer votre service).

7. Affectez à la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> la valeur <xref:System.ServiceProcess.ServiceStartMode.Automatic> à partir de la liste déroulante.

8. Quand vous avez terminé, la fenêtre **Propriétés** doit ressembler à la figure suivante :

     ![Propriétés du programme d’installation pour un service Windows](./media/windows-service-installer-properties.png "Propriétés du programme d’installation du service Windows")

9. En mode **Conception** pour **ProjectInstaller**, choisissez **serviceProcessInstaller1** pour un projet Visual C# ou **ServiceProcessInstaller1** pour un projet Visual Basic, puis choisissez **Propriétés** dans le menu contextuel. Affectez à la propriété <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> la valeur <xref:System.ServiceProcess.ServiceAccount.LocalSystem> à partir de la liste déroulante.

     Ce paramètre installe le service et l’exécute en utilisant le compte système local.

    > [!IMPORTANT]
    > Le compte <xref:System.ServiceProcess.ServiceAccount.LocalSystem> dispose d'autorisations générales, y compris la possibilité d'écrire dans le journal des événements. Utilisez ce compte avec précaution car il peut augmenter le risque d'attaques par des logiciels malveillants. Pour les autres tâches, utilisez le compte <xref:System.ServiceProcess.ServiceAccount.LocalService> , qui se comporte comme un utilisateur non privilégié de l'ordinateur local et présente des informations d'identification anonymes à tout serveur distant. Cet exemple échoue si vous essayez d'utiliser le compte <xref:System.ServiceProcess.ServiceAccount.LocalService> , car il doit disposer d'une autorisation pour écrire dans le journal des événements.

Pour plus d’informations sur les programmes d’installation, consultez [Comment : ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>(Facultatif) Définition de paramètres de démarrage

> [!NOTE]
> Avant de décider d’ajouter des paramètres de démarrage, déterminez si c’est le meilleur moyen de passer des informations à votre service. Bien qu’ils soient faciles à utiliser et à analyser et qu’un utilisateur puisse facilement les substituer, ils peuvent être plus difficiles à découvrir et utiliser pour un utilisateur sans documentation. En général, si votre service nécessite seulement quelques paramètres de démarrage, il est préférable d’utiliser plutôt le Registre ou un fichier de configuration.

Un service Windows peut accepter des arguments de ligne de commande ou des paramètres de démarrage. Quand vous ajoutez du code pour traiter des paramètres de démarrage, un utilisateur peut démarrer votre service avec ses propres paramètres de démarrage personnalisés dans la fenêtre des propriétés du service. Toutefois, ces paramètres de démarrage ne sont pas persistants lors du prochain démarrage du service. Pour définir des paramètres de démarrage de façon définitive, faites-le dans le Registre.

Chaque service Windows a une entrée de Registre sous la sous-clé **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services**. Sous la sous-clé de chaque service, utilisez la sous-clé **Parameters** pour stocker les informations auxquelles votre service peut accéder. Vous pouvez utiliser des fichiers de configuration d'application pour un service Windows de la même façon que vous le faites pour les autres types de programmes. Pour l’exemple de code, consultez <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.

### <a name="to-add-startup-parameters"></a>Pour ajouter des paramètres de démarrage

1. Sélectionnez **Program.cs** ou **MyNewService.Designer.vb**, puis choisissez **Afficher le code** dans le menu contextuel. Dans la méthode `Main`, modifiez le code pour ajouter un paramètre d’entrée et le passer au constructeur du service :

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. Dans **MyNewService.cs** ou **MyNewService.vb**, modifiez le constructeur `MyNewService` pour traiter le paramètre d’entrée comme suit :

   ```csharp
   using System.Diagnostics;

   public MyNewService(string[] args)
   {
       InitializeComponent();

       string eventSourceName = "MySource";
       string logName = "MyNewLog";

       if (args.Length > 0)
       {
          eventSourceName = args[0];
       }

       if (args.Length > 1)
       {
           logName = args[1];
       }

       eventLog1 = new EventLog();

       if (!EventLog.SourceExists(eventSourceName))
       {
           EventLog.CreateEventSource(eventSourceName, logName);
       }

       eventLog1.Source = eventSourceName;
       eventLog1.Log = logName;
   }
   ```

   ```vb
   Imports System.Diagnostics

   Public Sub New(ByVal cmdArgs() As String)
       InitializeComponent()
       Dim eventSourceName As String = "MySource"
       Dim logName As String = "MyNewLog"
       If (cmdArgs.Count() > 0) Then
           eventSourceName = cmdArgs(0)
       End If
       If (cmdArgs.Count() > 1) Then
           logName = cmdArgs(1)
       End If
       eventLog1 = New EventLog()
       If (Not EventLog.SourceExists(eventSourceName)) Then
           EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   Ce code définit la source de l’événement et le nom du journal en fonction des paramètres de démarrage fournis par l’utilisateur. Si aucun argument n’est fourni, les valeurs par défaut sont utilisées.

3. Pour spécifier les arguments de ligne de commande, ajoutez le code suivant à la classe `ProjectInstaller` dans **ProjectInstaller.cs** ou **ProjectInstaller.vb** :

   ```csharp
   protected override void OnBeforeInstall(IDictionary savedState)
   {
       string parameter = "MySource1\" \"MyLogFile1";
       Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
       base.OnBeforeInstall(savedState);
   }
   ```

   ```vb
   Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
       Dim parameter As String = "MySource1"" ""MyLogFile1"
       Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
       MyBase.OnBeforeInstall(savedState)
   End Sub
   ```

   En règle générale, cette valeur contient le chemin complet de l’exécutable du service Windows. Pour que le service démarre correctement, l’utilisateur doit fournir des guillemets pour le chemin et chaque paramètre individuel. Un utilisateur peut changer les paramètres dans l’entrée de Registre **ImagePath** pour changer les paramètres de démarrage du service Windows. Toutefois, un meilleur moyen consiste à changer la valeur programmatiquement et à exposer les fonctionnalités de manière conviviale, par exemple à l’aide d’un utilitaire de gestion ou de configuration.

## <a name="build-the-service"></a>Générer le service

1. Dans l’**Explorateur de solutions**, choisissez **Propriétés** dans le menu contextuel du projet **MyNewService**.

   Les pages de propriétés de votre projet s'affichent.

2. Sous l’onglet **Application**, dans la liste **Objet de démarrage**, choisissez **MyNewService.Program** ou **Sub Main** pour les projets Visual Basic.

3. Pour générer le projet, dans l’**Explorateur de solutions**, choisissez **Build** dans le menu contextuel de votre projet (ou appuyez sur **Ctrl**+**Maj**+**B**).

## <a name="install-the-service"></a>Installer le service

Maintenant que vous avez généré le service Windows, vous pouvez l'installer. Pour installer un service Windows, vous devez disposer d’informations d’identification d’administrateur sur l’ordinateur sur lequel il est installé.

1. Ouvrez [Invite de commandes développeur pour Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs) avec des informations d'identification administratives. À partir du menu **Démarrer** de Windows, sélectionnez **Invite de commandes développeur pour VS 2017** dans le dossier Visual Studio, puis sélectionnez **Plus** > **Exécuter en tant qu’administrateur** dans le menu contextuel.

2. Dans la fenêtre **Invite de commandes développeur pour Visual Studio**, accédez au dossier qui contient la sortie de votre projet (par défaut, le sous-répertoire *\bin\Debug* de votre projet).

3. Entrez la commande suivante :

    ```shell
    installutil MyNewService.exe
    ```

    Si le service s’installe correctement, la commande signale une réussite.

    Si le système ne trouve pas *installutil.exe*, vérifiez qu’il existe sur votre ordinateur. Cet outil est installé avec le .NET Framework dans le dossier *%windir%\Microsoft.NET\Framework [64] \\ &lt; &gt; version du .NET Framework*. Par exemple, le chemin par défaut pour la version 64 bits est *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

    Si le processus **installutil.exe** échoue, examinez le journal d’installation pour en connaître la raison. Par défaut, le journal se trouve dans le même dossier que l’exécutable du service. L’installation peut échouer si :
    - La classe <xref:System.ComponentModel.RunInstallerAttribute> n’est pas présente sur la classe `ProjectInstaller`.
    - L’attribut n’a pas la valeur `true`.
    - La classe `ProjectInstaller` n’est pas définie en tant que `public`.

Pour plus d’informations, consultez [procédure : installer et désinstaller des services](how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Démarrer et exécuter le service

1. Dans Windows, ouvrez l’application de bureau **Services**. Appuyez sur **Windows** + **R** pour ouvrir la zone **exécuter** , entrez *services. msc*, puis appuyez sur **entrée** ou sélectionnez **OK**.

     Votre service doit être répertorié dans **Services**, affiché par ordre alphabétique du nom d’affichage que vous lui avez donné.

     ![MyNewService dans la fenêtre Services.](./media/windowsservices-serviceswindow.PNG)

2. Pour démarrer le service, choisissez **Démarrer** dans le menu contextuel du service.

3. Pour arrêter le service, choisissez **Arrêter** dans le menu contextuel du service.

4. (Facultatif) À partir de la ligne de commande, utilisez les commandes **net start &lt;nom du service&gt;** et **net stop &lt;nom du service&gt;** pour démarrer et arrêter votre service.

### <a name="verify-the-event-log-output-of-your-service"></a>Vérifier la sortie du journal des événements de votre service

1. Dans Windows, ouvrez l’application de bureau **Observateur d’événements**. Entrez *Observateur d’événements* dans la barre de recherche Windows, puis sélectionnez **Observateur d’événements** dans les résultats de la recherche.

   > [!TIP]
   > Dans Visual Studio, vous pouvez accéder aux journaux des événements en ouvrant l’**Explorateur de serveurs** à partir du menu **Affichage** (ou appuyez sur **Ctrl**+**Alt**+**S**), puis en développant le nœud **Journaux des événements** pour l’ordinateur local.

2. Dans **l’Observateur d’événements**, développez **Journaux des applications et services**.

3. Recherchez le nom **MyNewLog** (ou **MyLogFile1**, si vous avez utilisé la procédure pour ajouter des arguments de ligne de commande) dans la liste, puis développez-le. Vous devez voir les entrées relatives aux deux actions (démarrage et arrêt) que votre service a effectuées.

     ![Utiliser l'Observateur d'événements pour visualiser les entrées du journal des événements](./media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous n’avez plus besoin de l’application de service Windows, vous pouvez la supprimer.

1. Ouvrez **Invite de commandes développeur pour Visual Studio** avec des informations d'identification administratives.

2. Dans la fenêtre **Invite de commandes développeur pour Visual Studio**, accédez au dossier qui contient la sortie de votre projet.

3. Entrez la commande suivante :

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Si le service se désinstalle correctement, la commande signale qu’il a été correctement supprimé. Pour plus d’informations, consultez [procédure : installer et désinstaller des services](how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez créé le service, vous pouvez :

- Créer un programme d’installation autonome utilisable par d’autres personnes pour installer votre service Windows. Utiliser [WiX Toolset](https://wixtoolset.org/) pour créer un programme d’installation pour un service Windows. Pour d’autres idées, consultez [Créer un package de programme d’installation](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

- Explorer le composant <xref:System.ServiceProcess.ServiceController>, qui vous permet d’envoyer des commandes au service que vous avez installé.

- Au lieu de créer le journal des événements quand l’application s’exécute, utilisez un programme d’installation pour créer un journal des événements quand vous installez l’application. Le journal des événements est supprimé par le programme d’installation quand vous désinstallez l’application. Pour plus d’informations, consultez <xref:System.Diagnostics.EventLogInstaller>.

## <a name="see-also"></a>Voir aussi

- [Applications de service Windows](index.md)
- [Présentation des applications de service Windows](introduction-to-windows-service-applications.md)
- [Comment : déboguer des applications de service Windows](how-to-debug-windows-service-applications.md)
- [Services (Windows)](/windows/desktop/Services/services)
