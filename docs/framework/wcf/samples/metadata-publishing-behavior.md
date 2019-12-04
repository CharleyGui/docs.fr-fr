---
title: Metadata Publishing Behavior
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 3b3057d845ac37280ff46e6e15415758f1f0ba77
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714779"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="9005d-102">Metadata Publishing Behavior</span><span class="sxs-lookup"><span data-stu-id="9005d-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="9005d-103">Cet exemple montre comment contrôler les fonctionnalités de publication des métadonnées d’un service.</span><span class="sxs-lookup"><span data-stu-id="9005d-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="9005d-104">Pour empêcher la divulgation non intentionnelle de métadonnées de service potentiellement sensibles, la configuration par défaut pour les services Windows Communication Foundation (WCF) désactive la publication de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9005d-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="9005d-105">Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="9005d-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9005d-106">Pour plus de clarté, cet exemple montre comment créer un point de terminaison de publication de métadonnées non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="9005d-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="9005d-107">De tels points de terminaison sont potentiellement disponibles aux consommateurs non authentifiés anonymes et il est nécessaire de se montrer vigilant et de s'assurer que la divulgation publique des métadonnées d'un service est appropriée avant de déployer de tels points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9005d-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="9005d-108">Consultez l’exemple de [point de terminaison de métadonnées sécurisées personnalisé](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) pour un exemple qui sécurise un point de terminaison de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9005d-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="9005d-109">L’exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente le contrat de service `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="9005d-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="9005d-110">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="9005d-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9005d-111">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9005d-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9005d-112">Pour qu'un service expose des métadonnées, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> doit être configuré sur le service.</span><span class="sxs-lookup"><span data-stu-id="9005d-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="9005d-113">Lorsque ce comportement est présent, vous pouvez publier des métadonnées en configurant un point de terminaison afin qu'il exposer le contrat <xref:System.ServiceModel.Description.IMetadataExchange> en tant qu'implémentation d'un protocole MEX (WS-MetadataExchange).</span><span class="sxs-lookup"><span data-stu-id="9005d-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="9005d-114">Par commodité, le nom de configuration abrégé « IMetadataExchange » a été donné à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="9005d-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="9005d-115">Cet exemple utilise `mexHttpBinding`, qui est une liaison standard équivalente à `wsHttpBinding` dont le mode de sécurité a la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="9005d-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="9005d-116">Une adresse relative de « MEX » est utilisée dans le point de terminaison, qui, lorsqu’elle est résolue par rapport à l’adresse de base des services, se traduit par une adresse de point de terminaison de `http://localhost/servicemodelsamples/service.svc/mex`.</span><span class="sxs-lookup"><span data-stu-id="9005d-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="9005d-117">La configuration de comportement se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9005d-117">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="9005d-118">Le point de terminaison MEX se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9005d-118">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="9005d-119">Cet exemple affecte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> à la propriété `true` qui expose également les métadonnées du service à l'aide de HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="9005d-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="9005d-120">Pour activer un point de terminaison de métadonnées HTTP GET, le service doit avoir une adresse de base HTTP.</span><span class="sxs-lookup"><span data-stu-id="9005d-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="9005d-121">La chaîne de requête `?wsdl` est utilisée sur l'adresse de base du service pour accéder aux métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9005d-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="9005d-122">Par exemple, pour afficher le fichier WSDL du service dans un navigateur Web, vous devez utiliser l’adresse `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="9005d-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="9005d-123">Vous pouvez également utiliser ce comportement pour exposer des métadonnées sur HTTPS en affectant <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> à `true`.</span><span class="sxs-lookup"><span data-stu-id="9005d-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="9005d-124">Cela requiert une adresse de base HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9005d-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="9005d-125">Pour accéder au point de terminaison MEX du service [, utilisez l’outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9005d-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="9005d-126">Cette opération génère un client basé sur les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="9005d-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="9005d-127">Pour accéder aux métadonnées du service à l’aide de HTTP, pointez votre navigateur sur `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="9005d-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="9005d-128">Si vous supprimez ce comportement et tentez d'ouvrir le service, vous obtenez une exception.</span><span class="sxs-lookup"><span data-stu-id="9005d-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="9005d-129">Cette erreur se produit car sans le comportement, le point de terminaison configuré avec le contrat `IMetadataExchange` n'a aucune implémentation.</span><span class="sxs-lookup"><span data-stu-id="9005d-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="9005d-130">Si vous affectez `HttpGetEnabled` à `false`, la page d'aide CalculatorService s'affiche à la place des métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="9005d-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9005d-131">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="9005d-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9005d-132">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9005d-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9005d-133">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9005d-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9005d-134">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9005d-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9005d-135">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9005d-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9005d-136">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="9005d-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="9005d-137">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9005d-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9005d-138">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="9005d-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
