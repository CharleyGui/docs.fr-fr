---
title: 'Procédure : spécifier une liaison de client dans la configuration'
description: Découvrez comment spécifier la liaison d’un client WCF de façon déclarative dans un fichier de configuration. Le client accède à un service dans cet exemple.
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: e8a552211b28c1323b2afd595c5b060db6b2824a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236505"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="d1d88-104">Procédure : spécifier une liaison de client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="d1d88-104">How to: Specify a Client Binding in Configuration</span></span>

<span data-ttu-id="d1d88-105">Dans cet exemple, une application console cliente est créée pour utiliser un service de calculatrice, et la liaison pour ce client est spécifiée de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="d1d88-105">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="d1d88-106">Le client accède au service `CalculatorService`, lequel implémente l'interface `ICalculator`. Le service et le client utilisent la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d1d88-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="d1d88-107">La procédure présentée suppose que le service de calculatrice est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="d1d88-107">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="d1d88-108">Pour plus d’informations sur la génération du service, consultez [Comment : spécifier une liaison de service dans la configuration](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d1d88-108">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="d1d88-109">Il utilise également l' [outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) que Windows Communication Foundation (WCF) fournit pour générer automatiquement les composants clients.</span><span class="sxs-lookup"><span data-stu-id="d1d88-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="d1d88-110">L'outil génère le code client et la configuration permettant d'accéder au service.</span><span class="sxs-lookup"><span data-stu-id="d1d88-110">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="d1d88-111">La construction du client se divise en deux parties.</span><span class="sxs-lookup"><span data-stu-id="d1d88-111">The client is built in two parts.</span></span> <span data-ttu-id="d1d88-112">L'outil Svcutil.exe génère la calculatrice `ClientCalculator` qui implémente l'interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="d1d88-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="d1d88-113">Cette application cliente est ensuite construite à l'aide d'une instance de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="d1d88-113">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="d1d88-114">Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="d1d88-114">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="d1d88-115">La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.</span><span class="sxs-lookup"><span data-stu-id="d1d88-115">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="d1d88-116">Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.</span><span class="sxs-lookup"><span data-stu-id="d1d88-116">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="d1d88-117">Vous pouvez effectuer toutes les étapes de configuration suivantes à l’aide de l' [outil Éditeur de configuration (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d1d88-117">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="d1d88-118">Pour obtenir la copie source de cet exemple, consultez l’exemple [BasicBinding](./samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d1d88-118">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="d1d88-119">Spécification d’une liaison de client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="d1d88-119">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="d1d88-120">Utilisez l'outil Svcutil.exe depuis la ligne de commande pour générer le code à partir des métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="d1d88-120">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="d1d88-121">Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.</span><span class="sxs-lookup"><span data-stu-id="d1d88-121">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="d1d88-122">Le client généré contient également l'implémentation de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="d1d88-122">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="d1d88-123">Svcutil.exe génère également la configuration du client qui utilise la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d1d88-123">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="d1d88-124">Quand vous utilisez Visual Studio, nommez ce fichier App.config. Notez que les informations d’adresse et de liaison ne sont pas spécifiées n’importe où dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="d1d88-124">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="d1d88-125">Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d1d88-125">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="d1d88-126">Créez une instance de `ClientCalculator` dans une application, puis appelez les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="d1d88-126">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="d1d88-127">Compilez, puis exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="d1d88-127">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d88-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1d88-128">See also</span></span>

- [<span data-ttu-id="d1d88-129">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d1d88-129">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
