---
title: 'Procédure : créer un service Web HTTP WCF de base'
description: Découvrez comment créer un service qui expose un point de terminaison Web dans WCF. Les points de terminaison Web envoient des données à l’aide de XML ou JSON. Il n’existe aucune enveloppe SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247102"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="cdf76-105">Procédure : créer un service Web HTTP WCF de base</span><span class="sxs-lookup"><span data-stu-id="cdf76-105">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="cdf76-106">Windows Communication Foundation (WCF) vous permet de créer un service qui expose un point de terminaison Web.</span><span class="sxs-lookup"><span data-stu-id="cdf76-106">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="cdf76-107">Les points de terminaison Web envoient des données par XML ou JSON, il n'y a aucune enveloppe SOAP.</span><span class="sxs-lookup"><span data-stu-id="cdf76-107">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="cdf76-108">Cette rubrique explique comment exposer un tel point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="cdf76-108">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="cdf76-109">La seule méthode pour sécuriser un point de terminaison Web est de l'exposer à travers HTTPS, à l'aide de la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="cdf76-109">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="cdf76-110">Lors de l'utilisation de la sécurité basée sur message, les informations de sécurité sont placées habituellement dans les en-têtes SOAP, et comme les messages envoyés aux points de terminaison non-SOAP ne contiennent aucune enveloppe SOAP, on ne peut placer les informations de sécurité nulle part et vous devez compter sur la sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="cdf76-110">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="cdf76-111">Pour créer un point de terminaison Web</span><span class="sxs-lookup"><span data-stu-id="cdf76-111">To create a Web endpoint</span></span>

1. <span data-ttu-id="cdf76-112">Définissez un contrat de service à l'aide d'une interface marquée avec les attributs <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> et <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cdf76-112">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="cdf76-113">Par défaut, <xref:System.ServiceModel.Web.WebInvokeAttribute> mappe des appels POST à l'opération.</span><span class="sxs-lookup"><span data-stu-id="cdf76-113">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="cdf76-114">Vous pouvez, toutefois, spécifier la méthode HTTP (par exemple, HEAD, PUT ou DELETE) pour le mappage à l'opération en spécifiant un paramètre « method= ».</span><span class="sxs-lookup"><span data-stu-id="cdf76-114">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="cdf76-115"><xref:System.ServiceModel.Web.WebGetAttribute> n'a pas de paramètre « method= » et mappe uniquement des appels GET à l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="cdf76-115"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="cdf76-116">Implémentez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="cdf76-116">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="cdf76-117">Pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="cdf76-117">To host the service</span></span>

1. <span data-ttu-id="cdf76-118">Créez un objet <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cdf76-118">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="cdf76-119">Ajoutez un <xref:System.ServiceModel.Description.ServiceEndpoint> avec <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="cdf76-119">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="cdf76-120">Si vous n'ajoutez pas de point de terminaison, <xref:System.ServiceModel.Web.WebServiceHost> crée automatiquement un point de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="cdf76-120">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="cdf76-121"><xref:System.ServiceModel.Web.WebServiceHost> ajoute également <xref:System.ServiceModel.Description.WebHttpBehavior> et désactive la page d'aide HTTP et la fonctionnalité WSDL (Web Services Description Language) GET afin que le point de terminaison des métadonnées n'interfère pas avec le point de terminaison HTTP par défaut.</span><span class="sxs-lookup"><span data-stu-id="cdf76-121"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="cdf76-122">Ajouter un point de terminaison non-SOAP avec une URL "" provoque un comportement inattendu en cas de tentative d'appeler une opération sur le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="cdf76-122">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="cdf76-123">Cela est dû au fait que l’URI d’écoute du point de terminaison est identique à l’URI de la page d’aide (la page qui s’affiche lorsque vous accédez à l’adresse de base d’un service WCF).</span><span class="sxs-lookup"><span data-stu-id="cdf76-123">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="cdf76-124">Vous pouvez recourir à l'une des actions suivantes pour l'empêcher :</span><span class="sxs-lookup"><span data-stu-id="cdf76-124">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="cdf76-125">Spécifiez toujours un URI non vierge pour un point de terminaison non-SOAP.</span><span class="sxs-lookup"><span data-stu-id="cdf76-125">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="cdf76-126">Désactivez la page d'aide.</span><span class="sxs-lookup"><span data-stu-id="cdf76-126">Turn off the help page.</span></span> <span data-ttu-id="cdf76-127">Pour ce faire, vous pouvez utiliser le code suivant :</span><span class="sxs-lookup"><span data-stu-id="cdf76-127">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="cdf76-128">Ouvrez l'hôte de service et attendez jusqu'à ce que l'utilisateur appuie sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="cdf76-128">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="cdf76-129">Cet exemple montre comment héberger un service de style Web avec une application console.</span><span class="sxs-lookup"><span data-stu-id="cdf76-129">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="cdf76-130">Vous pouvez également héberger un tel service dans IIS.</span><span class="sxs-lookup"><span data-stu-id="cdf76-130">You can also host such a service within IIS.</span></span> <span data-ttu-id="cdf76-131">Pour cela, spécifiez la classe <xref:System.ServiceModel.Activation.WebServiceHostFactory> dans un fichier .svc, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="cdf76-131">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="cdf76-132">Pour appeler des opérations de service mappées à GET dans Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="cdf76-132">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="cdf76-133">Ouvrez Internet Explorer et tapez « `http://localhost:8000/EchoWithGet?s=Hello, world!` », puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="cdf76-133">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="cdf76-134">L’URL contient l’adresse de base du service ( `http://localhost:8000/` ), l’adresse relative du point de terminaison (« »), l’opération de service à appeler («EchoWithGet ») et un point d’interrogation suivi d’une liste de paramètres nommés séparés par une esperluette (&).</span><span class="sxs-lookup"><span data-stu-id="cdf76-134">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="cdf76-135">Pour appeler des opérations de service dans le code</span><span class="sxs-lookup"><span data-stu-id="cdf76-135">To call service operations in code</span></span>

1. <span data-ttu-id="cdf76-136">Créez une instance de <xref:System.ServiceModel.ChannelFactory%601> dans un bloc `using`.</span><span class="sxs-lookup"><span data-stu-id="cdf76-136">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="cdf76-137">Ajoutez <xref:System.ServiceModel.Description.WebHttpBehavior> au point de terminaison appelé par le <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="cdf76-137">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="cdf76-138">Créez le canal et appelez le service.</span><span class="sxs-lookup"><span data-stu-id="cdf76-138">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="cdf76-139">Fermez le <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cdf76-139">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="cdf76-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="cdf76-140">Example</span></span>

<span data-ttu-id="cdf76-141">Les éléments suivants représentent l'intégralité du code pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="cdf76-141">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="cdf76-142">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="cdf76-142">Compiling the code</span></span>

<span data-ttu-id="cdf76-143">Lors de la compilation de Service.cs, référencez System.ServiceModel.dll et System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="cdf76-143">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdf76-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdf76-144">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="cdf76-145">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="cdf76-145">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
