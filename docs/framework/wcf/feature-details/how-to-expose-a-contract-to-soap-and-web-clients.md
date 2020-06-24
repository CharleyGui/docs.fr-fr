---
title: 'Comment : exposer un contrat à des clients SOAP et Web'
description: Découvrez comment rendre un point de terminaison de serveur WFC disponible pour les clients SOAP et non-SOAP. Par défaut, les points de terminaison sont uniquement disponibles pour les clients SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: b1bdb7af51e0e2795c36865058fbeb34a716e3e2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246972"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="349be-104">Comment : exposer un contrat à des clients SOAP et Web</span><span class="sxs-lookup"><span data-stu-id="349be-104">How to: Expose a Contract to SOAP and Web Clients</span></span>

<span data-ttu-id="349be-105">Par défaut, Windows Communication Foundation (WCF) rend les points de terminaison disponibles uniquement aux clients SOAP.</span><span class="sxs-lookup"><span data-stu-id="349be-105">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="349be-106">Dans [Comment : créer un service http Web WCF de base](how-to-create-a-basic-wcf-web-http-service.md), un point de terminaison est mis à la disposition des clients non-SOAP.</span><span class="sxs-lookup"><span data-stu-id="349be-106">In [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="349be-107">Dans certains cas, vous pouvez souhaiter rendre le même contrat disponible pour les deux, comme point de terminaison Web et comme point de terminaison SOAP.</span><span class="sxs-lookup"><span data-stu-id="349be-107">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="349be-108">Cette rubrique explique comment procéder.</span><span class="sxs-lookup"><span data-stu-id="349be-108">This topic shows an example of how to do this.</span></span>

## <a name="to-define-the-service-contract"></a><span data-ttu-id="349be-109">Pour définir le contrat de service</span><span class="sxs-lookup"><span data-stu-id="349be-109">To define the service contract</span></span>

1. <span data-ttu-id="349be-110">Définissez un contrat de service à l’aide d’une interface marquée avec le <xref:System.ServiceModel.ServiceContractAttribute> , <xref:System.ServiceModel.Web.WebInvokeAttribute> et les <xref:System.ServiceModel.Web.WebGetAttribute> attributs, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="349be-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code:</span></span>

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="349be-111">Par défaut, <xref:System.ServiceModel.Web.WebInvokeAttribute> mappe des appels POST à l'opération.</span><span class="sxs-lookup"><span data-stu-id="349be-111">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="349be-112">Toutefois, vous pouvez spécifier la méthode pour mapper à l'opération un paramètre pour "method=".</span><span class="sxs-lookup"><span data-stu-id="349be-112">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="349be-113"><xref:System.ServiceModel.Web.WebGetAttribute> n'a pas de paramètre « method= » et mappe uniquement des appels GET à l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="349be-113"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="349be-114">Implémentez le contrat de service, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="349be-114">Implement the service contract, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="349be-115">Pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="349be-115">To host the service</span></span>

1. <span data-ttu-id="349be-116">Créez un <xref:System.ServiceModel.ServiceHost> objet, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="349be-116">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <span data-ttu-id="349be-117">Ajoutez un <xref:System.ServiceModel.Description.ServiceEndpoint> avec <xref:System.ServiceModel.BasicHttpBinding> pour le point de terminaison SOAP, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="349be-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <span data-ttu-id="349be-118">Ajoutez un <xref:System.ServiceModel.Description.ServiceEndpoint> avec <xref:System.ServiceModel.WebHttpBinding> pour le point de terminaison non-SOAP et ajoutez le <xref:System.ServiceModel.Description.WebHttpBehavior> au point de terminaison, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="349be-118">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. <span data-ttu-id="349be-119">Appelez `Open()` sur une <xref:System.ServiceModel.ServiceHost> instance pour ouvrir l’hôte de service, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="349be-119">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="349be-120">Pour appeler des opérations de service mappées à GET dans Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="349be-120">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="349be-121">Ouvrez Internet Explorer et tapez « `http://localhost:8000/Web/EchoWithGet?s=Hello, world!` », puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="349be-121">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="349be-122">L’URL contient l’adresse de base du service ( `http://localhost:8000/` ), l’adresse relative du point de terminaison (« »), l’opération de service à appeler («EchoWithGet ») et un point d’interrogation suivi d’une liste de paramètres nommés séparés par une esperluette (&).</span><span class="sxs-lookup"><span data-stu-id="349be-122">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="349be-123">Pour appeler des opérations de service sur le point de terminaison Web dans le code</span><span class="sxs-lookup"><span data-stu-id="349be-123">To call service operations on the Web endpoint in code</span></span>

1. <span data-ttu-id="349be-124">Créez une instance de <xref:System.ServiceModel.Web.WebChannelFactory%601> au sein d'un bloc `using`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="349be-124">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> <span data-ttu-id="349be-125">`Close()` est automatiquement appelé sur le canal à la fin du bloc `using`.</span><span class="sxs-lookup"><span data-stu-id="349be-125">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>

1. <span data-ttu-id="349be-126">Créez le canal, puis appelez le service, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="349be-126">Create the channel and call the service, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="349be-127">Pour appeler des opérations de service sur le point de terminaison SOAP</span><span class="sxs-lookup"><span data-stu-id="349be-127">To call service operations on the SOAP endpoint</span></span>

1. <span data-ttu-id="349be-128">Créez une instance de <xref:System.ServiceModel.ChannelFactory> au sein d'un bloc `using`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="349be-128">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. <span data-ttu-id="349be-129">Créez le canal, puis appelez le service, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="349be-129">Create the channel and call the service, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a><span data-ttu-id="349be-130">Pour fermer l'hôte de service</span><span class="sxs-lookup"><span data-stu-id="349be-130">To close the service host</span></span>

1. <span data-ttu-id="349be-131">Fermez l'hôte de service comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="349be-131">Close the service host, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a><span data-ttu-id="349be-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="349be-132">Example</span></span>

<span data-ttu-id="349be-133">Voici la liste complète du code pour cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="349be-133">The following is the full code listing for this topic:</span></span>

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a><span data-ttu-id="349be-134">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="349be-134">Compiling the code</span></span>

 <span data-ttu-id="349be-135">Lors de la compilation de Service.cs, référencez System.ServiceModel.dll et System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="349be-135">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="349be-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="349be-136">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="349be-137">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="349be-137">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
