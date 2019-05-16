---
title: 'Procédure : héberger un service WCF dans une application managée'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: b6d1c9c38e2cc5f1b1b7b5538af0339987563de6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637576"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Procédure : Héberger un service WCF dans une application gérée

Pour héberger un service à l'intérieur d'une application managée, incorporez le code du service à l'intérieur du code de l'application managée, définissez un point de terminaison pour le service soit de manière impérative dans le code, soit de façon déclarative par le biais de la configuration ou à l'aide des points de terminaison par défaut, puis créez une instance de <xref:System.ServiceModel.ServiceHost>.

Pour commencer à recevoir des messages, appelez <xref:System.ServiceModel.ICommunicationObject.Open%2A><xref:System.ServiceModel.ServiceHost>. De cette manière, vous créez et ouvrez l'écouteur pour le service. L'hébergement d'un service selon cette méthode est souvent appelé « auto-hébergement » parce que l'application managée effectue le travail d'hébergement elle-même. Pour fermer le service, appelez <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ServiceHost>.

Un service peut également être hébergé dans un service Windows managé, dans le service IIS (Internet Information Services), ou le service WAS (Windows Process Activation Service). Pour plus d’informations sur les options pour un service d’hébergement, consultez [Services d’hébergement](../../../docs/framework/wcf/hosting-services.md).

L'hébergement d'un service dans une application managée constitue l'option d'hébergement la plus flexible parce qu'il requiert le déploiement de moins d'infrastructure. Pour plus d’informations sur l’hébergement de services dans les applications managées, consultez [hébergement dans une Application gérée par](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

La procédure suivante montre comment implémenter un service auto-hébergé dans une application console.

## <a name="create-a-self-hosted-service"></a>Créer un service auto-hébergé

1. Créer une nouvelle application de console :

   1. Ouvrez Visual Studio et sélectionnez **New** > **projet** à partir de la **fichier** menu.

   2. Dans le **modèles installés** liste, sélectionnez **Visual C#** ou **Visual Basic**, puis sélectionnez **Windows Desktop**.

   3. Sélectionnez le **application Console** modèle. Type `SelfHost` dans le **nom** zone, puis choisissez **OK**.

2. Avec le bouton droit **SelfHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter une référence**. Sélectionnez **System.ServiceModel** à partir de la **.NET** onglet, puis choisissez **OK**.

    > [!TIP]
    > Si le **l’Explorateur de solutions** fenêtre n’est pas visible, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.

3. Double-cliquez sur **Program.cs** ou **Module1.vb** dans **l’Explorateur de solutions** pour l’ouvrir dans la fenêtre de code, s’il n’est pas déjà ouvert. Ajoutez les instructions suivantes en haut du fichier :

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Définissez et implémentez un contrat de service. Cet exemple définit un `HelloWorldService` qui retourne un message basé sur l'entrée au service.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Pour plus d’informations sur la façon de définir et implémenter une interface de service, consultez [Comment : Définir un contrat de Service](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) et [Comment : Implémenter un contrat de Service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).

5. En tête de la méthode `Main`, créez une instance de la classe <xref:System.Uri> avec l'adresse de base du service.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>, en passant un <xref:System.Type> qui représente le type de service et l'URI d'adresse de base (Uniform Resource Identifier) à <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Activez la publication des métadonnées, puis appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost> pour initialiser le service et le préparer à recevoir des messages.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > Cet exemple utilise les points de terminaison par défaut et aucun fichier de configuration n'est requis pour ce service. Si aucun point de terminaison n'est configuré, le runtime en crée un pour chaque adresse de base pour chaque contrat de service implémenté par le service. Pour plus d’informations sur les points de terminaison par défaut, consultez [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) et [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

7. Appuyez sur **Ctrl**+**MAJ**+**B** pour générer la solution.

## <a name="test-the-service"></a>Tester le service

1. Appuyez sur **Ctrl**+**F5** pour exécuter le service.

2. Ouvrez **Client Test WCF**.

    > [!TIP]
    > Pour ouvrir **Client Test WCF**, ouvrez l’invite de commandes développeur pour Visual Studio et exécutez **WcfTestClient.exe**.

3. Sélectionnez **ajouter un Service** à partir de la **fichier** menu.

4. Type `http://localhost:8080/hello` dans la zone d’adresse et cliquez sur **OK**.

    > [!TIP]
    > Assurez-vous que le service est en cours d'exécution, sinon cette étape échouera. Si vous avez changé l'adresse de base dans le code, utilisez cette adresse modifiée dans cette étape.

5. Double-cliquez sur **SayHello** sous le **Mes projets de Service** nœud. Tapez votre nom dans la **valeur** colonne dans le **demande** liste, puis cliquez sur **Invoke**.

   Un message de réponse s’affiche dans le **réponse** liste.

## <a name="example"></a>Exemple

L'exemple suivant crée un objet <xref:System.ServiceModel.ServiceHost> pour héberger un service de type `HelloWorldService`, puis appelle la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost>. Une adresse de base est fournie dans le code, la publication des métadonnées est activée et les points de terminaison par défaut sont utilisés.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Guide pratique pour Héberger un Service WCF dans IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Auto-hébergement](../../../docs/framework/wcf/samples/self-host.md)
- [Hébergement de services](../../../docs/framework/wcf/hosting-services.md)
- [Guide pratique pour Définir un contrat de Service](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Guide pratique pour Implémenter un contrat de Service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Liaisons fournies par le système](../../../docs/framework/wcf/system-provided-bindings.md)
