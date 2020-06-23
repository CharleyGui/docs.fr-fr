---
title: Hôte de service WCF (WcfSvcHost.exe)
description: Utilisez l’hôte de service WCF pour héberger et tester un service que vous avez implémenté. Vous pouvez tester le service à l’aide du client test WCF ou de votre propre client.
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: efc9512766d2a9cc814083ab632226d98917bf4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245724"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Hôte de service WCF (WcfSvcHost.exe)

L’hôte de service (WcfSvcHost.exe) Windows Communication Foundation (WCF) vous permet de lancer le débogueur Visual Studio (F5) pour héberger et tester automatiquement un service que vous avez implémenté. Vous pouvez ensuite tester le service à l’aide du client test WCF (WcfTestClient.exe) ou de votre propre client pour rechercher et corriger les erreurs potentielles.

## <a name="wcf-service-host"></a>Hôte de service WCF

L’hôte de service WCF énumère les services dans un projet de service WCF, charge la configuration du projet et instancie un hôte pour chaque service qu’il trouve. L’outil est intégré à Visual Studio par le biais du modèle de service WCF et est appelé lorsque vous commencez à déboguer votre projet.

À l’aide de l’hôte de service WCF, vous pouvez héberger un service WCF (dans un projet de bibliothèque de service WCF) sans écrire de code supplémentaire ou effectuer de validation sur un ordinateur hôte spécifique pendant le développement.

> [!NOTE]
> L’hôte de service WCF ne prend pas en charge la confiance partielle. Si vous souhaitez utiliser un service WCF en confiance partielle, n’utilisez pas le modèle de projet Bibliothèque du service WCF dans Visual Studio pour générer votre service. Au lieu de cela, créez un nouveau site Web dans Visual Studio en choisissant le modèle de site Web du service WCF, qui peut héberger le service dans un serveur Web sur lequel la confiance partielle WCF est prise en charge.

## <a name="project-types-hosted-by-wcf-service-host"></a>Types de projet hébergés par l'hôte de service WCF

L’hôte de service WCF peut héberger les types de projets de bibliothèque de service WCF suivants : bibliothèque de service WCF, bibliothèque de service de workflow séquentiel, bibliothèque du service de workflow d’ordinateur d’État et bibliothèque du service de syndication. L’hôte de service WCF peut également héberger les services qui peuvent être ajoutés à un projet de bibliothèque de service à l’aide de la fonctionnalité **Ajouter un élément** . Cela comprend le service WCF, le service de machine à États WF, le service séquentiel WF, le service d’ordinateur d’État WF XAML et le service séquentiel WF XAML.

Toutefois, il est à noter que l'outil ne vous aidera pas à configurer un hôte. Pour cette tâche, vous devez modifier le fichier App.config manuellement. L'outil ne permet pas non plus de valider les fichiers de configuration définis par l'utilisateur.

> [!CAUTION]
> Vous ne devez pas utiliser l’hôte de service WCF pour héberger des services dans un environnement de production, car il n’a pas été conçu à cet effet.  L’hôte de service WCF ne prend pas en charge les exigences de fiabilité, de sécurité et de facilité de gestion d’un tel environnement. Utilisez plutôt IIS car cette solution présente une fiabilité et des fonctionnalités de surveillance plus élevées ; elle constitue en outre la solution recommandée pour les services d’hébergement. Une fois le développement de vos services terminé, vous devez migrer les services de l’hôte de service WCF vers IIS.

## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scénarios d'utilisation de l'hôte de service WCF dans Visual Studio

Le tableau suivant répertorie tous les paramètres de la boîte de dialogue arguments de la **ligne de commande** , accessibles en cliquant avec le bouton droit sur votre projet dans l' **Explorateur de solutions** de Visual Studio, en sélectionnant **Propriétés**, puis en sélectionnant l’onglet **Déboguer** et en cliquant sur **Démarrer le projet**. Ces paramètres sont utiles pour configurer l’hôte de service WCF.

|Paramètre|Signification|
|---------------|-------------|
|`/client`|Paramètre facultatif qui spécifie le chemin d’accès à un fichier exécutable à utiliser une fois les services hébergés. Cela lance le client test WCF après l’hébergement.|
|`/clientArg`|Spécifie une chaîne en tant qu'argument passé à l'application cliente personnalisée.|
|`/?`|Affiche le texte de l'aide.|

#### <a name="using-wcf-test-client"></a>Utilisation du client test WCF

Après avoir créé un projet de service WCF et appuyé sur la touche F5 pour démarrer le débogueur, l’hôte de service WCF démarre et héberge tous les services qu’il trouve dans votre projet. Le client test WCF s’ouvre automatiquement et affiche la liste des points de terminaison de service définis dans le fichier de configuration. Dans la fenêtre principale, vous pouvez tester les paramètres et appeler votre service.

Pour vous assurer que le client test WCF est utilisé, cliquez avec le bouton droit sur votre projet dans l' **Explorateur de solutions** dans Visual Studio, sélectionnez **Propriétés**, puis sélectionnez l’onglet **Déboguer** . cliquez sur **Démarrer le projet** et assurez-vous que les éléments suivants s’affichent dans la boîte de dialogue arguments de la **ligne de commande** .

`/client:WcfTestClient.exe`

#### <a name="using-a-custom-client"></a>Utilisation d'un client personnalisé

