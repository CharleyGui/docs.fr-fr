---
title: 'Tutorial: Créer un client Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184099"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="ab3a4-102">Tutorial: Créer un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ab3a4-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="ab3a4-103">Ce tutoriel décrit la quatrième des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ab3a4-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ab3a4-104">Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="ab3a4-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="ab3a4-105">La prochaine tâche pour créer une application WCF est de créer un client en récupérant des métadonnées à partir d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="ab3a4-106">Vous utilisez Visual Studio pour ajouter une référence de service, qui obtient les métadonnées à partir du point de terminaison MEX du service.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="ab3a4-107">Visual Studio génère ensuite un fichier de code source géré pour un proxy client dans la langue que vous avez choisie.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="ab3a4-108">Il crée également un fichier de configuration client (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="ab3a4-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="ab3a4-109">Ce fichier permet à l’application client de se connecter au service à un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-109">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="ab3a4-110">Si vous appelez un service WCF à partir d’un projet de bibliothèque de classe dans Visual Studio, utilisez la fonction **Add Service Reference** pour générer automatiquement un fichier de configuration proxy et associé.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="ab3a4-111">Toutefois, comme les projets de bibliothèque de classe n’utilisent pas ce fichier de configuration, vous devez ajouter les paramètres du fichier de configuration généré au fichier *App.config* pour l’exécutable qui appelle la bibliothèque de classe.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="ab3a4-112">Comme alternative, utilisez [l’outil ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) au lieu de Visual Studio pour générer la classe proxy et le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="ab3a4-113">L'application cliente utilise la classe proxy générée pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="ab3a4-114">Cette procédure est décrite dans [Tutorial: Utilisez un client](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="ab3a4-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="ab3a4-115">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="ab3a4-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ab3a4-116">Créez et configurez un projet d’application console pour le client WCF.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="ab3a4-117">Ajoutez une référence de service au service WCF pour générer la classe proxy et les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="ab3a4-118">Créer un client de la Fondation Windows Communication</span><span class="sxs-lookup"><span data-stu-id="ab3a4-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="ab3a4-119">Créez un projet d’application console dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="ab3a4-119">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="ab3a4-120">Du menu **Fichier,** sélectionnez **Open** > **Project/Solution** et naviguez vers la solution **GettingStarted** que vous avez déjà créée (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="ab3a4-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="ab3a4-121">Sélectionnez **uvrir**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-121">Select **Open**.</span></span>

    2. <span data-ttu-id="ab3a4-122">Du menu **View,** sélectionnez **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="ab3a4-123">Dans la fenêtre **Solution Explorer,** sélectionnez la solution **GettingStarted** (nœud supérieur), puis **sélectionnez Ajouter** > **un nouveau projet** dans le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="ab3a4-124">Dans la fenêtre **Add New Project,** sur le côté gauche, sélectionnez la catégorie **Windows Desktop** sous Visual **C ou** **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="ab3a4-125">Sélectionnez le modèle **Console App (.NET Framework)** et *entrez GettingStartedClient* pour le **nom**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="ab3a4-126">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-126">Select **OK**.</span></span>

2. <span data-ttu-id="ab3a4-127">Ajoutez une référence dans le projet **GettingStartedClient** à l’assemblage <xref:System.ServiceModel> :</span><span class="sxs-lookup"><span data-stu-id="ab3a4-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="ab3a4-128">Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **Références** dans le cadre du projet **GettingStartedClient,** puis **sélectionnez Ajouter la référence** dans le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="ab3a4-129">Dans la fenêtre **Add Reference,** sous **les assemblées** sur le côté gauche de la fenêtre, sélectionnez **Cadre**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="ab3a4-130">Trouver et sélectionner **System.ServiceModel**, puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="ab3a4-131">Enregistrer la solution en sélectionnant **File** > **Save All**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="ab3a4-132">Ajouter une référence de service au service de calculatrice :</span><span class="sxs-lookup"><span data-stu-id="ab3a4-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="ab3a4-133">Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **Références** dans le cadre du projet **GettingStartedClient,** puis **sélectionnez Ajouter** la référence de service dans le menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="ab3a4-134">Dans la fenêtre **Add Service Reference,** sélectionnez **Discover**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="ab3a4-135">Le service CalculatorService démarre et Visual Studio l’affiche dans la boîte **services.**</span><span class="sxs-lookup"><span data-stu-id="ab3a4-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="ab3a4-136">Sélectionnez **CalculatorService** pour l’élargir et afficher les contrats de service mis en œuvre par le service.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="ab3a4-137">Laissez **l’espace nom** par défaut et choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="ab3a4-138">Visual Studio ajoute un nouvel article sous le dossier **Services connectés** dans le projet **GettingStartedClient.**</span><span class="sxs-lookup"><span data-stu-id="ab3a4-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="ab3a4-139">Outil utilitaire De métadonnées de service</span><span class="sxs-lookup"><span data-stu-id="ab3a4-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="ab3a4-140">Les exemples suivants montrent comment utiliser en option [l’outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le fichier de classe proxy.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="ab3a4-141">Cet outil génère le fichier de classe proxy et le fichier *App.config.*</span><span class="sxs-lookup"><span data-stu-id="ab3a4-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="ab3a4-142">Les exemples suivants montrent comment générer le proxy dans C et Visual Basic, respectivement:</span><span class="sxs-lookup"><span data-stu-id="ab3a4-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="ab3a4-143">Fichier de configuration du client</span><span class="sxs-lookup"><span data-stu-id="ab3a4-143">Client configuration file</span></span>

<span data-ttu-id="ab3a4-144">Après avoir créé le client, Visual Studio crée le fichier de configuration **App.config** dans le projet **GettingStartedClient,** qui doit être similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ab3a4-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="ab3a4-145">Dans la [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) [ \<section system.serviceModel>,](../configure-apps/file-schema/wcf/system-servicemodel.md) remarquez le critère de>élément.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="ab3a4-146">\*\* &lt;L’élément&gt; de point de terminaison\*\* définit le critère d’évaluation que le client utilise pour accéder au service comme suit :</span><span class="sxs-lookup"><span data-stu-id="ab3a4-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="ab3a4-147">Adresse: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="ab3a4-148">Adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-148">The address of the endpoint.</span></span>
- <span data-ttu-id="ab3a4-149">Contrat de `ServiceReference1.ICalculator`service: .</span><span class="sxs-lookup"><span data-stu-id="ab3a4-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="ab3a4-150">Le contrat de service traite de la communication entre le client WCF et le service.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="ab3a4-151">Visual Studio a généré ce contrat lorsque vous avez utilisé sa fonction **Add Service Reference.**</span><span class="sxs-lookup"><span data-stu-id="ab3a4-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="ab3a4-152">Il s’agit essentiellement d’une copie du contrat que vous avez défini dans le projet GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="ab3a4-153">Liaison: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="ab3a4-154">La liaison spécifie HTTP comme le transport, la sécurité interopérable, et d’autres détails de configuration.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ab3a4-155">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ab3a4-155">Next steps</span></span>

<span data-ttu-id="ab3a4-156">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="ab3a4-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ab3a4-157">Créez et configurez un projet d’application console pour le client WCF.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="ab3a4-158">Ajoutez une référence de service au service WCF pour générer la classe de proxy et les fichiers de configuration pour l’application client.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="ab3a4-159">Avancez au tutoriel suivant pour apprendre à utiliser le client généré.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab3a4-160">Tutorial: Utilisez un client WCF</span><span class="sxs-lookup"><span data-stu-id="ab3a4-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
