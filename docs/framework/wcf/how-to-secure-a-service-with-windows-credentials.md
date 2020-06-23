---
title: "Comment : sécuriser un service à l'aide d'informations d'identification Windows"
description: Découvrez comment activer la sécurité de transport sur un service WCF résidant dans un domaine Windows et appelé par des clients dans le même domaine.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 8ef164e1475bfd5f047a99426a2bed43a7aa7353
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244631"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Comment : sécuriser un service à l'aide d'informations d'identification Windows

Cette rubrique montre comment activer la sécurité de transport sur un service Windows Communication Foundation (WCF) qui réside dans un domaine Windows et qui est appelé par des clients dans le même domaine. Pour plus d’informations sur ce scénario, consultez [sécurité du transport avec l’authentification Windows](./feature-details/transport-security-with-windows-authentication.md). Pour obtenir un exemple d’application, consultez l’exemple [WSHttpBinding](./samples/wshttpbinding.md) .

Cette rubrique suppose que vous avez une interface de contrat existante et que l'implémentation est déjà définie et s'ajoute à cela. Vous pouvez également modifier un service et un client existants.

Vous pouvez sécuriser complètement un service avec les informations d'identification Windows dans le code. Vous pouvez également omettre un peu du code en utilisant un fichier de configuration. Cette rubrique décrit les deux approches. Veillez à n'en utiliser qu'une seule, pas les deux.

Les trois premières procédures indiquent comment sécuriser le service à l'aide du code. Les quatrième et cinquième procédures indiquent comment le faire avec un fichier de configuration.

## <a name="using-code"></a>Utilisation du code

L'intégralité du code du service et du client est présentée dans la section Exemple à la fin de cette rubrique.

La première procédure vous guide tout au long de la création et la configuration d'une classe <xref:System.ServiceModel.WSHttpBinding> dans le code. La liaison utilise le transport HTTP. La même liaison est utilisée sur le client.

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Pour créer un WSHttpBinding qui utilise des informations d'identification Windows et la sécurité de message

1. Le code de cette procédure est inséré au début de la méthode `Run` de la classe `Test` dans le code de service indiqué à la section Exemple.

2. Créez une instance de la classe <xref:System.ServiceModel.WSHttpBinding>.

3. Affectez la valeur <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> à la propriété <xref:System.ServiceModel.WSHttpSecurity> de la classe <xref:System.ServiceModel.SecurityMode.Message>.

4. Affectez la valeur <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> à la propriété <xref:System.ServiceModel.MessageSecurityOverHttp> de la classe <xref:System.ServiceModel.MessageCredentialType.Windows>.

5. Le code de cette procédure se présente comme suit :

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a>Utilisation de la liaison dans un service

Il s’agit de la deuxième procédure, qui indique comment utiliser la liaison dans un service auto-hébergé. Pour plus d’informations sur les services d’hébergement, consultez [Hébergement de services](hosting-services.md).

##### <a name="to-use-a-binding-in-a-service"></a>Pour utiliser une liaison dans un service

1. Insérez le code de cette procédure après celui de la procédure précédente.

2. Créez une variable <xref:System.Type> nommée `contractType` et assignez-lui le type de l'interface (`ICalculator`). Quand vous utilisez Visual Basic, utilisez l' `GetType` opérateur. quand vous utilisez C#, utilisez le `typeof` mot clé.

3. Créez une deuxième variable <xref:System.Type> nommée `serviceType` et assignez-lui le type du contrat implémenté (`Calculator`).

4. Créez une instance de la classe <xref:System.Uri> nommée `baseAddress` avec l'adresse de base du service. L'adresse de base doit avoir un schéma qui correspond au transport. Dans ce cas, le schéma de transport est HTTP, et l’adresse comprend l’Uniform Resource Identifier spéciale (URI) « localhost » et un numéro de port (8036), ainsi qu’une adresse de point de terminaison de base («serviceModelSamples/) : `http://localhost:8036/serviceModelSamples/` .

5. Créez une instance de la classe <xref:System.ServiceModel.ServiceHost> avec les variables `serviceType` et `baseAddress`.

6. Ajoutez un point de terminaison au service à l'aide du `contractType`, de la liaison et d'un nom de point de terminaison (secureCalculator). Un client doit concaténer l'adresse de base et le nom de point de terminaison lors du lancement d'un appel au service.

7. Appelez la méthode <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> pour démarrer le service. Le code de cette procédure est indiqué ici :

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a>Utilisation de la liaison sur un client