Pour utiliser un client personnalisé, cliquez avec le bouton droit sur votre projet dans l' **Explorateur de solutions** dans Visual Studio, sélectionnez **Propriétés**, puis sélectionnez l’onglet **Déboguer** . cliquez sur **Démarrer le projet** et modifiez le `/client` paramètre dans la boîte de dialogue **arguments de ligne de commande** pour pointer vers votre client personnalisé, comme indiqué dans l’exemple suivant.

`/client:"path/CustomClient.exe"`

Lorsque vous appuyez sur F5 pour redémarrer le service, l’hôte de service WCF démarre automatiquement votre client personnalisé lorsque vous lancez le débogueur.

Vous pouvez également utiliser le paramètre `/clientArg:` pour spécifier une chaîne en tant qu’argument qui est passé à l’application cliente personnalisée, comme indiqué dans l’exemple suivant.

`/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`

Par exemple, si vous utilisez le modèle de bibliothèque du service de syndication, vous pouvez utiliser les arguments de la ligne de commandes suivante :

`/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`

#### <a name="specifying-no-client"></a>Spécification d'aucun client

Pour spécifier qu’aucun client ne sera utilisé après l’hébergement du service WCF, cliquez avec le bouton droit sur votre projet dans l' **Explorateur de solutions** dans Visual Studio, sélectionnez **Propriétés**, puis sélectionnez l’onglet **Déboguer** . cliquez sur **Démarrer le projet** et laissez la boîte de dialogue arguments de **ligne de commande** vide.

#### <a name="using-a-custom-host"></a>Utilisation d'un hôte personnalisé

Pour utiliser un hôte personnalisé, cliquez avec le bouton droit sur votre projet dans l' **Explorateur de solutions** dans Visual Studio, sélectionnez **Propriétés**, puis sélectionnez l’onglet **Déboguer** . cliquez sur **Démarrer le programme externe** et entrez le chemin d’accès complet à l’hôte personnalisé. Vous pouvez également utiliser la boîte de dialogue **arguments de ligne de commande** pour spécifier les arguments à passer à l’hôte.

## <a name="wcf-service-host-user-interface"></a>Interface utilisateur de l'Hôte de service WCF

Lorsque vous appelez initialement l’hôte de service WCF (en appuyant sur F5 dans Visual Studio), la fenêtre **hôte de service WCF** s’ouvre automatiquement. Lorsque l’hôte de service WCF est en cours d’exécution, l’icône du programme s’affiche dans la zone de notification. Double-cliquez sur l’icône pour ouvrir la fenêtre **hôte de service WCF** .

Lorsque des erreurs se produisent pendant l’hébergement du service, la boîte de dialogue hôte de service WCF s’ouvre pour afficher les informations pertinentes.

La fenêtre principale de l' **hôte de service WCF** contient deux menus :

- **Fichier**: contient les commandes **Fermer** et **quitter** . Lorsque vous cliquez sur **Fermer**, la boîte de dialogue **hôte de service WCF** se ferme, mais les services continuent à être hébergés. Lorsque vous cliquez sur **quitter**, l’hôte de service WCF est également arrêté. Cela arrête également tous les services hébergés.

- **Aide**: contient la commande **à propos** de qui contient des informations de version. Elle contient également la commande **d’aide** qui permet d’ouvrir un fichier d’aide.

La fenêtre principale de l' **hôte de service WCF** contient deux zones :

- La première zone est **service**. Elle contient une liste qui affiche des informations de base sur tous les services. Ces informations incluent :

  - **Service**: répertorie tous les services.

  - **État**: indique l’état du service. Les valeurs valides sont « Started », « Stopped » et « Error ».

  - **Adresse des métadonnées**: affiche l’adresse des métadonnées des services.

- La deuxième zone est **des informations supplémentaires**. Elle affiche une explication détaillée de l’état du service lorsque la ligne de service spécifique est sélectionnée dans la zone **service** . Si l'état est Erreur, vous pouvez consulter le message d'erreur complet qui s'affiche à l'écran.

## <a name="stopping-wcf-service-host"></a>Arrêt de l'Hôte de service WCF

Vous pouvez arrêter l’hôte de service WCF de l’une des quatre manières suivantes :

- Arrêtez la session de débogage dans Visual Studio.

- Sélectionnez **quitter** dans le menu **fichier** de la fenêtre **hôte de service WCF** .

- Sélectionnez **quitter** dans le menu contextuel de l’icône de la barre d’État hôte du service WCF dans la zone de notification système.

- Quittez le client test WCF s’il est en cours d’utilisation.

## <a name="using-service-host-without-administrator-privilege"></a>Utilisation de l'hôte de service sans privilège d'administrateur

Pour permettre aux utilisateurs sans privilège d’administrateur de développer des services WCF, une liste de contrôle d’accès (ACL) (liste Access Control) est créée pour l’espace de noms « http://+:8731/Design_Time_Addresses » pendant l’installation de Visual Studio. La liste ACL a la valeur (UI), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur. Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste de contrôle d’accès, ou ouvrir des ports supplémentaires. Cette liste de contrôle d’accès permet aux utilisateurs d’utiliser l’hôte auto du service WCF (wcfSvcHost.exe) sans leur accorder des privilèges d’administrateur.

Vous pouvez modifier l’accès à l’aide de l’outil netsh.exe dans Windows Vista sous le compte d’administrateur avec élévation de privilèges. Ceci est un exemple d'utilisation de netsh.exe .

```console
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>
```

Pour plus d’informations sur la netsh.exe, consultez «[utilisation de l’outil Netsh.exe et des commutateurs de ligne de commande](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))».

## <a name="see-also"></a>Voir aussi

- [Client test WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
