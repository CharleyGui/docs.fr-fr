---
title: 'Procédure : configurer des informations d’identification sur un service de fédération'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 792d2f1b113c0743bd91ccf2f7ff894d7f7d319f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912197"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Procédure : configurer des informations d’identification sur un service de fédération
Dans Windows Communication Foundation (WCF), la création d’un service fédéré se compose des procédures principales suivantes:  
  
1. Configuration d'un <xref:System.ServiceModel.WSFederationHttpBinding> ou d'une liaison personnalisée similaire. Pour plus d’informations sur la création d’une liaison [appropriée, consultez Procédure: Créez un WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2. Configuration de <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> qui contrôle la manière dont les jetons émis présentés au service sont authentifiés.  
  
 Cette rubrique fournit des détails sur la deuxième étape. Pour plus d’informations sur le fonctionnement d’un service fédéré, consultez [Federation](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Pour définir les propriétés de IssuedTokenServiceCredential dans le code  
  
1. Utilisez la propriété <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> de la classe <xref:System.ServiceModel.Description.ServiceCredentials> pour retourner une référence à une instance <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>. La propriété est accessible à partir de la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> de la classe <xref:System.ServiceModel.ServiceHostBase>.  
  
2. Affectez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> à `true` la propriété la valeur si des jetons auto-émis tels que les cartes CardSpace doivent être authentifiés. Par défaut, il s’agit de `false`.  
  
3. Remplissez la collection retournée par la propriété <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> avec les instances de la classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>. Chaque instance représente un émetteur à partir duquel le service authentifiera des jetons.  
  
    > [!NOTE]
    > Contrairement à la collection côté client retournée par la propriété <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>, la collection des certificats connus n'est pas une collection à clé. Le service accepte les jetons que les certificats spécifiés émettent indépendamment de l'adresse du client qui a envoyé le message contenant le jeton émis (sous réserve des contraintes supplémentaires décrites plus loin dans cette rubrique).  
  
4. Affectez l'une des valeurs de l'énumération <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> à la propriété <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Cette opération peut s'effectuer uniquement dans le code. Par défaut, il s’agit de <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Si la propriété <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> a la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, assignez une instance de la classe personnalisée <xref:System.IdentityModel.Selectors.X509CertificateValidator> à la propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A>.  
  
6. Si <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> a la valeur `ChainTrust` ou `PeerOrChainTrust`, affectez l'une des valeurs appropriées de l'énumération <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> à la propriété <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Notez que le mode de révocation n’est pas utilisé dans les modes de validation `PeerTrust` ou `Custom`.  
  
7. Si nécessaire, assignez une instance d'une classe personnalisée <xref:System.IdentityModel.Tokens.SamlSerializer> à la propriété <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A>. Un sérialiseur SAML (Security Assertions Markup Language) personnalisé est nécessaire, par exemple pour l'analyse des assertions SAML personnalisées.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Pour définir les propriétés de IssuedTokenServiceCredential dans la configuration  
  
1. Crée un `<issuedTokenAuthentication>` élément en tant qu’enfant d’un`serviceCredentials`élément < >.  
  
2. Affectez `allowUntrustedRsaIssuers` à l’attribut `<issuedTokenAuthentication>` de l' `true` élément la valeur en cas d’authentification d’un jeton auto-émis, par exemple une carte CardSpace.  
  
3. Créez un élément `<knownCertificates>` en tant qu'enfant de l'élément `<issuedTokenAuthentication>`.  
  
4. Créez zéro ou plusieurs éléments `<add>` en tant qu'enfants de l'élément `<knownCertificates>` et spécifiez comment localiser le certificat à l'aide des attributs `storeLocation`, `storeName`, `x509FindType` et `findValue`.  
  
5. Si nécessaire, affectez `samlSerializer` le nom de type`issuedTokenAuthentication`de la classe personnalisée <xref:System.IdentityModel.Tokens.SamlSerializer> à l’attribut de l’élément < >.  
  
## <a name="example"></a>Exemples  
 L'exemple suivant définit les propriétés de <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> dans le code.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Pour qu'un service fédéré authentifie un client, les conditions suivantes doivent être vérifiées pour le jeton émis :  
  
- Lorsque la signature numérique du jeton émis utilise un identificateur de clé de sécurité RSA, la propriété <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> doit avoir la valeur `true`.  
  
- Lorsque la signature du jeton émis utilise un numéro de série d’émetteur X.509, un identificateur de clé du sujet X.509 ou un identificateur de sécurité d’empreinte numérique X.509, le jeton émis doit être signé par un certificat de la collection retournée par la propriété <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> de la classe <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>.  
  
- Lorsque le jeton émis est signé à l'aide d'un certificat X.509, le certificat doit valider suivant la sémantique spécifiée par la valeur de la propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A>, indépendamment du fait que le certificat a été envoyé à la partie de confiance en tant que <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> ou qu'il a été obtenu à partir de la propriété <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>. Pour plus d’informations sur la validation des certificats X. 509, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Par exemple, si vous affectez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> à <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust>, les jetons émis dont le certificat de signature se trouve dans le magasin de certificats `TrustedPeople` sont authentifiés. Dans ce cas, affectez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> ou <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> à la propriété <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Vous pouvez sélectionner d'autres modes, dont <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Lorsque `Custom` est sélectionné, vous devez assigner une instance de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> à la propriété <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A>. Le validateur personnalisé peut valider des certificats à l'aide de n'importe quel critère. Pour plus d’informations, consultez [Guide pratique pour Créez un service qui utilise un validateur](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)de certificat personnalisé.  
  
## <a name="see-also"></a>Voir aussi

- [Fédération](../../../../docs/framework/wcf/feature-details/federation.md)
- [Fédération et confiance](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Exemple de fédération](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Guide pratique : Désactiver les sessions sécurisées sur un WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Guide pratique pour Créer un WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Guide pratique pour Créer un client fédéré](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Modes d’authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
