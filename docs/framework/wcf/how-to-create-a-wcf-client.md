---
title: 'Tutoriel : Créer un client Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928903"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="817db-102">Tutoriel : Créer un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="817db-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="817db-103">Ce didacticiel décrit la quatrième des cinq tâches nécessaires à la création d’une application de base Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="817db-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="817db-104">Pour obtenir une vue d’ensemble des didacticiels, consultez [didacticiel : Prise en main des applications](getting-started-tutorial.md)Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="817db-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="817db-105">La tâche suivante pour créer une application WCF consiste à créer un client en extrayant les métadonnées d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="817db-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="817db-106">Vous utilisez Visual Studio pour ajouter une référence de service, qui obtient les métadonnées du point de terminaison MEX du service.</span><span class="sxs-lookup"><span data-stu-id="817db-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="817db-107">Visual Studio génère ensuite un fichier de code source managé pour un proxy client dans le langage que vous avez choisi.</span><span class="sxs-lookup"><span data-stu-id="817db-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="817db-108">Il crée également un fichier de configuration client (*app. config*).</span><span class="sxs-lookup"><span data-stu-id="817db-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="817db-109">Ce fichier permet à l’application cliente de se connecter au service au niveau d’un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="817db-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="817db-110">Si vous appelez un service WCF à partir d’un projet de bibliothèque de classes dans Visual Studio, utilisez la fonctionnalité **Ajouter une référence de service** pour générer automatiquement un proxy et un fichier de configuration associé.</span><span class="sxs-lookup"><span data-stu-id="817db-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="817db-111">Toutefois, étant donné que les projets de bibliothèque de classes n’utilisent pas ce fichier de configuration, vous devez ajouter les paramètres dans le fichier de configuration généré au fichier *app. config* pour l’exécutable qui appelle la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="817db-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="817db-112">Vous pouvez également utiliser l' [outil ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) au lieu de Visual Studio pour générer la classe proxy et le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="817db-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="817db-113">L'application cliente utilise la classe proxy générée pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="817db-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="817db-114">Cette procédure est décrite dans [le didacticiel : Utilisez un client](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="817db-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="817db-115">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="817db-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="817db-116">Créez et configurez un projet d’application console pour le client WCF.</span><span class="sxs-lookup"><span data-stu-id="817db-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="817db-117">Ajoutez une référence de service au service WCF pour générer la classe proxy et les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="817db-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="817db-118">Créer un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="817db-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="817db-119">Créez un projet d’application console dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="817db-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="817db-120">Dans le menu **fichier** , sélectionnez **ouvrir** > un**projet/une solution** , puis accédez à la solution **gettingstarted** que vous avez créée précédemment (*gettingstarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="817db-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="817db-121">Sélectionnez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="817db-121">Select **Open**.</span></span>

    2. <span data-ttu-id="817db-122">Dans le menu **affichage** , sélectionnez **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="817db-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="817db-123">Dans la fenêtre **Explorateur de solutions** , sélectionnez la solution **gettingstarted** (nœud supérieur), puis sélectionnez **Ajouter** > **un nouveau projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="817db-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="817db-124">Dans la fenêtre **Ajouter un nouveau projet** , sur le côté gauche, sélectionnez la catégorie **Bureau Windows** sous  **C# Visual** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="817db-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="817db-125">Sélectionnez le modèle **application console (.NET Framework)** , puis entrez *GettingStartedClient* pour le **nom**.</span><span class="sxs-lookup"><span data-stu-id="817db-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="817db-126">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="817db-126">Select **OK**.</span></span>

2. <span data-ttu-id="817db-127">Ajoutez une référence dans le projet **GettingStartedClient** à l' <xref:System.ServiceModel> assembly :</span><span class="sxs-lookup"><span data-stu-id="817db-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="817db-128">Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedClient** , puis sélectionnez Ajouter une **référence** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="817db-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="817db-129">Dans la fenêtre **Ajouter une référence** , sous **assemblys** sur le côté gauche de la fenêtre, sélectionnez **Framework**.</span><span class="sxs-lookup"><span data-stu-id="817db-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="817db-130">Recherchez et sélectionnez **System. ServiceModel**, puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="817db-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="817db-131">Enregistrez la solution en sélectionnant **fichier** > **enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="817db-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="817db-132">Ajoutez une référence de service au service de calculatrice :</span><span class="sxs-lookup"><span data-stu-id="817db-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="817db-133">Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedClient** , puis sélectionnez **Ajouter une référence de service** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="817db-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="817db-134">Dans la fenêtre **Ajouter une référence de service** , sélectionnez **découvrir**.</span><span class="sxs-lookup"><span data-stu-id="817db-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="817db-135">Le service CalculatorService démarre et Visual Studio l’affiche dans la zone **services** .</span><span class="sxs-lookup"><span data-stu-id="817db-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="817db-136">Sélectionnez **CalculatorService** pour le développer et afficher les contrats de service implémentés par le service.</span><span class="sxs-lookup"><span data-stu-id="817db-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="817db-137">Laissez l' **espace de noms** par défaut et choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="817db-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="817db-138">Visual Studio ajoute un nouvel élément sous le dossier **services connectés** dans le projet **GettingStartedClient** .</span><span class="sxs-lookup"><span data-stu-id="817db-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="817db-139">Outil utilitaire de métadonnées ServiceModel</span><span class="sxs-lookup"><span data-stu-id="817db-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="817db-140">Les exemples suivants montrent comment utiliser l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le fichier de classe proxy.</span><span class="sxs-lookup"><span data-stu-id="817db-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="817db-141">Cet outil génère le fichier de classe proxy et le fichier *app. config* .</span><span class="sxs-lookup"><span data-stu-id="817db-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="817db-142">Les exemples suivants montrent comment générer le proxy dans C# et Visual Basic, respectivement :</span><span class="sxs-lookup"><span data-stu-id="817db-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="817db-143">Fichier de configuration du client</span><span class="sxs-lookup"><span data-stu-id="817db-143">Client configuration file</span></span>

<span data-ttu-id="817db-144">Une fois le client créé, Visual Studio crée le fichier de configuration **app. config** dans le projet **GettingStartedClient** , qui doit ressembler à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="817db-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

<span data-ttu-id="817db-145">Dans la [ \<section System. ServiceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) , notez l’élément [ \<> de point de terminaison](../configure-apps/file-schema/wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="817db-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="817db-146">L’élément de **point de terminaison&gt; définit le point de terminaison que le client utilise pour accéder au service comme suit : &lt;**</span><span class="sxs-lookup"><span data-stu-id="817db-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="817db-147">Adresse : `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="817db-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="817db-148">Adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="817db-148">The address of the endpoint.</span></span>
- <span data-ttu-id="817db-149">Contrat de service `ServiceReference1.ICalculator`:.</span><span class="sxs-lookup"><span data-stu-id="817db-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="817db-150">Le contrat de service gère la communication entre le client WCF et le service.</span><span class="sxs-lookup"><span data-stu-id="817db-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="817db-151">Visual Studio a généré ce contrat lorsque vous avez utilisé sa fonction **Ajouter une référence de service** .</span><span class="sxs-lookup"><span data-stu-id="817db-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="817db-152">Il s’agit essentiellement d’une copie du contrat que vous avez défini dans le projet GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="817db-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="817db-153">Liaison : <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="817db-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="817db-154">La liaison spécifie HTTP comme transport, la sécurité interopérable et d’autres détails de configuration.</span><span class="sxs-lookup"><span data-stu-id="817db-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="817db-155">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="817db-155">Next steps</span></span>

<span data-ttu-id="817db-156">Dans ce tutoriel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="817db-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="817db-157">Créez et configurez un projet d’application console pour le client WCF.</span><span class="sxs-lookup"><span data-stu-id="817db-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="817db-158">Ajoutez une référence de service au service WCF pour générer la classe proxy et les fichiers de configuration pour l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="817db-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="817db-159">Passez au didacticiel suivant pour découvrir comment utiliser le client généré.</span><span class="sxs-lookup"><span data-stu-id="817db-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="817db-160">Tutoriel : Utiliser un client WCF</span><span class="sxs-lookup"><span data-stu-id="817db-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
