---
title: 'Comment : héberger un service WCF dans WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 9945e398bbd33776cce808b44388a4415da297a1
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964769"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="a82fc-102">Comment : héberger un service WCF dans WAS</span><span class="sxs-lookup"><span data-stu-id="a82fc-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="a82fc-103">Cette rubrique décrit les étapes de base requises pour créer un service de Windows Communication Foundation hébergé (WCF) des services d’activation de processus Windows (également appelé WAS).</span><span class="sxs-lookup"><span data-stu-id="a82fc-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="a82fc-104">WAS est le nouveau service d’activation de processus généralisant les fonctionnalités des services IIS (Internet Information Services) qui fonctionnent avec des protocoles de transport non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="a82fc-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="a82fc-105">WCF utilise l’interface d’adaptateur d’écouteur pour communiquer les demandes d’activation reçues sur les protocoles non-HTTP pris en charge par WCF, tels que TCP, les canaux nommés et les Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="a82fc-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="a82fc-106">Cette option d'hébergement requiert que les composants d'activation WAS soient installés et configurés correctement, mais ne requiert pas l'écriture du code d'hébergement dans le cadre de l'application.</span><span class="sxs-lookup"><span data-stu-id="a82fc-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="a82fc-107">Pour plus d’informations sur l’installation et la configuration de WAS, consultez [Comment : installer et configurer des composants d’activation WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="a82fc-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a82fc-108">L’activation de WAS n’est pas prise en charge si le pipeline de traitement de demande du serveur web est en mode classique.</span><span class="sxs-lookup"><span data-stu-id="a82fc-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="a82fc-109">Le pipeline de traitement de demande du serveur Web doit être en mode intégré si l'activation de WAS doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="a82fc-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="a82fc-110">Lorsqu’un service WCF est hébergé dans WAS, les liaisons standard sont utilisées de la façon habituelle.</span><span class="sxs-lookup"><span data-stu-id="a82fc-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="a82fc-111">Toutefois, lors de l'utilisation de <xref:System.ServiceModel.NetTcpBinding> et de <xref:System.ServiceModel.NetNamedPipeBinding> pour configurer un service hébergé WAS, une contrainte doit être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="a82fc-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="a82fc-112">Lorsque des points de terminaison différents utilisent le même transport, les paramètres de liaison doivent correspondre dans les sept propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a82fc-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="a82fc-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="a82fc-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="a82fc-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="a82fc-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="a82fc-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="a82fc-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="a82fc-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="a82fc-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="a82fc-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="a82fc-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="a82fc-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a82fc-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="a82fc-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="a82fc-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="a82fc-120">Sinon, le point de terminaison initialisé en premier détermine toujours les valeurs de ces propriétés et les points de terminaison ajoutés ultérieurement lèvent un <xref:System.ServiceModel.ServiceActivationException> s'ils ne correspondent pas à ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="a82fc-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="a82fc-121">Pour obtenir la copie source de cet exemple, consultez [activation TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="a82fc-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="a82fc-122">Pour créer un service de base hébergé par WAS</span><span class="sxs-lookup"><span data-stu-id="a82fc-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="a82fc-123">Définissez un contrat de service pour le type de service.</span><span class="sxs-lookup"><span data-stu-id="a82fc-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="a82fc-124">Implémentez le contrat de service dans une classe de service.</span><span class="sxs-lookup"><span data-stu-id="a82fc-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="a82fc-125">Notez que l’adresse ou les informations de liaison ne sont pas spécifiées dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="a82fc-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="a82fc-126">Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="a82fc-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="a82fc-127">Créez un fichier Web.config pour définir la liaison <xref:System.ServiceModel.NetTcpBinding> à utiliser par les points de terminaison `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="a82fc-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="a82fc-128">Créez un fichier Service.svc contenant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a82fc-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="a82fc-129">Placez le fichier Service.svc dans votre rɰertoire virtuel IIS.</span><span class="sxs-lookup"><span data-stu-id="a82fc-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="a82fc-130">Pour créer un client qui utilise le service</span><span class="sxs-lookup"><span data-stu-id="a82fc-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="a82fc-131">Utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) à partir de la ligne de commande pour générer le code à partir des métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="a82fc-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="a82fc-132">Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.</span><span class="sxs-lookup"><span data-stu-id="a82fc-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="a82fc-133">L'application cliente générée contient également l'implémentation de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a82fc-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="a82fc-134">Notez que les informations d’adresse et de liaison ne sont pas spécifiées n’importe où dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="a82fc-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="a82fc-135">Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="a82fc-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="a82fc-136">La configuration du client qui utilise <xref:System.ServiceModel.NetTcpBinding> est également générée par Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a82fc-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="a82fc-137">Ce fichier doit être nommé dans le fichier App.config lors de l'utilisation de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a82fc-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. <span data-ttu-id="a82fc-138">Créez une instance `ClientCalculator` dans une application, puis appelez les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="a82fc-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="a82fc-139">Compilez, puis exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="a82fc-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a82fc-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a82fc-140">See also</span></span>

- [<span data-ttu-id="a82fc-141">Activation TCP</span><span class="sxs-lookup"><span data-stu-id="a82fc-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- <span data-ttu-id="a82fc-142">[Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a82fc-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
