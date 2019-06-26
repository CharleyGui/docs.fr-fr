---
title: Vue d'ensemble de la sécurité des transports
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 450d10c0356a8c22741275e2c1e1a842c1fd4627
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402052"
---
# <a name="transport-security-overview"></a>Vue d'ensemble de la sécurité des transports
Mécanismes de sécurité de transport dans Windows Communication Foundation (WCF) dépendent de la liaison et le transport utilisé. Par exemple, lors de l'utilisation de la classe <xref:System.ServiceModel.WSHttpBinding>, le transport correspond à HTTP et le mécanisme principal utilisé pour sécuriser ce transport correspond à SSL (Secure Sockets Layer) sur HTTP, c'est-à-dire à HTTPS. Cette rubrique décrit les mécanismes de sécurité de transport principales utilisées dans les liaisons fournies par le système WCF.  
  
> [!NOTE]
>  Lors de la sécurité SSL est utilisée avec le .NET Framework 3.5 et versions ultérieures un client WCF utilise les deux les certificats intermédiaires dans son magasin de certificats et les certificats intermédiaires reçus au cours de la négociation SSL pour effectuer la validation de chaîne de certificats sur le service certificat. .NET Framework 3.0 n'utilise que les certificats intermédiaires installés dans le magasin de certificats local.  
  
> [!WARNING]
>  Si la sécurité de transport est utilisée, la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> peut être remplacée. Pour éviter cela, affectez la <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> à <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> est un comportement de service qui peut être défini dans la description du service.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Par défaut, la classe <xref:System.ServiceModel.BasicHttpBinding> n'offre aucune sécurité. Cette liaison est conçue pour assurer l’interopérabilité avec les fournisseurs de services Web, lesquels n’implémentent pas de sécurité. Vous pouvez toutefois activer la sécurité en affectant à la propriété <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> toutes valeurs autres que <xref:System.ServiceModel.BasicHttpSecurityMode.None>. Pour activer la sécurité du transport, affectez à la propriété la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
### <a name="interoperation-with-iis"></a>Interaction avec IIS  
 La classe <xref:System.ServiceModel.BasicHttpBinding> est utilisée principalement pour interagir avec les services Web existants, hébergés pour un grand nombre d'entre eux par les services Internet (IIS). C'est pourquoi la sécurité de transport de cette liaison est conçue pour interagir de façon transparente avec les sites IIS. Pour permettre cette interaction, il suffit d'affecter au mode de sécurité <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>, puis de définir le type d'informations d'identification du client. Les valeurs de ce type correspondent aux mécanismes de sécurité du répertoire IIS. Dans l'exemple de code suivant, le mode est en cours de définition et la valeur Windows est affectée au type d'informations d'identification. Vous pouvez utiliser cette configuration lorsque le client et le serveur figurent tous les deux dans le même domaine Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Ou dans la configuration :  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Les sections suivantes abordent d'autres types d'informations d'identification.  
  
