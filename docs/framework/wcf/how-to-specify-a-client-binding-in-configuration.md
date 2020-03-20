---
title: 'Comment : spécifier une liaison de client dans la configuration'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184037"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="aa566-102">Comment : spécifier une liaison de client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="aa566-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="aa566-103">Dans cet exemple, une application console cliente est créée pour utiliser un service de calculatrice, et la liaison pour ce client est spécifiée de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="aa566-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="aa566-104">Le client accède au service `CalculatorService`, lequel implémente l'interface `ICalculator`. Le service et le client utilisent la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="aa566-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="aa566-105">La procédure présentée suppose que le service de calculatrice est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="aa566-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="aa566-106">Pour plus d’informations sur la façon de construire le service, voir [comment : Spécifier une liaison de service dans la configuration](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="aa566-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="aa566-107">Il utilise également [l’outil utilitaire De métadonnées de servicemodel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) que Windows Communication Foundation (WCF) fournit pour générer automatiquement les composants du client.</span><span class="sxs-lookup"><span data-stu-id="aa566-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="aa566-108">L'outil génère le code client et la configuration permettant d'accéder au service.</span><span class="sxs-lookup"><span data-stu-id="aa566-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="aa566-109">La construction du client se divise en deux parties.</span><span class="sxs-lookup"><span data-stu-id="aa566-109">The client is built in two parts.</span></span> <span data-ttu-id="aa566-110">L'outil Svcutil.exe génère la calculatrice `ClientCalculator` qui implémente l'interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="aa566-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="aa566-111">Cette application cliente est ensuite construite à l'aide d'une instance de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="aa566-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="aa566-112">Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="aa566-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="aa566-113">La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.</span><span class="sxs-lookup"><span data-stu-id="aa566-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="aa566-114">Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.</span><span class="sxs-lookup"><span data-stu-id="aa566-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="aa566-115">Vous pouvez effectuer toutes les étapes de configuration suivantes en utilisant [l’outil d’éditeur de configuration (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aa566-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="aa566-116">Pour la copie source de cet exemple, voir l’échantillon [BasicBinding.](./samples/basicbinding.md)</span><span class="sxs-lookup"><span data-stu-id="aa566-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="aa566-117">Spécification d’une liaison de client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="aa566-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="aa566-118">Utilisez l'outil Svcutil.exe depuis la ligne de commande pour générer le code à partir des métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="aa566-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="aa566-119">Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.</span><span class="sxs-lookup"><span data-stu-id="aa566-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="aa566-120">Le client généré contient également l'implémentation de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="aa566-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="aa566-121">Svcutil.exe génère également la configuration du client qui utilise la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="aa566-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="aa566-122">Lorsque vous utilisez Visual Studio, nommez ce fichier App.config. Notez que l’adresse et les informations contraignantes ne sont spécifiées nulle part à l’intérieur de la mise en œuvre du service.</span><span class="sxs-lookup"><span data-stu-id="aa566-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="aa566-123">Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="aa566-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="aa566-124">Créez une instance de `ClientCalculator` dans une application, puis appelez les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="aa566-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="aa566-125">Compilez, puis exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="aa566-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa566-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa566-126">See also</span></span>

- [<span data-ttu-id="aa566-127">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="aa566-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
