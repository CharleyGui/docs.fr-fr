---
title: Protocoles de services Web pris en charge par des liaisons d’interopérabilité fournies par le système
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 80fa0e501f425bd5b917059e90f2811f075db651
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746898"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protocoles de services Web pris en charge par des liaisons d’interopérabilité fournies par le système
Windows Communication Foundation (WCF) est conçu pour interagir avec les services Web qui prennent en charge un ensemble de spécifications connues sous le nom de spécifications de services Web. Pour simplifier la configuration de service pour les meilleures pratiques d’interopérabilité, WCF introduit trois liaisons interopérables fournies par le système : <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>et <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Pour l’interopérabilité avec l’Organisation pour l’avancement des normes OASIS (Structured Information Standards), WCF comprend une liaison interopérable fournie par le système : <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Pour la publication de métadonnées, WCF comprend deux liaisons interopérables fournies par le système : [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) et [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Cette rubrique répertorie les spécifications prises en charge par les liaisons interopérable fournies par le système.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protocoles de services Web pris en charge par basicHttpBinding, wsHttpBinding, ws2007HttpBinding et wsDualHttpBinding Bindings  
  
### <a name="all-bindings"></a>Toutes les liaisons  
 Les liaisons [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)et [\<WS2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) prennent en charge les protocoles suivants.  
  
> [!NOTE]
> Pour plus d’informations sur les liaisons utilisées pour publier des métadonnées, consultez la section « Liaisons de métadonnées fournies par le système » développée ultérieurement dans cette rubrique.  
  
|Catégorie|Protocole|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding` et `WS2007HttpBinding` utilisent les transports HTTP et HTTPS.|  
|Messagerie|MTOM|[MTOM](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding` et `ws2007HttpBinding` prennent en charge MTOM (Message Transmission Optimization Mechanism). Non utilisé par défaut. Pour utiliser MTOM, affectez `messageEncoding` à l'attribut `"Mtom"`.<br /><br /> Exemple :<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Métadonnées|WSDL 1.1|[WSDL 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF utilise Web Services Description Language (WSDL) pour décrire les services.|  
|Métadonnées|WS-Policy|[WS-Policy](https://www.w3.org/Submission/WS-Policy/)<br /><br /> WCF utilise la spécification WS-Policy avec des assertions spécifiques au domaine pour décrire les exigences et les fonctionnalités du service.|  
|Métadonnées|WS-Policy 1.5|[WS-Policy 1,5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> WCF utilise la spécification WS-Policy avec des assertions spécifiques au domaine pour décrire les exigences et les fonctionnalités du service.|  
|Métadonnées|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF implémente WS-PolicyAttachment pour joindre des expressions de stratégie à différentes étendues dans Web Services Description Language (WSDL).|  
|Métadonnées|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Catégorie|Protocole|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Messagerie|SOAP 1,1|[SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> Conformément à Basic Profile 1.1, l'élément `basicHttpBinding` implémente le protocole de messagerie SOAP 1.1.|  
|Sécurité|WSS SOAP Message Security 1.0|[Sécurité des messages SOAP WSS 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Conformément à Basic Security Profile, l'élément `basicHttpBinding` implémente la spécification WSS (Web Services Security) SOAP Message Security 1.0 pour le nom d'utilisateur/mot de passe et la sécurité basée sur les certificats X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Sécurité|WSS SOAP Message Security UsernameToken Profile 1.0|[WSS SOAP Message Security UsernameToken Profile 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Sécurité|WSS SOAP Message Security X. 509 Certificate Token Profile 1,0|[WSS SOAP Message Security X. 509 Certificate Token Profile 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding et wsDualHttpBinding  
  
|Catégorie|Protocole|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Messagerie|SOAP 1.2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Infrastructure de messagerie](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Compléments (y compris la liaison HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Messagerie|WS-Addressing 2005/08|[Adressage de services Web 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Adressage de services Web 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding` et `wsDualHttpBinding` implémentent la recommandation W3C (World Wide Web Consortium) WS-Addressing pour activer la messagerie asynchrone, la corrélation de messages et les mécanismes d’adressage indépendant du transport.<br /><br /> WCF ne prend pas en charge le chiffrement des en-têtes WS-Addressing bien que cela soit autorisé par les spécifications WS-*.|  
|Messagerie|WS-Addressing 1.0 - Métadonnées|[WS-Addressing 1,0 métadonnées](https://www.w3.org/2007/05/addressing/metadata/) La prise en charge de ce protocole est activée en définissant la version de stratégie dans le comportement ServiceMetadata-avec PolicyVersion défini sur 1,2 (valeur par défaut), la description WSDL est conforme à WS-Addressing WSDL, avec PolicyVersion défini sur 1,5, la description WSDL est conforme aux métadonnées WS-Addressing.<br /><br /> WCF ne prend pas en charge le chiffrement des en-têtes WS-Addressing bien que cela soit autorisé par les spécifications WS-*.|  
|Sécurité|WSS SOAP Message Security 1.0|[Sécurité des messages SOAP WSS 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Utilisé lorsque l'attribut `securityMode` a la valeur "wsSecurityOverHttp" (valeur par défaut) et que les paramètres sont configurés à l'aide d'un élément enfant `wsSecurity`.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Sécurité|WSS SOAP Message Security UsernameToken Profile 1,1|[WSS SOAP Message Security UsernameToken Profile 1,0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Utilisé lorsque l'attribut `wsSecurity` de l'élément `authenticationMode` a la valeur "Username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Sécurité|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[WSS SOAP Message Security X. 509 Certificate Token Profile 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> Utilisé pour la protection des messages lorsque l'attribut `wsSecurity` de l'élément `authenticationMode` a la valeur "Username", "Certificate" ou "None". Il est par ailleurs utilisé pour l'authentification du client lorsque l'attribut `wsSecurity` de l'élément `authenticationMode` a la valeur "Certificate".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Sécurité|WSS SOAP Message Security Kerberos Token Profile 1.1|[WSS SOAP Message Security Kerberos Token Profile 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> Utilisé pour l'authentification et la protection des messages lorsque l'attribut `wsSecurity` de l'élément `authenticationMode` a la valeur "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Sécurité|WS-SecureConversation|[Spécification WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Utilisé pour fournir une session sécurisée lorsque l'attribut `security/@mode` a la valeur "Message" et l'attribut `message/@establishSecurityContext` a la valeur "true" (valeur par défaut).|  
|Sécurité|WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> Utilisé par WS-SecureConversation (voir ci-dessus).|  
|Messagerie fiable|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Utilisé lorsque la liaison est configurée pour utiliser `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|transactions|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> À utiliser pour la communication entre les gestionnaires de transactions. Les clients et les services WCF utilisent toujours des gestionnaires de transactions locaux.|  
|transactions|WS-Coordination|[WS-coordination](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> Utilisé pour transmettre le contexte de transaction lorsque l’attribut `flowTransactions` a la valeur "Allowed" ou "Required".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding et ws2007FederationHttpBinding  
 Les éléments [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) et [\<WS2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) sont introduits pour fournir une prise en charge des scénarios fédérés, où un tiers émet un jeton utilisé pour authentifier un client. Outre les protocoles utilisés par `wsHttpBinding`, `wsFederationHttpBinding` tire parti de :  
  
- `WS-Trust` pour l'émission de jeton.  
  
- WSS SAML (Security Assertions Markup Language) Token Profile 1.0 et 1.1 pour le format de jeton le plus fréquemment émis.  
  
 Exemple :  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"   
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =   
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 Pour plus d’informations, consultez [Federation](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Liaisons de métadonnées fournies par le système  
 Les tableaux suivants décrivent les protocoles pris en charge par les liaisons de métadonnées interopérables fournies par le système exposées par la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 La liaison [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) prend en charge les protocoles suivants. Pour plus d’informations sur l’utilisation de cette liaison, consultez [publication de métadonnées](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Catégorie|Protocole|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Messagerie|SOAP 1.2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Infrastructure de messagerie](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Compléments (y compris la liaison HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Messagerie|WS-Addressing 2005/08|[Adressage de services Web 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Adressage de services Web 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Métadonnées|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) prend en charge les protocoles suivants. Pour plus d’informations sur l’utilisation de cette liaison, consultez [publication de métadonnées](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Catégorie|Protocole|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> La sécurité de transport est activée.|  
|Messagerie|SOAP 1.2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Infrastructure de messagerie](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Compléments (y compris la liaison HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Messagerie|WS-Addressing 2005/08|[Adressage de services Web 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Adressage de services Web 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Métadonnées|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
  
## <a name="see-also"></a>Voir aussi

- [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
