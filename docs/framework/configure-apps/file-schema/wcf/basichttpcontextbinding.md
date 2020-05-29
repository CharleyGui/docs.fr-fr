---
title: <basicHttpContextBinding>
ms.date: 03/30/2017
ms.assetid: 39b16b82-4ec6-4eff-8031-67e026870961
ms.openlocfilehash: 78372970c7dc0f5a29e7fc9fdfc80aa443107b6d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201174"
---
# \<basicHttpContextBinding>
Spécification d’une liaison qui fournit le contexte correspondant au <xref:System.ServiceModel.BasicHttpBinding> à échanger en activant les cookies HTTP comme mécanisme d’échange.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpContextBinding>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<basicHttpContextBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="String" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpContextBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`allowCookies`|Valeur booléenne qui indique si le client accepte les cookies et les propage dans de futures demandes. Par défaut, il s’agit de `false`.<br /><br /> Vous pouvez utiliser cette propriété lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies. De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.|  
|`bypassProxyOnLocal`|Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales. Par défaut, il s’agit de `false`.<br /><br /> Une ressource Internet est locale si elle dispose d'une adresse locale. Une adresse locale est une adresse sur le même ordinateur, le réseau local ou l’intranet et est identifiée, syntaxiquement, par l’absence de point (.) comme dans les URI `http://webserver/` et `http://localhost/` .<br /><br /> La définition de cet attribut détermine si les points de terminaison configurés avec le BasicHttpBinding utilisent le serveur proxy lors de l'accès aux ressources locales. Si cet attribut est `true`, les demandes adressées à des ressources Internet locales n'utilisent pas le serveur proxy. Utilisez le nom d'hôte (plutôt que localhost) si vous souhaitez que les clients traversent un proxy lorsqu'ils parlent aux services sur le même ordinateur et que cet attribut a la valeur `true`.<br /><br /> Si cet attribut est `false`, toutes les demandes Internet sont exécutées par le serveur proxy.|  
|`closeTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`hostNameComparisonMode`|Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI. Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI. La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.|  
|`maxBufferPoolSize`|Entier qui spécifie la quantité de mémoire maximale allouée pour une utilisation par le gestionnaire de tampons des messages qui reçoivent des messages du canal. La valeur par défaut est de 524 288 (0x80000) octets.<br /><br /> Le gestionnaire de tampons réduit le coût d'utilisation des mémoires tampons à l'aide d'un pool de mémoires tampons. Les mémoires tampons sont requises par le service pour traiter des messages lorsqu'ils sortent du canal. S’il n’y a pas mémoire suffisante dans le pool de mémoires tampons pour traiter la charge de message, le gestionnaire de mémoires tampons doit allouer de la mémoire additionnelle dans le segment de mémoire CLR, ce qui augmente le traitement du garbage collection. Une allocation importante de mémoire issue du tas de garbage CLR indique que la taille du pool de mémoires tampons est insuffisante et qu'il est possible d'améliorer les performances en augmentant la limite spécifiée par cet attribut.|  
|`maxBufferSize`|Entier qui spécifie la taille maximale, en octets, d’une mémoire tampon qui stocke des messages pendant qu’ils sont traités pour un point de terminaison configuré avec cette liaison. La valeur par défaut est de 65 536 octets.|  
|`maxReceivedMessageSize`|Entier positif qui définit la taille maximale du message, en octets, y compris les en-têtes d’un message pouvant être reçu sur un canal configuré avec cette liaison. L'expéditeur reçoit une erreur SOAP si le message est trop grand pour le récepteur. Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi. La valeur par défaut est 65 536 octets.|  
|`messageEncoding`|Définit l'encodeur utilisé pour encoder le message SOAP. Les valeurs valides sont les suivantes :<br /><br /> -Text : utilisez un encodeur de message texte.<br />-MTOM : utilisez un encodeur de transmission de message de l’organisme de transmission de messages 1,0 (MTOM).<br /><br /> La valeur par défaut est Text. Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.|  
|`messageVersion`|Spécifie la version de message utilisée par les clients et les services configurés avec la liaison. Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.|  
|`name`|Chaîne qui contient le nom de configuration de la liaison. Cette valeur doit être unique car elle permet d'identifier la liaison. À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`proxyAddress`|URI qui contient l'adresse du proxy HTTP. Si `useSystemWebProxy` a la valeur `true` ce paramètre doit avoir la valeur `null`. Par défaut, il s’agit de `null`.|  
|`receiveTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:10:00.|  
|`sendTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`textEncoding`|Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison. Les valeurs valides sont les suivantes :<br /><br /> -BigEndianUnicode : encodage BigEndian Unicode.<br />-Unicode : encodage 16 bits.<br />-UTF8 : encodage 8 bits<br /><br /> La valeur par défaut est UTF-8. Cet attribut est de type <xref:System.Text.Encoding>.|  
|`transferMode`|Valeur <xref:System.ServiceModel.TransferMode> valide qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu dans une demande ou une réponse.|  
|`useDefaultWebProxy`|Valeur booléenne qui spécifie si le proxy HTTP du système, configuré automatiquement, doit être utilisé, le cas échéant. Par défaut, il s’agit de `true`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|Définit les paramètres de sécurité de la liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément de liaison fournit un niveau de protection et un mécanisme d'échange dans le cadre du contexte pour `BasicHttpBinding`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.BasicHttpContextBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpContextBindingElement>
- <xref:System.ServiceModel.Channels.ContextBindingElement>
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<basicHttpBinding>](basichttpbinding.md)
