---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 815f6917413afebc71f0ec6e1c81eb1de14547a4
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876792"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Cet exemple montre comment générer un canal de protocole personnalisé pour utiliser des cookies HTTP pour la gestion des sessions. Ce canal permet la communication entre les services Windows Communication Foundation (WCF) et les clients ASMX ou entre les clients WCF et les services ASMX.  
  
 Lorsqu’un client appelle une méthode Web dans un service Web ASMX qui est basé sur session, le moteur ASP.NET effectue les opérations suivantes :  
  
- Il génère un ID unique (ID de session).  
  
- Il génère l'objet session et l'associe à l'ID unique.  
  
- Il ajoute l'ID unique à un en-tête de réponse HTTP Set-Cookie et l'envoie au client.  
  
- Il identifie le client sur les appels suivants selon l'ID de session qu'il lui envoie.  
  
 Le client inclut cet ID de session dans ses demandes suivantes au serveur. Le serveur utilise l'ID de session du client pour charger l'objet session approprié pour le contexte HTTP actuel.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Modèle d'échange de messages de canal HttpCookieSession   
 Cet exemple active des sessions pour les scénarios de type ASMX. En bas de notre pile de canaux, nous avons le transport HTTP qui prend en charge <xref:System.ServiceModel.Channels.IRequestChannel> et <xref:System.ServiceModel.Channels.IReplyChannel>. C'est le travail du canal de fournir des sessions aux niveaux supérieurs de la pile de canaux. L'exemple implémente deux canaux, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> et <xref:System.ServiceModel.Channels.IReplySessionChannel>) qui prennent en charge les sessions.  
  
## <a name="service-channel"></a>Canal de service  
 L'exemple fournit un canal de service dans la classe `HttpCookieReplySessionChannelListener`. Cette classe implémente l'interface <xref:System.ServiceModel.Channels.IChannelListener> et convertit le canal <xref:System.ServiceModel.Channels.IReplyChannel> du bas de la pile de canaux en un <xref:System.ServiceModel.Channels.IReplySessionChannel>. Ce processus peut être divisé en ce qui suit :  
  
- Lorsque l'écouteur de canal est ouvert, il accepte un canal interne de son écouteur interne. Vu que l'écouteur interne est un écouteur de datagramme et que la durée de vie d'un canal accepté est découplée de la durée de vie de l'écouteur, nous pouvons fermer l'écouteur interne et conserver uniquement le canal interne  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- Lorsque le processus ouvert se termine, nous installons une boucle de messages pour recevoir des messages du canal interne.  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- Lorsqu'un message arrive, le canal de service examine l'identificateur de session et procède à un démultiplexage vers le canal de session approprié. L'écouteur de canal maintient un dictionnaire qui mappe les identificateurs de session aux instances du canal de la session.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 Le `HttpCookieReplySessionChannel` la classe implémente <xref:System.ServiceModel.Channels.IReplySessionChannel>. Les niveaux supérieurs de la pile de canaux appellent la méthode <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> pour lire des demandes pour cette session. Chaque canal de session a une file d'attente de messages privée remplie par le canal de service.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 Dans le cas où quelqu'un appelle la méthode <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> et qu'il n'y a pas de messages dans la file d'attente de messages, le canal attend un certain temps avant de s'arrêter. Cela nettoie les canaux de session créés pour les clients non-WCF.  
  
 Nous utilisons le `channelMapping` pour suivre les `ReplySessionChannels`, et nous ne fermons pas notre `innerChannel` sous-jacent avant que tous les canaux acceptés n'aient été fermés. De cette façon, `HttpCookieReplySessionChannel` peut exister au-delà de la durée de vie de `HttpCookieReplySessionChannelListener`. Nous n'avons pas à nous inquiéter du fait que l'écouteur soit récupéré par le garbage collector en dessous de nous parce que les canaux acceptés conservent une référence à leur écouteur à travers le rappel `OnClosed`.  
  
## <a name="client-channel"></a>Canal client  
 Le canal client correspondant est dans la classe `HttpCookieSessionChannelFactory`. Lors de la création du canal, la fabrication de canal encapsule le canal de demande interne dans un `HttpCookieRequestSessionChannel`. La classe `HttpCookieRequestSessionChannel` transfère les appels au canal de demande sous-jacent. Lorsque le client ferme le proxy, `HttpCookieRequestSessionChannel` envoie un message au service qui indique que le canal est fermé. Donc, la pile de canaux de service peut fermer doucement le canal de session en cours d'utilisation.  
  
## <a name="binding-and-binding-element"></a>Liaison et élément de liaison  
 Après avoir créé les canaux de service et le client, l’étape suivante consiste à les intégrer dans le runtime WCF. Les canaux sont exposés à WCF via les liaisons et éléments de liaison. Une liaison se compose d'un ou de plusieurs éléments de liaison. WCF offre plusieurs liaisons définies par le système ; par exemple, BasicHttpBinding ou WSHttpBinding. La classe `HttpCookieSessionBindingElement` contient l'implémentation pour l'élément de liaison. Elle substitue l'écouteur de canal et les méthodes de création des fabrications de canaux pour procéder aux instanciations requises de l'écouteur de canal ou de la fabrication de canal.  
  
 L'exemple utilise des assertions de stratégie pour décrire le service. Cela permet à l'exemple de publier ses spécifications de canal sur d'autres clients qui peuvent consommer le service. Par exemple, cet élément de liaison publie des assertions de stratégie pour permettre à des clients potentiels de savoir qu’il prend en charge des sessions. Vu que l’exemple active la propriété `ExchangeTerminateMessage` dans la configuration de l’élément de liaison, il ajoute les assertions nécessaires pour montrer que le service prend en charge une action d’échange de messages supplémentaire pour mettre fin à la conversation de la session. Les clients peuvent ensuite utiliser cette action. Le code WSDL suivant illustre les assertions de stratégie créées à partir de l'`HttpCookieSessionBindingElement`.  
  
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
  
 La classe `HttpCookieSessionBinding` est une liaison fournie par le système qui utilise l'élément de liaison décrit précédemment.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Ajout du canal au système de configuration  
 L'exemple fournit deux classes qui exposent l'exemple de canal à travers la configuration. La première est un <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pour l'`HttpCookieSessionBindingElement`. Le bloc de l'implémentation est délégué à `HttpCookieSessionBindingConfigurationElement`, qui dérive de <xref:System.ServiceModel.Configuration.StandardBindingElement>. L'`HttpCookieSessionBindingConfigurationElement` a des propriétés qui correspondent aux propriétés de l'`HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Section d’extension de l’élément de liaison  
 La section `HttpCookieSessionBindingElementSection` est un <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> qui expose `HttpCookieSessionBindingElement` au système de configuration. Avec quelques substitutions, l’exemple définit le nom de section de configuration, le type de l’élément de liaison et la méthode utilisée pour le créer. Nous pouvons ensuite enregistrer la section d'extension dans un fichier de configuration comme suit :  
  
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
  
## <a name="test-code"></a>Code de test  
 Le code de test pour utiliser cet exemple de transport est disponible dans les répertoires Client et Service. Il se compose de deux tests, un test utilise une liaison avec `allowCookies` la valeur `true` sur le client. Le deuxième test active l’arrêt explicite (à l’aide de la fermeture de l’échange de messages) sur la liaison.  
  
 Lorsque vous exécutez l'exemple, vous devez obtenir la sortie suivante :  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Installer ASP.NET 4.0 à l’aide de la commande suivante.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
