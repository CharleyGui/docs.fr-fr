---
title: Compatibilité des fonctionnalités dans un environnement de confiance partielle
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: baf7758bc83419a68f900aa51233006ecb61d8e0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247991"
---
# <a name="partial-trust-feature-compatibility"></a>Compatibilité des fonctionnalités dans un environnement de confiance partielle

Windows Communication Foundation (WCF) prend en charge un sous-ensemble limité de fonctionnalités lors de l’exécution dans un environnement de confiance partielle. Les fonctionnalités de confiance partielle prises en charge sont conçues autour d’un ensemble spécifique de scénarios, comme décrit dans la rubrique [Supported Deployment Scenarios](supported-deployment-scenarios.md) .  
  
## <a name="minimum-permission-requirements"></a>Autorisations minimales requises  

 WCF prend en charge un sous-ensemble de fonctionnalités dans les applications qui s’exécutent sous l’un des jeux d’autorisations nommés standard suivants :  
  
- Autorisations de confiance moyenne  
  
- Autorisations de la zone Internet  
  
 Toute tentative d’utilisation de WCF dans des applications de confiance partielle avec des autorisations plus restrictives peut entraîner des exceptions de sécurité au moment de l’exécution.  
  
## <a name="contracts"></a>Contrats  

 Les contrats sont soumis aux restrictions suivantes lors de leur exécution dans un environnement de confiance partielle :  
  
- La classe de service qui implémente l'interface `[ServiceContract]` doit être `public` et doit avoir un constructeur `public` . Si elle définit des méthodes `[OperationContract]` , celles-ci doivent être `public`. Si, au lieu de cela, elle implémente une interface `[ServiceContract]` , ces implémentations de méthode peuvent être explicites ou `private`, pourvu que l'interface `[ServiceContract]` soit `public`.  
  
- Lors de l'utilisation de l'attribut `[ServiceKnownType]` , la méthode spécifiée doit être `public`.  
  
- Les classes`[MessageContract]` et leurs membres peuvent être `public`. Si la classe `[MessageContract]` est définie dans l'assembly d'application, elle peut être `internal` et avoir des membres `internal` .  
  
## <a name="system-provided-bindings"></a>Liaisons fournies par le système  

 <xref:System.ServiceModel.BasicHttpBinding> et <xref:System.ServiceModel.WebHttpBinding> sont totalement pris en charge dans un environnement de confiance partielle. <xref:System.ServiceModel.WSHttpBinding> est pris en charge uniquement pour le mode de sécurité Transport.  
  
 Les liaisons qui utilisent des transports autres que HTTP, comme <xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>ou <xref:System.ServiceModel.NetMsmqBinding>, ne sont pas prises en charge lors de l'exécution dans un environnement de confiance partielle.  
  
## <a name="custom-bindings"></a>Liaisons personnalisées  

 Les liaisons personnalisées peuvent être créées et utilisées dans un environnement de confiance partielle, mais elles doivent respecter les restrictions décrites dans cette section.  
  
### <a name="transports"></a>Transports  

 Les seuls éléments de liaison de transport autorisés sont <xref:System.ServiceModel.Channels.HttpTransportBindingElement> et <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Encodeurs  

 Les encodeurs suivants sont autorisés :  
  
