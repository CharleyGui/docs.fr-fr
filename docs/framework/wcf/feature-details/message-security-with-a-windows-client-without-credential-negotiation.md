---
title: Sécurité de message avec un client Windows sans négociation d'informations d'identification
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 0e4ac18d4c5835f3bd0539f2a79d68b59860b6e6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637937"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Sécurité de message avec un client Windows sans négociation d'informations d'identification
Le scénario suivant montre un client Windows Communication Foundation (WCF) et le service sécurisé par le protocole Kerberos.  
  
 Le service et le client appartiennent au même domaine ou domaines approuvés.  
  
> [!NOTE]
>  La différence entre ce scénario et [sécurité de Message avec un Client Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) est que ce scénario ne négocie pas les informations d’identification de service avec le service avant d’envoyer le message de l’application. En outre, comme cette opération requiert le protocole Kerberos, ce scénario requiert un environnement de domaine Windows.  
  
 ![Sécurité sans négociation d’informations d’identification de message](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Mode de sécurité|Message|  
|Interopérabilité|Oui, WS-Security avec des clients compatibles avec le profil de jeton Kerberos|  
|Authentification (serveur)|Authentification mutuelle du serveur et du client|  
|Authentification (client)|Authentification mutuelle du serveur et du client|  
|Intégrité|Oui|  
|Confidentialité|Oui|  
|Transport|HTTP|  
|Liaison|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Service  
 La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment. Effectuez l’une des opérations suivantes :  
  
- Créez un service autonome à l'aide du code sans configuration.  
  
- Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.  
  
### <a name="code"></a>Code  
 Le code ci-dessous crée un point de terminaison de service qui utilise la sécurité de message. Le code désactive la négociation des informations d'identification du service, et l'établissement d'un jeton de contexte de sécurité (SCT).  
  
> [!NOTE]
>  Pour utiliser le type d'informations d'identification Windows sans négociation, le compte d'utilisateur du service doit avoir accès au nom de principal du service (SPN) enregistré avec le domaine Active Directory. Pour cela, deux solutions s'offrent à vous :  
  
1. Utilisez le compte `NetworkService` ou `LocalSystem` pour exécuter votre service. Étant donné que ces comptes ont accès à l’ordinateur SPN établi lorsque l’ordinateur rejoint le domaine Active Directory, WCF génère automatiquement l’élément SPN approprié à l’intérieur du point de terminaison du service dans les métadonnées du service (Web Services Description Language ou WSDL).  
  
2. Utilisez un compte de domaine Active Directory arbitraire pour exécuter votre service. Dans ce cas, vous devez établir un nom de principal du service pour ce compte de domaine. Une façon de procéder consiste à faire appel à l'utilitaire Setspn.exe. Une fois que le SPN est créé pour le compte du service, configurez WCF pour publier ce SPN sur les clients du service via ses métadonnées (WSDL). Cette opération s'effectue en définissant l'identité de point de terminaison pour le point de terminaison exposé, par le biais d'un fichier de configuration de l'application ou du code. L'exemple suivant publie l'identité par programme.  
  
 Pour plus d’informations sur les SPN, le protocole Kerberos et Active Directory, consultez [Kerberos Technical Supplement pour Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Pour plus d’informations sur les identités de point de terminaison, consultez [Modes d’authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Configuration  
 La configuration ci-dessous peut être utilisée à la place du code.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="KerberosBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator"   
                  listenUri="net.tcp://localhost/metadata" >  
         <identity>  
            <servicePrincipalName value="service_spn_name" />  
         </identity>  
        </endpoint>  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="KerberosBinding">  
          <security>  
            <message negotiateServiceCredential="false"   
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Client  
 La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment. Effectuez l’une des opérations suivantes :  
  
- Créez un client autonome à l'aide du code (et du code client).  
  
- Créez un client qui ne définit pas d'adresse de point de terminaison. Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument. Exemple :  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Code  
 Le code ci-dessous configure le client. Le mode de sécurité a la valeur Message, et le type d'informations d'identification du client a la valeur Windows. Notez que les propriétés <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> et <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> ont la valeur `false`.  
  
> [!NOTE]
>  Pour utiliser le type d'informations d'identification Windows sans négociation, le client doit être configuré avec le compte SPN du service avant de commencer la communication avec le service. Le client utilise le nom de principal du service pour obtenir le jeton Kerberos afin d'authentifier et de sécuriser la communication avec le service. L'exemple suivant montre comment configurer le client avec le nom principal du service. Si vous utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le client, le SPN du service sera propagé automatiquement au client à partir des métadonnées du service (WSDL), si les métadonnées du service contient Ces informations. Pour plus d’informations sur la façon de configurer le service pour inclure son SPN dans les métadonnées du service, consultez la section « Service » plus loin dans cette rubrique.  
>   
>  Pour plus d’informations sur les SPN, Kerberos et Active Directory, consultez [Kerberos Technical Supplement pour Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Pour plus d’informations sur les identités de point de terminaison, consultez [Modes d’authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) rubrique.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Configuration  
 Le code ci-dessous configure le client. Notez que le [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) doit être défini pour faire correspondre le SPN du service enregistré pour le compte du service dans le domaine Active Directory.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Windows"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <servicePrincipalName value="service_spn_name" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Identité du service et authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Modèle de sécurité pour Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
