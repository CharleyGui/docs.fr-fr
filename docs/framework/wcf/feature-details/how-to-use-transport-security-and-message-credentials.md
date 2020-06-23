---
title: "Comment : utiliser des informations d'identification de sécurité de transport et de message"
description: Apprenez à implémenter la sécurité de transport avec les informations d’identification de message, qui offre le meilleur des modes de transport et de sécurité des messages dans WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246647"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Comment : utiliser des informations d'identification de sécurité de transport et de message
La sécurisation d’un service avec les informations d’identification de transport et de message utilise le meilleur des modes de sécurité de transport et de message dans Windows Communication Foundation (WCF). En résumé, la sécurité de la couche de transport assure l'intégrité et la confidentialité des informations tandis que la sécurité de la couche de message offre diverses informations d'identification, lesquelles ne sont pas disponibles lorsque seule la sécurité de niveau transport est utilisée. Cette rubrique contient la procédure par étape permettant d’implémenter la sécurité de transport avec les informations d’identification de message à l’aide des liaisons <xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.NetTcpBinding>. Pour plus d’informations sur la définition du mode de sécurité, consultez [Comment : définir le mode de sécurité](../how-to-set-the-security-mode.md).  
  
 Lorsque vous affectez au mode de sécurité la valeur `TransportWithMessageCredential`, le mécanisme chargé d'offrir la sécurité de niveau transport dépend du transport utilisé. Pour le transport HTTP, le mécanisme utilisé est Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire HTTPS, pour le transport TCP, il s'agit de SSL sur TCP ou de Windows.  
  
 Si le transport correspond à HTTP (à l'aide de la liaison <xref:System.ServiceModel.WSHttpBinding>), la sécurité de niveau transport est assurée par SSL sur HTTP. Dans ce cas, vous devez configurer l’ordinateur hébergeant le service en attribuant un certificat SSL à l’un de ses ports, comme indiqué ci-après dans cette rubrique.  
  
 Si le transport correspond à TCP (à l'aide de la liaison <xref:System.ServiceModel.NetTcpBinding>), la sécurité de niveau transport est assurée par la sécurité Windows ou par SSL sur TCP. Lorsque vous utilisez la sécurité SSL sur TCP, vous devez spécifier le certificat à l'aide de la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>, comme indiqué ci-après dans cette rubrique.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Pour utiliser la liaison WSHttpBinding avec un certificat pour la sécurité de niveau transport (dans le code)  
  
1. Utilisez l’outil HttpCfg.exe pour attribuer un certificat SSL à l’un des ports de l’ordinateur. Pour plus d’informations, consultez [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2. Créez une instance de la classe <xref:System.ServiceModel.WSHttpBinding>, puis affectez à la propriété <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> la valeur <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3. Affectez à la propriété <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> une valeur appropriée. (Pour plus d’informations, consultez [sélection d’un type d’informations d’identification](selecting-a-credential-type.md).) Le code suivant utilise la <xref:System.ServiceModel.MessageCredentialType.Certificate> valeur.  
  
4. Créez une instance de la classe <xref:System.Uri> en utilisant une adresse de base appropriée. Remarque : cette adresse doit utiliser le schéma HTTPS et contenir le véritable nom de l’ordinateur ainsi que le numéro de port auquel le certificat SSL a été attribué. Vous pouvez également définir l'adresse de base dans la configuration.  
  
5. Ajoutez un point de terminaison de service à l'aide de la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
6. Créez une instance de <xref:System.ServiceModel.ServiceHost>, puis appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A>, comme illustré dans l'exemple de code suivant.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Pour utiliser la liaison NetTcpBinding avec un certificat pour la sécurité de niveau transport (dans le code)  
  
1. Créez une instance de la classe <xref:System.ServiceModel.NetTcpBinding>, puis affectez à la propriété <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> la valeur <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2. Affectez à la propriété <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> une valeur appropriée. Dans l'exemple de code suivant, la valeur <xref:System.ServiceModel.MessageCredentialType.Certificate> est utilisée.  
  
3. Créez une instance de la classe <xref:System.Uri> en utilisant une adresse de base appropriée. Remarque : cette adresse doit utiliser le schéma « net.tcp ». Vous pouvez également définir l'adresse de base dans la configuration.  
  
4. Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>.  
  
5. Utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> pour définir de manière explicite le certificat X.509 de ce service.  
  
6. Ajoutez un point de terminaison de service à l'aide de la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
7. Appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A>, comme illustré dans le code suivant :  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Pour utiliser la liaison NetTcpBinding avec Windows comme sécurité de transport (dans le code)  
  
1. Créez une instance de la classe <xref:System.ServiceModel.NetTcpBinding>, puis affectez à la propriété <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> la valeur <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2. Configurez la sécurité de transport sur Windows en affectant à la propriété <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> la valeur <xref:System.ServiceModel.TcpClientCredentialType.Windows>. Remarque : il s'agit de la valeur par défaut.  
  
3. Affectez à la propriété <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> une valeur appropriée. Dans l'exemple de code suivant, la valeur <xref:System.ServiceModel.MessageCredentialType.Certificate> est utilisée.  
  
4. Créez une instance de la classe <xref:System.Uri> en utilisant une adresse de base appropriée. Remarque : cette adresse doit utiliser le schéma « net.tcp ». Vous pouvez également définir l'adresse de base dans la configuration.  
  
5. Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>.  
  
6. Utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> pour définir de manière explicite le certificat X.509 de ce service.  
  
7. Ajoutez un point de terminaison de service à l'aide de la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
8. Appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A>, comme illustré dans le code suivant :  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Utilisation de la configuration  
  
#### <a name="to-use-the-wshttpbinding"></a>Pour utiliser la liaison WSHttpBinding  
  
1. Configurez l’ordinateur en attribuant un certificat SSL à l’un de ses ports. (Pour plus d’informations, consultez [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md)). Vous n’avez pas besoin de définir une `transport` valeur d’élément <> avec cette configuration.  
  
2. Spécifiez le type d'informations d'identification pour la sécurité de niveau message. L’exemple suivant affecte la `clientCredentialType` valeur à l’attribut de l' `message` élément <> `UserName` .  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Pour utiliser la liaison NetTcpBinding avec un certificat pour la sécurité de transport  
  
1. Pour la sécurité SSL sur TCP, vous devez spécifier de manière explicite le certificat dans l'élément `<behaviors>`. Dans l'exemple suivant, le certificat spécifié est publié par un émetteur figurant dans l'emplacement de magasin par défaut (ordinateur local et magasins personnels).  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Ajoutez un [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) à la section Bindings.  
  
3. Ajoutez un élément de liaison, puis affectez à l’attribut `name` une valeur adéquate.  
  
4. Ajoutez un `security` élément <> et affectez à l’attribut la valeur `mode` `TransportWithMessageCredential` .  
  
5. Ajoutez un `message>` élément <et affectez `clientCredentialType` à l’attribut une valeur appropriée.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Pour utiliser la liaison NetTcpBinding avec Windows comme sécurité de transport  
  
1. Ajoutez un [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) à la section Bindings,  
  
2. Ajoutez un `binding` élément <> et affectez `name` à l’attribut une valeur appropriée.  
  
3. Ajoutez un `security` élément <> et affectez à l’attribut la valeur `mode` `TransportWithMessageCredential` .  
  
4. Ajoutez un `transport` élément <> et affectez `clientCredentialType` à l’attribut la valeur `Windows` .  
  
5. Ajoutez un `message` élément <> et affectez `clientCredentialType` à l’attribut une valeur appropriée. Dans l'exemple de code suivant, un certificat est affecté à la valeur.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Comment : définir le mode de sécurité](../how-to-set-the-security-mode.md)
- [Sécurisation de services](../securing-services.md)
- [Securing Services and Clients](securing-services-and-clients.md)
