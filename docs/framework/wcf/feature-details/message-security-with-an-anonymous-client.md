---
title: Sécurité de message avec un client anonyme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: aed56be359f094db483ab1d012bd77a1096433b6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553764"
---
# <a name="message-security-with-an-anonymous-client"></a>Sécurité de message avec un client anonyme

Le scénario suivant montre un client et un service sécurisés par Windows Communication Foundation (WCF) la sécurité des messages. L'un des objectifs de conception consiste à utiliser la sécurité de message plutôt que la sécurité de transport, afin qu'à l'avenir il puisse prendre en charge un modèle plus riche basé sur les revendications. Pour plus d’informations sur l’utilisation de revendications riches pour l’autorisation, consultez [gestion des revendications et autorisation avec le modèle d’identité](managing-claims-and-authorization-with-the-identity-model.md).

Pour obtenir un exemple d’application, consultez [sécurité de message anonyme](../samples/message-security-anonymous.md).

![Sécurité des messages avec un client anonyme](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")

|Caractéristique|Description|
|--------------------|-----------------|
|Mode de sécurité|Message|
|Interopérabilité|WCF uniquement|
|Authentification (serveur)|La négociation initiale requiert l'authentification du serveur, mais pas l'authentification du client|
|Authentification (client)|None|
|Intégrité|Oui, à l'aide du contexte de sécurité partagé|
|Confidentialité|Oui, à l'aide du contexte de sécurité partagé|
|Transport|HTTP|

## <a name="service"></a>Service

La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment. Effectuez l’une des actions suivantes :

- Créez un service autonome à l'aide du code sans configuration.

- Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.

### <a name="code"></a>Code

Le code suivant montre comment créer un point de terminaison de service qui utilise la sécurité de message.

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a>Configuration

La configuration ci-dessous peut être utilisée à la place du code. L'élément de comportement du service est utilisé pour spécifier un certificat servant à authentifier le service auprès du client. L'élément de service doit spécifier le comportement à l'aide de l'attribut `behaviorConfiguration`. L’élément de liaison spécifie que le type d’informations d’identification du client est `None`, ce qui permet aux clients anonymes d’utiliser le service.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a>Client

La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment. Effectuez l’une des actions suivantes :

- Créez un client autonome à l'aide du code (et du code client).

- Créez un client qui ne définit pas d'adresse de point de terminaison. Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument. Exemple :

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Code

Le code suivant crée une instance du client. La liaison utilise le mode de sécurité au niveau du message, et le type d’informations d’identification du client a la valeur Aucun.

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a>Configuration

Le code ci-dessous configure le client.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Présentation de la sécurité](security-overview.md)
- [Sécurité des applications distribuées](distributed-application-security.md)
- [Message Security Anonymous](../samples/message-security-anonymous.md)
- [Identité du service et authentification](service-identity-and-authentication.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
