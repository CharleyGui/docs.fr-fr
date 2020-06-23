---
title: 'Comment : héberger un service WCF dans une application managée'
description: Découvrez comment héberger un service WCF dans une application managée en créant un service auto-hébergé et en le testant.
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 7d1d61b683f60a6c643d2a2f03d367a6ae6c6c15
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246166"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Comment : héberger un service WCF dans une application gérée

Pour héberger un service à l'intérieur d'une application managée, incorporez le code du service à l'intérieur du code de l'application managée, définissez un point de terminaison pour le service soit de manière impérative dans le code, soit de façon déclarative par le biais de la configuration ou à l'aide des points de terminaison par défaut, puis créez une instance de <xref:System.ServiceModel.ServiceHost>.

Pour commencer à recevoir des messages, appelez <xref:System.ServiceModel.ICommunicationObject.Open%2A><xref:System.ServiceModel.ServiceHost>. De cette manière, vous créez et ouvrez l'écouteur pour le service. L'hébergement d'un service selon cette méthode est souvent appelé « auto-hébergement » parce que l'application managée effectue le travail d'hébergement elle-même. Pour fermer le service, appelez <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ServiceHost>.

Un service peut également être hébergé dans un service Windows managé, dans le service IIS (Internet Information Services), ou le service WAS (Windows Process Activation Service). Pour plus d’informations sur les options d’hébergement pour un service, consultez [services d’hébergement](hosting-services.md).

L'hébergement d'un service dans une application managée constitue l'option d'hébergement la plus flexible parce qu'il requiert le déploiement de moins d'infrastructure. Pour plus d’informations sur les services d’hébergement dans les applications managées, consultez [hébergement dans une application managée](./feature-details/hosting-in-a-managed-application.md).

La procédure suivante montre comment implémenter un service auto-hébergé dans une application console.

## <a name="create-a-self-hosted-service"></a>Créer un service auto-hébergé

1. Créez une application de console :

   1. Ouvrez Visual Studio et sélectionnez **nouveau**  >  **projet** dans le menu **fichier** .

   2. Dans la liste **modèles installés** , sélectionnez **Visual C#** ou **Visual Basic**, puis sélectionnez **Bureau Windows**.

   3. Sélectionnez le modèle **application console** . Tapez `SelfHost` dans la zone **nom** , puis choisissez **OK**.

2. Cliquez avec le bouton droit sur **selfHost** dans **Explorateur de solutions** , puis sélectionnez **Ajouter une référence**. Sélectionnez **System. ServiceModel** à partir de l’onglet **.net** , puis choisissez **OK**.

    > [!TIP]
    > Si la fenêtre de **Explorateur de solutions** n’est pas visible, sélectionnez **Explorateur de solutions** dans le menu **affichage** .

3. Double-cliquez sur **Program.cs** ou **Module1. vb** dans **Explorateur de solutions** pour l’ouvrir dans la fenêtre de code, s’il n’est pas déjà ouvert. Ajoutez les instructions suivantes en haut du fichier :

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Définissez et implémentez un contrat de service. Cet exemple définit un `HelloWorldService` qui retourne un message basé sur l'entrée au service.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Pour plus d’informations sur la définition et l’implémentation d’une interface de service, voir [Comment : définir un contrat de service](how-to-define-a-wcf-service-contract.md) et [Comment : implémenter un contrat de service](how-to-implement-a-wcf-contract.md).

5. En tête de la méthode `Main`, créez une instance de la classe <xref:System.Uri> avec l'adresse de base du service.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>, en passant un <xref:System.Type> qui représente le type de service et l'URI d'adresse de base (Uniform Resource Identifier) à <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Activez la publication des métadonnées, puis appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost> pour initialiser le service et le préparer à recevoir des messages.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > Cet exemple utilise les points de terminaison par défaut et aucun fichier de configuration n'est requis pour ce service. Si aucun point de terminaison n'est configuré, le runtime en crée un pour chaque adresse de base pour chaque contrat de service implémenté par le service. Pour plus d’informations sur les points de terminaison par défaut, consultez [configuration simplifiée](simplified-configuration.md) et [configuration simplifiée pour les services WCF](./samples/simplified-configuration-for-wcf-services.md).

7. Appuyez sur **CTRL** + **MAJ** + **B** pour générer la solution.

## <a name="test-the-service"></a>Testez le service

1. Appuyez sur **CTRL** + **F5** pour exécuter le service.

2. Ouvrez le **client test WCF**.

    > [!TIP]
    > Pour ouvrir le **client test WCF**, ouvrez invite de commandes développeur pour Visual Studio et exécutez **WcfTestClient.exe**.

3. Sélectionnez **Ajouter un service** dans le menu **fichier** .

4. Tapez `http://localhost:8080/hello` dans la zone adresse, puis cliquez sur **OK**.

    > [!TIP]
    > Assurez-vous que le service est en cours d'exécution, sinon cette étape échouera. Si vous avez changé l'adresse de base dans le code, utilisez cette adresse modifiée dans cette étape.

5. Double-cliquez sur **sayHello** sous le nœud **mes projets de service** . Tapez votre nom dans la colonne **valeur** de la liste **demande** , puis cliquez sur **appeler**.

   Un message de réponse s’affiche dans la liste des **réponses** .

## <a name="example"></a>Exemple

L'exemple suivant crée un objet <xref:System.ServiceModel.ServiceHost> pour héberger un service de type `HelloWorldService`, puis appelle la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost>. Une adresse de base est fournie dans le code, la publication des métadonnées est activée et les points de terminaison par défaut sont utilisés.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Comment : héberger un service WCF dans IIS](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Self-Host](./samples/self-host.md)
- [Hébergement de services](hosting-services.md)
- [Guide pratique pour définir un contrat de service](how-to-define-a-wcf-service-contract.md)
- [Guide pratique pour implémenter un contrat de service](how-to-implement-a-wcf-contract.md)
- [Outil Service Model Metadata Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Utilisation de liaisons pour configurer des services et des clients](using-bindings-to-configure-services-and-clients.md)
- [Liaisons fournies par le système](system-provided-bindings.md)
