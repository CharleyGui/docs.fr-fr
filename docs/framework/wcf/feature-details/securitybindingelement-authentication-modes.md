---
title: Modes d'authentification SecurityBindingElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: 163645c16097b5371369618f2bd5f333feb75747
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595147"
---
# <a name="securitybindingelement-authentication-modes"></a>Modes d'authentification SecurityBindingElement
Windows Communication Foundation (WCF) fournit plusieurs modes par lesquels les clients et les services s’authentifient l’un l’autre. Vous pouvez créer des éléments de liaison de sécurité pour ces modes d'authentification à l'aide des méthodes statiques sur la classe <xref:System.ServiceModel.Channels.SecurityBindingElement> ou via la configuration. Cette rubrique décrit brièvement les 18 modes d'authentification.  
  
 Pour obtenir un exemple d’utilisation de l’élément pour l’un des modes d’authentification, consultez [Comment : créer un SecurityBindingElement pour un mode d’authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Programmation de configuration de base  
 La procédure suivante décrit comment définir le mode d'authentification dans un fichier de configuration.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Pour définir le mode d'authentification dans la configuration  
  
1. Pour l' [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) élément, ajoutez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .  
  
2. En tant qu’élément enfant, ajoutez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément à l' `<customBinding>` élément.  
  
3. Ajoutez un élément `<security>` à l'élément `<binding>`.  
  
4. Affectez l'une des valeurs décrites ci- dessous à l'attribut `authenticationMode`. Par exemple, le code suivant affecte `AnonymousForCertificate` au mode.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Pour définir le mode par programme  
  
1. Indiquez l’un des types de retour suivants : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2. Appelez la méthode statique appropriée de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>. Par exemple, le code suivant appelle la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A>.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3. Utilisez l’élément de liaison pour créer la liaison personnalisée. Pour plus d’informations, consultez [liaisons personnalisées](../extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Descriptions des modes  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 Avec ce mode d'authentification, le client est anonyme et le service est authentifié à l'aide d'un certificat X.509. L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A>. Vous pouvez également affecter la valeur `authenticationMode` à l’attribut de l' `security` élément <> `AnonymousForCertificate` .  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 Avec ce mode d'authentification, le client est anonyme et le service est authentifié à l'aide d'un certificat X.509 négocié au moment de l'exécution. L’élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> lorsqu’une valeur de `false` est passée pour le premier paramètre. Vous pouvez également affecter `authenticationMode` à l'attribut `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message. Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport. L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Avec ce mode d'authentification, le client ne s'authentifie pas au service en tant que tel. Au lieu de cela, il s'authentifie à un service de jeton de sécurité et reçoit un jeton SAML, qu'il présente ensuite au serveur pour prouver sa connaissance d'une clé partagée. Le service n'est pas authentifié auprès du client, en tant que tel, mais le service d'émission de jeton de sécurité chiffre la clé partagée dans le cadre du jeton émis afin que seul le service puisse déchiffrer la clé. L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 Avec ce mode d'authentification, le client ne s'authentifie pas au service en tant que tel. Au lieu de cela, il s'authentifie à un service de jeton de sécurité et reçoit un jeton SAML, qu'il présente ensuite au serveur pour prouver sa connaissance d'une clé partagée. Le jeton émis apparaît au niveau de la couche SOAP sous la forme d'un jeton de prise en charge d'endossement ou d'un jeton de porteur ; autrement dit, un jeton qui signe la signature de message. Le service s'authentifie auprès du client à l'aide d'un certificat X.509. L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 Avec ce mode d'authentification, le client ne s'authentifie pas au service en tant que tel. Au lieu de cela, il s'authentifie à un service de jeton de sécurité et reçoit un jeton SAML, qu'il présente ensuite au serveur pour prouver sa connaissance d'une clé partagée. Le jeton émis apparaît au niveau de la couche SOAP sous la forme d'un jeton de prise en charge d'endossement ou d'un jeton de porteur ; autrement dit, un jeton qui signe la signature de message. Le service est authentifié à l'aide d'un certificat X.509. L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 Avec ce mode d'authentification, le client ne s'authentifie pas au service en tant que tel. Au lieu de cela, il s'authentifie à un service de jeton de sécurité et reçoit un jeton SAML, qu'il présente ensuite au serveur pour prouver sa connaissance d'une clé partagée. Le jeton émis apparaît au niveau de la couche SOAP sous la forme d'un jeton de prise en charge d'endossement ou d'un jeton de porteur ; autrement dit, un jeton qui signe la signature de message. Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport. L'élément de liaison de sécurité est un `TransportSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Kerberos  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un ticket Kerberos. Ce même ticket fournit également l'authentification de serveur. L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `Kerberos`.  
  
> [!NOTE]
> Pour utiliser ce mode d'authentification, le compte de service doit être associé à un SPN (Service Principal Name, nom de principal du service). Pour ce faire, exécutez le service sous les comptes SERVICE RÉSEAU ou SYSTÈME LOCAL. Utilisez également l'outil SetSpn.exe pour créer un SPN pour le compte de service. Dans les deux cas, le client doit utiliser le SPN correct dans l' [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) élément, ou à l’aide du <xref:System.ServiceModel.EndpointAddress> constructeur. Pour plus d’informations, consultez [identité du service et authentification](service-identity-and-authentication.md).  
  
> [!NOTE]
> Lorsque le mode d'authentification `Kerberos` est utilisé, les niveaux d'emprunt d'identité <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> et <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> ne sont pas pris en charge.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un ticket Kerberos. Le jeton Kerberos apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message. Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport. L'élément de liaison de sécurité est un `TransportSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `KerberosOverTransport`.  
  
> [!NOTE]
> Pour utiliser ce mode d'authentification, le compte de service doit être associé à un SPN. Pour ce faire, exécutez le service sous les comptes SERVICE RÉSEAU ou SYSTÈME LOCAL. Utilisez également l'outil SetSpn.exe pour créer un SPN pour le compte de service. Dans les deux cas, le client doit utiliser le SPN correct dans l' [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) élément, ou à l’aide du <xref:System.ServiceModel.EndpointAddress> constructeur. Pour plus d’informations, consultez [identité du service et authentification](service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message. Le service est également authentifié à l'aide d'un certificat X.509. L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message. Le service est également authentifié à l'aide d'un certificat X.509. La liaison est un `AsymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `MutualCertificateDuplex`.  
  
### <a name="mutualsslnegotiated"></a>MutualSslNegotiated  
 Avec ce mode d'authentification, le client et le service s'authentifient à l'aide de certificats X.509. L’élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> lorsqu’une valeur de `true` est passée pour le premier paramètre. Vous pouvez également affecter `authenticationMode` à l'attribut `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>. Cette méthode prend <xref:System.ServiceModel.Channels.SecurityBindingElement> comme paramètre, qui est utilisé pendant l'initialisation pour établir la session sécurisée. Vous pouvez également affecter `authenticationMode` à l'attribut `SecureConversation`.  
  
 Si aucune liaison de démarrage n’est spécifiée, le mode d’authentification `SspiNegotiated` est utilisé pour le démarrage.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 Avec ce mode d'authentification, un protocole de négociation est utilisé pour effectuer l'authentification du client et du serveur. Kerberos est dans la mesure du possible utilisé, sinon c'est NTLM (NT LanMan). L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 Avec ce mode d'authentification, un protocole de négociation est utilisé pour effectuer l'authentification du client et du serveur. Le protocole Kerberos est dans la mesure du possible utilisé, sinon c'est NTLM. Le jeton résultant apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message. Le service est en outre authentifié au niveau de la couche de transport par un certificat X.509. L'élément de liaison de sécurité est un `TransportSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé ; autrement dit, un jeton signé par la signature de message. Le service s'authentifie auprès du client à l'aide d'un certificat X.509. L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `UserNameForCertificate`.  
  
 Pour le mode d'authentification `UserNameForCertificate`, le client et le service doivent tous deux utiliser WS-Security 1.1.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé ; autrement dit, un jeton signé par la signature de message. Le service est authentifié à l'aide d'un certificat X.509. L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé ; autrement dit, un jeton signé par la signature de message. Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport. L'élément de liaison de sécurité est un `TransportSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A>. Vous pouvez également affecter `authenticationMode` à l'attribut `UserNameOverTransport`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
