---
title: Migration des services Web WSE 3.0 vers WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 8f79674350109d111fe263704dee6c40c1a12451
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184571"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migration des services Web WSE 3.0 vers WCF
Les avantages de la migration des services Web WSE 3.0 à la Windows Communication Foundation (WCF) comprennent l’amélioration des performances et le soutien de transports supplémentaires, de scénarios de sécurité supplémentaires et de spécifications WSMD. Un service Web qui est migré de WSE 3.0 à WCF peut connaître jusqu’à une amélioration de performance de 200% à 400%. Pour plus d’informations sur les transports soutenus par WCF, voir [Choisir un transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Pour une liste des scénarios pris en charge par WCF, voir [scénarios de sécurité commune](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Pour une liste des spécifications qui sont prises en charge par WCF, voir [Web Services Protocols Interopérabilité Guide](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Les sections suivantes fournissent des conseils sur la façon de migrer une caractéristique spécifique d’un service Web WSE 3.0 vers WCF.  
  
## <a name="general"></a>Général  
 Les applications WSE 3.0 et WCF comprennent l’interopérabilité au niveau fil et un ensemble commun de terminologie. Les applications WSE 3.0 et WCF sont interopérables au niveau fil en fonction de l’ensemble des spécifications WS-MD qu’ils prennent tous les deux en charge. Lorsqu’une application WSE 3.0 ou WCF est développée, il existe un ensemble commun de terminologie, comme les noms des affirmations de sécurité clés en main dans WSE et les modes d’authentification.  
  
 Bien qu’il existe de nombreux aspects similaires entre les modèles de programmation WCF et ASP.NET ou WSE 3.0, ils sont différents. Pour plus de détails sur le modèle de programmation WCF, voir [Basic Programming Lifecycle](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
> Pour migrer un service Web WSE vers WCF, [l’outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) peut être utilisé pour générer un client. Ce client contient des interfaces et des classes qui peuvent être utilisées également comme point de départ pour un service WCF. Les interfaces générées ont l'attribut <xref:System.ServiceModel.OperationContractAttribute> appliqué aux membres du contrat avec la propriété <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> définie à `*`. Lorsqu’un client WSE appelle un service Web avec ce paramètre, l’exception suivante est lancée : **Web.Services3.ResponseProcessingException: WSE910: Une erreur s’est produite pendant le traitement d’un message de réponse, et vous pouvez trouver l’erreur dans l’exception interne**. À des fins d'atténuation, affectez à la propriété <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> de l'attribut <xref:System.ServiceModel.OperationContractAttribute> une valeur non `null`, telle que `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Sécurité  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Services Web WSE 3.0 sécurisés à l'aide d'un fichier de stratégie  
 Les services WCF peuvent utiliser un fichier de configuration pour sécuriser un service et ce mécanisme est similaire à un fichier de stratégie WSE 3.0. Dans WSE 3.0, lorsque vous sécurisez un service Web à l'aide d'un fichier de stratégie, vous utilisez une assertion de sécurité clé en main ou une assertion de stratégie personnalisée. Les affirmations de sécurité clés en main sont étroitement cartographies au mode d’authentification d’un élément de liaison de sécurité WCF. Non seulement les modes d’authentification WCF et les affirmations de sécurité clés en main WSE 3.0 sont les mêmes ou de même, mais ils sécurisent les messages en utilisant les mêmes types d’identification. Par exemple, `usernameForCertificate` l’affirmation de sécurité clé en main dans `UsernameForCertificate` les cartes WSE 3.0 au mode d’authentification dans WCF. Les exemples de code suivants montrent `usernameForCertificate` comment une politique minimale qui utilise l’affirmation `UsernameForCertificate` de sécurité clé en main dans les cartes WSE 3.0 à un mode d’authentification dans WCF dans une liaison personnalisée.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Pour migrer les paramètres de sécurité d’un service Web WSE 3.0 spécifié dans un fichier de stratégie vers WCF, une liaison personnalisée doit être créée dans un fichier de configuration et l’affirmation de sécurité clé en main doit être définie à son mode d’authentification équivalent. En outre, la liaison personnalisée doit être configurée de façon à utiliser la spécification WS-Addressing d’août 2004 lorsque des clients WSE 3.0 communiquent avec le service. Lorsque le service WCF migré ne nécessite pas de communication avec les clients WSE 3.0 et ne doit maintenir que la parité de sécurité, envisagez d’utiliser les liaisons définies par le système WCF avec des paramètres de sécurité appropriés au lieu de créer une liaison personnalisée.  
  
 Le tableau suivant répertorie la cartographie entre un fichier de politique WSE 3.0 et la liaison personnalisée équivalente dans WCF.  
  
|Assertion de sécurité clé en main WSE 3.0|Configuration de liaison personnalisée WCF|  
|----------------------------------------|--------------------------------------|  
|\<nom d’utilisateurOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<nom d’utilisateurForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymeForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Pour plus d’informations sur la création de fixations personnalisées dans WCF, voir [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Services Web WSE 3.0 sécurisés à l'aide du code d'application  
 Que le WSE 3.0 ou le WCF soit utilisé, les exigences de sécurité peuvent être spécifiées dans le code d’application plutôt que dans la configuration. Dans WSE 3.0, cette tâche est accomplie en créant une classe qui dérive de la classe `Policy`, puis en ajoutant les spécifications en appelant la méthode `Add`. Pour plus de détails sur la spécologie des exigences de sécurité dans le code, voir [comment : Sécuriser un service Web sans utiliser un fichier de politique](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10)). Dans WCF, pour spécifier les exigences <xref:System.ServiceModel.Channels.BindingElementCollection> de sécurité dans <xref:System.ServiceModel.Channels.SecurityBindingElement> le <xref:System.ServiceModel.Channels.BindingElementCollection>code, créer une instance de la classe et ajouter une instance de a à la . Les exigences de l’assertion de sécurité sont définies à l’aide des méthodes d’assistance de mode d’authentification statiques de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>. Pour plus de détails sur la spécification des exigences de sécurité dans le code à l’aide de WCF, voir [Comment : Créer une liaison personnalisée à l’aide de l’Element SecurityBinding](how-to-create-a-custom-binding-using-the-securitybindingelement.md) et comment : Créer un [securityBindingElement pour un mode d’authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Assertion de stratégie personnalisée WSE 3.0  
 Dans WSE 3.0, il existe deux types d'assertions de stratégie personnalisées : celles qui sécurisent un message SOAP et celles qui ne le font pas. Les affirmations de politique qui sécurisent les `SecurityPolicyAssertion` messages SOAP dérivent de <xref:System.ServiceModel.Channels.SecurityBindingElement> la classe WSE 3.0 et l’équivalent conceptuel dans WCF est la classe.  
  
 Un point important à noter est que les affirmations de sécurité clés en main WSE 3.0 sont un sous-ensemble des modes d’authentification WCF. Si vous avez créé une affirmation de stratégie personnalisée dans WSE 3.0, il peut y avoir un mode d’authentification WCF équivalent. Par exemple, WSE 3.0 ne fournit pas d'assertion de sécurité CertificateOverTransport qui équivaut à l'assertion de sécurité clé en main `UsernameOverTransport`, mais il utilise un certificat X.509 à des fins d'authentification du client. Si vous avez défini votre propre affirmation de politique personnalisée pour ce scénario, WCF rend la migration simple. WCF définit un mode d’authentification pour ce scénario, de sorte que vous<xref:System.ServiceModel.Channels.SecurityBindingElement>pouvez profiter des méthodes d’aide au mode d’authentification statique pour configurer un WCF .  
  
 Lorsqu’il n’existe pas de mode d’authentification WCF équivalent à <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>une <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>affirmation de stratégie personnalisée qui sécurise les messages SOAP, dérivez une classe des classes, ou WCF et spécifiez l’élément de liaison équivalent. Pour plus de détails, voir [Comment : Créer une liaison personnalisée à l’aide de l’Element SecurityBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Pour convertir une affirmation de stratégie personnalisée qui ne sécurise pas un message SOAP, voir [Filtering](../../../../docs/framework/wcf/feature-details/filtering.md) et l’intercepteur de [messages personnalisés](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)échantillon .  
  
### <a name="wse-30-custom-security-token"></a>Jeton de sécurité personnalisé WSE 3.0  
 Le modèle de programmation WCF pour la création d’un jeton personnalisé est différent de WSE 3.0. Pour plus de détails sur la création d’un jeton personnalisé en WSE, voir [Créer des jetons de sécurité personnalisés](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10)). Pour plus de détails sur la création d’un jeton personnalisé dans WCF, voir [Comment: Créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>Gestionnaire de jetons personnalisés WSE 3.0  
 Le modèle de programmation pour créer un gestionnaire de jetons personnalisé est différent dans WCF que WSE 3.0. Pour plus de détails sur la façon de créer un gestionnaire de jetons personnalisé et les autres composants qui sont nécessaires pour un jeton de sécurité personnalisé, voir [Comment: Créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
> Si vous avez `UsernameToken` créé un gestionnaire de jetons de sécurité personnalisé, WCF fournit un mécanisme plus facile pour spécifier la logique d’authentification que la création d’un gestionnaire de jetons de sécurité personnalisé. Pour plus de détails, voir [Comment : Utilisez un nom d’utilisateur personnalisé et un validateur de mot de passe.](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Services Web WSE 3.0 qui utilisent des messages SOAP encodés MTOM  
 Comme une application WSE 3, une application WCF peut spécifier le message MTOM codant en configuration. Pour migrer ce paramètre, ajoutez le [ \<mtomMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) à la liaison pour le service. L’exemple de code suivant montre comment l’encodage MTOM est spécifié dans WSE 3.0 pour un service équivalent dans WCF.  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Messagerie  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>Applications WSE 3.0 qui utilisent l'API de messagerie WSE  

 Lorsque l'API de messagerie WSE est utilisée pour obtenir un accès direct au XML communiqué entre le client et le service Web, l'application peut être convertie de façon à utiliser le « Plain Old XML » (POX). Pour plus de détails sur POX, voir [Interopérabilité avec LES applications POX](interoperability-with-pox-applications.md). Pour plus de détails sur l’API de messagerie WSE, voir [envoyer et recevoir des messages SOAP à l’aide de l’API de messagerie WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10)).  
  
## <a name="transports"></a>Transports  
  
### <a name="tcp"></a>TCP  
 Par défaut, les clients et les services Web WSE 3.0 qui envoient des messages SOAP utilisant le transport TCP n’interopéront pas avec les clients WCF et les services Web. Cette incompatibilité est due aux différences de tramage utilisé dans le protocole TCP et aux performances. Cependant, un échantillon WCF détaille comment mettre en œuvre une session TCP personnalisée qui interopère avec WSE 3.0. Pour plus de détails sur cet exemple, voir [Transport: WSE 3.0 TCP Interopérabilité](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Pour spécifier qu’une application WCF utilise le transport TCP, utilisez le [ \<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Transport personnalisé  
 L’équivalent d’un transport personnalisé WSE 3.0 dans WCF est une extension de canal. Pour plus de détails sur la création d’une extension de canal, voir [Extending the Channel Layer](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Voir aussi

- [Cycle de vie de la programmation de base](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
