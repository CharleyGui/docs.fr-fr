---
title: Vue d'ensemble de la sécurité des transports
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 5c6b6389122b32ed8db701020a8c13ba17225867
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585686"
---
# <a name="transport-security-overview"></a>Vue d'ensemble de la sécurité des transports
Les mécanismes de sécurité de transport dans Windows Communication Foundation (WCF) dépendent de la liaison et du transport utilisés. Par exemple, lors de l'utilisation de la classe <xref:System.ServiceModel.WSHttpBinding>, le transport correspond à HTTP et le mécanisme principal utilisé pour sécuriser ce transport correspond à SSL (Secure Sockets Layer) sur HTTP, c'est-à-dire à HTTPS. Cette rubrique présente les principaux mécanismes de sécurité de transport utilisés dans les liaisons fournies par le système WCF.  
  
> [!NOTE]
> Lorsque la sécurité SSL est utilisée avec .NET Framework 3,5 et versions ultérieures, un client WCF utilise à la fois les certificats intermédiaires dans son magasin de certificats et les certificats intermédiaires reçus pendant la négociation SSL pour effectuer la validation de la chaîne de certificats sur le certificat du service. .NET Framework 3.0 n'utilise que les certificats intermédiaires installés dans le magasin de certificats local.  
  
> [!WARNING]
> Si la sécurité de transport est utilisée, la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> peut être remplacée. Pour éviter ce problème, affectez <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> à la valeur <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType> . <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> est un comportement de service qui peut être défini dans la description du service.  
  
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
  
#### <a name="basic"></a>De base  
 Il s'agit de la méthode d'authentification de base dans IIS. Lorsque ce mode est utilisé, le serveur IIS doit être configuré avec des comptes utilisateur Windows et les autorisations de système de fichiers NTFS adéquates. Pour plus d’informations sur IIS 6,0, voir activation de l' [authentification de base et configuration du nom de domaine](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10)). Pour plus d’informations sur IIS 7,0, voir [configurer l’authentification de base (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10)).  
  
#### <a name="certificate"></a>Certificat  
 Sur les services IIS, une option permet de spécifier que les clients doivent se connecter en utilisant un certificat. Cette fonctionnalité permet également aux services IIS de mapper les certificats clients aux comptes Windows correspondants. Pour plus d’informations sur IIS 6,0, voir [activation de certificats clients dans iis 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10)). Pour plus d’informations sur IIS 7,0, voir [Configuration des certificats de serveur dans IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="digest"></a>Digest  
 L'authentification Digest s'apparente à l'authentification de base tout en présentant l'avantage supplémentaire de permettre l'envoi des informations d'identification dans un texte haché plutôt qu'en texte clair. Pour plus d’informations sur IIS 6,0, consultez [authentification Digest dans iis 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)). Pour plus d’informations sur IIS 7,0, consultez [configurer l’authentification Digest (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10)).  
  
#### <a name="windows"></a>Windows  
 Il s'agit de l'authentification Windows intégrée à IIS. Lorsque ce mode d'authentification est activé, le serveur doit également figurer dans un domaine Windows utilisant le protocole Kerberos comme contrôleur. Dans le cas contraire ou si le système Kerberos connaît une défaillance, vous pouvez utiliser l'authentification NT LAN Manager (NTLM), abordée dans la section suivante. Pour plus d’informations sur IIS 6,0, voir [authentification Windows intégrée dans iis 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10)). Pour plus d’informations sur IIS 7,0, voir [Configuration des certificats de serveur dans IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
#### <a name="ntlm"></a>NTLM  
 Cela permet au serveur d'utiliser NTLM pour l'authentification si le fournisseur Kerberos échoue. Pour plus d’informations sur la configuration d’IIS dans IIS 6,0, consultez la page [forcer l’authentification NTLM](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10)). Pour IIS 7,0, l’authentification Windows comprend l’authentification NTLM. Pour plus d'informations, consultez [Configuration des certificats de serveur dans IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 La classe <xref:System.ServiceModel.WSHttpBinding> est conçue pour interagir avec les services qui implémentent les spécifications WS-*. La sécurité de transport de cette liaison correspond à Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire à HTTPS. Pour créer une application WCF qui utilise SSL, utilisez IIS pour héberger l’application. Si vous créez une application auto-hébergée, vous pouvez également utiliser l'outil HttpCfg.exe afin d'attribuer un certificat X.509 à un port spécifique de l'ordinateur. Le numéro de port est spécifié dans le cadre de l’application WCF sous la forme d’une adresse de point de terminaison. Lorsqu'un mode de transport est utilisé, l'adresse de point de terminaison doit comporter le protocole HTTPS. Dans le cas contraire, une exception sera levée pendant l'exécution. Pour plus d’informations, consultez [sécurité du transport http](http-transport-security.md).  
  
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
> Si vous utilisez la sécurité Windows, aucun certificat n'est requis.  
  
 Le code suivant utilise l'empreinte numérique de certificat, propre à chaque certificat. Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Vous pouvez également spécifier le certificat dans la configuration du client à l’aide d’un [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) élément dans la section comportements.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"
      storeLocation="LocalMachine" storeName="My"
      X509FindType="FindByThumbPrint">  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 La classe <xref:System.ServiceModel.NetNamedPipeBinding> est conçue pour assurer une communication interne efficace au sein des ordinateurs, c'est-à-dire entre les processus s'exécutant sur les mêmes ordinateurs, bien qu'il soit possible de créer des canaux nommés entre deux ordinateurs figurant sur le même réseau. Cette liaison offre uniquement une sécurité de niveau transport. Lorsque des applications sont créées à l’aide de cette liaison, les adresses de point de terminaison doivent comporter « net.pipe » dans leur protocole.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Lorsqu'un transport de sécurité est utilisé, cette liaison utilise SSL sur HTTP, c'est-à-dire HTTPS avec un jeton émis (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Pour plus d’informations sur les applications de Fédération, consultez [Fédération et jetons émis](federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 La classe <xref:System.ServiceModel.NetPeerTcpBinding> correspond à un transport sécurisé, conçu pour assurer une communication efficace à l’aide de la fonctionnalité de réseau pair à pair. Comme indiqué par le nom de la classe et de la liaison, TCP correspond au protocole. Lorsque le mode de sécurité a la valeur transport, la liaison implémente TLS sur TCP. Pour plus d’informations sur la fonctionnalité d’égal à égal, consultez [mise en réseau pair à pair](peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding et NetMsmqBinding  
 Pour une description complète de la sécurité de transport avec Message Queuing (précédemment appelé MSMQ), consultez [sécurisation des messages à l’aide](securing-messages-using-transport-security.md)de la sécurité de transport.  
  
## <a name="see-also"></a>Voir aussi

- [Programmation de la sécurité dans WCF](programming-wcf-security.md)
