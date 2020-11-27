---
title: 'Transport : UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 815a0a50e42e68040673e34e5ebccad17dfeecda
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258749"
---
# <a name="transport-udp"></a>Transport : UDP

L’exemple de transport UDP montre comment implémenter la monodiffusion et la multidiffusion UDP comme un transport Windows Communication Foundation (WCF) personnalisé. L’exemple décrit la procédure recommandée pour créer un transport personnalisé dans WCF, en utilisant l’infrastructure de canal et les meilleures pratiques WCF suivantes. Les étapes de la création d'un transport personnalisé sont les suivantes :  
  
1. Déterminez lequel des [modèles d’échange de messages](#MessageExchangePatterns) de canal (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel) que votre ChannelFactory et ChannelListener prendra en charge. Déterminez ensuite si vous prendrez en charge les variantes de session de ces interfaces.  
  
2. Créez une fabrication et un écouteur de canal qui prennent en charge votre modèle d’échange de messages.  
  
3. Assurez-vous que les exceptions spécifiques au réseau sont normalisées selon la classe dérivée appropriée de <xref:System.ServiceModel.CommunicationException>.  
  
4. Ajoutez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément qui ajoute le transport personnalisé à une pile de canaux. Pour plus d’informations, consultez [Ajout d’un élément de liaison](#AddingABindingElement).  
  
5. Ajoutez une section d’extension d’élément de liaison afin d’exposer le nouvel élément de liaison au système de configuration.  
  
6. Ajoutez des extensions de métadonnées pour communiquer des fonctionnalités à d'autres points de terminaison.  
  
7. Ajoutez une liaison qui préconfigure une pile d’éléments de liaison d’après un profil bien défini. Pour plus d’informations, consultez [Ajout d’une liaison standard](#AddingAStandardBinding).  
  
8. Ajoutez une section de liaison ainsi qu'un élément de configuration de liaison afin d'exposer la liaison au système de configuration. Pour plus d’informations, consultez Ajout de la [prise en charge](#AddingConfigurationSupport)de la configuration.  
  
<a name="MessageExchangePatterns"></a>

## <a name="message-exchange-patterns"></a>Modèles d’échange de messages  

 La première étape de l’écriture d’un transport personnalisé consiste à déterminer les MEP (Message Exchange Pattern, modèle d’échange de messages) requis pour le transport. Trois MEP sont disponibles :  
  
- Datagramme (IInputChannel/IOutputChannel)  
  
     Lorsque vous utilisez un MEP datagramme, un client envoie un message en utilisant un échange de type « déclenché et oublié » (fire and forget). Un échange de ce type requiert une confirmation hors bande de la réussite de la remise. Le message peut être perdu lors de la transmission et ne jamais atteindre le service. Si l'opération d'envoi s'exécute correctement au niveau du client, cela ne garantit pas que le point de terminaison distant a effectivement reçu le message. Le datagramme est un bloc de construction de messagerie fondamental. Vous pouvez en effet définir vos propres protocoles au-dessus de ce bloc, notamment des protocoles fiables et sécurisés. Les canaux de datagramme du client implémentent l'interface <xref:System.ServiceModel.Channels.IOutputChannel> et ceux du service implémentent l'interface <xref:System.ServiceModel.Channels.IInputChannel>.  
  
- Demande-réponse (IRequestChannel/IReplyChannel)  
  
     Dans ce MEP, un message est envoyé et une réponse est reçue. Ce modèle se compose de paires demande-réponse. Parmi les exemples d'appels demande-réponse figurent notamment les appels de procédure distante (RPC) et les demandes GET de navigateur. Ce modèle est également connu sous le nom de mode semi-duplex. Dans ce MEP, les canaux du client implémentent <xref:System.ServiceModel.Channels.IRequestChannel> et ceux du service implémentent <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
- Duplex (IDuplexChannel)  
  
     Le MEP duplex permet à un nombre aléatoire de messages d'être envoyés par un client et d'être reçus dans un ordre indifférencié. Le MEP duplex est similaire à une conversation téléphonique, où chaque mot prononcé correspond à un message. Les deux côtés pouvant envoyer et recevoir des messages dans ce MEP, l'interface implémentée par les canaux du client et du service est <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Chacun de ces MEP peut également prendre en charge des sessions. Les fonctionnalités fournies par un canal de session permettent de corréler tous les messages envoyés et reçus sur un canal. Le modèle demande-réponse correspond à une session autonome à deux messages, la demande et la réponse étant corrélées. En revanche, le modèle demande-réponse qui prend en charge les sessions implique que toutes les paires demande/réponse sur ce canal soient corrélées les unes avec les autres. Six MEP sont donc disponibles au total : datagramme, demande-réponse, duplex, datagramme avec sessions, demande-réponse avec sessions et duplex avec sessions.  
  
> [!NOTE]
> Concernant le transport UDP, le seul MEP pris en charge est datagramme, le protocole UDP étant de part nature un protocole de type « déclenché et oublié ».  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>ICommunicationObject et cycle de vie des objets WCF  

 WCF possède un ordinateur d’État commun qui est utilisé pour gérer le cycle de vie d’objets tels que <xref:System.ServiceModel.Channels.IChannel> , <xref:System.ServiceModel.Channels.IChannelFactory> , et <xref:System.ServiceModel.Channels.IChannelListener> qui sont utilisés pour la communication. Ces objets de communication peuvent avoir cinq états différents. Ces états sont représentés par l'énumération <xref:System.ServiceModel.CommunicationState> et sont les suivants :  
  
- Created : état d'un <xref:System.ServiceModel.ICommunicationObject> lorsqu'il est instancié pour la première fois. Aucune entrée/sortie (E/S) ne se produit dans cet état.  
  
- Opening : les objets passent à cet état lorsque <xref:System.ServiceModel.ICommunicationObject.Open%2A> est appelé. À ce stade, les propriétés sont rendues immuables, et les entrées/sorties peuvent commencer. Cette transition est uniquement valide à partir de l'état Created.  
  
- Opened : les objets passent à cet état lorsque le processus d'ouverture est terminé. Cette transition est uniquement valide à partir de l'état Opening. À ce stade, l'objet est totalement utilisable pour le transfert.  
  
- Closing : les objets passent à cet état lorsque <xref:System.ServiceModel.ICommunicationObject.Close%2A> est appelé pour un arrêt approprié. Cette transition est uniquement valide à partir de l'état Opened.  
  
- Closed : dans cet état, les objets ne sont plus utilisables. En général, la configuration est encore accessible pour l'inspection, mais aucune communication ne peut se produire. Cet état est équivalent à la suppression des objets.  
  
- Faulted : dans cet état, les objets sont accessibles pour l'inspection, mais e sont plus utilisables. Lorsqu'une erreur non récupérable se produit, l'objet passe à cet état. La seule transition valide à partir de cet État est à l' `Closed` État.  
  
 Des événements se déclenchent pour chaque transition d'état. La méthode <xref:System.ServiceModel.ICommunicationObject.Abort%2A> peut être appelée à tout moment et provoquer la transition immédiate de l'objet de son état actuel à l'état Closed. L'appel de <xref:System.ServiceModel.ICommunicationObject.Abort%2A> termine toute tâche inachevée.  
  
<a name="ChannelAndChannelListener"></a>

## <a name="channel-factory-and-channel-listener"></a>Fabrication et écouteur de canal  

 L'étape suivante de l'écriture d'un transport personnalisé consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelFactory> pour les canaux clients et de <xref:System.ServiceModel.Channels.IChannelListener> pour les canaux de service. La couche de canal utilise un modèle de fabrication pour construire des canaux. WCF fournit des applications auxiliaires de classe de base pour ce processus.  
  
- La classe <xref:System.ServiceModel.Channels.CommunicationObject> implémente <xref:System.ServiceModel.ICommunicationObject> et applique la machine d'état précédemment décrite à l'étape 2.

- La <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implémente <xref:System.ServiceModel.Channels.CommunicationObject> et fournit une classe de base unifiée pour <xref:System.ServiceModel.Channels.ChannelFactoryBase> et <xref:System.ServiceModel.Channels.ChannelListenerBase> . La classe <xref:System.ServiceModel.Channels.ChannelManagerBase> fonctionne avec <xref:System.ServiceModel.Channels.ChannelBase>, qui est une classe de base implémentant <xref:System.ServiceModel.Channels.IChannel>.  
  
- La <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implémente <xref:System.ServiceModel.Channels.ChannelManagerBase> et <xref:System.ServiceModel.Channels.IChannelFactory> consolide les `CreateChannel` surcharges dans une `OnCreateChannel` méthode abstraite.  
  
- La <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implémente <xref:System.ServiceModel.Channels.IChannelListener> . Elle se charge de la gestion d'état de base.  
  
 Dans cet exemple, l'implémentation de la fabrication est contenue dans UdpChannelFactory.cs et l'implémentation de l'écouteur est contenue dans UdpChannelListener.cs. Les implémentations <xref:System.ServiceModel.Channels.IChannel> sont contenues dans UdpOutputChannel.cs et UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>Fabrication de canal UDP  

 `UdpChannelFactory` dérive de <xref:System.ServiceModel.Channels.ChannelFactoryBase>. L'exemple substitue <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> pour fournir un accès à la version du message de l'encodeur de message. L'exemple substitue également <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> afin de nous permettre de détruire notre instance de <xref:System.ServiceModel.Channels.BufferManager> lors des transitions de la machine d'état.  
  
#### <a name="the-udp-output-channel"></a>Canal de sortie UDP  

 `UdpOutputChannel` implémente <xref:System.ServiceModel.Channels.IOutputChannel>. Le constructeur valide les arguments et construit un objet <xref:System.Net.EndPoint> de destination reposant sur le <xref:System.ServiceModel.EndpointAddress> qui est passé.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Le canal peut être fermé de façon appropriée ou incorrecte. Si le canal est fermé de façon normale, le socket est fermé et un appel à la méthode `OnClose` de la classe de base est réalisé. Si une exception est alors levée, l'infrastructure appelle `Abort` pour veiller à ce que le canal soit nettoyé.  
  
```csharp
this.socket.Close(0);  
```  
  
 Nous implémentons ensuite `Send()` et `BeginSend()` / `EndSend()` . Deux phases peuvent alors être distinguées. Tout d'abord, la sérialisation du message dans un tableau d'octets.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Puis, l'envoi des données résultantes sur le câble.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  

 Le `UdpChannelListener` que l’exemple implémente dérive de la <xref:System.ServiceModel.Channels.ChannelListenerBase> classe. Il utilise un socket UDP unique pour recevoir des datagrammes. La méthode `OnOpen` reçoit des données à l'aide du socket UDP dans une boucle asynchrone. Les données sont ensuite converties en messages à l'aide de l'infrastructure d'encodage de message.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Étant donné que le même canal de datagramme représente des messages qui arrivent de plusieurs sources, l'`UdpChannelListener` est un écouteur Singleton. Il y a, au plus, un actif <xref:System.ServiceModel.Channels.IChannel> associé à cet écouteur à la fois. L'exemple en génère un autre uniquement si un canal retourné par la méthode `AcceptChannel` est disposé par la suite. Lorsqu'un message est reçu, il est mis en file d'attente dans ce canal singleton.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  

 La `UdpInputChannel` classe implémente `IInputChannel` . Elle se compose d'une file d'attente de messages entrants remplie par le socket de `UdpChannelListener`. Ces messages sont extraits de la file d'attente par la méthode `IInputChannel.Receive`.  
  
<a name="AddingABindingElement"></a>

## <a name="adding-a-binding-element"></a>Ajout d'un élément de liaison  

 Maintenant que les fabrications de canaux sont construites, nous devons les exposer à l’exécution de ServiceModel via une liaison. Une liaison est une collection d’éléments de liaison qui représente la pile de communication associée à une adresse de service. Chaque élément de la pile est représenté par un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément.  
  
 Dans notre exemple, l'élément de liaison est `UdpTransportBindingElement`, lequel dérive de <xref:System.ServiceModel.Channels.TransportBindingElement>. Il substitue les méthodes suivantes pour générer les fabrications associées à notre liaison.  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Il contient également des membres permettant de cloner `BindingElement` et de retourner notre schéma (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Ajout de la prise en charge des métadonnées pour un élément de liaison de transport  

 Pour intégrer notre transport dans le système de métadonnées, nous devons prendre à la fois en charge l'importation et l'exportation de stratégie. Cela nous permet de générer des clients de notre liaison via l' [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Ajout de la prise en charge WSDL  

 L’élément de liaison de transport d’une liaison est chargé d’exporter et d’importer les informations d’adressage dans les métadonnées. Lors de l'utilisation d'une liaison SOAP, l'élément de liaison de transport doit également exporter un URI de transport correct dans les métadonnées.  
  
#### <a name="wsdl-export"></a>Exportation WSDL  

 Pour exporter des informations d'adressage, `UdpTransportBindingElement` implémente l'interface `IWsdlExportExtension`. La méthode `ExportEndpoint` ajoute les informations d'adressage correctes au port WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 L’implémentation `UdpTransportBindingElement` de la méthode `ExportEndpoint` exporte également un URI de transport lorsque le point de terminaison utilise une liaison SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importation WSDL  

 Pour étendre le système d'importation WSDL afin de gérer l'importation des adresses, nous devons ajouter la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Lorsque vous exécutez Svcutil.exe, deux méthodes permettent de faire en sorte que Svcutil.exe charge les extensions d’importation WSDL :  
  
1. Pointez Svcutil.exe vers notre fichier de configuration à l’aide du en utilisant/svcutilConfig : \<file> .  
  
2. Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.  
  
 Le type `UdpBindingElementImporter` implémente l'interface `IWsdlImportExtension`. La méthode `ImportEndpoint` importe l'adresse à partir du port WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Ajout de la prise en charge de la stratégie  

 L’élément de liaison personnalisé peut exporter des assertions de stratégie dans la liaison WSDL d’un point de terminaison de service pour exprimer les fonctionnalités de cet élément de liaison.  
  
#### <a name="policy-export"></a>Exportation de stratégie  

 Le `UdpTransportBindingElement` type implémente `IPolicyExportExtension` pour ajouter la prise en charge de l’exportation de la stratégie. En conséquence, `System.ServiceModel.MetadataExporter` inclut `UdpTransportBindingElement` dans la génération de stratégie des liaisons qui l’incluent.  
  
 Dans `IPolicyExportExtension.ExportPolicy`, nous ajoutons une assertion pour UDP et une autre si nous sommes en mode multicast. Cela est dû au fait que le mode multicast affecte la manière dont la pile est construite, et doit donc être coordonné entre les deux côtés.  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix,
        UdpPolicyStrings.MulticastAssertion,
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Les éléments de liaison de transport personnalisés étant chargés de gérer l’adressage, l’implémentation `IPolicyExportExtension` sur `UdpTransportBindingElement` doit également gérer l’exportation des assertions de stratégie WS-Addressing appropriées pour indiquer la version de WS-Addressing utilisée.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importation de stratégie  

 Pour étendre le système d'importation de stratégie, nous devons ajouter la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Puis nous implémentons `IPolicyImporterExtension` à partir de la classe enregistrée (`UdpBindingElementImporter`). Dans `ImportPolicy()`, nous examinons les assertions dans notre espace de noms, puis traitons celles permettant de générer le transport et vérifions s'il est multicast. Nous devons également supprimer les assertions que nous gérons de la liste des assertions de liaison. Une fois encore, il existe deux méthodes d'intégration possibles lorsque vous exécutez Svcutil.exe :  
  
1. Pointez Svcutil.exe vers notre fichier de configuration à l’aide du en utilisant/svcutilConfig : \<file> .  
  
2. Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>

## <a name="adding-a-standard-binding"></a>Ajout d’une liaison standard  

 Notre élément de liaison peut être utilisé des deux façons suivantes :  
  
- Via une liaison personnalisée : une liaison personnalisée permet à l’utilisateur de créer sa propre la liaison en fonction d’un ensemble arbitraire d’éléments de liaison.  
  
- En utilisant une liaison fournie par le système qui inclut notre élément de liaison. WCF fournit un certain nombre de ces liaisons définies par le système, telles que `BasicHttpBinding` , `NetTcpBinding` et `WsHttpBinding` . Chacune de ces liaisons est associée à un profil bien défini.  
  
 L'exemple implémente la liaison de profil dans `SampleProfileUdpBinding`, lequel dérive de <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` contient jusqu'à quatre éléments de liaison : `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement` et `ReliableSessionBindingElement`.  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Ajout d'un importateur de liaison standard personnalisé  

 Par défaut, Svcutil.exe et le type `WsdlImporter` reconnaissent et importent les liaisons définies par le système. Sinon, la liaison est importée en tant qu'instance `CustomBinding`. Pour permettre à Svcutil.exe et `WsdlImporter` d’importer `SampleProfileUdpBinding`, `UdpBindingElementImporter` agit également comme un importateur de liaison standard personnalisé.  
  
 Un importateur de liaison standard personnalisé implémente la méthode `ImportEndpoint` sur l'interface `IWsdlImportExtension` pour examiner l'instance `CustomBinding` importée à partir des métadonnées afin de vérifier si elle peut avoir été générée par une liaison standard spécifique.  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 En général, l’implémentation d’un importateur de liaison standard personnalisé implique la vérification des propriétés des éléments de liaison importés afin de s’assurer que seules les propriétés pouvant avoir été définies par la liaison standard ont été modifiées et que toutes les autres ont été définies à leurs valeurs par défaut. L’une des stratégies de base permettant d’implémenter un importateur de liaison standard consiste à créer une instance de la liaison standard, à propager les propriétés des éléments de liaison vers l’instance de liaison standard que la liaison standard prend en charge, et à comparer les éléments de liaison de la liaison standard avec les éléments de liaison importés.  
  
<a name="AddingConfigurationSupport"></a>

## <a name="adding-configuration-support"></a>Ajout de la prise en charge de la configuration  

 Pour exposer notre transport via la configuration, nous devons implémenter deux sections de configuration. La première est `BindingElementExtensionElement` pour `UdpTransportBindingElement`. C'est de cette façon que les implémentations `CustomBinding` référencent notre élément de liaison. La deuxième est `Configuration` pour `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Élément d’extension de l’élément de liaison  

 La section `UdpTransportElement` est un `BindingElementExtensionElement` qui expose `UdpTransportBindingElement` au système de configuration. Avec quelques substitutions de base, nous définissons le nom de notre section de configuration, le type de notre élément de liaison et la méthode utilisée pour le créer. Nous pouvons ensuite enregistrer notre section d’extension dans un fichier de configuration, tel qu’indiqué dans le code suivant.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 L'extension peut être référencée à partir des liaisons personnalisées pour utiliser UDP comme transport.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a>Section de liaison  

 La section `SampleProfileUdpBindingCollectionElement` est un `StandardBindingCollectionElement` qui expose `SampleProfileUdpBinding` au système de configuration. Le bloc de l'implémentation est délégué à `SampleProfileUdpBindingConfigurationElement`, qui dérive de `StandardBindingElement`. `SampleProfileUdpBindingConfigurationElement`A des propriétés qui correspondent aux propriétés de `SampleProfileUdpBinding` et aux fonctions à mapper à partir de la `ConfigurationElement` liaison. Enfin, nous substituons `OnApplyConfiguration` dans notre `SampleProfileUdpBinding`, tel qu'indiqué dans l'exemple de code suivant.  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 Pour enregistrer ce gestionnaire avec le système de configuration, nous ajoutons la section suivante au fichier de configuration approprié.  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Il pourra ensuite être référencé à partir de la section de configuration serviceModel.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a>Client et service de test UDP  

 Le code de test permettant d'utiliser cet exemple de transport est disponible dans les répertoires UdpTestService et UdpTestClient. Le code de service se compose de deux tests : le premier définit les liaisons et les points de terminaison à partir du code, et le deuxième le fait via la configuration. Ces deux tests utilisent deux points de terminaison. Un point de terminaison utilise la `SampleUdpProfileBinding` avec la [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) valeur `true` . L'autre utilise une liaison personnalisée avec `UdpTransportBindingElement`. Cela équivaut à utiliser `SampleUdpProfileBinding` avec avec la [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) valeur `false` . Ces deux tests créent un service, ajoutent  un point de terminaison pour chaque liaison, ouvrent le service, puis attendent que l'utilisateur tape ENTER avant de fermer le service.  
  
 Lorsque vous démarrez l'application de test de service, la sortie suivante doit s'afficher.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Vous pouvez ensuite exécuter l'application de test cliente sur les points de terminaison publiés. L'application de test cliente crée un client pour chaque point de terminaison et envoie cinq messages à chacun. Sortie sur le client :  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Sortie complète sur le service :  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 Pour exécuter l'application cliente sur des points de terminaison publiés à l'aide de la configuration, tapez ENTER sur le service, puis exécutez de nouveau le client test. La sortie suivante doit s'afficher sur le service.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 La réexécution du client génère les mêmes résultats que ceux obtenus précédemment.  
  
 Pour régénérer le code client et la configuration à l'aide de Svcutil.exe, démarrez l'application de service, puis exécutez le fichier Svcutil.exe suivant à partir du répertoire racine de l'exemple.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Svcutil.exe ne générant pas de configuration d’extension de liaison pour `SampleProfileUdpBinding`, vous devez donc l’ajouter manuellement.  
  
```xml
<configuration>  
  <system.serviceModel>
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
2. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
3. Référez-vous à la section « Client et service de test UDP » développée précédemment.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
