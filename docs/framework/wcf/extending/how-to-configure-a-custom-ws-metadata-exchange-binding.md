---
title: 'Procédure : configurer une liaison WS-Metadata Exchange personnalisée'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: b4a4005a23c8c74edecb00475669e019b50a17af
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851223"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="68769-102">Procédure : configurer une liaison WS-Metadata Exchange personnalisée</span><span class="sxs-lookup"><span data-stu-id="68769-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="68769-103">Cette rubrique explique comment configurer une liaison d'échange WS-Metadata personnalisée.</span><span class="sxs-lookup"><span data-stu-id="68769-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="68769-104">Windows Communication Foundation (WCF) comprend quatre liaisons de métadonnées définies par le système, mais vous pouvez publier des métadonnées à l’aide de n’importe quelle liaison de votre choix.</span><span class="sxs-lookup"><span data-stu-id="68769-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="68769-105">Cette rubrique indique comment publier des métadonnées à l'aide du `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="68769-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="68769-106">Cette liaison vous donne la possibilité d’exposer des métadonnées de manière sécurisée.</span><span class="sxs-lookup"><span data-stu-id="68769-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="68769-107">Le code de cet article est basé sur le [prise en main](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="68769-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="68769-108">Utilisation d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="68769-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="68769-109">Dans le fichier de configuration du service, ajoutez un comportement de service qui contient la balise `serviceMetadata` :</span><span class="sxs-lookup"><span data-stu-id="68769-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="68769-110">Ajoutez un attribut `behaviorConfiguration` à la balise de service qui référence ce nouveau comportement :</span><span class="sxs-lookup"><span data-stu-id="68769-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. <span data-ttu-id="68769-111">Ajoutez un point de terminaison de métadonnées qui spécifie mex comme adresse, `wsHttpBinding` comme liaison et <xref:System.ServiceModel.Description.IMetadataExchange> comme contrat :</span><span class="sxs-lookup"><span data-stu-id="68769-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="68769-112">Pour vérifier que le point de terminaison d’échange de métadonnées fonctionne correctement, ajoutez une étiquette de point de terminaison dans le fichier de configuration de client :</span><span class="sxs-lookup"><span data-stu-id="68769-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="68769-113">Dans la méthode Main() du client, créez une instance <xref:System.ServiceModel.Description.MetadataExchangeClient>, affectez à sa propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `true`, appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, puis effectuez une itération au sein de la collection de métadonnées retournée :</span><span class="sxs-lookup"><span data-stu-id="68769-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="68769-114">Configuration par code</span><span class="sxs-lookup"><span data-stu-id="68769-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="68769-115">Créez une instance de liaison <xref:System.ServiceModel.WSHttpBinding> :</span><span class="sxs-lookup"><span data-stu-id="68769-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="68769-116">Créez une instance <xref:System.ServiceModel.ServiceHost> :</span><span class="sxs-lookup"><span data-stu-id="68769-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="68769-117">Ajoutez un point de terminaison de service et ajoutez une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior> :</span><span class="sxs-lookup"><span data-stu-id="68769-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="68769-118">Ajoutez un point de terminaison d'échange de métadonnées, en spécifiant le <xref:System.ServiceModel.WSHttpBinding> créé précédemment :</span><span class="sxs-lookup"><span data-stu-id="68769-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="68769-119">Pour vérifier que le point de terminaison d’échange de métadonnées fonctionne correctement, ajoutez une étiquette de point de terminaison dans le fichier de configuration de client :</span><span class="sxs-lookup"><span data-stu-id="68769-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="68769-120">Dans la méthode Main() du client, créez une instance <xref:System.ServiceModel.Description.MetadataExchangeClient>, affectez à la propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `true`, appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, puis effectuez une itération au sein de la collection de métadonnées retournée :</span><span class="sxs-lookup"><span data-stu-id="68769-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="68769-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68769-121">See also</span></span>

- [<span data-ttu-id="68769-122">Comportement de publication des métadonnées</span><span class="sxs-lookup"><span data-stu-id="68769-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="68769-123">Récupérer des métadonnées</span><span class="sxs-lookup"><span data-stu-id="68769-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="68769-124">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="68769-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="68769-125">Publication de métadonnées</span><span class="sxs-lookup"><span data-stu-id="68769-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="68769-126">Publication de points de terminaison de métadonnées</span><span class="sxs-lookup"><span data-stu-id="68769-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
