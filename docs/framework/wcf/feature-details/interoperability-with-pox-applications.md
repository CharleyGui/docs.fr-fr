---
title: Interopérabilité avec les applications POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 17b85ab41589a130e950cd52c759305cc17e92b7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591048"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="20908-102">Interopérabilité avec les applications POX</span><span class="sxs-lookup"><span data-stu-id="20908-102">Interoperability with POX applications</span></span>

<span data-ttu-id="20908-103">« Plain Old XML » les applications (POX) communiquent en échangeant des messages HTTP bruts qui contiennent uniquement les données d’application XML qui ne sont pas comprises dans une enveloppe SOAP.</span><span class="sxs-lookup"><span data-stu-id="20908-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="20908-104">Windows Communication Foundation (WCF) peut fournir les services et les clients qui utilisent des messages POX.</span><span class="sxs-lookup"><span data-stu-id="20908-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="20908-105">Sur le service, WCF peut être utilisé pour implémenter des services qui exposent des points de terminaison clients tels que des navigateurs Web et langages de script qui envoient et reçoivent des messages POX.</span><span class="sxs-lookup"><span data-stu-id="20908-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="20908-106">Sur le client, le modèle de programmation WCF peut être utilisé pour implémenter des clients qui communiquent avec les services POX.</span><span class="sxs-lookup"><span data-stu-id="20908-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20908-107">Ce document a été initialement écrit pour le .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="20908-107">This document was originally written for the .NET Framework 3.0.</span></span>  <span data-ttu-id="20908-108">.NET framework 3.5 prend en charge pour l’utilisation des applications POX.</span><span class="sxs-lookup"><span data-stu-id="20908-108">.NET Framework 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="20908-109">Pour plus d’informations sur, consultez [modèle de programmation WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="20908-109">For more information about see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="20908-110">Programmation POX avec WCF</span><span class="sxs-lookup"><span data-stu-id="20908-110">POX programming with WCF</span></span>

<span data-ttu-id="20908-111">Les services WCF qui communiquent par HTTP à l’aide de messages POX utilisent une [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="20908-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="20908-112">Cette liaison personnalisée contient deux éléments :</span><span class="sxs-lookup"><span data-stu-id="20908-112">This custom binding contains two elements:</span></span>

- [<span data-ttu-id="20908-113">\<httpTransport></span><span class="sxs-lookup"><span data-stu-id="20908-113">\<httpTransport></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [<span data-ttu-id="20908-114">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="20908-114">\<textMessageEncoding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="20908-115">La norme encodeur de Message texte WCF est spécialement configuré pour utiliser le <xref:System.ServiceModel.Channels.MessageVersion.None%2A> valeur, ce qui lui permet de traiter le message charges utiles XML qui n’arrivent pas encapsulés dans une enveloppe SOAP.</span><span class="sxs-lookup"><span data-stu-id="20908-115">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="20908-116">Les clients WCF qui communiquent par HTTP à l’aide de messages POX utilisent une liaison semblable (illustrée dans le code impératif suivant).</span><span class="sxs-lookup"><span data-stu-id="20908-116">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

<span data-ttu-id="20908-117">Étant donné que les clients POX doivent spécifier explicitement les URI auxquels ils envoient des messages, ils doivent généralement configurer le <xref:System.ServiceModel.Channels.HttpTransportBindingElement> avec un mode d'adressage manuel en affectant à la propriété <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> la valeur `true` sur l'élément.</span><span class="sxs-lookup"><span data-stu-id="20908-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="20908-118">Cela permet aux messages d'être adressés explicitement par le code d'application et il n'est pas nécessaire de créer une <xref:System.ServiceModel.ChannelFactory> chaque fois qu'une application envoie un message à un URI HTTP différent.</span><span class="sxs-lookup"><span data-stu-id="20908-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="20908-119">Étant donné que les messages POX n'utilisent pas d'en-tête SOAP pour acheminer des informations de protocole importantes, les clients et les services POX doivent souvent traiter des parties de la requête HTTP sous-jacente utilisée pour envoyer ou recevoir un message.</span><span class="sxs-lookup"><span data-stu-id="20908-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="20908-120">Informations de protocole HTTP spécifiques tels que les en-têtes HTTP et les codes d’état sont affichées dans le modèle de programmation WCF à travers deux classes :</span><span class="sxs-lookup"><span data-stu-id="20908-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="20908-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, qui contient des informations à propos de la requête HTTP, telles que la méthode HTTP et les en-têtes de demande.</span><span class="sxs-lookup"><span data-stu-id="20908-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="20908-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, qui contient des informations à propos de la réponse HTTP, telles que le code d'état HTTP et la description de l'état, ainsi que des en-têtes de réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="20908-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="20908-123">L’exemple de code suivant montre comment créer un message de demande HTTP GET adressé à `http://localhost:8100/customers`.</span><span class="sxs-lookup"><span data-stu-id="20908-123">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="20908-124">En premier lieu, un demande <xref:System.ServiceModel.Channels.Message> vide est créée en appelant <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="20908-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="20908-125">Le paramètre <xref:System.ServiceModel.Channels.MessageVersion.None%2A> est utilisé pour indiquer qu'une enveloppe SOAP n'est pas requise et le paramètre <xref:System.String.Empty> est passé comme Action.</span><span class="sxs-lookup"><span data-stu-id="20908-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="20908-126">Puis le message de demande est adressé en affectant à l'en-tête <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> l'URI désiré.</span><span class="sxs-lookup"><span data-stu-id="20908-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="20908-127">Ensuite, une <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> est créée et la <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> a pour valeur la méthode GET de verbe HTTP et le <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> a la valeur `true` pour indiquer qu'aucunes données ne doivent être envoyées dans le corps du message de requête HTTP sortant.</span><span class="sxs-lookup"><span data-stu-id="20908-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="20908-128">Enfin, la propriété de demande est ajoutée à la collection <xref:System.ServiceModel.Channels.Message.Properties%2A> du message de demande de manière à pouvoir influencer la manière dont le transport HTTP envoie la demande.</span><span class="sxs-lookup"><span data-stu-id="20908-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="20908-129">Le message est alors prêt à être envoyé sur une instance appropriée de <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="20908-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="20908-130">Des techniques semblables peuvent être utilisées sur le service pour extraire la <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> d'un message entrant et construire une réponse.</span><span class="sxs-lookup"><span data-stu-id="20908-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
