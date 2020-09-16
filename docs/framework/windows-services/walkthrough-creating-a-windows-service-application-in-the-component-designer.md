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
ms.openlocfilehash: 04f27729b5713c325a73cbdeb1c6c673fe749c00
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544204"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="5605f-104">Didacticiel : créer une application de service Windows</span><span class="sxs-lookup"><span data-stu-id="5605f-104">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="5605f-105">Cet article explique comment créer, dans Visual Studio, une application de service Windows qui écrit des messages dans un journal des événements.</span><span class="sxs-lookup"><span data-stu-id="5605f-105">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="5605f-106">Créer un service</span><span class="sxs-lookup"><span data-stu-id="5605f-106">Create a service</span></span>

<span data-ttu-id="5605f-107">Pour commencer, créez le projet et définissez les valeurs nécessaires au fonctionnement correct du service.</span><span class="sxs-lookup"><span data-stu-id="5605f-107">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="5605f-108">Dans le menu **Fichier** de Visual Studio, sélectionnez **Nouveau** > **Projet** (ou appuyez sur **Ctrl**+**Maj**+**N**) pour ouvrir la fenêtre **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="5605f-108">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="5605f-109">Accédez au modèle de projet **Service Windows (.NET Framework)** et sélectionnez-le.</span><span class="sxs-lookup"><span data-stu-id="5605f-109">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="5605f-110">Pour le trouver, développez **Installé** et \*\*Visual C# \*\* ou **Visual Basic**, puis sélectionnez **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="5605f-110">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="5605f-111">Ou entrez *Service Windows* dans la zone de recherche en haut à droite et appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="5605f-111">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Modèle Windows Service dans la boîte de dialogue Nouveau projet de Visual Studio](./media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="5605f-113">Si vous ne voyez pas le modèle de **service Windows** , vous devrez peut-être installer la charge de travail **développement .net Desktop** :</span><span class="sxs-lookup"><span data-stu-id="5605f-113">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="5605f-114">Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Ouvrir Visual Studio Installer** dans l’angle inférieur gauche.</span><span class="sxs-lookup"><span data-stu-id="5605f-114">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="5605f-115">Sélectionnez la charge de travail **Développement .NET Desktop**, puis sélectionnez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="5605f-115">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="5605f-116">Dans **Nom**, entrez *MyNewService*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="5605f-116">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="5605f-117">L’onglet **Conception** apparaît (**Service1.cs [Conception]** ou **Service1.vb [Conception]**).</span><span class="sxs-lookup"><span data-stu-id="5605f-117">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="5605f-118">Le modèle de projet inclut une classe Component appelée `Service1` qui hérite de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5605f-118">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5605f-119">Elle contient une grande partie du code de service de base, comme le code pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="5605f-119">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="5605f-120">Renommer le service</span><span class="sxs-lookup"><span data-stu-id="5605f-120">Rename the service</span></span>

