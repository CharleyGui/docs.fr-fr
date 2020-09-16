---
title: <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: 4070b9659b6d3936dec38fc6a30cf7cd673691f5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556165"
---
# \<netMsmqBinding>
Définit une liaison mise en file d’attente adaptée à la communication entre ordinateurs.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netMsmqBinding>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netMsmqBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxBufferPoolSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           poisonMessageHandling="Disabled/EnabledIfSupported"
           queueTransferProtocol="Native/Srmp/SrmpSecure"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           rejectAfterLastRetry="Boolean"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           timeToLive="TimeSpan"
           useActiveDirectory="Boolean"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/InfoCard" />
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`customDeadLetterQueue`|URI contenant l'emplacement de la file d'attente de lettres mortes pour chaque application et dans laquelle sont placés les messages ayant expiré ou dont le transfert ou la remise a échoué.<br /><br /> La file d'attente de lettres mortes est une file d'attente du gestionnaire de files d'attente de l'application émettrice pour les messages ayant expiré et dont la remise a échoué.<br /><br /> L'URI spécifié par <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> doit utiliser le schéma net.msmq.|  
|`deadLetterQueue`|Valeur <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> spécifiant le type de file d'attente de lettres mortes à utiliser (le cas échéant).<br /><br /> Une file d'attente de lettres mortes est l'emplacement d'où les messages de l'application dont la remise a échoué seront transférés.<br /><br /> Pour les messages qui requièrent l’assurance `exactlyOnce` (autrement dit, l’attribut `exactlyOnce` a la valeur `true`), cet attribut a comme valeur par défaut la file d’attente de lettres mortes transactionnelle à l’échelle du système dans MSMQ.<br /><br /> Pour les messages qui ne requièrent pas de garanties, cet attribut a `null` comme valeur par défaut.|  
|`durable`|Valeur booléenne qui indique si le message est fiable ou volatil dans la file d'attente. Un message durable survit à une panne du gestionnaire de files d'attente, alors qu'un message volatil n'y survit pas. Les messages volatils sont utiles lorsque les applications requièrent la latence plus faible et peuvent autoriser la perte occasionnelle de messages. Si l'attribut `exactlyOnce` a la valeur `true`, les messages doivent être fiables. La valeur par défaut est `true`.|  
|`exactlyOnce`|Valeur booléenne qui indique si chaque message traité par cette liaison est remis uniquement une fois. L'expéditeur est ensuite notifié des échecs de remise. Lorsque `durable` a pour valeur `false`, cet attribut est ignoré et les messages sont transférés sans garantie de remise. La valeur par défaut est `true`. Pour plus d'informations, consultez <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison. La valeur par défaut est 8.|  
|`maxReceivedMessageSize`|Entier positif qui définit la taille maximale du message (en octets, en-têtes compris), qui est traité par cette liaison. L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP. Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi. La valeur par défaut est 65536. Cette limite de taille des messages a pour but d'atténuer l'exposition aux attaques par déni de service (DoS).|  
|`maxRetryCycles`|Entier indiquant le nombre de cycles de tentatives utilisés par la fonctionnalité de détection de messages incohérents. Un message devient incohérent lorsque toutes les tentatives de remise de tous les cycles échouent. La valeur par défaut est 3. Pour plus d'informations, consultez <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Attribut requis. Chaîne qui contient le nom de configuration de la liaison. Cette valeur doit être unique car elle permet d'identifier la liaison. À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`QueueTransferProtocol`|Valeur <xref:System.ServiceModel.QueueTransferProtocol> valide qui spécifie le transport du canal de communication en file d'attente que cette liaison utilise. MSMQ ne prend pas en charge l'adressage Active Directory lors de l'utilisation du protocole SRMP (SOAP Reliable Messaging). Par conséquent, vous ne devez pas affecter à cet attribut `Srmp` `Srmps` la valeur ou lorsque l' `useActiveDirectory` attribut a la valeur `true` .|  
|`receiveErrorHandling`|Valeur <xref:System.ServiceModel.ReceiveErrorHandling> qui spécifie la façon dont sont gérés les messages incohérents et ne pouvant être distribués.|  
|`receiveRetryCount`|Entier qui spécifie le nombre maximum de tentatives que le gestionnaire de files d'attente doit effectuer pour envoyer un message avant de le transférer à la file d'attente des nouvelles tentatives.|  
|`receiveTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:10:00.|  
|`retryCycleDelay`|Valeur TimeSpan qui spécifie l'intervalle entre les cycles de nouvelles tentatives de remise d'un message n'ayant pas pu être remis immédiatement. Cette valeur définit uniquement le délai d'attente minimum, car le temps d'attente réel peut être plus long. La valeur par défaut est 00:10:00. Pour plus d'informations, consultez <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`timeToLive`|Valeur TimeSpan qui spécifie la durée de validité des messages avant leur expiration et leur déplacement dans la file d'attente de lettres mortes. La valeur par défaut est 1.00:00:00.<br /><br /> Cet attribut est configuré de façon à garantir que les messages dépendants de l'heure n'expirent pas avant d'être traités par les applications de réception. Un message dans une file d'attente qui n'est pas consommé par l'application de réception dans l'intervalle de temps spécifié est considéré comme ayant expiré. Les messages ayant expiré sont envoyés dans une file d'attente spéciale appelée file d'attente de lettres mortes. L'emplacement de cette file d'attente est défini par l'attribut `DeadLetterQueue` ou par la valeur par défaut appropriée, en fonction des garanties utilisées.|  
|`usingActiveDirectory`|Valeur booléenne qui spécifie si les adresses mises en file d'attente doivent être converties à l'aide d'Active Directory.<br /><br /> Les adresses de file d'attente MSMQ peuvent se composer de noms de chemin d'accès ou de noms de format direct. Avec un nom de format direct, MSMQ résout le nom de l'ordinateur à l'aide de DNS, NetBIOS ou IP. Avec un nom de chemin d'accès, MSMQ résout le nom de l'ordinateur à l'aide d'Active Directory.<br /><br /> Par défaut, le transport Windows Communication Foundation (WCF) mis en file d’attente convertit l’URI d’une file d’attente de messages en un nom de format direct. En affectant la valeur true à la propriété `UseActiveDirectory`, une application peut spécifier que le transport de mise en file d'attente doit résoudre le nom de l'ordinateur à l'aide d'Active Directory plutôt qu'à l'aide de DNS, NetBIOS ou IP.|  
|`useMsmqTracing`|Valeur booléenne indiquant si les messages traités par cette liaison doivent être suivis. La valeur par défaut est `false`. Lorsque le suivi est activé, des messages de rapport sont créés et envoyés à la file d'attente de rapports chaque fois que le message quitte ou atteint un ordinateur Message Queuing.|  
|`useSourceJournal`|Valeur booléenne qui spécifie si les copies de messages traitées par cette liaison doivent être stockées dans le journal source. La valeur par défaut est `false`.<br /><br /> Les applications en file d'attente souhaitant conserver une trace des messages qui ont quitté la file d'attente sortante de l'ordinateur peuvent copier les messages dans une file d'attente de journal. Une fois qu'un message quitte la file d'attente sortante et qu'un accusé de réception est envoyé par l'ordinateur de destination, une copie du message est conservée dans la file d'attente du journal système de l'ordinateur émetteur.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<security>](security-of-netmsmqbinding.md)|Définit les paramètres de sécurité de la liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## <a name="remarks"></a>Notes  
 La liaison `netMsmqBinding` fournit la prise en charge de la mise en file d'attente en utilisant MSMQ (Microsoft Message Queuing) comme transport et active la prise en charge des applications faiblement couplées, de l'isolation de défaillance, du nivellement de charge et des opérations hors circuit. Pour plus d’informations sur ces fonctionnalités, consultez [files d’attente dans WCF](../../../wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Exemple  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netMsmqBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 sourceJournal="true"
                 useMsmqTracing="true"
                 useActiveDirectory="true">
          <security>
            <message clientCredentialType="Windows" />
          </security>
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>
- [\<binding>](bindings.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [Files d’attente dans WCF](../../../wcf/feature-details/queues-in-wcf.md)
