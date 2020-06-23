---
title: 'Didacticiel : créer un client Windows Communication Foundation'
description: Apprenez à créer un client en extrayant les métadonnées d’un service WCF dans le cadre d’une série d’articles qui vous aideront à créer une application WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246322"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="4e656-103">Didacticiel : créer un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4e656-103">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="4e656-104">Ce didacticiel décrit la quatrième des cinq tâches nécessaires à la création d’une application de base Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4e656-104">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="4e656-105">Pour obtenir une vue d’ensemble des didacticiels, consultez [Didacticiel : prise en main des applications Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="4e656-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="4e656-106">La tâche suivante pour créer une application WCF consiste à créer un client en extrayant les métadonnées d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="4e656-106">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="4e656-107">Vous utilisez Visual Studio pour ajouter une référence de service, qui obtient les métadonnées du point de terminaison MEX du service.</span><span class="sxs-lookup"><span data-stu-id="4e656-107">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="4e656-108">Visual Studio génère ensuite un fichier de code source managé pour un proxy client dans le langage que vous avez choisi.</span><span class="sxs-lookup"><span data-stu-id="4e656-108">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="4e656-109">Il crée également un fichier de configuration client (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="4e656-109">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="4e656-110">Ce fichier permet à l’application cliente de se connecter au service au niveau d’un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4e656-110">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="4e656-111">Si vous appelez un service WCF à partir d’un projet de bibliothèque de classes dans Visual Studio, utilisez la fonctionnalité **Ajouter une référence de service** pour générer automatiquement un proxy et un fichier de configuration associé.</span><span class="sxs-lookup"><span data-stu-id="4e656-111">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="4e656-112">Toutefois, étant donné que les projets de bibliothèque de classes n’utilisent pas ce fichier de configuration, vous devez ajouter les paramètres dans le fichier de configuration généré au fichier *App.config* pour l’exécutable qui appelle la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="4e656-112">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="4e656-113">Vous pouvez également utiliser l' [outil ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) au lieu de Visual Studio pour générer la classe proxy et le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="4e656-113">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="4e656-114">L'application cliente utilise la classe proxy générée pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="4e656-114">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="4e656-115">Cette procédure est décrite dans [Didacticiel : utiliser un client](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="4e656-115">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="4e656-116">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="4e656-116">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4e656-117">Créez et configurez un projet d’application console pour le client WCF.</span><span class="sxs-lookup"><span data-stu-id="4e656-117">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="4e656-118">Ajoutez une référence de service au service WCF pour générer la classe proxy et les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="4e656-118">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="4e656-119">Créer un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4e656-119">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="4e656-120">Créez un projet d’application console dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="4e656-120">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="4e656-121">Dans le menu **fichier** , sélectionnez **ouvrir**  >  un**projet/une solution** , puis accédez à la solution **gettingstarted** que vous avez créée précédemment (*gettingstarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="4e656-121">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="4e656-122">Sélectionnez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="4e656-122">Select **Open**.</span></span>

    2. <span data-ttu-id="4e656-123">Dans le menu **affichage** , sélectionnez **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="4e656-123">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="4e656-124">Dans la fenêtre **Explorateur de solutions** , sélectionnez la solution **gettingstarted** (nœud supérieur), puis sélectionnez **Ajouter**  >  **un nouveau projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4e656-124">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="4e656-125">Dans la fenêtre **Ajouter un nouveau projet** , sur le côté gauche, sélectionnez la catégorie **Bureau Windows** sous **Visual C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="4e656-125">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="4e656-126">Sélectionnez le modèle **application console (.NET Framework)** , puis entrez *GettingStartedClient* pour le **nom**.</span><span class="sxs-lookup"><span data-stu-id="4e656-126">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="4e656-127">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e656-127">Select **OK**.</span></span>

2. <span data-ttu-id="4e656-128">Ajoutez une référence dans le projet **GettingStartedClient** à l' <xref:System.ServiceModel> assembly :</span><span class="sxs-lookup"><span data-stu-id="4e656-128">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="4e656-129">Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedClient** , puis sélectionnez Ajouter une **référence** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4e656-129">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="4e656-130">Dans la fenêtre **Ajouter une référence** , sous **assemblys** sur le côté gauche de la fenêtre, sélectionnez **Framework**.</span><span class="sxs-lookup"><span data-stu-id="4e656-130">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="4e656-131">Recherchez et sélectionnez **System. ServiceModel**, puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e656-131">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="4e656-132">Enregistrez la solution en sélectionnant **fichier**  >  **enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="4e656-132">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="4e656-133">Ajoutez une référence de service au service de calculatrice :</span><span class="sxs-lookup"><span data-stu-id="4e656-133">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="4e656-134">Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedClient** , puis sélectionnez **Ajouter une référence de service** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4e656-134">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="4e656-135">Dans la fenêtre **Ajouter une référence de service** , sélectionnez **découvrir**.</span><span class="sxs-lookup"><span data-stu-id="4e656-135">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="4e656-136">Le service CalculatorService démarre et Visual Studio l’affiche dans la zone **services** .</span><span class="sxs-lookup"><span data-stu-id="4e656-136">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="4e656-137">Sélectionnez **CalculatorService** pour le développer et afficher les contrats de service implémentés par le service.</span><span class="sxs-lookup"><span data-stu-id="4e656-137">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="4e656-138">Laissez l' **espace de noms** par défaut et choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e656-138">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="4e656-139">Visual Studio ajoute un nouvel élément sous le dossier **services connectés** dans le projet **GettingStartedClient** .</span><span class="sxs-lookup"><span data-stu-id="4e656-139">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="4e656-140">Outil utilitaire de métadonnées ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4e656-140">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="4e656-141">Les exemples suivants montrent comment utiliser l' [outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le fichier de classe proxy.</span><span class="sxs-lookup"><span data-stu-id="4e656-141">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="4e656-142">Cet outil génère le fichier de classe proxy et le fichier *App.config* .</span><span class="sxs-lookup"><span data-stu-id="4e656-142">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="4e656-143">Les exemples suivants montrent comment générer le proxy en C# et Visual Basic, respectivement :</span><span class="sxs-lookup"><span data-stu-id="4e656-143">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="4e656-144">Fichier de configuration du client</span><span class="sxs-lookup"><span data-stu-id="4e656-144">Client configuration file</span></span>

<span data-ttu-id="4e656-145">Une fois le client créé, Visual Studio crée le **App.config** fichier de configuration dans le projet **GettingStartedClient** , qui doit ressembler à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4e656-145">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="4e656-146">Sous la [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notez l' [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="4e656-146">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="4e656-147">L’élément de \*\* &lt; point de terminaison &gt; \*\* définit le point de terminaison que le client utilise pour accéder au service comme suit :</span><span class="sxs-lookup"><span data-stu-id="4e656-147">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="4e656-148">Adresse : `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="4e656-148">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="4e656-149">Adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4e656-149">The address of the endpoint.</span></span>
- <span data-ttu-id="4e656-150">Contrat de service : `ServiceReference1.ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="4e656-150">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="4e656-151">Le contrat de service gère la communication entre le client WCF et le service.</span><span class="sxs-lookup"><span data-stu-id="4e656-151">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="4e656-152">Visual Studio a généré ce contrat lorsque vous avez utilisé sa fonction **Ajouter une référence de service** .</span><span class="sxs-lookup"><span data-stu-id="4e656-152">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="4e656-153">Il s’agit essentiellement d’une copie du contrat que vous avez défini dans le projet GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="4e656-153">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="4e656-154">Liaison : <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="4e656-154">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="4e656-155">La liaison spécifie HTTP comme transport, la sécurité interopérable et d’autres détails de configuration.</span><span class="sxs-lookup"><span data-stu-id="4e656-155">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4e656-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4e656-156">Next steps</span></span>

<span data-ttu-id="4e656-157">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="4e656-157">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4e656-158">Créez et configurez un projet d’application console pour le client WCF.</span><span class="sxs-lookup"><span data-stu-id="4e656-158">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="4e656-159">Ajoutez une référence de service au service WCF pour générer la classe proxy et les fichiers de configuration pour l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="4e656-159">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="4e656-160">Passez au didacticiel suivant pour découvrir comment utiliser le client généré.</span><span class="sxs-lookup"><span data-stu-id="4e656-160">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4e656-161">Didacticiel : utiliser un client WCF</span><span class="sxs-lookup"><span data-stu-id="4e656-161">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