<span data-ttu-id="5605f-121">Renommez le service **Service1** en **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="5605f-121">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="5605f-122">Dans l’**Explorateur de solutions**, sélectionnez **Service1.cs** ou **Service1.vb**, puis choisissez **Renommer** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="5605f-122">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="5605f-123">Renommez le fichier **MyNewService.cs** ou **MyNewService.vb**, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="5605f-123">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="5605f-124">Une fenêtre contextuelle vous invite à indiquer si vous voulez renommer toutes les références à l’élément de code *Service1*.</span><span class="sxs-lookup"><span data-stu-id="5605f-124">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="5605f-125">Dans la fenêtre contextuelle, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="5605f-125">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="5605f-126">![Renommer l’invite](./media/windows-service-rename.png "Invite de changement de nom du service Windows")</span><span class="sxs-lookup"><span data-stu-id="5605f-126">![Rename prompt](./media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="5605f-127">Sous l’onglet **Conception**, sélectionnez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="5605f-127">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="5605f-128">Dans la fenêtre **Propriétés**, remplacez la valeur **ServiceName** par *MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="5605f-128">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="5605f-129">![Propriétés du service](./media/windows-service-properties.png "Propriétés du service Windows")</span><span class="sxs-lookup"><span data-stu-id="5605f-129">![Service properties](./media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="5605f-130">Sélectionnez **Enregistrer tout** dans le menu **Fichier**.</span><span class="sxs-lookup"><span data-stu-id="5605f-130">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="5605f-131">Ajouter des fonctionnalités au service</span><span class="sxs-lookup"><span data-stu-id="5605f-131">Add features to the service</span></span>

<span data-ttu-id="5605f-132">Dans cette section, vous ajoutez un journal des événements personnalisé au service Windows.</span><span class="sxs-lookup"><span data-stu-id="5605f-132">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="5605f-133">Le composant <xref:System.Diagnostics.EventLog> est un exemple du type de composant que vous pouvez ajouter à un service Windows.</span><span class="sxs-lookup"><span data-stu-id="5605f-133">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="5605f-134">Ajouter une fonctionnalité de journal des événements personnalisé</span><span class="sxs-lookup"><span data-stu-id="5605f-134">Add custom event log functionality</span></span>

1. <span data-ttu-id="5605f-135">Dans l’**Explorateur de solutions**, dans le menu contextuel de **MyNewService.cs** ou **MyNewService.vb**, choisissez **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="5605f-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="5605f-136">Dans **Boîte à outils**, développez **Composants**, puis faites glisser le composant **EventLog** vers l’onglet **Service1.cs [Conception]** ou \*\* Service1.vb [Conception]\*\*.</span><span class="sxs-lookup"><span data-stu-id="5605f-136">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="5605f-137">Dans l’**Explorateur de solutions**, dans le menu contextuel de **MyNewService.cs** ou **MyNewService.vb**, choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="5605f-137">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="5605f-138">Définissez un journal des événements personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5605f-138">Define a custom event log.</span></span> <span data-ttu-id="5605f-139">Pour C#, modifiez le constructeur `MyNewService()` existant ; pour Visual Basic, ajoutez le constructeur `New()` :</span><span class="sxs-lookup"><span data-stu-id="5605f-139">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="5605f-140">Ajoutez une instruction `using` à **MyNewService.cs** (si elle n’existe pas déjà) ou une instruction `Imports` à **MyNewService.vb**, pour l’espace de noms <xref:System.Diagnostics?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="5605f-140">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="5605f-141">Sélectionnez **Enregistrer tout** dans le menu **Fichier**.</span><span class="sxs-lookup"><span data-stu-id="5605f-141">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="5605f-142">Définir les actions à effectuer lors du démarrage du service</span><span class="sxs-lookup"><span data-stu-id="5605f-142">Define what occurs when the service starts</span></span>

<span data-ttu-id="5605f-143">Dans l’éditeur de code pour **MyNewService.cs** ou **MyNewService.vb**, localisez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ; Visual Studio a automatiquement créé une définition de méthode vide quand vous avez créé le projet.</span><span class="sxs-lookup"><span data-stu-id="5605f-143">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="5605f-144">Ajoutez du code qui écrit une entrée dans le journal des événements lorsque le service démarre :</span><span class="sxs-lookup"><span data-stu-id="5605f-144">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="5605f-145">Interrogation</span><span class="sxs-lookup"><span data-stu-id="5605f-145">Polling</span></span>

<span data-ttu-id="5605f-146">Étant donné qu’une application de service est conçue pour être durable, elle interroge ou supervise généralement le système, que vous configurez dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="5605f-146">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="5605f-147">La méthode `OnStart` doit retourner au système d’exploitation une fois que le service a commencé à fonctionner pour que le système ne soit pas bloqué.</span><span class="sxs-lookup"><span data-stu-id="5605f-147">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="5605f-148">Pour configurer un mécanisme d’interrogation simple, utilisez le composant <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5605f-148">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="5605f-149">Le minuteur déclenche un événement <xref:System.Timers.Timer.Elapsed> à intervalles réguliers, moment auquel votre service peut effectuer sa supervision.</span><span class="sxs-lookup"><span data-stu-id="5605f-149">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="5605f-150">Vous utilisez le composant <xref:System.Timers.Timer> comme suit :</span><span class="sxs-lookup"><span data-stu-id="5605f-150">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="5605f-151">Définissez les propriétés du composant <xref:System.Timers.Timer> dans la méthode `MyNewService.OnStart`.</span><span class="sxs-lookup"><span data-stu-id="5605f-151">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="5605f-152">Démarrez le minuteur en appelant la méthode <xref:System.Timers.Timer.Start%2A>.</span><span class="sxs-lookup"><span data-stu-id="5605f-152">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="5605f-153">Configurez le mécanisme d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="5605f-153">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="5605f-154">Ajoutez le code suivant dans l’événement `MyNewService.OnStart` pour configurer le mécanisme d’interrogation :</span><span class="sxs-lookup"><span data-stu-id="5605f-154">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

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

2. <span data-ttu-id="5605f-155">Ajoutez une instruction `using` à **MyNewService.cs** ou une instruction `Imports` à **MyNewService.vb** pour l’espace de noms <xref:System.Timers?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="5605f-155">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="5605f-156">Dans la classe `MyNewService`, ajoutez la méthode `OnTimer` pour gérer l’événement <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="5605f-156">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

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

4. <span data-ttu-id="5605f-157">Dans la classe `MyNewService`, ajoutez une variable membre.</span><span class="sxs-lookup"><span data-stu-id="5605f-157">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="5605f-158">Celle-ci contient l’identificateur de l’événement suivant à écrire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="5605f-158">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="5605f-159">Au lieu d’exécuter tout votre travail sur le thread principal, vous pouvez exécuter des tâches à l’aide de threads de travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5605f-159">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="5605f-160">Pour plus d'informations, consultez <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5605f-160">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="5605f-161">Définir les actions à effectuer lors de l'arrêt du service</span><span class="sxs-lookup"><span data-stu-id="5605f-161">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="5605f-162">Insérez une ligne de code dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStop%2A> qui ajoute une entrée dans le journal des événements lorsque le service est arrêté :</span><span class="sxs-lookup"><span data-stu-id="5605f-162">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="5605f-163">Définir d'autres actions du service</span><span class="sxs-lookup"><span data-stu-id="5605f-163">Define other actions for the service</span></span>

<span data-ttu-id="5605f-164">Vous pouvez substituer les méthodes <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> et <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> afin de définir d'autres types de traitement pour votre composant.</span><span class="sxs-lookup"><span data-stu-id="5605f-164">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="5605f-165">Le code suivant montre comment substituer la méthode <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> dans la classe `MyNewService` :</span><span class="sxs-lookup"><span data-stu-id="5605f-165">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="5605f-166">Définir l’état du service</span><span class="sxs-lookup"><span data-stu-id="5605f-166">Set service status</span></span>

<span data-ttu-id="5605f-167">Les services indiquent leur état au [Gestionnaire de contrôle des services](/windows/desktop/Services/service-control-manager). Les utilisateurs peuvent ainsi déterminer si un service fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="5605f-167">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="5605f-168">Par défaut, un service qui hérite de <xref:System.ServiceProcess.ServiceBase> signale un ensemble limité de paramètres d’état, qui incluent SERVICE_STOPPED, SERVICE_PAUSED et SERVICE_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="5605f-168">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="5605f-169">Si un service prend du temps à démarrer, il s’avère utile de signaler un état SERVICE_START_PENDING.</span><span class="sxs-lookup"><span data-stu-id="5605f-169">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="5605f-170">Vous pouvez implémenter les paramètres d’état SERVICE_START_PENDING et SERVICE_STOP_PENDING en ajoutant du code qui appelle la fonction [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) Windows.</span><span class="sxs-lookup"><span data-stu-id="5605f-170">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="5605f-171">Implémenter l’état de service en attente</span><span class="sxs-lookup"><span data-stu-id="5605f-171">Implement service pending status</span></span>

1. <span data-ttu-id="5605f-172">Ajoutez une instruction `using` à **MyNewService.cs** ou une instruction `Imports` à **MyNewService.vb** pour l’espace de noms <xref:System.Runtime.InteropServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="5605f-172">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="5605f-173">Ajoutez le code suivant à **MyNewService.cs** ou **MyNewService.vb** pour déclarer les valeurs `ServiceState` et ajouter une structure pour l’état. Vous utiliserez cette structure dans un appel de code non managé :</span><span class="sxs-lookup"><span data-stu-id="5605f-173">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

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
    > <span data-ttu-id="5605f-174">La boîte de dialogue Gestionnaire de contrôle des services utilise les membres `dwWaitHint` et `dwCheckpoint` de la [structure SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) pour déterminer le délai d’attente avant le démarrage ou l’arrêt d’un service Windows.</span><span class="sxs-lookup"><span data-stu-id="5605f-174">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/win32/api/winsvc/ns-winsvc-service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="5605f-175">Si l’exécution de vos méthodes `OnStart` et `OnStop` est longue, votre service peut demander plus de temps en appelant à nouveau `SetServiceStatus` avec une valeur `dwCheckPoint` incrémentée.</span><span class="sxs-lookup"><span data-stu-id="5605f-175">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="5605f-176">Dans la classe `MyNewService`, déclarez la fonction [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) à l’aide d’un [appel de code non managé](../interop/consuming-unmanaged-dll-functions.md) :</span><span class="sxs-lookup"><span data-stu-id="5605f-176">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="5605f-177">Pour implémenter l’état SERVICE_START_PENDING, ajoutez le code suivant au début de la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> :</span><span class="sxs-lookup"><span data-stu-id="5605f-177">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

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

5. <span data-ttu-id="5605f-178">Ajoutez du code à la fin de la méthode `OnStart` pour affecter à l’état la valeur SERVICE_RUNNING :</span><span class="sxs-lookup"><span data-stu-id="5605f-178">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

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

6. <span data-ttu-id="5605f-179">(Facultatif) Si <xref:System.ServiceProcess.ServiceBase.OnStop%2A> est une méthode durable, répétez cette procédure dans la méthode `OnStop`.</span><span class="sxs-lookup"><span data-stu-id="5605f-179">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="5605f-180">Implémentez l’état SERVICE_STOP_PENDING et retournez l’état SERVICE_STOPPED avant la fin de la méthode `OnStop`.</span><span class="sxs-lookup"><span data-stu-id="5605f-180">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="5605f-181">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5605f-181">For example:</span></span>

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

## <a name="add-installers-to-the-service"></a><span data-ttu-id="5605f-182">Ajouter des programmes d'installation pour le service</span><span class="sxs-lookup"><span data-stu-id="5605f-182">Add installers to the service</span></span>

<span data-ttu-id="5605f-183">Avant d’exécuter un service Windows, vous devez l’installer, ce qui ’inscrit auprès du Gestionnaire de contrôle des services.</span><span class="sxs-lookup"><span data-stu-id="5605f-183">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="5605f-184">Ajoutez à votre projet des programmes d’installation pour gérer les détails de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="5605f-184">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="5605f-185">Dans l’**Explorateur de solutions**, dans le menu contextuel de **MyNewService.cs** ou **MyNewService.vb**, choisissez **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="5605f-185">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="5605f-186">En mode **Conception**, sélectionnez la zone d’arrière-plan, puis choisissez **Ajouter le programme d’installation** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="5605f-186">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="5605f-187">Par défaut, Visual Studio ajoute une classe Component nommée `ProjectInstaller`, qui contient deux programmes d’installation, à votre projet.</span><span class="sxs-lookup"><span data-stu-id="5605f-187">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="5605f-188">Ces programmes d’installation sont destinés à votre service et au processus associé du service.</span><span class="sxs-lookup"><span data-stu-id="5605f-188">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="5605f-189">En mode **Conception** pour **ProjectInstaller**, sélectionnez **serviceInstaller1** pour un projet Visual C# ou **ServiceInstaller1** pour un projet Visual Basic, puis choisissez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="5605f-189">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="5605f-190">Dans la fenêtre **Propriétés**, vérifiez que la propriété <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> a la valeur **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="5605f-190">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="5605f-191">Ajoutez du texte à la propriété <xref:System.ServiceProcess.ServiceInstaller.Description%2A>, comme *Un exemple de service*.</span><span class="sxs-lookup"><span data-stu-id="5605f-191">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="5605f-192">Ce texte apparaît dans la colonne **Description** de la fenêtre **Services** et explique le service à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5605f-192">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="5605f-193">![Description du service dans la fenêtre Services.](./media/windows-service-description.png "Description du service")</span><span class="sxs-lookup"><span data-stu-id="5605f-193">![Service description in the Services window.](./media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="5605f-194">Ajoutez du texte à la propriété <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A>.</span><span class="sxs-lookup"><span data-stu-id="5605f-194">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="5605f-195">Par exemple, *Nom complet de MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="5605f-195">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="5605f-196">Ce texte apparaît dans la colonne **Nom complet** de la fenêtre **Services**.</span><span class="sxs-lookup"><span data-stu-id="5605f-196">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="5605f-197">Ce nom peut être différent de la propriété <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, qui est le nom utilisé par le système (par exemple, le nom que vous utilisez pour la commande `net start` pour démarrer votre service).</span><span class="sxs-lookup"><span data-stu-id="5605f-197">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="5605f-198">Affectez à la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> la valeur <xref:System.ServiceProcess.ServiceStartMode.Automatic> à partir de la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5605f-198">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="5605f-199">Quand vous avez terminé, la fenêtre **Propriétés** doit ressembler à la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="5605f-199">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="5605f-200">![Propriétés du programme d’installation pour un service Windows](./media/windows-service-installer-properties.png "Propriétés du programme d’installation du service Windows")</span><span class="sxs-lookup"><span data-stu-id="5605f-200">![Installer Properties for a Windows service](./media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="5605f-201">En mode **Conception** pour **ProjectInstaller**, choisissez **serviceProcessInstaller1** pour un projet Visual C# ou **ServiceProcessInstaller1** pour un projet Visual Basic, puis choisissez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="5605f-201">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="5605f-202">Affectez à la propriété <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> la valeur <xref:System.ServiceProcess.ServiceAccount.LocalSystem> à partir de la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5605f-202">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="5605f-203">Ce paramètre installe le service et l’exécute en utilisant le compte système local.</span><span class="sxs-lookup"><span data-stu-id="5605f-203">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5605f-204">Le compte <xref:System.ServiceProcess.ServiceAccount.LocalSystem> dispose d'autorisations générales, y compris la possibilité d'écrire dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="5605f-204">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="5605f-205">Utilisez ce compte avec précaution car il peut augmenter le risque d'attaques par des logiciels malveillants.</span><span class="sxs-lookup"><span data-stu-id="5605f-205">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="5605f-206">Pour les autres tâches, utilisez le compte <xref:System.ServiceProcess.ServiceAccount.LocalService> , qui se comporte comme un utilisateur non privilégié de l'ordinateur local et présente des informations d'identification anonymes à tout serveur distant.</span><span class="sxs-lookup"><span data-stu-id="5605f-206">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="5605f-207">Cet exemple échoue si vous essayez d'utiliser le compte <xref:System.ServiceProcess.ServiceAccount.LocalService> , car il doit disposer d'une autorisation pour écrire dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="5605f-207">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="5605f-208">Pour plus d’informations sur les programmes d’installation, consultez [Comment : ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="5605f-208">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="5605f-209">(Facultatif) Définition de paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="5605f-209">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="5605f-210">Avant de décider d’ajouter des paramètres de démarrage, déterminez si c’est le meilleur moyen de passer des informations à votre service.</span><span class="sxs-lookup"><span data-stu-id="5605f-210">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="5605f-211">Bien qu’ils soient faciles à utiliser et à analyser et qu’un utilisateur puisse facilement les substituer, ils peuvent être plus difficiles à découvrir et utiliser pour un utilisateur sans documentation.</span><span class="sxs-lookup"><span data-stu-id="5605f-211">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="5605f-212">En général, si votre service nécessite seulement quelques paramètres de démarrage, il est préférable d’utiliser plutôt le Registre ou un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5605f-212">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="5605f-213">Un service Windows peut accepter des arguments de ligne de commande ou des paramètres de démarrage.</span><span class="sxs-lookup"><span data-stu-id="5605f-213">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="5605f-214">Quand vous ajoutez du code pour traiter des paramètres de démarrage, un utilisateur peut démarrer votre service avec ses propres paramètres de démarrage personnalisés dans la fenêtre des propriétés du service.</span><span class="sxs-lookup"><span data-stu-id="5605f-214">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="5605f-215">Toutefois, ces paramètres de démarrage ne sont pas persistants lors du prochain démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="5605f-215">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="5605f-216">Pour définir des paramètres de démarrage de façon définitive, faites-le dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="5605f-216">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="5605f-217">Chaque service Windows a une entrée de Registre sous la sous-clé **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services**.</span><span class="sxs-lookup"><span data-stu-id="5605f-217">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="5605f-218">Sous la sous-clé de chaque service, utilisez la sous-clé **Parameters** pour stocker les informations auxquelles votre service peut accéder.</span><span class="sxs-lookup"><span data-stu-id="5605f-218">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="5605f-219">Vous pouvez utiliser des fichiers de configuration d'application pour un service Windows de la même façon que vous le faites pour les autres types de programmes.</span><span class="sxs-lookup"><span data-stu-id="5605f-219">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="5605f-220">Pour l’exemple de code, consultez <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5605f-220">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="5605f-221">Pour ajouter des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="5605f-221">To add startup parameters</span></span>

1. <span data-ttu-id="5605f-222">Sélectionnez **Program.cs** ou **MyNewService.Designer.vb**, puis choisissez **Afficher le code** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="5605f-222">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="5605f-223">Dans la méthode `Main`, modifiez le code pour ajouter un paramètre d’entrée et le passer au constructeur du service :</span><span class="sxs-lookup"><span data-stu-id="5605f-223">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="5605f-224">Dans **MyNewService.cs** ou **MyNewService.vb**, modifiez le constructeur `MyNewService` pour traiter le paramètre d’entrée comme suit :</span><span class="sxs-lookup"><span data-stu-id="5605f-224">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

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

   <span data-ttu-id="5605f-225">Ce code définit la source de l’événement et le nom du journal en fonction des paramètres de démarrage fournis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5605f-225">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="5605f-226">Si aucun argument n’est fourni, les valeurs par défaut sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="5605f-226">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="5605f-227">Pour spécifier les arguments de ligne de commande, ajoutez le code suivant à la classe `ProjectInstaller` dans **ProjectInstaller.cs** ou **ProjectInstaller.vb** :</span><span class="sxs-lookup"><span data-stu-id="5605f-227">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

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

   <span data-ttu-id="5605f-228">En règle générale, cette valeur contient le chemin complet de l’exécutable du service Windows.</span><span class="sxs-lookup"><span data-stu-id="5605f-228">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="5605f-229">Pour que le service démarre correctement, l’utilisateur doit fournir des guillemets pour le chemin et chaque paramètre individuel.</span><span class="sxs-lookup"><span data-stu-id="5605f-229">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="5605f-230">Un utilisateur peut changer les paramètres dans l’entrée de Registre **ImagePath** pour changer les paramètres de démarrage du service Windows.</span><span class="sxs-lookup"><span data-stu-id="5605f-230">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="5605f-231">Toutefois, un meilleur moyen consiste à changer la valeur programmatiquement et à exposer les fonctionnalités de manière conviviale, par exemple à l’aide d’un utilitaire de gestion ou de configuration.</span><span class="sxs-lookup"><span data-stu-id="5605f-231">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="5605f-232">Générer le service</span><span class="sxs-lookup"><span data-stu-id="5605f-232">Build the service</span></span>

1. <span data-ttu-id="5605f-233">Dans l’**Explorateur de solutions**, choisissez **Propriétés** dans le menu contextuel du projet **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="5605f-233">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="5605f-234">Les pages de propriétés de votre projet s'affichent.</span><span class="sxs-lookup"><span data-stu-id="5605f-234">The property pages for your project appear.</span></span>

2. <span data-ttu-id="5605f-235">Sous l’onglet **Application**, dans la liste **Objet de démarrage**, choisissez **MyNewService.Program** ou **Sub Main** pour les projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5605f-235">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="5605f-236">Pour générer le projet, dans l’**Explorateur de solutions**, choisissez **Build** dans le menu contextuel de votre projet (ou appuyez sur **Ctrl**+**Maj**+**B**).</span><span class="sxs-lookup"><span data-stu-id="5605f-236">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="5605f-237">Installer le service</span><span class="sxs-lookup"><span data-stu-id="5605f-237">Install the service</span></span>

<span data-ttu-id="5605f-238">Maintenant que vous avez généré le service Windows, vous pouvez l'installer.</span><span class="sxs-lookup"><span data-stu-id="5605f-238">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="5605f-239">Pour installer un service Windows, vous devez disposer d’informations d’identification d’administrateur sur l’ordinateur sur lequel il est installé.</span><span class="sxs-lookup"><span data-stu-id="5605f-239">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="5605f-240">Ouvrez [Invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md) avec des informations d'identification administratives.</span><span class="sxs-lookup"><span data-stu-id="5605f-240">Open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) with administrative credentials.</span></span> <span data-ttu-id="5605f-241">À partir du menu **Démarrer** de Windows, sélectionnez **Invite de commandes développeur pour VS 2017** dans le dossier Visual Studio, puis sélectionnez **Plus** > **Exécuter en tant qu’administrateur** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="5605f-241">From the Windows **Start** menu, select **Developer Command Prompt for VS 2017** in the Visual Studio folder, then select **More** > **Run as Administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="5605f-242">Dans la fenêtre **Invite de commandes développeur pour Visual Studio**, accédez au dossier qui contient la sortie de votre projet (par défaut, le sous-répertoire *\bin\Debug* de votre projet).</span><span class="sxs-lookup"><span data-stu-id="5605f-242">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="5605f-243">Entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5605f-243">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="5605f-244">Si le service s’installe correctement, la commande signale une réussite.</span><span class="sxs-lookup"><span data-stu-id="5605f-244">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="5605f-245">Si le système ne trouve pas *installutil.exe*, vérifiez qu’il existe sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5605f-245">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="5605f-246">Cet outil est installé avec le .NET Framework dans le dossier *%windir%\Microsoft.NET\Framework [64] \\ &lt; &gt; version du .NET Framework*.</span><span class="sxs-lookup"><span data-stu-id="5605f-246">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="5605f-247">Par exemple, le chemin par défaut pour la version 64 bits est *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="5605f-247">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="5605f-248">Si le processus **installutil.exe** échoue, examinez le journal d’installation pour en connaître la raison.</span><span class="sxs-lookup"><span data-stu-id="5605f-248">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="5605f-249">Par défaut, le journal se trouve dans le même dossier que l’exécutable du service.</span><span class="sxs-lookup"><span data-stu-id="5605f-249">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="5605f-250">L’installation peut échouer si :</span><span class="sxs-lookup"><span data-stu-id="5605f-250">The installation can fail if:</span></span>
    - <span data-ttu-id="5605f-251">La classe <xref:System.ComponentModel.RunInstallerAttribute> n’est pas présente sur la classe `ProjectInstaller`.</span><span class="sxs-lookup"><span data-stu-id="5605f-251">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="5605f-252">L’attribut n’a pas la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="5605f-252">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="5605f-253">La classe `ProjectInstaller` n’est pas définie en tant que `public`.</span><span class="sxs-lookup"><span data-stu-id="5605f-253">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="5605f-254">Pour plus d’informations, consultez [procédure : installer et désinstaller des services](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="5605f-254">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="5605f-255">Démarrer et exécuter le service</span><span class="sxs-lookup"><span data-stu-id="5605f-255">Start and run the service</span></span>

1. <span data-ttu-id="5605f-256">Dans Windows, ouvrez l’application de bureau **Services**.</span><span class="sxs-lookup"><span data-stu-id="5605f-256">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="5605f-257">Appuyez sur **Windows** + **R** pour ouvrir la zone **exécuter** , entrez *services. msc*, puis appuyez sur **entrée** ou sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="5605f-257">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="5605f-258">Votre service doit être répertorié dans **Services**, affiché par ordre alphabétique du nom d’affichage que vous lui avez donné.</span><span class="sxs-lookup"><span data-stu-id="5605f-258">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService dans la fenêtre Services.](./media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="5605f-260">Pour démarrer le service, choisissez **Démarrer** dans le menu contextuel du service.</span><span class="sxs-lookup"><span data-stu-id="5605f-260">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="5605f-261">Pour arrêter le service, choisissez **Arrêter** dans le menu contextuel du service.</span><span class="sxs-lookup"><span data-stu-id="5605f-261">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="5605f-262">(Facultatif) À partir de la ligne de commande, utilisez les commandes **net start &lt;nom du service&gt;** et **net stop &lt;nom du service&gt;** pour démarrer et arrêter votre service.</span><span class="sxs-lookup"><span data-stu-id="5605f-262">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="5605f-263">Vérifier la sortie du journal des événements de votre service</span><span class="sxs-lookup"><span data-stu-id="5605f-263">Verify the event log output of your service</span></span>

1. <span data-ttu-id="5605f-264">Dans Windows, ouvrez l’application de bureau **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="5605f-264">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="5605f-265">Entrez *Observateur d’événements* dans la barre de recherche Windows, puis sélectionnez **Observateur d’événements** dans les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="5605f-265">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="5605f-266">Dans Visual Studio, vous pouvez accéder aux journaux des événements en ouvrant l’**Explorateur de serveurs** à partir du menu **Affichage** (ou appuyez sur **Ctrl**+**Alt**+**S**), puis en développant le nœud **Journaux des événements** pour l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5605f-266">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="5605f-267">Dans **l’Observateur d’événements**, développez **Journaux des applications et services**.</span><span class="sxs-lookup"><span data-stu-id="5605f-267">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="5605f-268">Recherchez le nom **MyNewLog** (ou **MyLogFile1**, si vous avez utilisé la procédure pour ajouter des arguments de ligne de commande) dans la liste, puis développez-le.</span><span class="sxs-lookup"><span data-stu-id="5605f-268">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="5605f-269">Vous devez voir les entrées relatives aux deux actions (démarrage et arrêt) que votre service a effectuées.</span><span class="sxs-lookup"><span data-stu-id="5605f-269">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Utiliser l'Observateur d'événements pour visualiser les entrées du journal des événements](./media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="5605f-271">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="5605f-271">Clean up resources</span></span>

<span data-ttu-id="5605f-272">Si vous n’avez plus besoin de l’application de service Windows, vous pouvez la supprimer.</span><span class="sxs-lookup"><span data-stu-id="5605f-272">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="5605f-273">Ouvrez **Invite de commandes développeur pour Visual Studio** avec des informations d'identification administratives.</span><span class="sxs-lookup"><span data-stu-id="5605f-273">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="5605f-274">Dans la fenêtre **Invite de commandes développeur pour Visual Studio**, accédez au dossier qui contient la sortie de votre projet.</span><span class="sxs-lookup"><span data-stu-id="5605f-274">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="5605f-275">Entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5605f-275">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="5605f-276">Si le service se désinstalle correctement, la commande signale qu’il a été correctement supprimé.</span><span class="sxs-lookup"><span data-stu-id="5605f-276">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="5605f-277">Pour plus d’informations, consultez [procédure : installer et désinstaller des services](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="5605f-277">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5605f-278">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5605f-278">Next steps</span></span>

<span data-ttu-id="5605f-279">Maintenant que vous avez créé le service, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="5605f-279">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="5605f-280">Créer un programme d’installation autonome utilisable par d’autres personnes pour installer votre service Windows.</span><span class="sxs-lookup"><span data-stu-id="5605f-280">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="5605f-281">Utiliser [WiX Toolset](https://wixtoolset.org/) pour créer un programme d’installation pour un service Windows.</span><span class="sxs-lookup"><span data-stu-id="5605f-281">Use the [WiX Toolset](https://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="5605f-282">Pour d’autres idées, consultez [Créer un package de programme d’installation](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="5605f-282">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="5605f-283">Explorer le composant <xref:System.ServiceProcess.ServiceController>, qui vous permet d’envoyer des commandes au service que vous avez installé.</span><span class="sxs-lookup"><span data-stu-id="5605f-283">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="5605f-284">Au lieu de créer le journal des événements quand l’application s’exécute, utilisez un programme d’installation pour créer un journal des événements quand vous installez l’application.</span><span class="sxs-lookup"><span data-stu-id="5605f-284">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="5605f-285">Le journal des événements est supprimé par le programme d’installation quand vous désinstallez l’application.</span><span class="sxs-lookup"><span data-stu-id="5605f-285">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="5605f-286">Pour plus d'informations, consultez <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="5605f-286">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5605f-287">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5605f-287">See also</span></span>

- [<span data-ttu-id="5605f-288">Applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="5605f-288">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="5605f-289">Présentation des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="5605f-289">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="5605f-290">Comment : déboguer des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="5605f-290">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="5605f-291">Services (Windows)</span><span class="sxs-lookup"><span data-stu-id="5605f-291">Services (Windows)</span></span>](/windows/desktop/Services/services)