#### <a name="basic"></a>Basic  
 Il s'agit de la méthode d'authentification de base dans IIS. Lorsque ce mode est utilisé, le serveur IIS doit être configuré avec des comptes utilisateur Windows et les autorisations de système de fichiers NTFS adéquates. Pour plus d’informations sur IIS 6.0, consultez [l’activation de l’authentification de base et la configuration du nom de domaine](https://go.microsoft.com/fwlink/?LinkId=88592). Pour plus d’informations sur [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [IIS 7.0 Beta : Configurer l’authentification de base](https://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>Certificat  
 Sur les services IIS, une option permet de spécifier que les clients doivent se connecter en utilisant un certificat. Cette fonctionnalité permet également aux services IIS de mapper les certificats clients aux comptes Windows correspondants. Pour plus d’informations sur IIS 6.0, consultez [activation des certificats Client dans IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88594). Pour plus d’informations sur [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [IIS 7.0 Beta : Configuration des certificats de serveur dans IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>Digest  
 L'authentification Digest s'apparente à l'authentification de base tout en présentant l'avantage supplémentaire de permettre l'envoi des informations d'identification dans un texte haché plutôt qu'en texte clair. Pour plus d’informations sur IIS 6.0, consultez [l’authentification Digest dans IIS 6.0](https://go.microsoft.com/fwlink/?LinkID=88443). Pour plus d’informations sur [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [IIS 7.0 Beta : Configurer l’authentification Digest](https://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 Il s'agit de l'authentification Windows intégrée à IIS. Lorsque ce mode d'authentification est activé, le serveur doit également figurer dans un domaine Windows utilisant le protocole Kerberos comme contrôleur. Dans le cas contraire ou si le système Kerberos connaît une défaillance, vous pouvez utiliser l'authentification NT LAN Manager (NTLM), abordée dans la section suivante. Pour plus d’informations sur IIS 6.0, consultez [l’authentification Windows intégrée dans IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88597). Pour plus d’informations sur [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [IIS 7.0 Beta : Configuration des certificats de serveur dans IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>NTLM  
 Cela permet au serveur d'utiliser NTLM pour l'authentification si le fournisseur Kerberos échoue. Pour plus d’informations sur la configuration d’IIS dans IIS 6.0, consultez [forcer l’authentification NTLM](https://go.microsoft.com/fwlink/?LinkId=88598). Pour [!INCLUDE[iisver](../../../../includes/iisver-md.md)], l'authentification Windows intègre l'authentification NTLM. Pour plus d’informations, consultez [IIS 7.0 Beta : Configuration des certificats de serveur dans IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 La classe <xref:System.ServiceModel.WSHttpBinding> est conçue pour interagir avec les services qui implémentent les spécifications WS-*. La sécurité de transport de cette liaison correspond à Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire à HTTPS. Pour créer une application WCF qui utilise le protocole SSL, utilisez IIS pour héberger l’application. Si vous créez une application auto-hébergée, vous pouvez également utiliser l'outil HttpCfg.exe afin d'attribuer un certificat X.509 à un port spécifique de l'ordinateur. Le numéro de port est spécifié en tant que partie de l’application WCF comme une adresse de point de terminaison. Lorsqu'un mode de transport est utilisé, l'adresse de point de terminaison doit comporter le protocole HTTPS. Dans le cas contraire, une exception sera levée pendant l'exécution. Pour plus d’informations, consultez [sécurité du Transport HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pour l'authentification client, affectez à la propriété <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> de la classe <xref:System.ServiceModel.HttpTransportSecurity> l'une des valeurs d'énumération <xref:System.ServiceModel.HttpClientCredentialType>. Les valeurs d'énumération sont identiques aux types d'informations d'identification client pour <xref:System.ServiceModel.BasicHttpBinding> et sont conçues pour être hébergées dans les services IIS.  
  
 Dans l'exemple suivant, une liaison est utilisée avec un type d'informations d'identification client de Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Cette liaison offre uniquement une sécurité de niveau message et non une sécurité de niveau transport.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 La classe <xref:System.ServiceModel.NetTcpBinding> utilise le transport TCP pour les messages. La sécurité de niveau transport est assurée par l'implémentation de la sécurité Transport Layer Security (TLS) sur TCP. L'implémentation TLS est assurée par le système d'exploitation.  
  
 Vous pouvez également spécifier le type d'informations d'identification client en affectant à la propriété <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> de la classe <xref:System.ServiceModel.TcpTransportSecurity> l'une des valeurs <xref:System.ServiceModel.TcpClientCredentialType>, comme illustré dans l'exemple de code suivant.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Client  
 Côté client, vous devez spécifier un certificat à l'aide de la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.  
  
> [!NOTE]
>  Si vous utilisez la sécurité Windows, aucun certificat n'est requis.  
  
 Le code suivant utilise l'empreinte numérique de certificat, propre à chaque certificat. Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Vous pouvez également spécifier un certificat dans la configuration du client à l’aide un [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) élément dans la section des comportements.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 La classe <xref:System.ServiceModel.NetNamedPipeBinding> est conçue pour assurer une communication interne efficace au sein des ordinateurs, c'est-à-dire entre les processus s'exécutant sur les mêmes ordinateurs, bien qu'il soit possible de créer des canaux nommés entre deux ordinateurs figurant sur le même réseau. Cette liaison offre uniquement une sécurité de niveau transport. Lorsque des applications sont créées à l’aide de cette liaison, les adresses de point de terminaison doivent comporter « net.pipe » dans leur protocole.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Lorsqu'un transport de sécurité est utilisé, cette liaison utilise SSL sur HTTP, c'est-à-dire HTTPS avec un jeton émis (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Pour plus d’informations sur les applications de fédération, consultez [fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 La classe <xref:System.ServiceModel.NetPeerTcpBinding> correspond à un transport sécurisé, conçu pour assurer une communication efficace à l’aide de la fonctionnalité de réseau pair à pair. Comme indiqué par le nom de la classe et de la liaison, TCP correspond au protocole. Lorsque le mode de sécurité a la valeur transport, la liaison implémente TLS sur TCP. Pour plus d’informations sur la fonctionnalité de peer-to-peer, consultez [mise en réseau Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding et NetMsmqBinding  
 Pour une description complète du transport de sécurité avec Message Queuing (précédemment appelé MSMQ), consultez [sécurisation des Messages à l’aide de sécurité du Transport](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Voir aussi

- [Programmation de la sécurité dans WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
