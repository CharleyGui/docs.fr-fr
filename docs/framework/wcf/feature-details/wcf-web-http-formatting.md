---
title: Mise en forme HTTP Web WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: e9346cd1bb3798ad0beac5e9e28a8536007d897b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266907"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="7839c-102">Mise en forme HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="7839c-102">WCF Web HTTP formatting</span></span>

<span data-ttu-id="7839c-103">Le modèle de programmation HTTP Web WCF vous permet de déterminer dynamiquement le format le plus approprié pour permettre à une opération de service de retourner sa réponse.</span><span class="sxs-lookup"><span data-stu-id="7839c-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="7839c-104">Deux méthodes pour déterminer le format approprié sont prises en charge : automatique et explicite.</span><span class="sxs-lookup"><span data-stu-id="7839c-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="7839c-105">Mise en forme automatique</span><span class="sxs-lookup"><span data-stu-id="7839c-105">Automatic formatting</span></span>  

 <span data-ttu-id="7839c-106">Lorsqu'elle est activée, la mise en forme automatique choisit le meilleur format dans lequel retourner la réponse.</span><span class="sxs-lookup"><span data-stu-id="7839c-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="7839c-107">Elle détermine le meilleur format en vérifiant dans l'ordre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="7839c-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="7839c-108">Types de médias dans l'en-tête Accept du message de demande.</span><span class="sxs-lookup"><span data-stu-id="7839c-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="7839c-109">Type de contenu du message de demande.</span><span class="sxs-lookup"><span data-stu-id="7839c-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="7839c-110">Paramètre de format par défaut dans l'opération.</span><span class="sxs-lookup"><span data-stu-id="7839c-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="7839c-111">Paramètre de format par défaut dans le WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="7839c-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="7839c-112">Si le message de demande contient un en-tête Accept, l’infrastructure Windows Communication Foundation (WCF) recherche un type qu’il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="7839c-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="7839c-113">Si l'en-tête `Accept` spécifie des priorités pour ses types de médias, elles sont respectées.</span><span class="sxs-lookup"><span data-stu-id="7839c-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="7839c-114">Si aucun format approprié ne se trouve dans l'en-tête `Accept`, le type de contenu du message de demande est utilisé.</span><span class="sxs-lookup"><span data-stu-id="7839c-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="7839c-115">Si aucun type de contenu approprié n'est spécifié, le paramètre de format par défaut de l'opération est utilisé.</span><span class="sxs-lookup"><span data-stu-id="7839c-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="7839c-116">Le format par défaut est défini par le paramètre `ResponseFormat` des attributs <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7839c-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="7839c-117">Si aucun format par défaut n'est spécifié sur l'opération, la valeur de la propriété <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="7839c-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="7839c-118">La mise en forme automatique s'appuie sur la propriété <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="7839c-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="7839c-119">Lorsque cette propriété a la valeur `true`, l'infrastructure WCF détermine le meilleur format à utiliser.</span><span class="sxs-lookup"><span data-stu-id="7839c-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="7839c-120">La sélection automatique du format est désactivée par défaut à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="7839c-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="7839c-121">La sélection automatique du format peut être activée par programme ou par configuration.</span><span class="sxs-lookup"><span data-stu-id="7839c-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="7839c-122">L'exemple suivant montre comment activer la sélection automatique du format dans le code.</span><span class="sxs-lookup"><span data-stu-id="7839c-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="7839c-123">La mise en forme automatique peut également être activée par configuration.</span><span class="sxs-lookup"><span data-stu-id="7839c-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="7839c-124">Vous pouvez définir la propriété <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> directement sur <xref:System.ServiceModel.Description.WebHttpBehavior> ou à l'aide de <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="7839c-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="7839c-125">L'exemple suivant montre comment activer la sélection automatique du format sur le <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7839c-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="7839c-126">L'exemple suivant montre comment activer la sélection automatique du format à l'aide de <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="7839c-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="7839c-127">Mise en forme explicite</span><span class="sxs-lookup"><span data-stu-id="7839c-127">Explicit formatting</span></span>  

 <span data-ttu-id="7839c-128">Comme son nom l'indique, dans une mise en forme explicite le développeur détermine le meilleur format à utiliser dans le code d'opération.</span><span class="sxs-lookup"><span data-stu-id="7839c-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="7839c-129">Si le meilleur format est XML ou JSON, le développeur affecte à la propriété <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> la valeur <xref:System.ServiceModel.Web.WebMessageFormat.Xml> ou <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="7839c-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="7839c-130">Si la propriété <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> n'est pas définie de manière explicite, le format par défaut de l'opération est utilisé.</span><span class="sxs-lookup"><span data-stu-id="7839c-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="7839c-131">L'exemple suivant cherche un format à utiliser dans le paramètre de chaîne de demande du format.</span><span class="sxs-lookup"><span data-stu-id="7839c-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="7839c-132">S'il a été spécifié, il définit le format de l'opération à l'aide de la propriété <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span><span class="sxs-lookup"><span data-stu-id="7839c-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="7839c-133">Si vous devez prendre en charge d’autres formats que XML ou JSON, définissez votre opération pour qu’elle ait un type de retour de <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="7839c-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="7839c-134">Dans le code d'opération, déterminez le format approprié à utiliser, puis créez un objet <xref:System.ServiceModel.Channels.Message> à l'aide de l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7839c-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="7839c-135">Chacune de ces méthodes prend le contenu et crée un message au format approprié.</span><span class="sxs-lookup"><span data-stu-id="7839c-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="7839c-136">La méthode `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` peut être utilisée pour obtenir une liste des formats préférés du client par ordre préférentiel décroissant.</span><span class="sxs-lookup"><span data-stu-id="7839c-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="7839c-137">L'exemple suivant indique comment utiliser `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` pour déterminer le format à utiliser, puis il utilise la méthode de réponse appropriée pour créer le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="7839c-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7839c-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7839c-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="7839c-139">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="7839c-139">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="7839c-140">UriTemplate et UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="7839c-140">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="7839c-141">Vue d'ensemble du modèle de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="7839c-141">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="7839c-142">Modèle objet de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="7839c-142">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
