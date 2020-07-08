---
title: "Comment : échanger des messages au sein d'une session fiable"
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 39dd6636f80b107ced1caac29869c6c66e67e21e
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052037"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Comment : échanger des messages au sein d'une session fiable

Cette rubrique décrit les étapes requises pour activer une session fiable utilisant l’une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut. Vous activez une session fiable de façon impérative à l’aide du code ou de façon déclarative dans votre fichier de configuration. Cette procédure utilise les fichiers de configuration du client et du service pour activer la session fiable et stipuler que les messages arrivent dans l’ordre dans lequel ils ont été envoyés.

La partie clé de cette procédure est que l’élément de configuration de point de terminaison contient un `bindingConfiguration` attribut qui fait référence à une configuration de liaison nommée `Binding1` . L' [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) élément de configuration fait référence à ce nom pour activer des sessions fiables en affectant `enabled` à l’attribut de l’élément la valeur [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` . Vous spécifiez les assurances de remise ordonnée pour la session fiable en affectant à l'attribut `ordered` la valeur `true`.

Pour obtenir la copie source de cet exemple, consultez [WS Reliable session](../samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurer le service avec une liaison WSHttpBinding pour utiliser une session fiable

1. Définissez un contrat de service pour le type de service.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implémentez le contrat de service dans une classe de service. Notez que l’adresse ou les informations de liaison ne sont pas spécifiées dans l’implémentation du service. Vous n’êtes pas obligé d’écrire du code pour récupérer l’adresse ou les informations de liaison à partir du fichier de configuration.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Créez un fichier de *Web.config* pour configurer un point de terminaison pour le `CalculatorService` qui utilise <xref:System.ServiceModel.WSHttpBinding> avec la session fiable activée et la livraison chronologique des messages requise.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Créez un fichier *service. svc* qui contient la ligne :

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Placez le fichier *service. svc* dans votre répertoire virtuel Internet Information Services (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurer le client avec une liaison WSHttpBinding pour utiliser une session fiable

1. Utilisez l' [outil ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) à partir de la ligne de commande pour générer le code à partir des métadonnées de service :

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Le client généré contient l' `ICalculator` interface qui définit le contrat de service que l’implémentation du client doit satisfaire.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. L'application cliente générée contient également l'implémentation de `ClientCalculator`. Notez que les informations d’adresse et de liaison ne sont pas spécifiées n’importe où dans l’implémentation du service. Vous n’êtes pas obligé d’écrire du code pour récupérer l’adresse ou les informations de liaison à partir du fichier de configuration.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* génère également la configuration du client qui utilise la <xref:System.ServiceModel.WSHttpBinding> classe. Nommez le fichier de configuration *App.config* lors de l’utilisation de Visual Studio.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Créez une instance de `ClientCalculator` dans une application et appelez les opérations de service.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Compilez, puis exécutez le client.

## <a name="example"></a>Exemple

Plusieurs liaisons fournies par le système prennent en charge des sessions fiables par défaut. notamment :

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Pour obtenir un exemple de création d’une liaison personnalisée qui prend en charge les sessions fiables, consultez Guide pratique [pour créer une liaison de session fiable personnalisée avec HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Voir aussi

- [Sessions fiables](reliable-sessions.md)
