---
title: Protocoles de services Web pris en charge par des liaisons d’interopérabilité fournies par le système
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 963325604f66ddd4f8470933584b7880c86403bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951561"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protocoles de services Web pris en charge par des liaisons d’interopérabilité fournies par le système
Windows Communication Foundation (WCF) est conçu pour interagir avec les services Web qui prennent en charge un ensemble de spécifications connues sous le nom de spécifications de services Web. Pour simplifier la configuration de service pour les meilleures pratiques d’interopérabilité, WCF introduit trois liaisons interopérables <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>fournies <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>par le <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>système:, et. Pour l’interopérabilité avec l’Organisation pour la progression des normes OASIS (Structured Information Standards), WCF comprend une liaison interopérable fournie <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>par le système:. Pour la publication de métadonnées, WCF comprend deux liaisons interopérables fournies par le système: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) et [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Cette rubrique répertorie les spécifications prises en charge par les liaisons interopérable fournies par le système.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protocoles de services Web pris en charge par basicHttpBinding, wsHttpBinding, ws2007HttpBinding et wsDualHttpBinding Bindings  
  
### <a name="all-bindings"></a>Toutes les liaisons  
 [ Les\<liaisons BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)et [ \<WS2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) prennent en charge les protocoles suivants.  
  
> [!NOTE]
> Pour plus d’informations sur les liaisons utilisées pour publier des métadonnées, consultez la section « Liaisons de métadonnées fournies par le système » développée ultérieurement dans cette rubrique.  
  
|Catégorie|Protocol|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding` et `WS2007HttpBinding` utilisent les transports HTTP et HTTPS.|  
|Messagerie|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding` et `ws2007HttpBinding` prennent en charge MTOM (Message Transmission Optimization Mechanism). Non utilisé par défaut. Pour utiliser MTOM, affectez `messageEncoding` à l'attribut `"Mtom"`.<br /><br /> Exemple :<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Métadonnées|WSDL 1.1|[WSDL 1,1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF utilise Web Services Description Language (WSDL) pour décrire les services.|  
|Métadonnées|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> WCF utilise la spécification WS-Policy avec des assertions spécifiques au domaine pour décrire les exigences et les fonctionnalités du service.|  
|Métadonnées|WS-Policy 1.5|[WS-Policy 1,5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> WCF utilise la spécification WS-Policy avec des assertions spécifiques au domaine pour décrire les exigences et les fonctionnalités du service.|  
|Métadonnées|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> WCF implémente WS-PolicyAttachment pour joindre des expressions de stratégie à différentes étendues dans Web Services Description Language (WSDL).|  
|Métadonnées|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Catégorie|Protocol|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Messagerie|SOAP 1,1|[SOAP 1,1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Conformément à Basic Profile 1.1, l'élément `basicHttpBinding` implémente le protocole de messagerie SOAP 1.1.|  
|Sécurité|WSS SOAP Message Security 1.0|[Sécurité des messages SOAP WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Conformément à Basic Security Profile, l'élément `basicHttpBinding` implémente la spécification WSS (Web Services Security) SOAP Message Security 1.0 pour le nom d'utilisateur/mot de passe et la sécurité basée sur les certificats X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Sécurité|WSS SOAP Message Security UsernameToken Profile 1.0|[WSS SOAP Message Security UsernameToken Profile 1,0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Sécurité|WSS SOAP Message Security X. 509 Certificate Token Profile 1,0|[WSS SOAP Message Security X. 509 Certificate Token Profile 1,0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding et wsDualHttpBinding  
  
|Catégorie|Protocol|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Messagerie|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Infrastructure de messagerie](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Compléments (y compris la liaison HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Messagerie|WS-Addressing 2005/08|[Adressage de services Web 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adressage de services Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding` et `wsDualHttpBinding` implémentent la recommandation W3C (World Wide Web Consortium) WS-Addressing pour activer la messagerie asynchrone, la corrélation de messages et les mécanismes d’adressage indépendant du transport.<br /><br /> WCF ne prend pas en charge le chiffrement des en-têtes WS-Addressing bien que cela soit autorisé par les spécifications WS-*.|  
|Messagerie|WS-Addressing 1.0 - Métadonnées|[WS-Addressing 1,0 métadonnées](https://www.w3.org/2007/05/addressing/metadata) La prise en charge de ce protocole est activée en définissant la version de stratégie dans le comportement ServiceMetadata-avec PolicyVersion défini sur 1,2 (valeur par défaut), la description WSDL est conforme à WS-Addressing WSDL, avec PolicyVersion défini sur 1,5, la description WSDL est conforme aux métadonnées WS-Addressing.<br /><br /> WCF ne prend pas en charge le chiffrement des en-têtes WS-Addressing bien que cela soit autorisé par les spécifications WS-*.|  
|Sécurité|WSS SOAP Message Security 1.0|[Sécurité des messages SOAP WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Utilisé lorsque l'attribut `securityMode` a la valeur "wsSecurityOverHttp" (valeur par défaut) et que les paramètres sont configurés à l'aide d'un élément enfant `wsSecurity`.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Sécurité|WSS SOAP Message Security UsernameToken Profile 1,1|[WSS SOAP Message Security UsernameToken Profile 1,0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Utilisé lorsque l'attribut `wsSecurity` de l'élément `authenticationMode` a la valeur "Username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Sécurité|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[WSS SOAP Message Security X. 509 Certificate Token Profile 1,1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Utilisé pour la protection des messages lorsque l'attribut `wsSecurity` de l'élément `authenticationMode` a la valeur "Username", "Certificate" ou "None". Il est par ailleurs utilisé pour l'authentification du client lorsque l'attribut `wsSecurity` de l'élément `authenticationMode` a la valeur "Certificate".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Sécurité|WSS SOAP Message Security Kerberos Token Profile 1.1|[WSS SOAP Message Security Kerberos Token Profile 1,1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Utilisé pour l'authentification et la protection des messages lorsque l'attribut `wsSecurity` de l'élément `authenticationMode` a la valeur "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Sécurité|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Utilisé pour fournir une session sécurisée lorsque l'attribut `security/@mode` a la valeur "Message" et l'attribut `message/@establishSecurityContext` a la valeur "true" (valeur par défaut).|  
|Sécurité|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Utilisé par WS-SecureConversation (voir ci-dessus).|  
|Messagerie fiable|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Utilisé lorsque la liaison est configurée pour utiliser `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transactions|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> À utiliser pour la communication entre les gestionnaires de transactions. Les clients et les services WCF utilisent toujours des gestionnaires de transactions locaux.|  
|Transactions|WS-Coordination|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Utilisé pour transmettre le contexte de transaction lorsque l’attribut `flowTransactions` a la valeur "Allowed" ou "Required".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding et ws2007FederationHttpBinding  
 Les éléments [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) et [ \<WS2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) sont introduits pour assurer la prise en charge des scénarios fédérés, où un tiers émet un jeton utilisé pour authentifier un client. Outre les protocoles utilisés par `wsHttpBinding`, `wsFederationHttpBinding` tire parti de :  
  
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
 La liaison de [ \<> mexHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) prend en charge les protocoles suivants. Pour plus d’informations sur l’utilisation de cette liaison, consultez [publication](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)de métadonnées.  
  
|Catégorie|Protocol|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|Messagerie|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Infrastructure de messagerie](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Compléments (y compris la liaison HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Messagerie|WS-Addressing 2005/08|[Adressage de services Web 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adressage de services Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Métadonnées|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding > prend en charge les protocoles suivants. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Pour plus d’informations sur l’utilisation de cette liaison, consultez [publication](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)de métadonnées.  
  
|Catégorie|Protocol|Spécification et utilisation|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> La sécurité de transport est activée.|  
|Messagerie|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Infrastructure de messagerie](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Compléments (y compris la liaison HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Messagerie|WS-Addressing 2005/08|[Adressage de services Web 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adressage de services Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Métadonnées|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
  
## <a name="see-also"></a>Voir aussi

- [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