Cette procédure indique comment générer un proxy qui communique avec le service. Le proxy est généré avec l' [outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) qui utilise les métadonnées de service pour créer le proxy.

Cette procédure crée également une instance de la classe <xref:System.ServiceModel.WSHttpBinding> pour communiquer avec le service, puis appelle ce dernier.

Cet exemple utilise uniquement du code pour créer le client. Vous pouvez aussi, si vous le souhaitez, utiliser un fichier de configuration, indiqué dans la section qui suit cette procédure.

#### <a name="to-use-a-binding-in-a-client-with-code"></a>Pour utiliser une liaison sur un client avec le code

1. Utilisez l'outil SvcUtil.exe pour générer le code du proxy à partir des métadonnées du service. Pour plus d’informations, consultez [Comment : créer un client](how-to-create-a-wcf-client.md). Le code proxy généré hérite de la <xref:System.ServiceModel.ClientBase%601> classe, ce qui garantit que chaque client dispose des constructeurs, méthodes et propriétés nécessaires pour communiquer avec un service WCF. Dans cet exemple, le code généré inclut la classe `CalculatorClient`, qui implémente l'interface `ICalculator`, activant ainsi la compatibilité avec le code de service.

2. Le code de cette procédure est inséré au début de la méthode `Main` du programme client.

3. Créez une instance de la classe <xref:System.ServiceModel.WSHttpBinding> et affectez à son mode de sécurité la valeur `Message` et à son type d'informations d'identification client la valeur `Windows`. L'exemple nomme la variable `clientBinding`.

4. Créez une instance de la classe <xref:System.ServiceModel.EndpointAddress> nommée `serviceAddress`. Initialisez l'instance avec l'adresse de base concaténée avec le nom de point de terminaison.

5. Créez une instance de la classe de client générée avec les variables `serviceAddress` et `clientBinding`.

6. Appelez la méthode <xref:System.ServiceModel.ClientBase%601.Open%2A>, comme illustré dans le code suivant :

7. Appelez le service et affichez les résultats.

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a>Utilisation du fichier de configuration

Au lieu de créer la liaison avec le code de procédure, vous pouvez utiliser le code suivant indiqué pour la section Liaisons du fichier de configuration.

Si vous n’avez pas encore défini de service, consultez [conception et implémentation de services](designing-and-implementing-services.md)et [Configuration des services](configuring-services.md).

> [!NOTE]
> Ce code de configuration est utilisé dans les fichiers de configuration du service et du client.

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Pour activer la sécurité de transfert sur un service dans un domaine Windows à l'aide de la configuration

1. Ajoutez un [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) élément à la [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section de l’élément du fichier de configuration.

2. Ajoutez un `binding` élément <> à l' `WSHttpBinding` élément> <et affectez `configurationName` à l’attribut une valeur appropriée à votre application.

3. Ajoutez un `security` élément <> et affectez `mode` à l’attribut la valeur message.

4. Ajoutez un `message` élément <> et affectez `clientCredentialType` à l’attribut la valeur Windows.

5. Dans le fichier de configuration du service, remplacez la section `<bindings>` par le code suivant. Si vous n’avez pas encore de fichier de configuration de service, consultez [utilisation de liaisons pour configurer des services et des clients](using-bindings-to-configure-services-and-clients.md).

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a>Utilisation de la liaison sur un client

Cette procédure indique comment générer deux fichiers : un proxy qui communique avec le service et un fichier de configuration. Elle décrit également les modifications du programme client, qui est le troisième fichier utilisé sur le client.

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Pour utiliser une liaison sur un client avec la configuration

1. Utilisez l'outil SvcUtil.exe pour générer le code proxy et le fichier de configuration à partir des métadonnées du service. Pour plus d’informations, consultez [Comment : créer un client](how-to-create-a-wcf-client.md).

2. Remplacez la [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section du fichier de configuration généré par le code de configuration de la section précédente.

3. Le code de la procédure est inséré au début de la méthode `Main` du programme client.

4. Créez une instance de la classe de client générée qui passe le nom de la liaison dans le fichier de configuration comme un paramètre d'entrée.

5. Appelez la méthode <xref:System.ServiceModel.ClientBase%601.Open%2A>, comme illustré dans le code suivant :

6. Appelez le service et affichez les résultats.

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a>Exemple

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.WSHttpBinding>
- [Outil Service Model Metadata Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Guide pratique pour créer un client](how-to-create-a-wcf-client.md)
- [Sécurisation de services](securing-services.md)
- [Présentation de la sécurité](./feature-details/security-overview.md)
