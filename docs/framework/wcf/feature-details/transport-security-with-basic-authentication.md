---
title: Sécurité de transport avec l'authentification de base
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: eace5ce9a84d99cb2526896cca36a9e2a13fd5f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742699"
---
# <a name="transport-security-with-basic-authentication"></a>Sécurité de transport avec l'authentification de base
L’illustration suivante montre un service et un client Windows Communication Foundation (WCF). Le serveur nécessite un certificat X.509 valide qui peut être utilisé pour SSL (Secure Sockets Layer) et les clients doivent approuver le certificat du serveur. De plus, le service Web contient déjà une implémentation SSL disponible. Pour plus d’informations sur l’activation de l’authentification de base sur les Internet Information Services (IIS), consultez <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.  
  
 ![Capture d’écran montrant la sécurité de transport avec l’authentification de base.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Mode de sécurité|Transport|  
|Interopérabilité|Avec les clients de service Web et les services existants|  
|Authentification (serveur)<br /><br /> Authentification (client)|Oui (à l'aide de HTTPS)<br /><br /> Oui (à l'aide du Nom d'utilisateur/Mot de passe)|  
|Intégrité|Oui|  
|Confidentialité|Oui|  
|Transport|HTTPS|  
|Liaison|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Service  
 La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment. Effectuez l'une des opérations suivantes :  
  
- Créez un service autonome à l'aide du code sans configuration.  
  
- Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.  
  
### <a name="code"></a>Code  
 Le code suivant montre comment créer un point de terminaison de service qui utilise un nom d'utilisateur de domaine et un mot de passe Windows pour la sécurité de transfert. Notez que le service requiert un certificat X.509 pour s'authentifier auprès du client. Pour plus d’informations, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) et [procédure : configurer un port avec un certificat SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Configuration  
 Les éléments suivants configurent un service pour utiliser l'authentification de base avec la sécurité au niveau du transport :  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Client  
  
### <a name="code"></a>Code  
 Le code suivant affiche le code client qui inclut le nom d'utilisateur et le mot de passe. Notez que l'utilisateur doit fournir un nom d'utilisateur et un mot de passe Windows valides. Le code pour retourner le nom d'utilisateur et le mot de passe n'est pas indiqué. Utilisez une boîte de dialogue ou une autre interface pour demander les informations à l'utilisateur.  
  
> [!NOTE]
> Le nom d'utilisateur et le mot de passe peuvent être définis uniquement à l'aide de code.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Configuration  
 Le code suivant affiche la configuration du client.  
  
> [!NOTE]
> Vous ne pouvez pas utiliser la configuration pour définir le nom d'utilisateur et le mot de passe. La configuration indiquée ici doit être augmentée à l'aide du code pour définir le nom d'utilisateur et le mot de passe.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Guide pratique pour configurer un port avec un certificat SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Vue d’ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- [Modèle de sécurité pour Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
