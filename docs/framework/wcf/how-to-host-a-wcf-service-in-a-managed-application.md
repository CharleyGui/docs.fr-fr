---
title: 'Comment : héberger un service WCF dans une application managée'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: e3adcad6ba70aa64b797325cd45a043301d7e680
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320978"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="a48a9-102">Comment : héberger un service WCF dans une application gérée</span><span class="sxs-lookup"><span data-stu-id="a48a9-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="a48a9-103">Pour héberger un service à l'intérieur d'une application managée, incorporez le code du service à l'intérieur du code de l'application managée, définissez un point de terminaison pour le service soit de manière impérative dans le code, soit de façon déclarative par le biais de la configuration ou à l'aide des points de terminaison par défaut, puis créez une instance de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a48a9-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="a48a9-104">Pour commencer à recevoir des messages, appelez <xref:System.ServiceModel.ICommunicationObject.Open%2A><xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a48a9-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a48a9-105">De cette manière, vous créez et ouvrez l'écouteur pour le service.</span><span class="sxs-lookup"><span data-stu-id="a48a9-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="a48a9-106">L'hébergement d'un service selon cette méthode est souvent appelé « auto-hébergement » parce que l'application managée effectue le travail d'hébergement elle-même.</span><span class="sxs-lookup"><span data-stu-id="a48a9-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="a48a9-107">Pour fermer le service, appelez <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a48a9-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="a48a9-108">Un service peut également être hébergé dans un service Windows managé, dans le service IIS (Internet Information Services), ou le service WAS (Windows Process Activation Service).</span><span class="sxs-lookup"><span data-stu-id="a48a9-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="a48a9-109">Pour plus d’informations sur les options d’hébergement pour un service, consultez [services d’hébergement](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="a48a9-109">For more information about hosting options for a service, see [Hosting Services](hosting-services.md).</span></span>

