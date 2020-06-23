---
title: Sécurité de transport avec un client anonyme
description: Passez en revue ce scénario WCF, qui utilise la sécurité de transport pour authentifier un serveur à l’aide d’un certificat approuvé par le client. Le client n’est pas authentifié.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 08cfb8c1a5581f17a251224430018764bed80b0f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245009"
---
# <a name="transport-security-with-an-anonymous-client"></a>Sécurité de transport avec un client anonyme

Ce scénario de Windows Communication Foundation (WCF) utilise la sécurité de transport (HTTPs) pour garantir la confidentialité et l’intégrité. Le serveur doit être authentifié à l'aide d'un certificat SSL (Secure Sockets Layer). Les clients doivent ensuite faire confiance à ce certificat. Aucun mécanisme n'authentifie les clients, ceux-ci restent donc anonymes.

Pour obtenir un exemple d’application, consultez la page relative à la [sécurité du transport WS](../samples/ws-transport-security.md). Pour plus d’informations sur la sécurité du transport, consultez [vue d’ensemble de la sécurité du transport](transport-security-overview.md).

Pour plus d’informations sur l’utilisation d’un certificat avec un service, consultez [utilisation des certificats](working-with-certificates.md) et [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

![Utilisation de la sécurité de transport avec un client anonyme](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|Caractéristique|Description|
|--------------------|-----------------|
|Mode de sécurité|Transport|
|Interopérabilité|Avec les services Web et les clients existants|
|Authentification (serveur)<br /><br /> Authentification (client)|Yes<br /><br /> Niveau de l’application (aucune prise en charge WCF)|
|Intégrité|Yes|
|Confidentialité|Yes|
|Transport|HTTPS|
|Liaison|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a>Service

La configuration et le code ci-dessous sont conçus pour s'exécuter indépendamment. Effectuez l’une des actions suivantes :

- Créez un service autonome à l'aide du code sans configuration.

- Créez un service à l'aide de la configuration fournie, mais ne définissez pas de point de terminaison.

### <a name="code"></a>Code

Le code suivant illustre comment créer un point de terminaison à l'aide de la sécurité de transport :

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a>Configuration

Le code ci-dessous configure le même point de terminaison en utilisant la configuration. Aucun mécanisme n'authentifie les clients, ceux-ci restent donc anonymes.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="SecuredByTransportEndpoint"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator">
          <security mode="Transport">
            <transport clientCredentialType="None" />
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

- Créez un client qui ne définit pas d'adresse de point de terminaison. Au lieu de cela, utilisez le constructeur client qui accepte le nom de configuration comme argument. Par exemple :

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Code

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a>Configuration

La configuration suivante peut être utilisée à la place du code pour paramétrer le service :

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Transport">
            <transport clientCredentialType="None" />
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

- [Présentation de la sécurité](security-overview.md)
- [WS Transport Security](../samples/ws-transport-security.md)
- [Vue d'ensemble de la sécurité des transports](transport-security-overview.md)
- [Modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