- Encodeur de texte (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
- Encodeur binaire (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
- Encodeur de message Web (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Les encodeurs MTOM (Message Transmission Optimization Mechanism) ne sont pas pris en charge.  
  
### <a name="security"></a>Sécurité  

 Les applications de confiance partielle peuvent utiliser les fonctionnalités de sécurité au niveau du transport de WCF pour sécuriser leur communication. La sécurité au niveau message n'est pas prise en charge. La configuration d'une liaison pour utiliser la sécurité au niveau message entraîne une exception pendant l'exécution.  
  
### <a name="unsupported-bindings"></a>Liaisons non prises en charge  

 Les liaisons qui utilisent une messagerie fiable, des transactions ou une sécurité au niveau du message ne sont pas prises en charge.  
  
## <a name="serialization"></a>Sérialisation  

 Le <xref:System.Runtime.Serialization.DataContractSerializer> et le <xref:System.Xml.Serialization.XmlSerializer> sont pris en charge dans un environnement de confiance partielle. Toutefois, l'utilisation du <xref:System.Runtime.Serialization.DataContractSerializer> est soumise aux conditions suivantes :  
  
- Tous les types `[DataContract]` sérialisables doivent être `public`.  
  
- Tous les champs ou les propriétés `[DataMember]` sérialisables dans un type `[DataContract]` doivent être "public" et en lecture/écriture. La sérialisation et la désérialisation des champs [ReadOnly](https://go.microsoft.com/fwlink/?LinkID=98854) ne sont pas prises en charge lors de l’exécution de WCF dans une application de confiance partielle.  
  
- Le modèle de programmation `[Serializable]`/ISerializable n'est pas pris en charge dans un environnement de confiance partielle.  
  
- Les types connus doivent être spécifiés dans le code ou la configuration au niveau de l'ordinateur (machine.config). Les types connus ne peuvent pas être spécifiés dans la configuration au niveau de l'application pour des raisons de sécurité.  
  
- Les types qui implémentent <xref:System.Runtime.Serialization.IObjectReference> lèvent une exception dans un environnement de confiance partielle.  
  
 Consultez la section Sérialisation de [Partial Trust Best Practices](partial-trust-best-practices.md) pour plus d’informations sur la sécurité lors de l’utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> dans une application partiellement fiable.  
  
### <a name="collection-types"></a>Types de collection  

 Certains types de collection implémentent <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.Collections.IEnumerable>. Les exemples incluent des types qui implémentent <xref:System.Collections.Generic.ICollection%601>. Ces types peuvent mettre en œuvre une implémentation `public` de `GetEnumerator()`et une implémentation explicite de `GetEnumerator()`. Dans ce cas, <xref:System.Runtime.Serialization.DataContractSerializer> appelle l'implémentation `public` de `GetEnumerator()`et non l'implémentation explicite de `GetEnumerator()`. Si aucune des implémentations de `GetEnumerator()` n’est `public` et que toutes sont des implémentations explicites, <xref:System.Runtime.Serialization.DataContractSerializer> appelle `IEnumerable.GetEnumerator()`.  
  
 Pour les types de collection lorsque WCF s’exécute dans un environnement de confiance partielle, si aucune des `GetEnumerator()` implémentations n’est `public` , ou si aucune des implémentations d’interface n’est explicite, une exception de sécurité est levée.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  

 De nombreux types de collection .NET Framework, tels que <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> et <xref:System.Collections.Hashtable> ne sont pas pris en charge par le <xref:System.Runtime.Serialization.NetDataContractSerializer> dans l'environnement de confiance partielle. L'attribut `[Serializable]` de ces types est défini et, comme indiqué précédemment à la section Sérialisation, cet attribut n'est pas pris en charge dans un environnement de confiance partielle. Le <xref:System.Runtime.Serialization.DataContractSerializer> traite les collections de manière spéciale et peut ainsi contourner cette restriction ; en revanche, le <xref:System.Runtime.Serialization.NetDataContractSerializer> n'a pas de tel mécanisme pour contourner cette restriction.  
  
 Le type <xref:System.DateTimeOffset> n'est pas pris en charge par le <xref:System.Runtime.Serialization.NetDataContractSerializer> dans un environnement de confiance partielle.  
  
 Il n'est pas possible d'utiliser un substitut avec le <xref:System.Runtime.Serialization.NetDataContractSerializer> (à l'aide du mécanisme <xref:System.Runtime.Serialization.SurrogateSelector> ) lors de son exécution dans un environnement de confiance partielle. Notez que cette restriction s'applique à l'utilisation d'un substitut, pas à sa sérialisation.  
  
## <a name="enabling-common-behaviors-to-run"></a>Activation de l'exécution des comportements courants  

 Les comportements de service ou de point de terminaison non marqués avec l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA) qui sont ajoutés à la [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section d’un fichier de configuration ne sont pas exécutés quand l’application s’exécute dans un environnement de confiance partielle et aucune exception n’est levée lorsque cela se produit. Pour appliquer l'exécution des comportements courants, vous devez effectuer l'une des actions suivantes :  
  
- Marquez votre comportement courant avec l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> afin qu'il soit exécuté lorsqu'il est déployé comme une application de confiance partielle. Notez qu'une entrée de Registre peut être définie sur l'ordinateur pour interdire l'exécution des assemblys marqués avec l'attribut APTCA. .  
  
- Si l'application est déployée comme une application de confiance partielle, vérifiez que les utilisateurs ne peuvent pas modifier les paramètres de sécurité d'accès du code pour exécuter l'application dans un environnement de confiance partielle. S'ils peuvent le faire, le comportement ne s'exécute pas et aucune exception n'est levée. Pour ce faire, consultez l’option **LevelFinal** à l’aide de [Caspol.exe (outil stratégie de sécurité d’accès du code)](../../tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Pour obtenir un exemple de comportement courant, consultez [Comment : verrouiller des points de terminaison dans l’entreprise](../extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Configuration  

 À une exception près, le code d’un niveau de confiance partiel ne peut charger que les sections de configuration WCF dans le `app.config` fichier local. Pour charger des sections de configuration WCF qui font référence à des sections WCF dans machine.config ou dans un fichier racine web.config requiert une autorisation ConfigurationPermission (sans restriction). Sans cette autorisation, les références aux sections de configuration WCF (comportements, liaisons) en dehors du fichier de configuration local entraînent une exception lorsque la configuration est chargée.  
  
 L'unique exception est la configuration de type connu pour la sérialisation, comme décrit à la section Sérialisation de cette rubrique.  
  
> [!IMPORTANT]
> Les extensions de configuration ne sont prises en charge que lors de l'exécution à un niveau de confiance totale.  
  
## <a name="diagnostics"></a>Diagnostics  
  
### <a name="event-logging"></a>Journalisation des événements  

 La journalisation des événements limitée est prise en charge dans un environnement de confiance partielle. Seul les échecs d'activation de service et les échecs de suivi/journalisation de message sont consignés dans le journal des événements. Le nombre d'événements maximal qui peuvent être enregistrés par un processus est égal à 5, pour éviter d'écrire un trop grand nombre de messages dans le journal des événements.  
  
### <a name="message-logging"></a>Journalisation des messages  

 L’enregistrement des messages ne fonctionne pas lorsque WCF est exécuté dans un environnement de confiance partielle. En cas d'activation avec un niveau de confiance partiel, il ne met pas en échec l'activation du service, mais aucun message n'est enregistré.  
  
### <a name="tracing"></a>Traçage  

 Des fonctionnalités de traçage restreintes sont disponibles lors de l'exécution dans un environnement de confiance partielle. Dans l' `listeners` élément <> dans le fichier de configuration, les seuls types que vous pouvez ajouter sont <xref:System.Diagnostics.TextWriterTraceListener> et le nouveau <xref:System.Diagnostics.EventSchemaTraceListener> . L'utilisation de <xref:System.Diagnostics.XmlWriterTraceListener> standard peut provoquer des journaux incomplets ou incorrects.  
  
 Les sources de suivi prises en charge sont :  
  
- <xref:System.ServiceModel>  
  
- <xref:System.Runtime.Serialization>  
  
- <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors> et <xref:System.IdentityModel.Tokens>.  
  
 Les sources de suivi suivantes ne sont pas prises en charge :  
  
- CardSpace  
  
- <xref:System.IO.Log>  

- [System. ServiceModel. Internal. TransactionBridge](/previous-versions/aa346556(v=vs.110))]
  
 Les membres suivants de l'énumération <xref:System.Diagnostics.TraceOptions> ne doivent pas être spécifiés:  
  
- <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 Lors de l'utilisation du traçage dans un environnement de confiance partielle, assurez-vous que l'application dispose des autorisations nécessaires pour stocker la sortie de l'écouteur de trace. Par exemple, lors de l'utilisation de <xref:System.Diagnostics.TextWriterTraceListener> pour écrire le résultat du traçage dans un fichier texte, assurez-vous que l'application bénéficie de l'autorisation FileIOPermission requise pour écrire dans le fichier de trace.  
  
> [!NOTE]
> Pour éviter de saturer les fichiers de trace avec des erreurs en double, WCF désactive le suivi de la ressource ou de l’action après le premier échec de sécurité. Une trace d'exception est créée pour chaque échec de l'accès aux ressources lors de la première tentative d'accès à la ressource ou d'accomplissement de l'action.  
  
## <a name="wcf-service-host"></a>Hôte de service WCF  

 L’hôte de service WCF ne prend pas en charge la confiance partielle. Si vous souhaitez utiliser un service WCF en confiance partielle, n’utilisez pas le modèle de projet Bibliothèque du service WCF dans Visual Studio pour générer votre service. Au lieu de cela, créez un nouveau site Web dans Visual Studio en choisissant le modèle de site Web du service WCF, qui peut héberger le service dans un serveur Web sur lequel la confiance partielle WCF est prise en charge.  
  
## <a name="other-limitations"></a>Autres limitations  

  WCF est généralement limité aux considérations de sécurité imposées par l’application d’hébergement. Par exemple, si WCF est hébergé dans une application de navigateur XAML (XBAP), il est soumis aux limitations XBAP, comme décrit dans [Windows Presentation Foundation sécurité de confiance partielle](/dotnet/desktop/wpf/wpf-partial-trust-security).  
  
 Les fonctionnalités supplémentaires suivantes ne sont pas activées en cas d’exécution d’indigo2 dans un environnement de confiance partielle :  
  
- Windows Management Instrumentation (WMI)  
  
- La journalisation des événements n'est activée que partiellement (consultez la discussion dans la section **Diagnostics** ).  
  
- Compteurs de performance  
  
 L’utilisation de fonctionnalités WCF qui ne sont pas prises en charge dans un environnement de confiance partielle peut entraîner des exceptions au moment de l’exécution.  
  
## <a name="unlisted-features"></a>Fonctionnalités non répertoriées  

 La meilleure méthode pour découvrir qu'une information ou qu'une action n'est pas disponible en cas d'exécution dans un environnement de confiance partielle est d'essayer d'accéder à la ressource ou d'exécuter l'action dans un bloc `try` , puis d'intercepter l'échec via `catch` . Pour éviter de saturer les fichiers de trace avec des erreurs en double, WCF désactive le suivi de la ressource ou de l’action après le premier échec de sécurité. Une trace d'exception est créée pour chaque échec de l'accès aux ressources lors de la première tentative d'accès à la ressource ou d'accomplissement de l'action.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Scénarios de déploiement pris en charge](supported-deployment-scenarios.md)
- [Meilleures pratiques dans un environnement de confiance partielle](partial-trust-best-practices.md)
