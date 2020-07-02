---
title: Déploiement d'applications et du .NET Framework
description: Commencez à déployer .NET avec votre application. .NET fournit des applications sans impact, des composants privés par défaut, le partage de code contrôlé, et bien plus encore.
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: cce888c962c9ab83c13cce4040eb9ba50270972d
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803499"
---
# <a name="deploying-the-net-framework-and-applications"></a>Déploiement d'applications et du .NET Framework

Cet article est conçu pour vous aider à prendre en main le processus de déploiement du .NET Framework avec votre application. Les informations fournies sont principalement destinées aux développeurs, aux OEM et aux administrateurs d'entreprise. Les utilisateurs qui souhaitent installer le .NET Framework sur leurs ordinateurs sont invités à lire la page [Installer le .NET Framework](../install/index.md).

## <a name="key-deployment-resources"></a>Ressources principales de déploiement

Utilisez les liens suivants vers d'autres articles MSDN pour obtenir des informations spécifiques sur le déploiement et la maintenance du .NET Framework.

**Configuration et déploiement**

- Informations générales relatives au programme d'installation et au déploiement :

  - Options du programme d'installation :

    - [Programme d’installation web](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [Programme d’installation hors connexion](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - Modes d'installation :

    - [Installation sans assistance](deployment-guide-for-developers.md#chaining_custom)

    - [Affichage d’une interface utilisateur](deployment-guide-for-developers.md#chaining_default)

  - [Réduction des redémarrages du système lors des installations .NET Framework 4,5](reducing-system-restarts.md)

  - [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- Déploiement du .NET Framework avec une application cliente (pour les développeurs) :

  - [Utilisation d'InstallShield](deployment-guide-for-developers.md#installshield-deployment) dans un projet d'installation et de déploiement

  - [Utilisation d’une application ClickOnce de Visual Studio](deployment-guide-for-developers.md#clickonce-deployment)

  - [Création d’un package d’installation WiX](deployment-guide-for-developers.md#wix)

  - [Utilisation d’un programme d’installation personnalisé](deployment-guide-for-developers.md#chaining)

  - [Informations supplémentaires](deployment-guide-for-developers.md) pour les développeurs

- Déploiement du .NET Framework (pour les OEM et les administrateurs) :

  - [Kit de déploiement et d’évaluation (ADK) Windows](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [Guide de l’administrateur](guide-for-administrators.md)

**Maintenance**

- Pour obtenir des informations générales, consultez le [blog .NET Framework](https://devblogs.microsoft.com/dotnet/).

- [Détection des versions](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [Détection des Service Packs et des mises à jour](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a>Fonctionnalités d’aide au déploiement

Le .NET Framework offre de nombreuses fonctionnalités de base qui facilitent le déploiement de vos applications :

- Applications sans impact.

     Cette fonctionnalité permet d'isoler les applications et élimine les conflits de DLL. Par défaut, les composants n'ont pas d'incidence sur d'autres applications.

- Composants privés par défaut.

     Par défaut, les composants sont déployés dans le répertoire de l'application et sont accessibles uniquement par l'application conteneur.

- Partage de code contrôlé.

     Avec cette fonctionnalité, vous devez explicitement rendre le code disponible pour le partager (ce n'est plus le comportement par défaut).

- Contrôle de version côte à côte.

     Plusieurs versions d'un composant ou d'une application peuvent coexister. Vous pouvez choisir les versions à utiliser et le common language runtime applique la stratégie de contrôle de version.

- Déploiement et réplication XCOPY.

     Les composants et les applications autodescriptifs et autonomes peuvent être déployés sans entrées de Registre ni dépendances.

- Mises à jour instantanées.

     Les administrateurs peuvent utiliser des hôtes, tels que ASP.NET, pour mettre à jour les DLL de programmes, y compris sur des ordinateurs distants.

- Intégration avec Windows Installer.

     Les fonctionnalités de publication, de réparation et d'installation à la demande sont toutes disponibles pendant le déploiement de votre application.

- Déploiement d'entreprise.

     Cette fonctionnalité permet de distribuer facilement des logiciels, notamment avec Active Directory.

- Téléchargement et mise en cache.

     Les téléchargements incrémentiels permettent de réduire la taille des téléchargements. Les composants peuvent être isolés pour être utilisés uniquement par l'application et garantir ainsi un déploiement à faible impact.

- Code de confiance partielle.

     L'identité est basée sur le code au lieu de l'utilisateur. Aucune boîte de dialogue de certificat ne s'affiche.

## <a name="packaging-and-distributing-net-framework-applications"></a>Empaquetage et distribution d'applications .NET Framework

Certains aspects de l'empaquetage et du déploiement pour le .NET Framework sont traités dans d'autres sections de la documentation. Ces sections comportent des informations sur les unités autodescriptives appelées [assemblys](../../standard/assembly/index.md), qui ne nécessitent aucune entrée de Registre, les [assemblys portant un nom fort](../../standard/assembly/strong-named.md), qui garantissent l'unicité des noms et empêchent l'usurpation de noms, et le [contrôle de version des assemblys](../../standard/assembly/versioning.md), qui résout de nombreux problèmes liés aux conflits de DLL. Les sections suivantes fournissent des informations sur l'empaquetage et la distribution d'applications .NET Framework.

### <a name="packaging"></a>Packaging

Le .NET Framework offre les options suivantes pour empaqueter des applications :

- Sous forme d'un assembly unique ou d'une collection d'assemblys.

     Avec cette option, vous utilisez simplement les fichiers .dll ou .exe tels qu'ils ont été générés.

- Sous forme de fichiers CAB.

     Avec cette option, vous compressez les fichiers en fichiers .cab pour accélérer la distribution ou le téléchargement.

- Sous forme d'un package Windows Installer ou d'un autre format de programme d'installation.

     Avec cette option, vous créez des fichiers .msi utilisables avec Windows Installer ou vous empaquetez votre application pour l'utiliser avec un autre programme d'installation.

### <a name="distribution"></a>Distribution

Le .NET Framework offre les options suivantes pour distribuer des applications :

- Avec XCOPY ou FTP.

     Les applications du common language runtime sont autodescriptives et ne nécessitent aucune entrée de Registre. Vous pouvez donc utiliser XCOPY ou FTP pour copier simplement l'application dans un répertoire approprié. L'application peut ensuite être exécutée à partir de ce répertoire.

- Avec le téléchargement de code.

     Si vous distribuez votre application sur Internet ou via un intranet d'entreprise, vous pouvez simplement télécharger le code sur un ordinateur et exécuter l'application à partir de celui-ci.

- Avec un programme d'installation (tel que Windows Installer 2.0).

     Windows Installer 2.0 permet d'installer, de réparer ou de supprimer des assemblys .NET Framework dans le Global Assembly Cache et dans des répertoires privés.

### <a name="installation-location"></a>Emplacement d'installation

Pour déterminer où déployer les assemblys de votre application afin qu'ils puissent être localisés par le runtime, consultez la page [Méthode de localisation des assemblys par le runtime](how-the-runtime-locates-assemblies.md).

Prenez également en compte les considérations de sécurité dans votre choix de la méthode de déploiement de votre application. Des autorisations de sécurité sont accordées au code managé en fonction de l'emplacement du code. Le déploiement d'une application ou d'un composant à un emplacement présentant un niveau de confiance faible (Internet, par exemple) limite les actions réalisables par cette application ou ce composant. Pour plus d'informations sur le déploiement et la sécurité, consultez la page [Informations de base sur la sécurité d'accès du code](../misc/code-access-security-basics.md).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Méthode de localisation des assemblys par le runtime](how-the-runtime-locates-assemblies.md)|Décrit comment le common language runtime détermine quel assembly utiliser pour répondre à une demande de liaison.|
|[Bonnes pratiques pour le chargement d'assemblys](best-practices-for-assembly-loading.md)|Explique les moyens d'éviter les problèmes d'identités de type qui peuvent générer des exceptions <xref:System.InvalidCastException> et <xref:System.MissingMethodException>, et d'autres erreurs.|
|[Réduction des redémarrages système lors des installations du .NET Framework 4.5](reducing-system-restarts.md)|Décrit le Gestionnaire de redémarrage qui empêche les redémarrages si possible, et explique les avantages de son utilisation pour les applications qui installent le .NET Framework.|
|[Guide de déploiement pour les administrateurs](guide-for-administrators.md)|Explique comment un administrateur système peut déployer le .NET Framework et ses dépendances système sur un réseau à l’aide de points de terminaison Microsoft Configuration Manager.|
|[Guide de déploiement pour les développeurs](deployment-guide-for-developers.md)|Explique comment les développeurs peuvent installer le .NET Framework sur les ordinateurs des utilisateurs avec leurs applications.|
|[Déploiement d’applications, de services et de composants](/visualstudio/deployment/deploying-applications-services-and-components)|Présente les différentes options de déploiement dans Visual Studio, y compris les instructions de publication d'une application à l'aide des fonctionnalités ClickOnce et Windows Installer.|
|[Publication d’applications ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|Décrit comment empaqueter une application Windows Forms pour la déployer ensuite avec ClickOnce sur des ordinateurs clients d’un réseau.|
|[Packaging and Deploying Resources](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|Décrit le modèle « Hub and Spoke » utilisé par le .NET Framework pour empaqueter et déployer des ressources. Fournit des informations sur les conventions de dénomination des ressources, le processus de secours et les alternatives à l'empaquetage.|
|[Déploiement d'une application d'interopérabilité](../interop/deploying-an-interop-application.md)|Explique comment livrer et installer des applications Interop, qui comportent généralement un assembly client .NET Framework, un ou plusieurs assemblys d'interopérabilité représentant des bibliothèques de types COM distinctes et un ou plusieurs composants COM inscrits.|
|[How to: Get Progress from the .NET Framework 4.5 Installer](how-to-get-progress-from-the-dotnet-installer.md)|Décrit comment lancer et suivre le processus d'installation sans assistance du .NET Framework tout en affichant votre propre vue de la progression de l'installation.|

## <a name="see-also"></a>Voir aussi

- [Guide de développement](../development-guide.md)
