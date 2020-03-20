---
title: 'Tutorial: Hébergez et exécutez un service de base de la Fondation De communication Windows'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184082"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="0b71c-102">Tutorial: Hébergez et exécutez un service de base de la Fondation De communication Windows</span><span class="sxs-lookup"><span data-stu-id="0b71c-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="0b71c-103">Ce tutoriel décrit la troisième des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0b71c-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="0b71c-104">Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="0b71c-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="0b71c-105">La prochaine tâche pour créer une application WCF est d’héberger un service WCF dans une application console.</span><span class="sxs-lookup"><span data-stu-id="0b71c-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="0b71c-106">Un service WCF expose un ou plusieurs critères de *terminaison,* chacun d’eux qui expose une ou plusieurs opérations de service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="0b71c-107">Un critère de service spécifie les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0b71c-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="0b71c-108">Une adresse où vous pouvez trouver le service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-108">An address where you can find the service.</span></span>
- <span data-ttu-id="0b71c-109">Une liaison qui contient l’information qui décrit comment un client doit communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-109">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="0b71c-110">Un contrat qui définit la fonctionnalité que le service fournit à ses clients.</span><span class="sxs-lookup"><span data-stu-id="0b71c-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="0b71c-111">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="0b71c-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0b71c-112">Créez et configurez un projet d’application console pour l’hébergement d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="0b71c-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="0b71c-113">Ajoutez du code pour accueillir le service WCF.</span><span class="sxs-lookup"><span data-stu-id="0b71c-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="0b71c-114">Mettre à jour le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0b71c-114">Update the configuration file.</span></span>
> - <span data-ttu-id="0b71c-115">Démarrez le service WCF et vérifiez qu’il est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0b71c-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="0b71c-116">Créer et configurer un projet d’application console pour l’hébergement du service</span><span class="sxs-lookup"><span data-stu-id="0b71c-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="0b71c-117">Créez un projet d’application console dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="0b71c-117">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="0b71c-118">Du menu **Fichier,** sélectionnez **Open** > **Project/Solution** et naviguez vers la solution **GettingStarted** que vous avez déjà créée (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="0b71c-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="0b71c-119">Sélectionnez **uvrir**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-119">Select **Open**.</span></span>

    2. <span data-ttu-id="0b71c-120">Du menu **View,** sélectionnez **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-120">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="0b71c-121">Dans la fenêtre **Solution Explorer,** sélectionnez la solution **GettingStarted** (nœud supérieur), puis **sélectionnez Ajouter** > **un nouveau projet** dans le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="0b71c-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="0b71c-122">Dans la fenêtre **Add New Project,** sur le côté gauche, sélectionnez la catégorie **Windows Desktop** sous Visual **C ou** **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="0b71c-123">Sélectionnez le modèle **Console App (.NET Framework)** et *entrez GettingStartedHost* pour le **nom**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="0b71c-124">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-124">Select **OK**.</span></span>

2. <span data-ttu-id="0b71c-125">Ajoutez une référence dans le projet **GettingStartedHost** au projet **GettingStartedLib** :</span><span class="sxs-lookup"><span data-stu-id="0b71c-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="0b71c-126">Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **Références** dans le cadre du projet **GettingStartedHost,** puis **sélectionnez Ajouter la référence** dans le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="0b71c-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="0b71c-127">Dans le dialogue **Add Reference,** dans le cadre **de Projets** sur le côté gauche de la fenêtre, sélectionnez **Solution**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="0b71c-128">Sélectionnez **GettingStartedLib** dans la section centrale de la fenêtre, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="0b71c-129">Cette action met les types définis dans le projet **GettingStartedLib** à la disposition du projet **GettingStartedHost.**</span><span class="sxs-lookup"><span data-stu-id="0b71c-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="0b71c-130">Ajoutez une référence dans le projet **GettingStartedHost** à l’assemblage <xref:System.ServiceModel> :</span><span class="sxs-lookup"><span data-stu-id="0b71c-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="0b71c-131">Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **Références** dans le cadre du projet **GettingStartedHost,** puis **sélectionnez Ajouter la référence** dans le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="0b71c-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="0b71c-132">Dans la fenêtre **Add Reference,** sous **les assemblées** sur le côté gauche de la fenêtre, sélectionnez **Cadre**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="0b71c-133">Sélectionnez **System.ServiceModel**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-133">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="0b71c-134">Enregistrer la solution en sélectionnant **File** > **Save All**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="0b71c-135">Ajouter du code pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="0b71c-135">Add code to host the service</span></span>

