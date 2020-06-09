---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 8dba147ace7ada221b5d274cd233e4b9618835d9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585128"
---
# <a name="httpcookiesession"></a><span data-ttu-id="6df91-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="6df91-102">HttpCookieSession</span></span>
<span data-ttu-id="6df91-103">Cet exemple montre comment générer un canal de protocole personnalisé pour utiliser des cookies HTTP pour la gestion des sessions.</span><span class="sxs-lookup"><span data-stu-id="6df91-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="6df91-104">Ce canal active la communication entre les services Windows Communication Foundation (WCF) et les clients ASMX, ou entre les clients WCF et les services ASMX.</span><span class="sxs-lookup"><span data-stu-id="6df91-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="6df91-105">Lorsqu’un client appelle une méthode Web dans un service Web ASMX basé sur une session, le moteur ASP.NET effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6df91-105">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="6df91-106">Il génère un ID unique (ID de session).</span><span class="sxs-lookup"><span data-stu-id="6df91-106">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="6df91-107">Il génère l'objet session et l'associe à l'ID unique.</span><span class="sxs-lookup"><span data-stu-id="6df91-107">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="6df91-108">Il ajoute l'ID unique à un en-tête de réponse HTTP Set-Cookie et l'envoie au client.</span><span class="sxs-lookup"><span data-stu-id="6df91-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="6df91-109">Il identifie le client sur les appels suivants selon l'ID de session qu'il lui envoie.</span><span class="sxs-lookup"><span data-stu-id="6df91-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="6df91-110">Le client inclut cet ID de session dans ses demandes suivantes au serveur.</span><span class="sxs-lookup"><span data-stu-id="6df91-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="6df91-111">Le serveur utilise l'ID de session du client pour charger l'objet session approprié pour le contexte HTTP actuel.</span><span class="sxs-lookup"><span data-stu-id="6df91-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6df91-112">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6df91-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6df91-113">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6df91-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6df91-114">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6df91-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6df91-115">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6df91-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="6df91-116">Modèle d'échange de messages de canal HttpCookieSession </span><span class="sxs-lookup"><span data-stu-id="6df91-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="6df91-117">Cet exemple active des sessions pour les scénarios de type ASMX.</span><span class="sxs-lookup"><span data-stu-id="6df91-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="6df91-118">En bas de notre pile de canaux, nous avons le transport HTTP qui prend en charge <xref:System.ServiceModel.Channels.IRequestChannel> et <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="6df91-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="6df91-119">C'est le travail du canal de fournir des sessions aux niveaux supérieurs de la pile de canaux.</span><span class="sxs-lookup"><span data-stu-id="6df91-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="6df91-120">L'exemple implémente deux canaux, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> et <xref:System.ServiceModel.Channels.IReplySessionChannel>) qui prennent en charge les sessions.</span><span class="sxs-lookup"><span data-stu-id="6df91-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="6df91-121">Canal de service</span><span class="sxs-lookup"><span data-stu-id="6df91-121">Service Channel</span></span>  
 <span data-ttu-id="6df91-122">L'exemple fournit un canal de service dans la classe `HttpCookieReplySessionChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="6df91-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="6df91-123">Cette classe implémente l'interface <xref:System.ServiceModel.Channels.IChannelListener> et convertit le canal <xref:System.ServiceModel.Channels.IReplyChannel> du bas de la pile de canaux en un <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="6df91-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="6df91-124">Ce processus peut être divisé en ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="6df91-124">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="6df91-125">Lorsque l'écouteur de canal est ouvert, il accepte un canal interne de son écouteur interne.</span><span class="sxs-lookup"><span data-stu-id="6df91-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="6df91-126">Vu que l'écouteur interne est un écouteur de datagramme et que la durée de vie d'un canal accepté est découplée de la durée de vie de l'écouteur, nous pouvons fermer l'écouteur interne et conserver uniquement le canal interne</span><span class="sxs-lookup"><span data-stu-id="6df91-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="6df91-127">Lorsque le processus ouvert se termine, nous installons une boucle de messages pour recevoir des messages du canal interne.</span><span class="sxs-lookup"><span data-stu-id="6df91-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="6df91-128">Lorsqu'un message arrive, le canal de service examine l'identificateur de session et procède à un démultiplexage vers le canal de session approprié.</span><span class="sxs-lookup"><span data-stu-id="6df91-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="6df91-129">L'écouteur de canal maintient un dictionnaire qui mappe les identificateurs de session aux instances du canal de la session.</span><span class="sxs-lookup"><span data-stu-id="6df91-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="6df91-130">La `HttpCookieReplySessionChannel` classe implémente <xref:System.ServiceModel.Channels.IReplySessionChannel> .</span><span class="sxs-lookup"><span data-stu-id="6df91-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="6df91-131">Les niveaux supérieurs de la pile de canaux appellent la méthode <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> pour lire des demandes pour cette session.</span><span class="sxs-lookup"><span data-stu-id="6df91-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="6df91-132">Chaque canal de session a une file d'attente de messages privée remplie par le canal de service.</span><span class="sxs-lookup"><span data-stu-id="6df91-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="6df91-133">Dans le cas où quelqu'un appelle la méthode <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> et qu'il n'y a pas de messages dans la file d'attente de messages, le canal attend un certain temps avant de s'arrêter.</span><span class="sxs-lookup"><span data-stu-id="6df91-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="6df91-134">Cela nettoie les canaux de session créés pour les clients non-WCF.</span><span class="sxs-lookup"><span data-stu-id="6df91-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="6df91-135">Nous utilisons le `channelMapping` pour suivre les `ReplySessionChannels`, et nous ne fermons pas notre `innerChannel` sous-jacent avant que tous les canaux acceptés n'aient été fermés.</span><span class="sxs-lookup"><span data-stu-id="6df91-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="6df91-136">De cette façon, `HttpCookieReplySessionChannel` peut exister au-delà de la durée de vie de `HttpCookieReplySessionChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="6df91-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="6df91-137">Nous n'avons pas à nous inquiéter du fait que l'écouteur soit récupéré par le garbage collector en dessous de nous parce que les canaux acceptés conservent une référence à leur écouteur à travers le rappel `OnClosed`.</span><span class="sxs-lookup"><span data-stu-id="6df91-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="6df91-138">Canal client</span><span class="sxs-lookup"><span data-stu-id="6df91-138">Client channel</span></span>  
 <span data-ttu-id="6df91-139">Le canal client correspondant est dans la classe `HttpCookieSessionChannelFactory`.</span><span class="sxs-lookup"><span data-stu-id="6df91-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="6df91-140">Lors de la création du canal, la fabrication de canal encapsule le canal de demande interne dans un `HttpCookieRequestSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="6df91-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="6df91-141">La classe `HttpCookieRequestSessionChannel` transfère les appels au canal de demande sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="6df91-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="6df91-142">Lorsque le client ferme le proxy, `HttpCookieRequestSessionChannel` envoie un message au service qui indique que le canal est fermé.</span><span class="sxs-lookup"><span data-stu-id="6df91-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="6df91-143">Donc, la pile de canaux de service peut fermer doucement le canal de session en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="6df91-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="6df91-144">Liaison et élément de liaison</span><span class="sxs-lookup"><span data-stu-id="6df91-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="6df91-145">Après avoir créé le service et les canaux clients, l’étape suivante consiste à les intégrer dans le runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="6df91-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="6df91-146">Les canaux sont exposés à WCF via des liaisons et des éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="6df91-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="6df91-147">Une liaison se compose d'un ou de plusieurs éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="6df91-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="6df91-148">WCF offre plusieurs liaisons définies par le système. par exemple, BasicHttpBinding ou WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="6df91-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="6df91-149">La classe `HttpCookieSessionBindingElement` contient l'implémentation pour l'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="6df91-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="6df91-150">Elle substitue l'écouteur de canal et les méthodes de création des fabrications de canaux pour procéder aux instanciations requises de l'écouteur de canal ou de la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="6df91-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="6df91-151">L'exemple utilise des assertions de stratégie pour décrire le service.</span><span class="sxs-lookup"><span data-stu-id="6df91-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="6df91-152">Cela permet à l'exemple de publier ses spécifications de canal sur d'autres clients qui peuvent consommer le service.</span><span class="sxs-lookup"><span data-stu-id="6df91-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="6df91-153">Par exemple, cet élément de liaison publie des assertions de stratégie pour permettre à des clients potentiels de savoir qu’il prend en charge des sessions.</span><span class="sxs-lookup"><span data-stu-id="6df91-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="6df91-154">Vu que l’exemple active la propriété `ExchangeTerminateMessage` dans la configuration de l’élément de liaison, il ajoute les assertions nécessaires pour montrer que le service prend en charge une action d’échange de messages supplémentaire pour mettre fin à la conversation de la session.</span><span class="sxs-lookup"><span data-stu-id="6df91-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="6df91-155">Les clients peuvent ensuite utiliser cette action.</span><span class="sxs-lookup"><span data-stu-id="6df91-155">Clients can then use this action.</span></span> <span data-ttu-id="6df91-156">Le code WSDL suivant illustre les assertions de stratégie créées à partir de l'`HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="6df91-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="6df91-157">La classe `HttpCookieSessionBinding` est une liaison fournie par le système qui utilise l'élément de liaison décrit précédemment.</span><span class="sxs-lookup"><span data-stu-id="6df91-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="6df91-158">Ajout du canal au système de configuration</span><span class="sxs-lookup"><span data-stu-id="6df91-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="6df91-159">L'exemple fournit deux classes qui exposent l'exemple de canal à travers la configuration.</span><span class="sxs-lookup"><span data-stu-id="6df91-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="6df91-160">La première est un <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pour l'`HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="6df91-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="6df91-161">Le bloc de l'implémentation est délégué à `HttpCookieSessionBindingConfigurationElement`, qui dérive de <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="6df91-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="6df91-162">L'`HttpCookieSessionBindingConfigurationElement` a des propriétés qui correspondent aux propriétés de l'`HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="6df91-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="6df91-163">Section d’extension de l’élément de liaison</span><span class="sxs-lookup"><span data-stu-id="6df91-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="6df91-164">La section `HttpCookieSessionBindingElementSection` est un <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> qui expose `HttpCookieSessionBindingElement` au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="6df91-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="6df91-165">Avec quelques substitutions, l’exemple définit le nom de section de configuration, le type de l’élément de liaison et la méthode utilisée pour le créer.</span><span class="sxs-lookup"><span data-stu-id="6df91-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="6df91-166">Nous pouvons ensuite enregistrer la section d'extension dans un fichier de configuration comme suit :</span><span class="sxs-lookup"><span data-stu-id="6df91-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>
    <system.serviceModel>
      <extensions>
        <bindingElementExtensions>
          <add name="httpCookieSession"
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,
                    HttpCookieSessionExtension, Version=1.0.0.0,
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>
    </system.serviceModel>
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="6df91-167">Code de test</span><span class="sxs-lookup"><span data-stu-id="6df91-167">Test Code</span></span>  
 <span data-ttu-id="6df91-168">Le code de test pour utiliser cet exemple de transport est disponible dans les répertoires Client et Service.</span><span class="sxs-lookup"><span data-stu-id="6df91-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="6df91-169">Il se compose de deux tests : un test utilise une liaison avec `allowCookies` `true` la valeur sur le client.</span><span class="sxs-lookup"><span data-stu-id="6df91-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="6df91-170">Le deuxième test active l’arrêt explicite (à l’aide de la fermeture de l’échange de messages) sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="6df91-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="6df91-171">Lorsque vous exécutez l'exemple, vous devez obtenir la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6df91-171">When you run the sample, you should see the following output:</span></span>  
  
```console  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6df91-172">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6df91-172">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6df91-173">Installez ASP.NET 4,0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="6df91-173">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="6df91-174">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6df91-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="6df91-175">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6df91-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="6df91-176">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6df91-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
