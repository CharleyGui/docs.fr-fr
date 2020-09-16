---
title: Migration des services Web WSE 3.0 vers WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: c7feac0a44883e8019acfeaa288752fb051c667f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554089"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migration des services Web WSE 3.0 vers WCF
Les avantages de la migration des services Web WSE 3,0 vers Windows Communication Foundation (WCF) incluent des performances améliorées et la prise en charge de transports supplémentaires, de scénarios de sécurité supplémentaires et de spécifications WS-*. Un service Web qui est migré de WSE 3,0 à WCF peut bénéficier d’une amélioration des performances de 200% à 400%. Pour plus d’informations sur les transports pris en charge par WCF, consultez [choix d’un transport](choosing-a-transport.md). Pour obtenir la liste des scénarios pris en charge par WCF, consultez [scénarios de sécurité courants](common-security-scenarios.md). Pour obtenir la liste des spécifications prises en charge par WCF, consultez le [Guide d’interopérabilité des protocoles de services Web](web-services-protocols-interoperability-guide.md).  
  
 Les sections suivantes fournissent des conseils sur la façon de migrer une fonctionnalité spécifique d’un service Web WSE 3,0 vers WCF.  
  
## <a name="general"></a>Général  
 Les applications WSE 3,0 et WCF incluent l’interopérabilité au niveau du réseau et un ensemble commun de terminologie. Les applications WSE 3,0 et WCF sont interopérables au niveau du réseau en fonction de l’ensemble de spécifications WS-* qu’elles prennent en charge. Quand une application WSE 3,0 ou WCF est développée, il existe un ensemble commun de terminologie, comme les noms des assertions de sécurité clé en main dans WSE et les modes d’authentification.  
  
 Bien qu’il existe de nombreux aspects similaires entre les modèles de programmation WCF et ASP.NET ou WSE 3,0, ils sont différents. Pour plus d’informations sur le modèle de programmation WCF, consultez [cycle de vie de programmation de base](../basic-programming-lifecycle.md).  
  
> [!NOTE]
> Pour migrer un service Web WSE vers WCF [, l’outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) peut être utilisé pour générer un client. Ce client contient des interfaces et des classes qui peuvent être utilisées également comme point de départ pour un service WCF. Les interfaces générées ont l'attribut <xref:System.ServiceModel.OperationContractAttribute> appliqué aux membres du contrat avec la propriété <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> définie à `*`. Lorsqu’un client WSE appelle un service Web avec ce paramètre, l’exception suivante est levée : **Web. services3. ResponseProcessingException : WSE910 : une erreur s’est produite lors du traitement d’un message de réponse, et vous pouvez trouver l’erreur dans l’exception interne**. À des fins d'atténuation, affectez à la propriété <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> de l'attribut <xref:System.ServiceModel.OperationContractAttribute> une valeur non `null`, telle que `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Sécurité  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Services Web WSE 3.0 sécurisés à l'aide d'un fichier de stratégie  
 Les services WCF peuvent utiliser un fichier de configuration pour sécuriser un service et ce mécanisme est similaire à un fichier de stratégie WSE 3,0. Dans WSE 3.0, lorsque vous sécurisez un service Web à l'aide d'un fichier de stratégie, vous utilisez une assertion de sécurité clé en main ou une assertion de stratégie personnalisée. Les assertions de sécurité clé en main sont mappées étroitement au mode d’authentification d’un élément de liaison de sécurité WCF. Non seulement les modes d’authentification WCF et les assertions de sécurité clé en main WSE 3,0 ont un nom identique ou similaire, mais ils sécurisent les messages à l’aide des mêmes types d’informations d’identification. Par exemple, l' `usernameForCertificate` assertion de sécurité clé en main dans WSE 3,0 est mappée au `UsernameForCertificate` mode d’authentification dans WCF. Les exemples de code suivants montrent comment une stratégie minimale qui utilise l' `usernameForCertificate` assertion de sécurité clé en main dans WSE 3,0 correspond à un `UsernameForCertificate` mode d’authentification dans WCF dans une liaison personnalisée.  
  
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
  
 Pour migrer les paramètres de sécurité d’un service Web WSE 3,0 qui sont spécifiés dans un fichier de stratégie vers WCF, une liaison personnalisée doit être créée dans un fichier de configuration et l’assertion de sécurité clé en main doit être définie sur son mode d’authentification équivalent. En outre, la liaison personnalisée doit être configurée de façon à utiliser la spécification WS-Addressing d’août 2004 lorsque des clients WSE 3.0 communiquent avec le service. Lorsque le service WCF migré ne nécessite pas de communication avec les clients WSE 3,0 et doit uniquement maintenir la parité de sécurité, envisagez d’utiliser les liaisons définies par le système WCF avec les paramètres de sécurité appropriés au lieu de créer une liaison personnalisée.  
  
 Le tableau suivant répertorie le mappage entre un fichier de stratégie WSE 3,0 et la liaison personnalisée équivalente dans WCF.  
  
