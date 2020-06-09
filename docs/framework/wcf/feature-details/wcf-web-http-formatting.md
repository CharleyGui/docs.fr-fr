---
title: Mise en forme HTTP Web WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 011ff4f2e667268fac1aa2d82c0a2c4ffefc8dde
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585556"
---
# <a name="wcf-web-http-formatting"></a>Mise en forme HTTP Web WCF
Le modèle de programmation HTTP Web WCF vous permet de déterminer dynamiquement le format le plus approprié pour permettre à une opération de service de retourner sa réponse. Deux méthodes pour déterminer le format approprié sont prises en charge : automatique et explicite.  
  
## <a name="automatic-formatting"></a>Mise en forme automatique  
 Lorsqu'elle est activée, la mise en forme automatique choisit le meilleur format dans lequel retourner la réponse. Elle détermine le meilleur format en vérifiant dans l'ordre les éléments suivants :  
  
1. Types de médias dans l'en-tête Accept du message de demande.  
  
2. Type de contenu du message de demande.  
  
3. Paramètre de format par défaut dans l'opération.  
  
4. Paramètre de format par défaut dans le WebHttpBehavior.  
  
 Si le message de demande contient un en-tête Accept, l’infrastructure Windows Communication Foundation (WCF) recherche un type qu’il prend en charge. Si l'en-tête `Accept` spécifie des priorités pour ses types de médias, elles sont respectées. Si aucun format approprié ne se trouve dans l'en-tête `Accept`, le type de contenu du message de demande est utilisé. Si aucun type de contenu approprié n'est spécifié, le paramètre de format par défaut de l'opération est utilisé. Le format par défaut est défini par le paramètre `ResponseFormat` des attributs <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>. Si aucun format par défaut n'est spécifié sur l'opération, la valeur de la propriété <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> est utilisée. La mise en forme automatique s'appuie sur la propriété <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>. Lorsque cette propriété a la valeur `true`, l'infrastructure WCF détermine le meilleur format à utiliser. La sélection automatique du format est désactivée par défaut à des fins de compatibilité descendante. La sélection automatique du format peut être activée par programme ou par configuration. L'exemple suivant montre comment activer la sélection automatique du format dans le code.  
  
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
  
 La mise en forme automatique peut également être activée par configuration. Vous pouvez définir la propriété <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> directement sur <xref:System.ServiceModel.Description.WebHttpBehavior> ou à l'aide de <xref:System.ServiceModel.Description.WebHttpEndpoint>. L'exemple suivant montre comment activer la sélection automatique du format sur le <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
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
  
 L'exemple suivant montre comment activer la sélection automatique du format à l'aide de <xref:System.ServiceModel.Description.WebHttpEndpoint>.  
  
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
  
## <a name="explicit-formatting"></a>Mise en forme explicite  
 Comme son nom l'indique, dans une mise en forme explicite le développeur détermine le meilleur format à utiliser dans le code d'opération. Si le meilleur format est XML ou JSON, le développeur affecte à la propriété <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> la valeur <xref:System.ServiceModel.Web.WebMessageFormat.Xml> ou <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Si la propriété <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> n'est pas définie de manière explicite, le format par défaut de l'opération est utilisé.  
  
 L'exemple suivant cherche un format à utiliser dans le paramètre de chaîne de demande du format. S'il a été spécifié, il définit le format de l'opération à l'aide de la propriété <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
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
  
 Si vous devez prendre en charge d’autres formats que XML ou JSON, définissez votre opération pour qu’elle ait un type de retour de <xref:System.ServiceModel.Channels.Message>. Dans le code d'opération, déterminez le format approprié à utiliser, puis créez un objet <xref:System.ServiceModel.Channels.Message> à l'aide de l'une des méthodes suivantes :  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Chacune de ces méthodes prend le contenu et crée un message au format approprié. La méthode `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` peut être utilisée pour obtenir une liste des formats préférés du client par ordre préférentiel décroissant. L'exemple suivant indique comment utiliser `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` pour déterminer le format à utiliser, puis il utilise la méthode de réponse appropriée pour créer le message de réponse.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [Modèle de programmation HTTP Web WCF](wcf-web-http-programming-model.md)
- [UriTemplate et UriTemplateTable](uritemplate-and-uritemplatetable.md)
- [Vue d'ensemble du modèle de programmation Web HTTP WCF](wcf-web-http-programming-model-overview.md)
- [Modèle objet de programmation HTTP web WCF](wcf-web-http-programming-object-model.md)
