---
title: <msmqIntegration>
ms.date: 03/30/2017
ms.assetid: ab677405-1ffe-457a-803f-00c1770e51e2
ms.openlocfilehash: 143557833457f379d410c3b71d87199a5b9e783b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738896"
---
# \<msmqIntegration>
Spécifie un transport MSMQ pour liaison personnalisée.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqIntegration>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<msmqIntegration customDeadLetterQueue="Uri"
                 deadLetterQueue="Custom/None/System"
                 durable="Boolean"
                 exactlyOnce="Boolean"
                 manualAddressing="Boolean"
                 maxBufferPoolSize="Integer"
                 maxImmediateRetries="Integer"
                 maxReceivedMessageSize="Integer"
                 maxRetryCycles="Integer"
                 rejectAfterLastRetry="Boolean"
                 retryCycleDelay="TimeSpan"
                 serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"
                 timeToLive="TimeSpan"
                 useSourceJournal="Boolean"
                 useMsmqTracing="Boolean">
  <msmqTransportSecurity>
  </msmqTransportSecurity>
</msmqIntegration>
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|customDeadLetterQueue|URI contenant l'emplacement de la file d'attente de lettres mortes par application, dans laquelle sont placés les messages ayant expiré ou dont la remise à l'application a échoué.<br /><br /> Pour les messages qui requièrent des garanties ExactlyOnce (ceux pour lesquels l’attribut `exactlyOnce` a la valeur `true`), cet attribut a comme valeur par défaut la file d’attente de lettres mortes transactionnelle à l’échelle du système dans MSMQ.<br /><br /> Pour les messages qui ne requièrent pas de garanties (ceux pour lesquels `exactlyOnce` a la valeur `false`), cet attribut a la valeur par défaut `null`.<br /><br /> La valeur doit utiliser le schéma net.msmq. Par défaut, il s’agit de `null`.<br /><br /> Si `deadLetterQueue` a la valeur `None` ou `System`, cet attribut doit avoir la valeur `null`. S'il n'a pas la valeur `null`, `deadLetterQueue` doit avoir la valeur `Custom`.|  
|deadLetterQueue|Indique le type de file d'attente de lettres mortes à utiliser.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> -Custom : file d’attente de lettres mortes personnalisée.<br />-None : aucune file d’attente de lettres mortes ne doit être utilisée.<br />-System : utilisez la file d’attente lettres mortes du système.<br /><br /> Cet attribut est de type DeadLetterQueue.|  
|durable|Valeur booléenne indiquant si les messages traités par cette liaison sont fiables ou volatils. Par défaut, il s’agit de `true`.<br /><br /> Un message durable survit à une panne du gestionnaire de files d'attente, alors qu'un message volatil n'y survit pas. Les messages volatils sont utiles lorsque les applications requièrent la latence plus faible et peuvent autoriser la perte occasionnelle de messages.<br /><br /> Si `exactlyOnce` a la valeur `true`, les messages doivent être fiables.|  
|exactlyOnce|Valeur booléenne indiquant si les messages traités par cette liaison seront reçus une seule fois. Par défaut, il s’agit de `true`.<br /><br /> Un message peut être envoyé avec ou sans garanties. Une garantie permet à une application de s'assurer qu'un message envoyé atteint la file d'attente de messages de réception ou, si ce n'est pas le cas, l'application peut consulter la file d'attente de lettres mortes.<br /><br /> Si `exactlyOnce` a la valeur `true`, MSMQ garantit qu'un message envoyé est remis une seule et unique fois à la file d'attente de messages de réception. Si la remise échoue, le message est envoyé à la file d'attente de lettres mortes.<br /><br /> Les messages pour lesquels `exactlyOnce` a la valeur `true` doivent être envoyés uniquement à une file d'attente transactionnelle.|  
|manualAddressing|Valeur booléenne qui permet à l'utilisateur de prendre le contrôle de l'adressage de message. Cette propriété est utilisée habituellement dans les scénarios de routeur, dans lesquels l'application choisit à quelle destination envoyer un message.<br /><br /> Si cette propriété a la valeur `true`, le canal suppose que le message a déjà été adressé et n'y ajoute aucune information supplémentaire. L'utilisateur peut adresser ensuite individuellement chaque message.<br /><br /> Si cette propriété a la valeur `false`, le mécanisme d'adressage Windows Communication Foundation (WCF) par défaut crée automatiquement des adresses pour tous les messages.<br /><br /> Par défaut, il s’agit de `false`.|  
|maxBufferPoolSize|Entier positif indiquant la taille maximale du pool de mémoires tampons. La valeur par défaut est 524288.<br /><br /> De nombreux éléments de WCF utilisent des mémoires tampons. La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage. Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé. Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.|  
|maxImmediateRetries|Entier qui spécifie le nombre maximal de nouvelles tentatives immédiates sur un message qui est lu à partir de la file d’attente de l’application. La valeur par défaut est 5.<br /><br /> Si ce nombre est atteint et si le message n'est pas utilisé par l'application, il est envoyé à une file d'attente pour nouvelles tentatives ultérieures. Si aucun cycle de nouvelle tentative n'est indiqué, le message est envoyé à la file d'attente de messages incohérents, ou un accusé de réception négatif est renvoyé à l'expéditeur.|  
|maxReceivedMessageSize|Entier positif indiquant la taille maximale du message (en octets, en-têtes compris). L'expéditeur d'un message reçoit une erreur SOAP si ce message est trop volumineux pour le récepteur. Ce dernier dépose le message et crée une entrée d’événement dans le journal de suivi. La valeur par défaut est 65536.|  
|maxRetryCycles|Entier indiquant le nombre maximal de cycles de nouvelles tentatives pour la remise de messages à l'application de réception. Par défaut, il s’agit de <xref:System.Int32.MaxValue>.<br /><br /> Un seul cycle de nouvelle tentative tente de remettre un message à une application un certain nombre de fois. Le nombre de tentatives effectuées est défini par l'attribut `maxImmediateRetries`. Si l'application ne parvient pas à consommer le message une fois le nombre de tentatives atteint, le message est envoyé à une file d'attente de nouvelles tentatives de remise. Les cycles de nouvelles tentatives suivants consistent à renvoyer le message de la file d'attente de nouvelles tentatives de remise vers la file d'attente de l'application, afin d'effectuer une nouvelle tentative de remise à l'application après un délai spécifié par l'attribut `retryCycleDelay`. L'attribut `maxRetryCycles` spécifie le nombre de cycles de nouvelles tentatives effectués par l'application pour tenter de remettre le message.|  
|rejectAfterLastRetry|Valeur booléenne indiquant l'action à effectuer pour un message qui n'a pas pu être remis une fois le nombre maximal de tentatives atteint.<br /><br /> `true` signifie qu'un accusé de réception négatif est renvoyé à l'expéditeur et que le message est abandonné ; `false` indique que le message est envoyé à la file d'attente de messages incohérents. Par défaut, il s’agit de `false`.<br /><br /> Si la valeur est `false`, l'application de réception peut consulter la file d'attente de messages incohérents afin de traiter les messages incohérents (c'est-à-dire les messages qui n'ont pas pu être remis).<br /><br /> MSMQ 3.0 ne prend pas en charge le renvoi d'un accusé de réception négatif à l'expéditeur. Cet attribut ne sera donc pas pris en compte dans cette application.|  
|retryCycleDelay|<xref:System.TimeSpan> qui indique l'intervalle entre des cycles de nouvelles tentatives de remise d'un message n'ayant pas pu être remis immédiatement. La valeur par défaut est 00:10:00.<br /><br /> Un seul cycle de nouvelle tentative tente de remettre un message à une application de réception un certain nombre de fois. Le nombre de tentatives effectuées est spécifié par la propriété `maxImmediateRetries`. Si l'application ne peut pas consommer le message après le nombre spécifié de nouvelles tentatives immédiates, le message est envoyé à une file d'attente de nouvelles tentatives. Les cycles de nouvelles tentatives suivants consistent à renvoyer le message de la file d'attente de nouvelles tentatives de remise vers la file d'attente de l'application, afin d'effectuer une nouvelle tentative de remise à l'application après un délai spécifié par l'attribut `retryCycleDelay`. Le nombre de cycles de nouvelles tentatives est spécifié par l'attribut `maxRetryCycles`.|  
|serializationFormat|Indique le formateur utilisé pour sérialiser des objets envoyés comme partie d'un message MSMQ. Les valeurs valides sont les suivantes :<br /><br /> -ActiveX : le formateur ActiveX est utilisé lors de la sérialisation d’objets COM.<br />-Binary : sérialise l’objet en un paquet binaire.<br />-ByteArray : sérialise l’objet en un tableau d’octets.<br />-Stream : sérialise l’objet dans un flux.<br />-XML : sérialise l’objet en un paquet XML. La valeur par défaut est XML.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|<xref:System.TimeSpan> spécifiant la durée de validité des messages avant leur envoi dans la file d'attente de lettres mortes. La valeur par défaut est 1.00:00:00, soit une journée.<br /><br /> Cet attribut est configuré de façon à garantir que les messages dépendants de l'heure n'expirent pas avant d'être traités par les applications de réception. Un message dans une file d'attente qui n'est pas consommé par l'application de réception dans l'intervalle de temps spécifié est considéré comme ayant expiré. Les messages ayant expiré sont envoyés dans une file d'attente spéciale appelée file d'attente de lettres mortes. L'emplacement de cette file d'attente est défini par l'attribut `customDeadLetterQueue` ou par la valeur par défaut appropriée, en fonction des garanties utilisées.|  
|useMsmqTracing|Valeur booléenne indiquant si les messages traités par cette liaison doivent être suivis. Par défaut, il s’agit de `false`.<br /><br /> Lorsque le suivi est activé, des messages de rapport sont créés et envoyés à la file d'attente de rapports chaque fois que le message quitte ou atteint un ordinateur Message Queuing.|  
|useSourceJournal|Valeur booléenne indiquant si les copies des messages traités par cette liaison doivent être stockées dans la file d’attente du journal source. Par défaut, il s’agit de `false`.<br /><br /> Les applications en file d'attente souhaitant conserver une trace des messages qui ont quitté la file d'attente sortante de l'ordinateur peuvent copier les messages dans une file d'attente de journal. Une fois qu'un message quitte la file d'attente sortante et qu'un accusé de réception est envoyé par l'ordinateur de destination, une copie du message est conservée dans la file d'attente du journal système de l'ordinateur émetteur.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|msmqTransportSecurity|Indique les paramètres de sécurité du transport pour cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.MsmqIntegrationElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transports](../../../wcf/feature-details/transports.md)
- [Files d'attente dans WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Choix d'un transport](../../../wcf/feature-details/choosing-a-transport.md)
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