|Assertion de sécurité clé en main WSE 3.0|Configuration de liaison personnalisée WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Pour plus d’informations sur la création de liaisons personnalisées dans WCF, consultez [liaisons personnalisées](../extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Services Web WSE 3.0 sécurisés à l'aide du code d'application  
 Que WSE 3,0 ou WCF soit utilisé, les exigences de sécurité peuvent être spécifiées dans le code d’application plutôt que dans la configuration. Dans WSE 3.0, cette tâche est accomplie en créant une classe qui dérive de la classe `Policy`, puis en ajoutant les spécifications en appelant la méthode `Add`. Pour plus d’informations sur la spécification des exigences de sécurité dans le code, consultez [Comment : sécuriser un service Web sans utiliser de fichier de stratégie](/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10)). Dans WCF, pour spécifier des exigences de sécurité dans le code, créez une instance de la <xref:System.ServiceModel.Channels.BindingElementCollection> classe et ajoutez une instance d’un <xref:System.ServiceModel.Channels.SecurityBindingElement> au <xref:System.ServiceModel.Channels.BindingElementCollection> . Les exigences de l’assertion de sécurité sont définies à l’aide des méthodes d’assistance de mode d’authentification statiques de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>. Pour plus d’informations sur la spécification des exigences de sécurité dans le code à l’aide de WCF, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md) et [Comment : créer un SecurityBindingElement pour un mode d’authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Assertion de stratégie personnalisée WSE 3.0  
 Dans WSE 3.0, il existe deux types d'assertions de stratégie personnalisées : celles qui sécurisent un message SOAP et celles qui ne le font pas. Les assertions de stratégie qui sécurisent les messages SOAP dérivent de la classe WSE 3,0 et de l' `SecurityPolicyAssertion` équivalent conceptuel dans WCF est la <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.  
  
 Un point important à noter est que les assertions de sécurité clé en main WSE 3,0 sont un sous-ensemble des modes d’authentification WCF. Si vous avez créé une assertion de stratégie personnalisée dans WSE 3,0, il peut y avoir un mode d’authentification WCF équivalent. Par exemple, WSE 3.0 ne fournit pas d'assertion de sécurité CertificateOverTransport qui équivaut à l'assertion de sécurité clé en main `UsernameOverTransport`, mais il utilise un certificat X.509 à des fins d'authentification du client. Si vous avez défini votre propre assertion de stratégie personnalisée pour ce scénario, WCF rend la migration simple. WCF définit un mode d’authentification pour ce scénario, ce qui vous permet de tirer parti des méthodes d’assistance de mode d’authentification statique pour configurer un WCF <xref:System.ServiceModel.Channels.SecurityBindingElement> .  
  
 Lorsqu’il n’existe pas de mode d’authentification WCF équivalent à une assertion de stratégie personnalisée qui sécurise les messages SOAP, dérivez une classe de <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ou des <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> classes WCF et spécifiez l’élément de liaison équivalent. Pour plus d’informations, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Pour convertir une assertion de stratégie personnalisée qui ne sécurise pas un message SOAP, consultez [filtrage](filtering.md) et l’exemple d' [intercepteur de message personnalisé](../samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Jeton de sécurité personnalisé WSE 3.0  
 Le modèle de programmation WCF pour la création d’un jeton personnalisé est différent de WSE 3,0. Pour plus d’informations sur la création d’un jeton personnalisé dans WSE, consultez [création de jetons de sécurité personnalisés](/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10)). Pour plus d’informations sur la création d’un jeton personnalisé dans WCF, consultez [How to : Create a Custom Token](../extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>Gestionnaire de jetons personnalisés WSE 3.0  
 Le modèle de programmation pour la création d’un gestionnaire de jetons personnalisé est différent dans WCF par rapport à WSE 3,0. Pour plus d’informations sur la création d’un gestionnaire de jetons personnalisé et sur les autres composants requis pour un jeton de sécurité personnalisé, consultez [Comment : créer un jeton personnalisé](../extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
> Si vous avez créé un `UsernameToken` Gestionnaire de jetons de sécurité personnalisé, WCF fournit un mécanisme plus simple pour spécifier la logique d’authentification que de créer un gestionnaire de jetons de sécurité personnalisé. Pour plus d’informations, consultez [Comment : utiliser un validateur de nom d’utilisateur et de mot de passe personnalisé](how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Services Web WSE 3.0 qui utilisent des messages SOAP encodés MTOM  
 À l’instar d’une application WSE 3, une application WCF peut spécifier l’encodage de message MTOM dans la configuration. Pour migrer ce paramètre, ajoutez [\<mtomMessageEncoding>](../../configure-apps/file-schema/wcf/mtommessageencoding.md) à la liaison pour le service. L’exemple de code suivant montre comment l’encodage MTOM est spécifié dans WSE 3,0 pour un service équivalent dans WCF.  
  
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

 Lorsque l'API de messagerie WSE est utilisée pour obtenir un accès direct au XML communiqué entre le client et le service Web, l'application peut être convertie de façon à utiliser le « Plain Old XML » (POX). Pour plus d’informations sur POX, consultez [interopérabilité avec les applications POX](interoperability-with-pox-applications.md). Pour plus d’informations sur l’API de messagerie WSE, consultez [envoi et réception de messages SOAP à l’aide de l’API de messagerie WSE](/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10)).  
  
## <a name="transports"></a>Transports  
  
### <a name="tcp"></a>TCP  
 Par défaut, les clients WSE 3,0 et les services Web qui envoient des messages SOAP à l’aide du transport TCP n’interagissent pas avec les clients WCF et les services Web. Cette incompatibilité est due aux différences de tramage utilisé dans le protocole TCP et aux performances. Toutefois, un exemple WCF explique comment implémenter une session TCP personnalisée qui interagit avec WSE 3,0. Pour plus d’informations sur cet exemple, consultez [transport : interopérabilité TCP WSE 3,0](../samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Pour spécifier qu’une application WCF utilise le transport TCP, utilisez le [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) .  
  
### <a name="custom-transport"></a>Transport personnalisé  
 L’équivalent d’un transport personnalisé WSE 3,0 dans WCF est une extension de canal. Pour plus d’informations sur la création d’une extension de canal, consultez [extension de la couche de canal](../extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Voir aussi

- [Cycle de vie de la programmation de base](../basic-programming-lifecycle.md)
- [Liaisons personnalisées](../extending/custom-bindings.md)
- [Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Procédure : créer un SecurityBindingElement pour un mode d’authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