<span data-ttu-id="0b71c-136">Pour accueillir le service, vous ajoutez du code pour faire les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0b71c-136">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="0b71c-137">Créez un URI pour l’adresse de base.</span><span class="sxs-lookup"><span data-stu-id="0b71c-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="0b71c-138">Créez un exemple de classe pour l’hébergement du service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="0b71c-139">Créez un critère de service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="0b71c-140">Activer l'échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0b71c-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="0b71c-141">Ouvrez l’hôte du service pour écouter les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="0b71c-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="0b71c-142">Apportez les modifications suivantes au code :</span><span class="sxs-lookup"><span data-stu-id="0b71c-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="0b71c-143">Ouvrez le fichier **Program.cs** ou **Module1.vb** dans le projet **GettingStartedHost** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0b71c-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```

    <span data-ttu-id="0b71c-144">Pour plus d’informations sur le fonctionnement de ce code, voir [les étapes du programme d’hébergement service](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="0b71c-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="0b71c-145">Mettre à jour les propriétés du projet :</span><span class="sxs-lookup"><span data-stu-id="0b71c-145">Update the project properties:</span></span>

   1. <span data-ttu-id="0b71c-146">Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **GettingStartedHost,** puis sélectionnez **les propriétés** du menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="0b71c-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="0b71c-147">Sur la page des propriétés **GettingStartedHost,** sélectionnez **l’onglet Application** :</span><span class="sxs-lookup"><span data-stu-id="0b71c-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="0b71c-148">Pour les projets C, **sélectionnez GettingStartedHost.Program** dans la liste **d’objets Startup.**</span><span class="sxs-lookup"><span data-stu-id="0b71c-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="0b71c-149">Pour les projets Visual Basic, sélectionnez **Service.Program** de la liste **d’objets Startup.**</span><span class="sxs-lookup"><span data-stu-id="0b71c-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="0b71c-150">Dans le menu **Fichier,** sélectionnez **Enregistrer tous**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="0b71c-151">Vérifier le fonctionnement du service</span><span class="sxs-lookup"><span data-stu-id="0b71c-151">Verify the service is working</span></span>

1. <span data-ttu-id="0b71c-152">Construisez la solution, puis exécutez l’application de console **GettingStartedHost** depuis Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b71c-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="0b71c-153">Le service doit être exécuté avec les privilèges de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="0b71c-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="0b71c-154">Parce que vous avez ouvert Visual Studio avec des privilèges d’administrateur, lorsque vous **exécutez GettingStartedHost** dans Visual Studio, l’application est gérée avec des privilèges d’administrateur ainsi.</span><span class="sxs-lookup"><span data-stu-id="0b71c-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="0b71c-155">Comme alternative, vous pouvez ouvrir une nouvelle invite de commande en tant qu’administrateur (sélectionnez **More** > **Run comme administrateur** du menu raccourci) et exécuter **GettingStartedHost.exe** en elle.</span><span class="sxs-lookup"><span data-stu-id="0b71c-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="0b71c-156">Ouvrez un navigateur Web et naviguez `http://localhost:8000/GettingStarted/CalculatorService`sur la page du service à .</span><span class="sxs-lookup"><span data-stu-id="0b71c-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0b71c-157">Des services comme celui-ci nécessitent la permission appropriée d’enregistrer les adresses HTTP sur la machine pour l’écoute.</span><span class="sxs-lookup"><span data-stu-id="0b71c-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="0b71c-158">Les comptes Administrateur possèdent cette autorisation, mais l'autorisation pour les espaces de noms HTTP doit être accordée aux comptes qui ne sont pas administrateur.</span><span class="sxs-lookup"><span data-stu-id="0b71c-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="0b71c-159">Pour plus d’informations sur la configuration des réservations d’espaces de noms, consultez [Configuration de HTTP et HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="0b71c-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="0b71c-160">Étapes du programme d’hébergement de services</span><span class="sxs-lookup"><span data-stu-id="0b71c-160">Service hosting program steps</span></span>

<span data-ttu-id="0b71c-161">Les étapes du code que vous avez ajoutée pour héberger le service sont décrites comme suit :</span><span class="sxs-lookup"><span data-stu-id="0b71c-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="0b71c-162">**Étape 1**: Créez `Uri` une instance de la classe pour tenir l’adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="0b71c-163">Une URL qui contient une adresse de base dispose d’une URI facultative qui identifie un service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="0b71c-164">L’adresse de base est `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`formatée comme suit: .</span><span class="sxs-lookup"><span data-stu-id="0b71c-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="0b71c-165">L’adresse de base pour le service de calculatrice utilise le transport HTTP, localhost, port 8000, et le segment URI, GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="0b71c-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="0b71c-166">**Étape 2**: Créez <xref:System.ServiceModel.ServiceHost> une instance de la classe, que vous utilisez pour accueillir le service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="0b71c-167">Le constructeur prend deux paramètres : le type de classe qui met en œuvre le contrat de service et l’adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="0b71c-168">**Étape 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Créer une instance.</span><span class="sxs-lookup"><span data-stu-id="0b71c-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="0b71c-169">Un point de terminaison de service est composé d'une adresse, d'une liaison et d'un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="0b71c-170">Le <xref:System.ServiceModel.Description.ServiceEndpoint> constructeur est composé du type d’interface de contrat de service, d’une liaison et d’une adresse.</span><span class="sxs-lookup"><span data-stu-id="0b71c-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="0b71c-171">Le contrat de service est `ICalculator`, que vous définissez et implémentez dans le type de service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="0b71c-172">La liaison pour <xref:System.ServiceModel.WSHttpBinding>cet échantillon est , qui est une liaison intégrée et se connecte à des points de terminaison qui se conforment aux spécifications WS-MD.</span><span class="sxs-lookup"><span data-stu-id="0b71c-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="0b71c-173">Pour plus d’informations sur les liaisons WCF, voir [aperçu des liaisons WCF](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0b71c-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="0b71c-174">Vous appendicez l’adresse à l’adresse de base pour identifier le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0b71c-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="0b71c-175">Le code spécifie l’adresse en tant que `http://localhost:8000/GettingStarted/CalculatorService`CalculatorService et l’adresse entièrement qualifiée pour le point de terminaison comme .</span><span class="sxs-lookup"><span data-stu-id="0b71c-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0b71c-176">Pour .NET Framework Version 4 et plus tard, l’ajout d’un critère de service est facultatif.</span><span class="sxs-lookup"><span data-stu-id="0b71c-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="0b71c-177">Pour ces versions, si vous n’ajoutez pas votre code ou configuration, WCF ajoute un point de terminaison par défaut pour chaque combinaison d’adresse de base et de contrat implémenté par le service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="0b71c-178">Pour plus d’informations sur les paramètres par défaut, voir [Spécifier une adresse de point final](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="0b71c-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="0b71c-179">Pour plus d’informations sur les paramètres, les liaisons et les comportements par défaut, voir [configuration simplifiée](simplified-configuration.md) et [configuration simplifiée pour les services WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b71c-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="0b71c-180">**Étape 4**: Activez l’échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0b71c-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="0b71c-181">Les clients utilisent l’échange de métadonnées pour générer des procurations pour appeler les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="0b71c-182">Pour permettre l’échange de <xref:System.ServiceModel.Description.ServiceMetadataBehavior> métadonnées, `true`créez une `ServiceMetadataBehavior` instance, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> définissez <xref:System.ServiceModel.ServiceHost> sa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> propriété et ajoutez l’objet à la collection de l’instance.</span><span class="sxs-lookup"><span data-stu-id="0b71c-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="0b71c-183">**Étape 5** <xref:System.ServiceModel.ServiceHost> : Ouvert pour écouter les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="0b71c-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="0b71c-184">L’application vous attend pour appuyer **sur Enter**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="0b71c-185">Après l’application <xref:System.ServiceModel.ServiceHost>instantiates , il exécute un bloc d’essai/ capture.</span><span class="sxs-lookup"><span data-stu-id="0b71c-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="0b71c-186">Pour plus d’informations sur <xref:System.ServiceModel.ServiceHost>la capture en toute sécurité des exceptions jetées par , voir [Use Close et Abort pour libérer les ressources des clients WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="0b71c-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b71c-187">Lorsque vous ajoutez une bibliothèque de service WCF, Visual Studio l’héberge pour vous si vous la déboçonnez en lançant un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="0b71c-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="0b71c-188">Pour éviter les conflits, vous pouvez empêcher Visual Studio d’accueillir la bibliothèque de services WCF.</span><span class="sxs-lookup"><span data-stu-id="0b71c-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="0b71c-189">Sélectionnez le projet **GettingStartedLib** dans **Solution Explorer** et choisissez **les propriétés** dans le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="0b71c-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="0b71c-190">Sélectionnez **WCF Options** et décocher **Démarrer WCF Service Host lors de débogage d’un autre projet dans la même solution**.</span><span class="sxs-lookup"><span data-stu-id="0b71c-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0b71c-191">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0b71c-191">Next steps</span></span>

<span data-ttu-id="0b71c-192">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="0b71c-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0b71c-193">Créez et configurez un projet d’application console pour l’hébergement d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="0b71c-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="0b71c-194">Ajoutez du code pour accueillir le service WCF.</span><span class="sxs-lookup"><span data-stu-id="0b71c-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="0b71c-195">Mettre à jour le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0b71c-195">Update the configuration file.</span></span>
> - <span data-ttu-id="0b71c-196">Démarrez le service WCF et vérifiez qu’il est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0b71c-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="0b71c-197">Avancez au tutoriel suivant pour apprendre à créer un client WCF.</span><span class="sxs-lookup"><span data-stu-id="0b71c-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b71c-198">Tutorial: Créer un client WCF</span><span class="sxs-lookup"><span data-stu-id="0b71c-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
