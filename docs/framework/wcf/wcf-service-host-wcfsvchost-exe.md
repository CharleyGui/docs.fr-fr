---
title: Hôte de service WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: f8a081ed7c525b4346908f0419f0bb1ebf43683a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662638"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Hôte de service WCF (WcfSvcHost.exe)

Hôte de Service Windows Communication Foundation (WCF) (WcfSvcHost.exe) vous permet de lancer le débogueur de Visual Studio (F5) pour héberger et tester un service que vous avez implémenté automatiquement. Vous pouvez ensuite tester le service en utilisant le Client Test WCF (WcfTestClient.exe) ou votre propre client, pour rechercher et corriger les erreurs potentielles.

## <a name="wcf-service-host"></a>Hôte de service WCF

Hôte de Service WCF énumère les services dans un projet de service WCF, charge la configuration du projet et instancie un hôte pour chaque service qu’il trouve. L’outil est intégré à Visual Studio via le modèle de Service WCF et est appelé lorsque vous commencez à déboguer votre projet.

En utilisant l’hôte de Service WCF, vous pouvez héberger un service WCF (dans un projet de bibliothèque de service WCF) sans écrire de code supplémentaire ou se limiter à un hôte spécifique pendant le développement.

> [!NOTE]
> Hôte de Service WCF ne prend pas en charge la confiance partielle. Si vous souhaitez utiliser un Service WCF en confiance partielle, n’utilisez pas le modèle de projet de bibliothèque de Service WCF dans Visual Studio pour générer votre service. Au lieu de cela, créez un nouveau site Web dans Visual Studio en choisissant le modèle de site Web de Service WCF, qui peut héberger le service dans un serveur Web sur lequel une confiance partielle WCF est pris en charge.

## <a name="project-types-hosted-by-wcf-service-host"></a>Types de projet hébergés par l'hôte de service WCF

Hôte de Service WCF peut héberger les types de projet de bibliothèque de service WCF suivants : Bibliothèque du Service WCF, bibliothèque de Service de Workflow séquentiel, bibliothèque de Service de flux de travail de Machine d’état et bibliothèque du Service de Syndication. Hôte de Service WCF peut également héberger les services qui peuvent être ajoutés à un projet de bibliothèque de service à l’aide du **ajouter un élément** fonctionnalité. Cela inclut le Service WCF Service ordinateur d’état WF, de Service séquentiel WF XAML Service de Machine d’état WF et de Service séquentiel WF de XAML.

Toutefois, il est à noter que l'outil ne vous aidera pas à configurer un hôte. Pour cette tâche, vous devez modifier le fichier App.config manuellement. L'outil ne permet pas non plus de valider les fichiers de configuration définis par l'utilisateur.

> [!CAUTION]
> Vous ne devez pas utiliser hôte de Service WCF à héberger des services dans un environnement de production, car il n’était pas été conçu à cet effet.  Hôte de Service WCF ne prend pas en charge la fiabilité, la sécurité et la configuration requise de la facilité de gestion d’un tel environnement. Utilisez plutôt IIS car cette solution présente une fiabilité et des fonctionnalités de surveillance plus élevées ; elle constitue en outre la solution recommandée pour les services d’hébergement. Une fois le développement de vos services terminée, vous devez migrer les services à partir de l’hôte de Service WCF sur IIS.

## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scénarios d'utilisation de l'hôte de service WCF dans Visual Studio

Le tableau suivant répertorie tous les paramètres dans le **arguments de ligne de commande** boîte de dialogue, qui se trouve en double-cliquant sur votre projet dans **l’Explorateur de Solutions** dans Visual Studio, en sélectionnant **Propriétés**, puis en sélectionnant le **déboguer** onglet et en cliquant sur **démarrer le projet**. Ces paramètres sont utiles pour configurer l’hôte de Service WCF.

|Paramètre|Signification|
|---------------|-------------|
|`/client`|Paramètre facultatif qui spécifie le chemin d’accès à un fichier exécutable à utiliser une fois les services hébergés. Cette opération lance le Client Test WCF hébergement effectué.|
|`/clientArg`|Spécifie une chaîne en tant qu'argument passé à l'application cliente personnalisée.|
|`/?`|Affiche le texte de l'aide.|

#### <a name="using-wcf-test-client"></a>Utilisation du client test WCF

Une fois que vous créez un projet de service WCF et appuyez sur F5 pour démarrer le débogueur, hôte de Service WCF démarre tous les services qu’il trouve dans votre projet d’hébergement. Client Test WCF s’ouvre automatiquement et affiche la liste des points de terminaison de service définis dans le fichier de configuration. Dans la fenêtre principale, vous pouvez tester les paramètres et appeler votre service.

Pour vous assurer que le Client Test WCF est utilisé, cliquez sur votre projet dans **l’Explorateur de Solutions** dans Visual Studio, sélectionnez **propriétés**, puis sélectionnez le **déboguer** onglet. Cliquez sur **démarrer le projet** et vous assurer que ce qui suit s’affiche dans le **arguments de ligne de commande** boîte de dialogue.

`/client:WcfTestClient.exe`

#### <a name="using-a-custom-client"></a>Utilisation d'un client personnalisé

Pour utiliser un client personnalisé, cliquez sur votre projet dans **l’Explorateur de Solutions** dans Visual Studio, sélectionnez **propriétés**, puis sélectionnez le **déboguer** onglet. Cliquez sur **démarrer le projet** et modifier le `/client` paramètre dans le **arguments de ligne de commande** boîte de dialogue pour pointer vers votre client personnalisé, comme indiqué dans l’exemple suivant.

