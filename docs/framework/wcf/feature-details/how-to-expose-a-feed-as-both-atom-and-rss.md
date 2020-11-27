---
title: 'Procédure : exposer un flux en tant que flux Atom et RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 1b03434e4f9552b714b40d54ba36c8468d0e2ccd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265360"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="97d2a-102">Procédure : exposer un flux en tant que flux Atom et RSS</span><span class="sxs-lookup"><span data-stu-id="97d2a-102">How to: Expose a Feed as Both Atom and RSS</span></span>

<span data-ttu-id="97d2a-103">Windows Communication Foundation (WCF) vous permet de créer un service qui expose un flux de syndication.</span><span class="sxs-lookup"><span data-stu-id="97d2a-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="97d2a-104">Cette rubrique explique comment créer un service de syndication qui expose un flux de syndication à l'aide d'Atom 1.0 et de RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="97d2a-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="97d2a-105">Ce service expose un point de terminaison qui peut retourner l'un ou l'autre format de syndication.</span><span class="sxs-lookup"><span data-stu-id="97d2a-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="97d2a-106">Pour simplifier, le service utilisé dans cet exemple est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="97d2a-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="97d2a-107">Dans un environnement de production, un service de ce type est hébergé sous IIS ou WAS.</span><span class="sxs-lookup"><span data-stu-id="97d2a-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="97d2a-108">Pour plus d’informations sur les différentes options d’hébergement WCF, consultez [hébergement](hosting.md).</span><span class="sxs-lookup"><span data-stu-id="97d2a-108">For more information about the different WCF hosting options, see [Hosting](hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="97d2a-109">Pour créer un service de syndication de base</span><span class="sxs-lookup"><span data-stu-id="97d2a-109">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="97d2a-110">Définissez un contrat de service utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="97d2a-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="97d2a-111">Chaque opération exposée comme un flux de syndication retourne un objet <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="97d2a-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="97d2a-112">Notez les paramètres de <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="97d2a-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="97d2a-113">`UriTemplate` spécifie l'URL utilisée pour appeler cette opération de service.</span><span class="sxs-lookup"><span data-stu-id="97d2a-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="97d2a-114">La chaîne pour ce paramètre contient des littéraux et une variable entre accolades ({*format*}).</span><span class="sxs-lookup"><span data-stu-id="97d2a-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="97d2a-115">Cette variable correspond au paramètre `format` de l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="97d2a-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="97d2a-116">Pour plus d’informations, consultez <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="97d2a-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="97d2a-117">`BodyStyle` affecte la façon dont les messages que cette opération de service envoie et reçoit sont écrits.</span><span class="sxs-lookup"><span data-stu-id="97d2a-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="97d2a-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> spécifie que les données envoyées vers et depuis cette opération de service ne sont pas renvoyées à la ligne par les éléments XML définis dans l'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="97d2a-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="97d2a-119">Pour plus d’informations, consultez <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="97d2a-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="97d2a-120">Utilisez <xref:System.ServiceModel.ServiceKnownTypeAttribute> pour spécifier les types retournés par les opérations de service dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="97d2a-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="97d2a-121">Implémentez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="97d2a-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="97d2a-122">Créez un objet <xref:System.ServiceModel.Syndication.SyndicationFeed> et ajoutez un auteur, une catégorie et une description.</span><span class="sxs-lookup"><span data-stu-id="97d2a-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="97d2a-123">Créez plusieurs objets <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="97d2a-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="97d2a-124">Ajoutez les objets <xref:System.ServiceModel.Syndication.SyndicationItem> au flux.</span><span class="sxs-lookup"><span data-stu-id="97d2a-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="97d2a-125">Utilisez le paramètre de format pour retourner le format demandé.</span><span class="sxs-lookup"><span data-stu-id="97d2a-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="97d2a-126">Pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="97d2a-126">To host the service</span></span>  
  
1. <span data-ttu-id="97d2a-127">Créez un objet <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="97d2a-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="97d2a-128">La classe <xref:System.ServiceModel.Web.WebServiceHost> ajoute automatiquement un point de terminaison à l'adresse de base du service, sauf si un point est spécifié dans le code ou la configuration.</span><span class="sxs-lookup"><span data-stu-id="97d2a-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="97d2a-129">Dans cet exemple, aucun point de terminaison n'est spécifié. De ce fait, c'est le point de terminaison par défaut qui est exposé.</span><span class="sxs-lookup"><span data-stu-id="97d2a-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="97d2a-130">Ouvrez l'hôte de service, chargez le flux à partir du service, affichez le flux et attendez que l'utilisateur appuie sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="97d2a-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="97d2a-131">Pour appeler GetBlog avec un HTTP GET</span><span class="sxs-lookup"><span data-stu-id="97d2a-131">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="97d2a-132">Ouvrez Internet Explorer, tapez l’URL suivante, puis appuyez sur entrée : `http://localhost:8000/BlogService/GetBlog` .</span><span class="sxs-lookup"><span data-stu-id="97d2a-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="97d2a-133">L’URL contient l’adresse de base du service ( `http://localhost:8000/BlogService` ), l’adresse relative du point de terminaison et l’opération de service à appeler.</span><span class="sxs-lookup"><span data-stu-id="97d2a-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="97d2a-134">Pour appeler GetBlog() à partir d'un code</span><span class="sxs-lookup"><span data-stu-id="97d2a-134">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="97d2a-135">Créez un <xref:System.Xml.XmlReader> avec l'adresse de base et la méthode que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="97d2a-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="97d2a-136">Appelez la méthode <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> statique, en passant dans le <xref:System.Xml.XmlReader> que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="97d2a-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="97d2a-137">Cela appelle l'opération de service et remplit un nouvel objet <xref:System.ServiceModel.Syndication.SyndicationFeed> avec le module de formatage retourné à partir de l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="97d2a-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="97d2a-138">Accédez à l'objet de flux.</span><span class="sxs-lookup"><span data-stu-id="97d2a-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="97d2a-139"> Exemple</span><span class="sxs-lookup"><span data-stu-id="97d2a-139">Example</span></span>  

 <span data-ttu-id="97d2a-140">Les éléments suivants représentent l'intégralité du code pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="97d2a-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="97d2a-141">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="97d2a-141">Compiling the Code</span></span>  

 <span data-ttu-id="97d2a-142">Lors de la compilation du code précédent, référencez System.ServiceModel.dll et System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="97d2a-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d2a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97d2a-143">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
