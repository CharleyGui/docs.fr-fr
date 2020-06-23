---
title: 'Didacticiel : héberger et exécuter un service Windows Communication Foundation de base'
description: Découvrez comment héberger un service WCF dans une application console dans le cadre d’une série d’articles qui vous permettent de commencer à créer une application WCF.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 5318991087e71430523681d601d3b38c4513027b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246127"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="f2178-103">Didacticiel : héberger et exécuter un service Windows Communication Foundation de base</span><span class="sxs-lookup"><span data-stu-id="f2178-103">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="f2178-104">Ce didacticiel décrit la troisième des cinq tâches requises pour créer une application de base Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f2178-104">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="f2178-105">Pour obtenir une vue d’ensemble des didacticiels, consultez [Didacticiel : prise en main des applications Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f2178-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="f2178-106">La tâche suivante pour créer une application WCF consiste à héberger un service WCF dans une application console.</span><span class="sxs-lookup"><span data-stu-id="f2178-106">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="f2178-107">Un service WCF expose un ou plusieurs *points de terminaison*, chacun d’entre eux exposant une ou plusieurs opérations de service.</span><span class="sxs-lookup"><span data-stu-id="f2178-107">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="f2178-108">Un point de terminaison de service spécifie les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2178-108">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="f2178-109">Adresse à laquelle vous pouvez trouver le service.</span><span class="sxs-lookup"><span data-stu-id="f2178-109">An address where you can find the service.</span></span>
- <span data-ttu-id="f2178-110">Liaison qui contient les informations qui décrivent comment un client doit communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="f2178-110">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="f2178-111">Contrat qui définit les fonctionnalités fournies par le service à ses clients.</span><span class="sxs-lookup"><span data-stu-id="f2178-111">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="f2178-112">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="f2178-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f2178-113">Créez et configurez un projet d’application console pour l’hébergement d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="f2178-113">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="f2178-114">Ajoutez du code pour héberger le service WCF.</span><span class="sxs-lookup"><span data-stu-id="f2178-114">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="f2178-115">Mettez à jour le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f2178-115">Update the configuration file.</span></span>
> - <span data-ttu-id="f2178-116">Démarrez le service WCF et vérifiez qu’il est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f2178-116">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="f2178-117">Créer et configurer un projet d’application console pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="f2178-117">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="f2178-118">Créez un projet d’application console dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="f2178-118">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="f2178-119">Dans le menu **fichier** , sélectionnez **ouvrir**  >  un**projet/une solution** , puis accédez à la solution **gettingstarted** que vous avez créée précédemment (*gettingstarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="f2178-119">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="f2178-120">Sélectionnez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="f2178-120">Select **Open**.</span></span>

    2. <span data-ttu-id="f2178-121">Dans le menu **affichage** , sélectionnez **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="f2178-121">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="f2178-122">Dans la fenêtre **Explorateur de solutions** , sélectionnez la solution **gettingstarted** (nœud supérieur), puis sélectionnez **Ajouter**  >  **un nouveau projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f2178-122">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="f2178-123">Dans la fenêtre **Ajouter un nouveau projet** , sur le côté gauche, sélectionnez la catégorie **Bureau Windows** sous **Visual C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="f2178-123">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="f2178-124">Sélectionnez le modèle **application console (.NET Framework)** , puis entrez *GettingStartedHost* pour le **nom**.</span><span class="sxs-lookup"><span data-stu-id="f2178-124">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="f2178-125">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2178-125">Select **OK**.</span></span>

2. <span data-ttu-id="f2178-126">Ajoutez une référence dans le projet **GettingStartedHost** au projet **GettingStartedLib** :</span><span class="sxs-lookup"><span data-stu-id="f2178-126">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="f2178-127">Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedHost** , puis sélectionnez Ajouter une **référence** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f2178-127">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="f2178-128">Dans la boîte de dialogue **Ajouter une référence** , sous **projets** sur le côté gauche de la fenêtre, sélectionnez **solution**.</span><span class="sxs-lookup"><span data-stu-id="f2178-128">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="f2178-129">Sélectionnez **GettingStartedLib** dans la section centrale de la fenêtre, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2178-129">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="f2178-130">Cette action rend les types définis dans le projet **GettingStartedLib** disponibles pour le projet **GettingStartedHost** .</span><span class="sxs-lookup"><span data-stu-id="f2178-130">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="f2178-131">Ajoutez une référence dans le projet **GettingStartedHost** à l' <xref:System.ServiceModel> assembly :</span><span class="sxs-lookup"><span data-stu-id="f2178-131">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="f2178-132">Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedHost** , puis sélectionnez Ajouter une **référence** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f2178-132">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="f2178-133">Dans la fenêtre **Ajouter une référence** , sous **assemblys** sur le côté gauche de la fenêtre, sélectionnez **Framework**.</span><span class="sxs-lookup"><span data-stu-id="f2178-133">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="f2178-134">Sélectionnez **System. ServiceModel**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2178-134">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="f2178-135">Enregistrez la solution en sélectionnant **fichier**  >  **enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="f2178-135">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="f2178-136">Ajouter du code pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="f2178-136">Add code to host the service</span></span>

<span data-ttu-id="f2178-137">Pour héberger le service, vous ajoutez du code pour effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2178-137">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="f2178-138">Créez un URI pour l’adresse de base.</span><span class="sxs-lookup"><span data-stu-id="f2178-138">Create a URI for the base address.</span></span>
2. <span data-ttu-id="f2178-139">Créez une instance de classe pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="f2178-139">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="f2178-140">Créez un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="f2178-140">Create a service endpoint.</span></span>
4. <span data-ttu-id="f2178-141">Activer l'échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f2178-141">Enable metadata exchange.</span></span>
5. <span data-ttu-id="f2178-142">Ouvrez l’hôte de service pour écouter les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="f2178-142">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="f2178-143">Apportez les modifications suivantes au code :</span><span class="sxs-lookup"><span data-stu-id="f2178-143">Make the following changes to the code:</span></span>

1. <span data-ttu-id="f2178-144">Ouvrez le fichier **Program.cs** ou **Module1. vb** dans le projet **GettingStartedHost** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f2178-144">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
                    selfHost.Description.Behaviors.Add(smb);

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

    <span data-ttu-id="f2178-145">Pour plus d’informations sur le fonctionnement de ce code, consultez [étapes du programme d’hébergement de services](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="f2178-145">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="f2178-146">Mettez à jour les propriétés du projet :</span><span class="sxs-lookup"><span data-stu-id="f2178-146">Update the project properties:</span></span>

   1. <span data-ttu-id="f2178-147">Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **GettingStartedHost** , puis sélectionnez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f2178-147">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="f2178-148">Sur la page Propriétés de **GettingStartedHost** , sélectionnez l’onglet **application** :</span><span class="sxs-lookup"><span data-stu-id="f2178-148">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="f2178-149">Pour les projets C#, sélectionnez **GettingStartedHost. Program** dans la liste **objet de démarrage** .</span><span class="sxs-lookup"><span data-stu-id="f2178-149">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="f2178-150">Pour Visual Basic projets, sélectionnez **service. Program** dans la liste **objet de démarrage** .</span><span class="sxs-lookup"><span data-stu-id="f2178-150">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="f2178-151">Dans le menu **fichier** , sélectionnez **enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="f2178-151">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="f2178-152">Vérifier que le service fonctionne</span><span class="sxs-lookup"><span data-stu-id="f2178-152">Verify the service is working</span></span>

1. <span data-ttu-id="f2178-153">Générez la solution, puis exécutez l’application console **GettingStartedHost** à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2178-153">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="f2178-154">Le service doit être exécuté avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f2178-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="f2178-155">Étant donné que vous avez ouvert Visual Studio avec des privilèges d’administrateur, lorsque vous exécutez **GettingStartedHost** dans Visual Studio, l’application est également exécutée avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f2178-155">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="f2178-156">Vous pouvez également ouvrir une nouvelle invite de commandes en tant qu’administrateur (sélectionnez **plus**  >  **exécuter en tant qu’administrateur** dans le menu contextuel) et exécutez **GettingStartedHost.exe** dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="f2178-156">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="f2178-157">Ouvrez un navigateur Web et accédez à la page du service à l’adresse `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="f2178-157">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f2178-158">Les services tels que celui-ci requièrent l’autorisation appropriée pour inscrire des adresses HTTP sur l’ordinateur pour l’écoute.</span><span class="sxs-lookup"><span data-stu-id="f2178-158">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="f2178-159">Les comptes Administrateur possèdent cette autorisation, mais l'autorisation pour les espaces de noms HTTP doit être accordée aux comptes qui ne sont pas administrateur.</span><span class="sxs-lookup"><span data-stu-id="f2178-159">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="f2178-160">Pour plus d’informations sur la configuration des réservations d’espaces de noms, consultez [Configuration de HTTP et HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="f2178-160">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="f2178-161">Étapes du programme d’hébergement de service</span><span class="sxs-lookup"><span data-stu-id="f2178-161">Service hosting program steps</span></span>

<span data-ttu-id="f2178-162">Les étapes du code que vous avez ajouté pour héberger le service sont décrites comme suit :</span><span class="sxs-lookup"><span data-stu-id="f2178-162">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="f2178-163">**Étape 1**: créez une instance de la `Uri` classe pour contenir l’adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="f2178-163">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="f2178-164">Une URL qui contient une adresse de base a un URI facultatif qui identifie un service.</span><span class="sxs-lookup"><span data-stu-id="f2178-164">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="f2178-165">L’adresse de base est mise en forme comme suit : `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>` .</span><span class="sxs-lookup"><span data-stu-id="f2178-165">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="f2178-166">L’adresse de base pour le service de calculatrice utilise le transport HTTP, localhost, le port 8000 et le segment d’URI, GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="f2178-166">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="f2178-167">**Étape 2**: créez une instance de la <xref:System.ServiceModel.ServiceHost> classe, que vous utilisez pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="f2178-167">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="f2178-168">Le constructeur prend deux paramètres : le type de la classe qui implémente le contrat de service et l’adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="f2178-168">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="f2178-169">**Étape 3**: créer une <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span><span class="sxs-lookup"><span data-stu-id="f2178-169">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="f2178-170">Un point de terminaison de service est composé d'une adresse, d'une liaison et d'un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="f2178-170">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="f2178-171">Le <xref:System.ServiceModel.Description.ServiceEndpoint> constructeur est composé du type d’interface de contrat de service, d’une liaison et d’une adresse.</span><span class="sxs-lookup"><span data-stu-id="f2178-171">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="f2178-172">Le contrat de service est `ICalculator`, que vous définissez et implémentez dans le type de service.</span><span class="sxs-lookup"><span data-stu-id="f2178-172">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="f2178-173">La liaison de cet exemple est <xref:System.ServiceModel.WSHttpBinding> , qui est une liaison intégrée et se connecte aux points de terminaison conformes aux spécifications WS-\*.</span><span class="sxs-lookup"><span data-stu-id="f2178-173">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="f2178-174">Pour plus d’informations sur les liaisons WCF, consultez [vue d’ensemble des liaisons WCF](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f2178-174">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="f2178-175">Vous ajoutez l’adresse à l’adresse de base pour identifier le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f2178-175">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="f2178-176">Le code spécifie l’adresse comme CalculatorService et l’adresse complète du point de terminaison en tant que `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="f2178-176">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f2178-177">Pour .NET Framework version 4 et versions ultérieures, l’ajout d’un point de terminaison de service est facultatif.</span><span class="sxs-lookup"><span data-stu-id="f2178-177">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="f2178-178">Pour ces versions, si vous n’ajoutez pas votre code ou votre configuration, WCF ajoute un point de terminaison par défaut pour chaque combinaison d’adresse de base et de contrat implémentée par le service.</span><span class="sxs-lookup"><span data-stu-id="f2178-178">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="f2178-179">Pour plus d’informations sur les points de terminaison par défaut, consultez [spécification d’une adresse de point de terminaison](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="f2178-179">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="f2178-180">Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [configuration simplifiée](simplified-configuration.md) et [configuration simplifiée pour les services WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f2178-180">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="f2178-181">**Étape 4**: activer l’échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f2178-181">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="f2178-182">Les clients utilisent l’échange de métadonnées pour générer des proxies afin d’appeler les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="f2178-182">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="f2178-183">Pour activer l’échange de métadonnées, créez une <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, affectez à sa propriété la valeur <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> `true` et ajoutez l' `ServiceMetadataBehavior` objet à la <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection de l' <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="f2178-183">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="f2178-184">**Étape 5**: ouvrir <xref:System.ServiceModel.ServiceHost> pour écouter les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="f2178-184">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="f2178-185">L’application attend que vous appuyiez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="f2178-185">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="f2178-186">Une fois l’application instanciée <xref:System.ServiceModel.ServiceHost> , elle exécute un bloc try/catch.</span><span class="sxs-lookup"><span data-stu-id="f2178-186">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="f2178-187">Pour plus d’informations sur l’interception en toute sécurité des exceptions levées par <xref:System.ServiceModel.ServiceHost> , consultez la rubrique [utilisation de Close et Abort pour libérer des ressources clientes WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="f2178-187">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2178-188">Lorsque vous ajoutez une bibliothèque de service WCF, Visual Studio l’héberge pour vous si vous la déboguez en démarrant un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="f2178-188">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="f2178-189">Pour éviter les conflits, vous pouvez empêcher Visual Studio d’héberger la bibliothèque du service WCF.</span><span class="sxs-lookup"><span data-stu-id="f2178-189">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="f2178-190">Sélectionnez le projet **GettingStartedLib** dans **Explorateur de solutions** , puis choisissez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f2178-190">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="f2178-191">Sélectionnez **options WCF** et désactivez **Démarrer l’hôte de service WCF lors du débogage d’un autre projet dans la même solution**.</span><span class="sxs-lookup"><span data-stu-id="f2178-191">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2178-192">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f2178-192">Next steps</span></span>

<span data-ttu-id="f2178-193">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="f2178-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f2178-194">Créez et configurez un projet d’application console pour l’hébergement d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="f2178-194">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="f2178-195">Ajoutez du code pour héberger le service WCF.</span><span class="sxs-lookup"><span data-stu-id="f2178-195">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="f2178-196">Mettez à jour le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f2178-196">Update the configuration file.</span></span>
> - <span data-ttu-id="f2178-197">Démarrez le service WCF et vérifiez qu’il est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f2178-197">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="f2178-198">Passez au didacticiel suivant pour apprendre à créer un client WCF.</span><span class="sxs-lookup"><span data-stu-id="f2178-198">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f2178-199">Didacticiel : créer un client WCF</span><span class="sxs-lookup"><span data-stu-id="f2178-199">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