`/client:"path/CustomClient.exe"`

Lorsque vous appuyez sur F5 pour démarrer le service à nouveau, hôte de Service WCF démarre automatiquement votre client personnalisé lorsque vous lancez le débogueur.

Vous pouvez également utiliser le paramètre `/clientArg:` pour spécifier une chaîne en tant qu’argument qui est passé à l’application cliente personnalisée, comme indiqué dans l’exemple suivant.

`/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`

Par exemple, si vous utilisez le modèle de bibliothèque du service de syndication, vous pouvez utiliser les arguments de la ligne de commandes suivante :

`/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`

#### <a name="specifying-no-client"></a>Spécification d'aucun client

Pour spécifier qu’aucun client ne sera utilisé après l’hébergement de services WCF, cliquez sur votre projet dans **l’Explorateur de Solutions** dans Visual Studio, sélectionnez **propriétés**, puis sélectionnez le **déboguer** onglet. Cliquez sur **démarrer le projet** et laissez le **arguments de ligne de commande** boîte de dialogue vide.

#### <a name="using-a-custom-host"></a>Utilisation d'un hôte personnalisé

Pour utiliser un hôte personnalisé, cliquez sur votre projet dans **l’Explorateur de Solutions** dans Visual Studio, sélectionnez **propriétés**, puis sélectionnez le **déboguer** onglet. Cliquez sur **démarrer le programme externe** et entrez le chemin d’accès complet à l’hôte personnalisé. Vous pouvez également utiliser le **arguments de ligne de commande** boîte de dialogue pour spécifier des arguments à passer à l’hôte.

## <a name="wcf-service-host-user-interface"></a>Interface utilisateur de l'Hôte de service WCF

Lorsque vous appelez initialement hôte de Service WCF (en appuyant sur F5 dans Visual Studio), le **hôte de Service WCF** fenêtre s’ouvre automatiquement. Lors de l’hôte de Service WCF est en cours d’exécution, l’icône du programme apparaît dans la zone de notification. Double-cliquez sur l’icône pour ouvrir le **hôte de Service WCF** fenêtre

Lorsque des erreurs surviennent lors de l’hébergement de services, boîte de dialogue hôte de Service WCF s’ouvre et affiche des informations pertinentes.

Le **hôte de Service WCF** fenêtre principale contient deux menus :

- **Fichier**: Contient le **fermer** et **Exit** commandes. Lorsque vous cliquez sur **fermer**, le **hôte de Service WCF** boîte de dialogue se ferme, mais les services continuent d’être hébergés. Lorsque vous cliquez sur **Exit**, hôte de Service WCF est également arrêté. Cela arrête également tous les services hébergés.

- **Aide**: Contient le **sur** commande qui contient des informations de version. Il contient également le **aide** commande capable d’ouvrir un fichier d’aide.

La principale **hôte de Service WCF** fenêtre contient deux zones :

- La première zone est **Service**. Elle contient une liste qui affiche des informations de base sur tous les services. Ces informations incluent :

  - **Service** : Répertorie tous les services.

  - **état**: Répertorie l’état du service. Les valeurs valides sont « Démarré », « Arrêté » et « Erreur ».

  - **Adresse des métadonnées**: Affiche l’adresse des métadonnées des services.

- La deuxième zone est **des informations supplémentaires**. Il affiche une explication détaillée de l’état du service lors de la ligne de service spécifique est sélectionnée dans le **Service** zone. Si l'état est Erreur, vous pouvez consulter le message d'erreur complet qui s'affiche à l'écran.

## <a name="stopping-wcf-service-host"></a>Arrêt de l'Hôte de service WCF

Vous pouvez arrêter de l’hôte de Service WCF quatre manières suivantes :

- Arrêter la session de débogage dans Visual Studio.

- Sélectionnez **Exit** à partir de la **fichier** menu dans le **hôte de Service WCF** fenêtre.

- Sélectionnez **Exit** à partir du menu contextuel de l’icône de barre d’état d’hôte de Service WCF dans la zone de notification système.

- Quitter le Client Test WCF si elle est utilisée.

## <a name="using-service-host-without-administrator-privilege"></a>Utilisation de l'hôte de service sans privilège d'administrateur

Pour permettre aux utilisateurs sans privilège d’administrateur développer des services WCF, une liste ACL (Access Control List) est créée pour l’espace de noms « http://+:8731/Design_Time_Addresses » lors de l’installation de Visual Studio. La liste ACL a la valeur (UI), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur. Les administrateurs peuvent ajouter ou supprimer des utilisateurs dans cette liste ACL ou ouvrir des ports supplémentaires. Cette liste ACL permet aux utilisateurs d’utiliser l’hôte de Service WCF (wcfSvcHost.exe) sans leur accorder des privilèges d’administrateur.

Vous pouvez modifier l'accès grâce à l'outil netsh.exe dans [!INCLUDE[wv](../../../includes/wv-md.md)], via le compte d'administrateur avec élévation de privilèges. Ceci est un exemple d'utilisation de netsh.exe .

```
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>
```

Pour plus d’informations sur netsh.exe, consultez «[comment utiliser l’outil Netsh.exe et les commutateurs de ligne de commande](https://go.microsoft.com/fwlink/?LinkId=97877)».

## <a name="see-also"></a>Voir aussi

- [Client test WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