<span data-ttu-id="a48a9-110">L'hébergement d'un service dans une application managée constitue l'option d'hébergement la plus flexible parce qu'il requiert le déploiement de moins d'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="a48a9-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="a48a9-111">Pour plus d’informations sur les services d’hébergement dans les applications managées, consultez [hébergement dans une application managée](./feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="a48a9-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](./feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="a48a9-112">La procédure suivante montre comment implémenter un service auto-hébergé dans une application console.</span><span class="sxs-lookup"><span data-stu-id="a48a9-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="a48a9-113">Créer un service auto-hébergé</span><span class="sxs-lookup"><span data-stu-id="a48a9-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="a48a9-114">Créez une application de console :</span><span class="sxs-lookup"><span data-stu-id="a48a9-114">Create a new console application:</span></span>

   1. <span data-ttu-id="a48a9-115">Ouvrez Visual Studio et sélectionnez **nouveau** > **projet** dans le menu **fichier** .</span><span class="sxs-lookup"><span data-stu-id="a48a9-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="a48a9-116">Dans la liste **modèles installés** , sélectionnez **Visual C#**  ou **Visual Basic**, puis sélectionnez **Bureau Windows**.</span><span class="sxs-lookup"><span data-stu-id="a48a9-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="a48a9-117">Sélectionnez le modèle **application console** .</span><span class="sxs-lookup"><span data-stu-id="a48a9-117">Select the **Console App** template.</span></span> <span data-ttu-id="a48a9-118">Tapez `SelfHost` dans la zone **nom** , puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="a48a9-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="a48a9-119">Cliquez avec le bouton droit sur **selfHost** dans **Explorateur de solutions** , puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="a48a9-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="a48a9-120">Sélectionnez **System. ServiceModel** à partir de l’onglet **.net** , puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="a48a9-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a48a9-121">Si la fenêtre de **Explorateur de solutions** n’est pas visible, sélectionnez **Explorateur de solutions** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="a48a9-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="a48a9-122">Double-cliquez sur **Program.cs** ou **Module1. vb** dans **Explorateur de solutions** pour l’ouvrir dans la fenêtre de code, s’il n’est pas déjà ouvert.</span><span class="sxs-lookup"><span data-stu-id="a48a9-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="a48a9-123">Ajoutez les instructions suivantes en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="a48a9-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="a48a9-124">Définissez et implémentez un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="a48a9-124">Define and implement a service contract.</span></span> <span data-ttu-id="a48a9-125">Cet exemple définit un `HelloWorldService` qui retourne un message basé sur l'entrée au service.</span><span class="sxs-lookup"><span data-stu-id="a48a9-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="a48a9-126">Pour plus d’informations sur la définition et l’implémentation d’une interface de service, voir [Comment : définir un contrat de service](how-to-define-a-wcf-service-contract.md) et [Comment : implémenter un contrat de service](how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a48a9-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="a48a9-127">En tête de la méthode `Main`, créez une instance de la classe <xref:System.Uri> avec l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="a48a9-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="a48a9-128">Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>, en passant un <xref:System.Type> qui représente le type de service et l'URI d'adresse de base (Uniform Resource Identifier) à <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="a48a9-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="a48a9-129">Activez la publication des métadonnées, puis appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost> pour initialiser le service et le préparer à recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="a48a9-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="a48a9-130">Cet exemple utilise les points de terminaison par défaut et aucun fichier de configuration n'est requis pour ce service.</span><span class="sxs-lookup"><span data-stu-id="a48a9-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="a48a9-131">Si aucun point de terminaison n'est configuré, le runtime en crée un pour chaque adresse de base pour chaque contrat de service implémenté par le service.</span><span class="sxs-lookup"><span data-stu-id="a48a9-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="a48a9-132">Pour plus d’informations sur les points de terminaison par défaut, consultez [configuration simplifiée](simplified-configuration.md) et [configuration simplifiée pour les services WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a48a9-132">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="a48a9-133">Appuyez sur **Ctrl**+**Shift**+**B** pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="a48a9-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="a48a9-134">Tester le service</span><span class="sxs-lookup"><span data-stu-id="a48a9-134">Test the service</span></span>

1. <span data-ttu-id="a48a9-135">Appuyez sur **Ctrl**+**F5** pour exécuter le service.</span><span class="sxs-lookup"><span data-stu-id="a48a9-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="a48a9-136">Ouvrez le **client test WCF**.</span><span class="sxs-lookup"><span data-stu-id="a48a9-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a48a9-137">Pour ouvrir le **client test WCF**, ouvrez invite de commandes développeur pour Visual Studio et exécutez **WcfTestClient. exe**.</span><span class="sxs-lookup"><span data-stu-id="a48a9-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="a48a9-138">Sélectionnez **Ajouter un service** dans le menu **fichier** .</span><span class="sxs-lookup"><span data-stu-id="a48a9-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="a48a9-139">Tapez `http://localhost:8080/hello` dans la zone adresse, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a48a9-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a48a9-140">Assurez-vous que le service est en cours d'exécution, sinon cette étape échouera.</span><span class="sxs-lookup"><span data-stu-id="a48a9-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="a48a9-141">Si vous avez changé l'adresse de base dans le code, utilisez cette adresse modifiée dans cette étape.</span><span class="sxs-lookup"><span data-stu-id="a48a9-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="a48a9-142">Double-cliquez sur **sayHello** sous le nœud **mes projets de service** .</span><span class="sxs-lookup"><span data-stu-id="a48a9-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="a48a9-143">Tapez votre nom dans la colonne **valeur** de la liste **demande** , puis cliquez sur **appeler**.</span><span class="sxs-lookup"><span data-stu-id="a48a9-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="a48a9-144">Un message de réponse s’affiche dans la liste des **réponses** .</span><span class="sxs-lookup"><span data-stu-id="a48a9-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="a48a9-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="a48a9-145">Example</span></span>

<span data-ttu-id="a48a9-146">L'exemple suivant crée un objet <xref:System.ServiceModel.ServiceHost> pour héberger un service de type `HelloWorldService`, puis appelle la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a48a9-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a48a9-147">Une adresse de base est fournie dans le code, la publication des métadonnées est activée et les points de terminaison par défaut sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="a48a9-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="a48a9-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a48a9-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="a48a9-149">How to: Host a WCF Service in IIS (Comment : héberger un service WCF dans IIS)</span><span class="sxs-lookup"><span data-stu-id="a48a9-149">How to: Host a WCF Service in IIS</span></span>](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="a48a9-150">Auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="a48a9-150">Self-Host</span></span>](./samples/self-host.md)
- [<span data-ttu-id="a48a9-151">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="a48a9-151">Hosting Services</span></span>](hosting-services.md)
- [<span data-ttu-id="a48a9-152">Guide pratique pour définir un contrat de service</span><span class="sxs-lookup"><span data-stu-id="a48a9-152">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="a48a9-153">Guide pratique pour implémenter un contrat de service</span><span class="sxs-lookup"><span data-stu-id="a48a9-153">How to: Implement a Service Contract</span></span>](how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="a48a9-154">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="a48a9-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="a48a9-155">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a48a9-155">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a48a9-156">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a48a9-156">System-Provided Bindings</span></span>](system-provided-bindings.md)
