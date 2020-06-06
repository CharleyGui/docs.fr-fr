---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f1aa68bcdda43fd77bee397c079695f7937faa52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139468"
---
# \<netNamedPipeBinding>
Définit une liaison qui est sécurisée, fiable, optimisée pour la communication interprocessus sur l'ordinateur. Par défaut, elle génère une pile de communication du runtime avec WS-ReliableMessaging pour la fiabilité, la sécurité du transport pour la sécurité du transfert, des canaux nommés pour la remise de messages et l'encodage binaire de messages.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|closeTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|hostNameComparisonMode|Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI. Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI. La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.|  
|maxBufferPoolSize|Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison. La valeur par défaut est 524 288 octets (512 x 1024). De nombreuses parties de Windows Communication Foundation (WCF) utilisent des mémoires tampons. La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage. Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé. Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.|  
|maxBufferSize|Entier positif qui spécifie la taille maximale, en octets, de la mémoire tampon utilisée pour stocker des messages en mémoire. Si la mémoire tampon est pleine, les données excédentaires restent dans le socket sous-jacent jusqu'à ce que de l'espace disponible se libère dans la mémoire tampon. Cette valeur ne peut pas être inférieure à l'attribut `maxReceivedMessageSize`. La valeur par défaut est 65536. Pour plus d’informations, consultez <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Entier qui spécifie le nombre maximal de connexions sortantes et entrantes que le service créera/acceptera. Les connexions entrantes et sortantes sont comptées par rapport à une limite distincte spécifiée par cet attribut.<br /><br /> Les connexions entrantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.<br /><br /> Les connexions sortantes dépassant cette limite sont mises en file d'attente jusqu'à ce que de l'espace soit disponible sous cette limite.<br /><br /> La valeur par défaut est de 10.|  
|maxReceivedMessageSize|Entier positif qui spécifie la taille maximale du message, en octets, y compris les en-têtes, pouvant être reçu sur un canal configuré avec cette liaison. L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP. Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi. La valeur par défaut est 65536.|  
|name|Chaîne qui contient le nom de configuration de la liaison. Cette valeur doit être unique car elle permet d'identifier la liaison. À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|receiveTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:10:00.|  
|sendTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|transactionFlow|Valeur booléenne qui spécifie si la liaison prend en charge le flux WS-Transactions. Par défaut, il s’agit de `false`.|  
|transactionProtocol|Spécifie le protocole de transaction à utiliser avec cette liaison. Les valeurs valides sont les suivantes :<br /><br /> -OleTransactions<br />-WS-AtomicTransactionOctober2004<br /><br /> La valeur par défaut est OleTransactions. Cet attribut est de type <xref:System.ServiceModel.TransactionProtocol>.|  
|transferMode|Valeur <xref:System.ServiceModel.TransferMode> qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|Définit les paramètres de sécurité de la liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## <a name="remarks"></a>Remarques  
 `NetNamedPipeBinding` génère par défaut une pile de communication au moment de l'exécution, qui utilise la sécurité de transport, des canaux nommés pour la remise des messages et un encodage de message binaire. Cette liaison est une solution fournie par le système WCF (Windows Communication Foundation) adaptée à la communication sur les ordinateurs. Elle prend en outre en charge des transactions.  
  
 La configuration par défaut de `NetNamedPipeBinding` est similaire à celle fournie par `NetTcpBinding`, mais en plus simple, car l’implémentation de WCF est uniquement destinée à être utilisée sur un ordinateur, de sorte qu’il y a moins de fonctionnalités exposées. La différence la plus notable est que le paramètre `securityMode` offre uniquement les options `None` et `Transport`. La prise en charge de la sécurité SOAP ne fait pas partie des options incluses. Le comportement de sécurité est configurable à l'aide de l'attribut facultatif `securityMode`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre la liaison netNamedPipeBinding, qui fournit la communication interprocessus sur le même ordinateur. Les canaux nommés ne fonctionnent pas sur plusieurs ordinateurs.  
  
 La liaison est spécifiée dans les fichiers de configuration pour le client et le service. Le type de liaison est spécifié dans l’attribut `binding` de l’élément `<endpoint>`. Si vous souhaitez configurer la liaison netNamedPipeBinding et modifier quelques-uns de ses paramètres, vous devez définir une configuration de liaison. Le point de terminaison doit référencer la configuration de liaison par nom avec un attribut `bindingConfiguration`. Dans cet exemple, la configuration de liaison est nommée Binding1.  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
