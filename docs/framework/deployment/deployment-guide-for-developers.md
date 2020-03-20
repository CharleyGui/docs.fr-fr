---
title: Guide de déploiement du .NET Framework pour les développeurs
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
ms.openlocfilehash: 26c168040b0fa5e975e64a7518b0d0bf250c4711
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628122"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Guide de déploiement du .NET Framework pour les développeurs
Cette rubrique fournit des informations destinées aux développeurs qui souhaitent installer une version du .NET Framework (du .NET Framework 4.5 au [!INCLUDE[net_current](../../../includes/net-current-version.md)]) avec leurs applications.

Vous pouvez télécharger les paquets redistributables et les packs linguistiques pour .NET Framework à partir des pages de téléchargement:

- [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

 Remarques importantes :

- Les versions de .NET Framework de .NET Framework 4.5.1 à [!INCLUDE[net_current](../../../includes/net-current-version.md)] sont des mises à jour sur place vers .NET Framework 4.5, ce qui signifie qu'elles utilisent la même version du runtime. Toutefois, les versions d'assembly sont mises à jour et incluent de nouveaux types et membres.

- .NET Framework 4.5 et les versions ultérieures sont construites progressivement sur .NET Framework 4. Lorsque vous installez .NET Framework 4.5 ou des versions ultérieures sur un système qui a .NET Framework 4 installé, les assemblages de la version 4 sont remplacés par des versions plus nouvelles.

- Si vous faites référence à un [package hors bande](../get-started/the-net-framework-and-out-of-band-releases.md) Microsoft dans votre application, l’assembly est inclus dans le package de l’application.

- Vous devez avoir les privilèges de l’administrateur pour installer .NET Framework 4.5 ou des versions ultérieures.

- .NET Framework 4.5 est inclus dans Windows 8 et Windows Server 2012, de sorte que vous n’avez pas à le déployer avec votre application sur ces systèmes d’exploitation. De même, .NET Framework 4.5.1 est inclus dans Windows 8.1 et Windows Server 2012 R2. .NET Framework 4.5.2 n'est inclus dans aucun système d'exploitation. .NET Framework 4.6 est fourni avec Windows 10, .NET Framework 4.6.1 est inclus dans la Mise à jour de novembre de Windows 10, et .NET Framework 4.6.2 est inclus dans la Mise à jour anniversaire Windows 10.  .NET Framework 4.7 est inclus dans Windows 10 Creators Update, NET Framework 4.7.1 est inclus dans Windows 10 Fall Creators Update, et .NET Framework 4.7.2 est inclus dans la mise à jour d’octobre 2018 de Windows 10 et dans la mise à jour d’avril 2018 de Windows 10. .NET Framework 4.8 est inclus dans la mise à jour Windows 10 de mai 2019. Pour obtenir la liste complète des configurations matérielle et logicielle requises, consultez [Configuration système requise](../get-started/system-requirements.md).

- Depuis .NET Framework 4.5, vos utilisateurs peuvent afficher la liste des applications .NET Framework en cours d'exécution pendant l'installation et les fermer facilement. Cela peut contribuer à éviter les redémarrages système provoqués par les installations du .NET Framework. Consultez [Réduire le nombre de redémarrages système](reducing-system-restarts.md).

- Le déinstallation .NET Framework 4.5 ou les versions ultérieures supprime également les fichiers .NET Framework 4 préexistants. Si vous souhaitez revenir au .NET Framework 4, vous devrez le réinstaller et effectuer toutes ses mises à jour. Voir [Installer le cadre .NET 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).

- Le redistribuable .NET Framework 4.5 a été mis à jour le 9 octobre 2012 pour résoudre un problème lié à un horodatage incorrect sur un certificat numérique, ce qui a provoqué l'expiration prématurée de la signature numérique des fichiers produits et signés par Microsoft. Si vous avez déjà installé le paquet redistributable .NET Framework 4.5 en date du 16 août 2012, nous vous recommandons de mettre à jour votre copie avec la dernière redistributable à partir de la [page de téléchargement .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/net45). Pour plus d’informations sur ce problème, consultez l’ [avis de sécurité Microsoft 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Pour plus d’informations sur la façon dont un administrateur système peut déployer le .NET Framework et ses dépendances système sur un réseau, consultez le [Guide de déploiement pour les administrateurs](guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Options de déploiement de votre application

Lorsque vous êtes prêt à publier votre application sur un serveur web ou dans un autre emplacement centralisé, afin que les utilisateurs puissent l'installer, vous pouvez choisir différentes méthodes de déploiement. Certaines de ces méthodes sont fournies avec Visual Studio. Le tableau ci-dessous répertorie les options de déploiement de votre application et spécifie le package redistribuable du .NET Framework qui prend en charge chaque option. Outre ces options, vous pouvez écrire un programme d'installation personnalisé pour votre application. Pour plus d'informations, consultez la section [Chaînage de l'installation du .NET Framework à l'installation de votre application](#chaining).

|Stratégie de déploiement de votre application|Méthodes de déploiement disponibles|Redistribuable du .NET Framework à utiliser|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Installation à partir du web|- [Installaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Ensemble d'outils WiX](#wix)<br />- [Installation manuelle](#installing_manually)|[Programme d’installation web](#redistributable-packages)|
|Installation à partir d'un disque|- [Installaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Ensemble d'outils WiX](#wix)<br />- [Installation manuelle](#installing_manually)|[programme d’installation hors connexion](#redistributable-packages)|
|Installation à partir d'un réseau local (pour applications d'entreprise)|- [Clickonce](#clickonce-deployment)|[Programme d'installation web](#redistributable-packages) (voir [ClickOnce](#clickonce-deployment) pour connaître les restrictions) ou [programme d'installation hors connexion](#redistributable-packages)|

## <a name="redistributable-packages"></a>Forfaits redistributables

Le .NET Framework est disponible dans deux packages redistribuables : le programme d'installation web (programme d'amorçage) et le programme d'installation hors connexion (redistribuable autonome). Tous les téléchargements .NET Framework sont hébergés sur la [page Cadre Download .NET](https://dotnet.microsoft.com/download/dotnet-framework/). Le tableau suivant compare les deux paquets :

||programme d’installation web|programme d’installation hors connexion|
|-|-------------------|-----------------------|
|Connexion Internet requise ?|Oui|Non |
|Taille du téléchargement|Réduite (inclut le programme d'installation pour la plateforme cible uniquement)*|Étendue*|
|Modules linguistiques|Inclus**|Doivent être [installés séparément](#chain_langpack), sauf si vous utilisez le package qui cible tous les systèmes d'exploitation|
|Méthode de déploiement|Prend en charge toutes les méthodes :<br /><br />- [Clickonce](#clickonce-deployment)<br />- [Installaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [XML de Windows Installer (WiX)](#wix)<br />- [Installation manuelle](#installing_manually)<br />- [Installation personnalisée (chaînage)](#chaining)|Prend en charge toutes les méthodes :<br /><br /> - [Clickonce](#clickonce-deployment)<br />- [Installaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [XML de Windows Installer (WiX)](#wix)<br />- [Installation manuelle](#installing_manually)<br />- [Installation personnalisée (chaînage)](#chaining)|

\* Le programme d’installation hors connexion est plus volumineux, car il contient les composants pour toutes les plateformes cibles. Une fois que vous avez terminé l'installation, le système d'exploitation Windows met en cache uniquement le programme d'installation utilisé. Si le programme d'installation hors connexion est supprimé après l'installation, l'espace disque utilisé est identique à celui utilisé par le programme d'installation web. Si l'outil que vous utilisez (par exemple, [InstallAware](#installaware-deployment) ou [InstallShield](#installshield-deployment)) pour créer le programme d'installation de votre application fournit un dossier de fichiers d'installation qui est supprimé après l'installation, il est possible de supprimer automatiquement le programme d'installation hors connexion en le plaçant dans le dossier d'installation.

\*\* Si vous utilisez le programme d'installation web avec l'installation personnalisée, vous pouvez utiliser les paramètres de langue par défaut basés sur le paramètre de l'interface utilisateur multilingue de l'utilisateur ou vous pouvez spécifier un autre module linguistique en utilisant l'option `/LCID` sur la ligne de commande. Consultez la section [Chaînage à l'aide de l'interface utilisateur par défaut du .NET Framework](#chaining_default) pour obtenir des exemples.

## <a name="deployment-methods"></a>Méthodes de déploiement

 Quatre méthodes de déploiement sont disponibles :

- Vous pouvez définir une dépendance sur le .NET Framework. Vous pouvez définir le .NET Framework comme condition préalable à l'installation de votre application, à l'aide de l'une des méthodes suivantes :

  - Utilisation du [déploiement ClickOnce](#clickonce-deployment) (disponible dans Visual Studio)

  - Création d’un [projet InstallAware](#installaware-deployment) (édition gratuite disponible pour les utilisateurs de Visual Studio)

  - Création d'un [projet InstallShield](#installshield-deployment) (disponible dans Visual Studio)

  - Utilisation de l' [ensemble d'outils XML de Windows Installer (WiX)](#wix)

- Vous pouvez demander à vos utilisateurs d' [installer le .NET Framework manuellement](#installing_manually).

- Vous pouvez chaîner (inclure) le processus d'installation du .NET Framework dans l'installation de votre application, et déterminer la façon dont vous souhaitez gérer l'expérience d'installation du .NET Framework :

  - [Utilisez l'interface utilisateur par défaut](#chaining_default). Laissez le programme d'installation du .NET Framework fournir l'expérience d'installation.

  - [Personnalisez l'interface utilisateur](#chaining_custom) pour présenter une expérience d'installation unifiée et pour surveiller la progression de l'installation du .NET Framework.

Ces méthodes de déploiement sont discutées en détail dans les sections suivantes.

## <a name="setting-a-dependency-on-the-net-framework"></a>Définition d'une dépendance sur le .NET Framework

Si vous utilisez ClickOnce, InstallAware, InstallShield ou WiX pour déployer votre application, vous pouvez ajouter une dépendance sur le .NET Framework pour pouvoir l'installer dans le cadre de votre application.

### <a name="clickonce-deployment"></a>déploiement ClickOnce

Le déploiement ClickOnce est disponible pour les projets créés avec Visual Basic et Visual C#, mais pas Visual C++.

Dans Visual Studio, choisissez le déploiement ClickOnce et ajoutez une dépendance sur le .NET Framework :

1. Ouvrez le projet d'application que vous souhaitez publier.

2. Dans Solution Explorer, ouvrez le menu raccourci pour votre projet, puis choisissez **Properties**.

3. Choisissez le volet **Publier** .

4. Choisissez le bouton **Composants requis** .

5. Dans la boîte de dialogue **Composants requis** , vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.

6. Dans la liste des composants requis, recherchez la version du .NET Framework que vous avez utilisée pour générer votre projet et sélectionnez-la.

7. Choisissez une option pour spécifier l'emplacement source des composants requis, puis choisissez **OK**.

     Si vous fournissez une URL pour l’emplacement de téléchargement .NET Framework, vous pouvez spécifier soit la page de téléchargement .NET Framework ou un site de votre propre. Si vous placez le package redistribuable sur votre propre serveur, vous devez utiliser le programme d'installation hors connexion et non pas le programme d'installation web. Vous ne pouvez lier qu’à l’installateur web sur la page de téléchargement .NET Framework. L'URL peut également spécifier un disque sur lequel votre application est distribuée.

8. Dans la boîte de dialogue **Pages de propriétés** , choisissez **OK**.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>Déploiement d’InstallAware

InstallAware génère l’application Windows (APPX), Windows Installer (MSI), le code natif (EXE) et les packages App-V (Application Virtualization) à partir d’une source unique. [Incluez facilement une version quelconque du .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) dans votre configuration. Vous pouvez également personnaliser l’installation en [modifiant les scripts par défaut](https://www.installaware.com/msicode.htm) si nécessaire. Par exemple, InstallAware préinstalle des certificats sur Windows 7, sans lesquels le programme d’installation du .NET Framework 4.7 échouerait. Pour plus d’informations sur InstallAware, consultez le site web [InstallAware pour Windows Installer](https://www.installaware.com/).

### <a name="installshield-deployment"></a>Déploiement d'InstallShield

InstallShield construit des paquets d’applications Windows (MSIX, APPX), des forfaits d’installateur Windows (MSI) et des installateurs de code autochtone (EXE). InstallShield assure également l’intégration visual Studio. Pour plus d’informations, consultez le site [InstallShield.](https://www.flexerasoftware.com/install/products/installshield.html)

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Déploiement via XML de Windows Installer (WiX)

L'ensemble d'outils XML de Windows Installer (WiX) génère des packages d'installation Windows à partir de code source XML. WiX prend en charge un environnement en ligne de commande qui peut être intégré dans vos processus de génération pour générer des packages d'installation MSI et MSM. Grâce à WiX, vous pouvez [spécifier le .NET Framework en tant que composant requis](https://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)ou [créer un programme de chaînage](https://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) pour contrôler entièrement l’expérience de déploiement du .NET Framework. Pour plus d’informations sur WiX, consultez le site web [Ensemble d’outils du programme d’installation XML Windows (WiX)](https://wixtoolset.org/)

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>Installation manuelle du .NET Framework

Il est parfois peu pratique d'installer automatiquement le .NET Framework avec votre application. Dans ce cas, vous pouvez faire en sorte que les utilisateurs installent le .NET Framework eux-mêmes. Le package redistribuable est disponible dans [deux packages](#redistributable-packages). Dans votre processus d'installation, fournissez des instructions sur la manière dont les utilisateurs doivent chercher et installer le .NET Framework.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Chaînage de l'installation du .NET Framework à l'installation de votre application

Si vous créez un programme d'installation personnalisée pour votre application, vous pouvez chaîner (inclure) le processus d'installation du .NET Framework dans le processus d'installation de votre application. Le chaînage fournit deux options d'interface utilisateur pour l'installation du .NET Framework :

- Utiliser l'interface utilisateur par défaut fournie par le programme d'installation du .NET Framework.

- Créer une interface utilisateur personnalisée pour l'installation du .NET Framework pour des raisons de cohérence avec le programme d'installation de votre application.

Ces deux méthodes vous permettent d'utiliser le programme d'installation web ou le programme d'installation hors connexion. Chaque package présente ses propres avantages :

- Si vous utilisez le programme d'installation web, le processus d'installation du .NET Framework détermine quel package d'installation est obligatoire, et télécharge et installe uniquement ce package à partir du web.

- Si vous utilisez le programme d'installation hors connexion, vous pouvez inclure l'ensemble complet des packages d'installation du .NET Framework dans votre média de redistribution, afin que vos utilisateurs n'aient pas à télécharger de fichiers supplémentaires à partir d'Internet pendant l'installation.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Chaînage à l'aide de l'interface utilisateur par défaut du .NET Framework

Pour chaîner en mode silencieux le processus d'installation du .NET Framework et laisser le programme d'installation du .NET Framework fournir l'interface utilisateur, ajoutez la commande suivante à votre programme d'installation :

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

Par exemple, si votre programme exécutable est Contoso.exe et que vous souhaitez installer en mode silencieux le package redistribuable .NET Framework 4.5 hors connexion, utilisez la commande :

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

Vous pouvez utiliser des options de ligne de commande supplémentaires pour personnaliser l'installation. Par exemple :

- Pour permettre aux utilisateurs de fermer les applications .NET Framework en cours d'exécution, afin de réduire le nombre de redémarrages système, basculez en mode passif et utilisez l'option `/showrmui` comme suit :

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     Cette commande permet au Gestionnaire de redémarrage d'afficher une boîte de message permettant aux utilisateurs de fermer les applications .NET Framework avant d'installer .NET Framework.

- Si vous utilisez le programme d'installation web, vous pouvez utiliser l'option `/LCID` pour spécifier un module linguistique. Par exemple, pour chaîner le programme d'installation web .NET Framework 4.5 à votre programme d'installation Contoso et installer le module linguistique japonais, ajoutez la commande suivante au processus d'installation de votre application :

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     Si vous ne spécifiez pas l'option `/LCID` , le programme d'installation installe le module linguistique qui correspond au paramètre MUI de l'utilisateur.

    > [!NOTE]
    > Des modules linguistiques différents peuvent avoir des dates de publication différentes. Si le module linguistique spécifié n'est pas disponible dans le Centre de téléchargement, le programme d'installation installe le .NET Framework sans le module linguistique. Si le .NET Framework est déjà installé sur l'ordinateur de l'utilisateur, le programme d'installation installe uniquement le module linguistique.

Pour une liste complète des options, consultez la section [Options de ligne de commande](#command-line-options) .

Pour les codes de retour courants, consultez la section [Codes de retour](#return-codes) .

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Chaînage à l'aide d'une interface utilisateur personnalisée

Si vous possédez un package d'installation personnalisée, vous pouvez lancer et suivre en mode silencieux l'installation du .NET Framework tout en affichant votre propre vue de la progression de l'installation. Dans ce cas, assurez-vous que votre code prend en compte les points suivants :

- Vérifiez les [configurations matérielle et logicielle requises du .NET Framework](../get-started/system-requirements.md).

- [Détectez](#detect_net) si la version correcte du .NET Framework est déjà installée sur l'ordinateur de l'utilisateur.

    > [!IMPORTANT]
    > Pour déterminer si la version correcte du .NET Framework est déjà installée, vous devez vérifier si votre version cible *ou* une version ultérieure est installée, pas si votre version cible est installée. En d’autres termes, vous devez évaluer si la clé de version que vous récupérez à partir du Registre est supérieure ou égale à la clé de version de votre version cible, *pas* si elle est égale à la clé de version de votre version cible.

- [Détectez](#detecting-the-language-packs) si les modules linguistiques sont déjà installés sur l'ordinateur de l'utilisateur.

- Si vous souhaitez contrôler le déploiement, lancez et suivez en mode silencieux le processus d’installation du .NET Framework (consultez [Guide pratique : connaître la progression dans le programme d’installation du .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)

- Si vous déployez le programme d'installation hors connexion, [chaînez les modules linguistiques séparément](#chain_langpack).

- Personnalisez le déploiement à l'aide des [options de ligne de commande](#command-line-options). Par exemple, si vous chaînez le programme d'installation web du .NET Framework et que vous souhaitez remplacer le module linguistique par défaut, utilisez l'option `/LCID` , comme décrit dans la section précédente.

- [Dépannage](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>Détection du .NET Framework

Le programme d'installation du .NET Framework écrit des clés de Registre lorsque l'installation réussit. Vous pouvez savoir si le .NET Framework 4.5 ou version ultérieure est installé en vérifiant si le dossier `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` dans le Registre contient une valeur `DWORD` nommée `Release`. (Notez que « NET Framework Setup » ne commence pas par une période.) L’existence de cette clé indique que .NET Framework 4.5 ou une version ultérieure a été installé sur cet ordinateur. La valeur de `Release` indique quelle version du .NET Framework est installée.

> [!IMPORTANT]
> Vous devez rechercher une valeur  **supérieure ou égale** à la valeur du mot clé de la mise en production quand vous tentez de détecter si une version spécifique est présente.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Version|Valeur du paramètre DWORD Release|
|-------------|--------------------------------|
|.NET Framework 4.8 installé sur Windows 10 avec la mise à jour de mai 2019|528040|
|.NET Framework 4.8 installé sur toutes les versions du système d’exploitation, à l’exception de la mise à jour de mai 2019 de Windows 10|528049|
|.NET Framework 4.7.2 installé sur la mise à jour d’avril 2018 de Windows 10 et sur Windows Server, version 1803|461808|
|.NET Framework 4.7.2 installé sur toutes les versions de système d’exploitation, à l’exception de la mise à jour d’avril 2018 de Windows 10 et de Windows Server, version 1803. Cela inclut la mise à jour Windows 10 d’octobre 2018. |461814|
|.NET framework 4.7.1 installé sur Windows 10 Fall Creators Update et Windows Server, version 1709|461308|
|.NET Framework 4.7.1 installé sur toutes les versions de système d’exploitation autres que Windows 10 Fall Creators Update et Windows Server, version 1709|461310|
|.NET Framework 4.7 est installé sur Windows 10 Creators Update|460798|
|.NET framework 4.7 installé sur toutes les versions de système d’exploitation autres que Windows 10 Creators Update|460805|
|.NET Framework 4.6.2 installé sur la Mise à jour anniversaire Windows 10 et sur Windows Server 2016|394802|
|.NET Framework 4.6.2 installé sur toutes les versions de système d’exploitation autres que la Mise à jour anniversaire Windows 10 et Windows Server 2016|394806|
|.NET Framework 4.6.1 installé sur la mise à jour de novembre de Windows 10|394254|
|.NET Framework 4.6.1 installé sur toutes les versions de système d’exploitation autres que la mise à jour de novembre de Windows 10|394271|
|.NET Framework 4.6 installé sur Windows 10|393295|
|.NET Framework 4.6 installé sur toutes les versions du système d’exploitation, à l’exception de Windows 10|393297|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.5.1 installé avec Windows 8.1 ou Windows Server 2012 R2|378675|
|.NET Framework 4.5.1 installé sur Windows 8, Windows 7|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Détection des modules linguistiques

Vous pouvez vérifier si un module linguistique spécifique est installé en recherchant la valeur DWORD `Release` dans le dossier HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* du Registre. (Notez que « NET Framework Setup » ne commence pas par un point.) *dans le dossier HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\* spécifie un identificateur de paramètres régionaux ; consultez la liste des [langues prises en charge](#supported-languages) .

Par exemple, pour détecter si le pack en japonais complet (LCID-1041) est installé, récupérer la valeur nommée suivante du registre :

| | |
|-|-|
| Clé | HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-NET Framework Setup-NDP-v4-Full-1041 |
| Nom | Libérer |
| Type | DWORD |

Pour déterminer si la version finale d’un module linguistique est installée pour une version spécifique du .NET Framework (versions 4.5 à 4.7.2), vérifiez la valeur DWORD de la clé RELEASE décrite dans la section précédente, [Détection du .NET Framework](#detect_net).

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Chaînage des modules linguistiques au programme d’installation de votre application

Le .NET Framework fournit un ensemble de fichiers exécutables de modules linguistiques autonomes qui contiennent des ressources localisées pour des cultures spécifiques. Les packs linguistiques sont disponibles sur les pages Cadre Download .NET :

- [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

> [!IMPORTANT]
> Les modules linguistiques ne contiennent pas les composants .NET Framework requis pour exécuter une application. Vous devez installer le .NET Framework à l'aide du programme d'installation web ou hors connexion avant d'installer un module linguistique.

À compter de .NET Framework 4.5.1, les noms de packages prennent la forme NDP<`version`>-KB<`number`>-x86-x64-AllOS-<`culture`>.exe, où `version` est le numéro de version du .NET Framework, `number` est un numéro d’article de la Base de connaissances Microsoft, et `culture` spécifie un [pays/région](#supported-languages). Exemple de ce type de package : `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Les noms de packages sont répertoriés dans la section [Redistributable Packages](#redistributable-packages) plus haut dans cet article.

Pour installer un module linguistique à l'aide du programme d'installation hors connexion du .NET Framework, vous devez le chaîner à l'installation de votre application. Par exemple, pour déployer le programme d'installation hors connexion de .NET Framework 4.5.1 avec le module linguistique japonais, utilisez la commande suivante :

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

Vous n'êtes pas tenu de chaîner les modules linguistiques si vous utilisez le programme d'installation web. Ce dernier installe le module linguistique qui correspond au paramètre MUI de l'utilisateur. Pour installer une autre langue, vous pouvez utiliser l'option `/LCID` pour spécifier un module linguistique.

Pour une liste complète des options de ligne de commande, consultez la section [Options de ligne de commande](#command-line-options) .

### <a name="troubleshooting"></a>Dépannage

#### <a name="return-codes"></a>Codes de retour

Le tableau ci-dessous répertorie les codes de retour les plus courants relatifs au programme d'installation redistribuable du .NET Framework. Les codes de retour sont identiques pour toutes les versions du programme d'installation. Pour obtenir des liens vers des informations détaillées, consultez la section suivante.

|Code de retour|Description|
|-----------------|-----------------|
|0|Installation terminée.|
|1602|L'utilisateur a annulé l'installation.|
|1603|Une erreur irrécupérable s’est produite pendant l’installation.|
|1641|Un redémarrage est nécessaire pour terminer l'installation. Ce message indique que l'opération a réussi.|
|3010|Un redémarrage est nécessaire pour terminer l'installation. Ce message indique que l'opération a réussi.|
|5100|L'ordinateur de l'utilisateur n'a pas la configuration requise.|

#### <a name="download-error-codes"></a>Codes d'erreur de téléchargement

Consultez la

- [Codes d’erreur du service de transfert intelligent en arrière-plan (BITS)](https://go.microsoft.com/fwlink/?LinkId=180946)

- [Codes d’erreur du moniker d’URL](https://go.microsoft.com/fwlink/?LinkId=180947)

- [Codes d’erreur WinHttp](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Autres codes d'erreur

Consultez la

- [Codes d’erreur Windows Installer](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Codes de résultat de l’agent de mise à jour automatique Windows Update](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Désinstallation du .NET Framework

En commençant par Windows 8, vous pouvez désinstaller .NET Framework 4.5 ou des versions ultérieures en utilisant **les fonctionnalités Turn Windows sur et désactiver** dans le panneau de contrôle. Dans les anciennes versions de Windows, vous pouvez désinstaller .NET Framework 4.5 ou des versions ultérieures en utilisant **Add ou Supprimer les programmes** dans le panneau de contrôle.

> [!IMPORTANT]
> Pour Windows 7 et les systèmes d’exploitation antérieurs, désinstaller .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 ou 4.8 ne restaure pas les fichiers .NET Framework 4.5, et la désinstallation de .NET Framework 4.5 ne restaure pas les fichiers .NET Framework 4. Si vous souhaitez revenir à la version antérieure, vous devez la réinstaller et effectuer toutes les mises à jour correspondantes.

## <a name="appendix"></a>Annexe

### <a name="command-line-options"></a>Options de ligne de commande

Le tableau ci-dessous répertorie les options que vous pouvez inclure lorsque vous chaînez le package redistribuable .NET Framework 4.5 à l'installation de votre application.

|Option|Description|
|------------|-----------------|
|**/CEIPConsent**|Remplace le comportement par défaut et envoie des commentaires anonymes à Microsoft pour améliorer les futurs déploiements. Cette option peut être utilisée uniquement si l'utilisateur accepte d'envoyer des commentaires anonymes à Microsoft lorsqu'il y est invité par le programme d'installation.|
|**/chainingpackage** `packageName`|Spécifie le nom du fichier exécutable qui effectue le chaînage. Ces informations sont envoyées à Microsoft sous forme de commentaires anonymes pour améliorer les futurs déploiements.<br /><br /> Si le nom du package inclut des espaces, utilisez des guillemets doubles comme délimiteurs. Par exemple : **/chainingpackage "Lucerne Publishing"**. Pour un exemple d’un paquet d’enchaînement, voir [Obtenir des informations sur les progrès à partir d’un ensemble d’installation](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).|
|**/LCID**  `LCID`<br /><br /> où `LCID` spécifie un identificateur de paramètres régionaux (consultez la liste des [langues prises en charge](#supported-languages))|Installe le module linguistique spécifié par `LCID` et force l'affichage de l'interface utilisateur dans cette langue à moins que le mode silencieux soit défini.<br /><br /> Pour le programme d'installation web, cette option installe de manière chaînée le module linguistique à partir du web. **Remarque :**  Utilisez cette option uniquement avec le programme d’installation web.|
|**/log** `file` &#124; `folder`|Spécifie l'emplacement du fichier journal. L'emplacement par défaut est le répertoire temporaire du processus et le nom par défaut du fichier est basé sur le module. Si l'extension de fichier est .txt, un journal textuel est généré. Si vous spécifiez une autre extension ou aucune extension, un journal HTML est créé.|
|**/msioptions**|Spécifie les options à transmettre pour des éléments .msi et .msp ; par exemple : `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Empêche le programme d'installation de redémarrer automatiquement. Si vous utilisez cette option, l’application d’enchaînement doit capturer le code de retour et gérer le redémarrage (voir [Obtenir des informations de progrès à partir d’un package d’installation](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))).|
|**/passive**|Définit le mode passif. Affiche la barre de progression pour indiquer que l'installation est en cours, mais n'affiche aucune invite ni aucun message d'erreur pour l'utilisateur. Dans ce mode, lorsqu'il est chaîné par un programme d'installation, le package de chaînage doit gérer les [codes de retour](#return-codes).|
|**/pipe**|Crée un canal de communication pour permettre à un package de chaînage d'obtenir les données de progression.|
|**/promptrestart**|Mode passif uniquement, si le programme d'installation requiert un redémarrage, il invite l'utilisateur à redémarrer l'ordinateur. Cette option requiert une intervention de l'utilisateur si un redémarrage est requis.|
|**/q**|Active le mode silencieux.|
|**/réparation**|Déclenche la fonctionnalité de réparation.|
|**/serialdownload**|Force l'installation à démarrer une fois seulement que le package a été téléchargé.|
|**/showfinalerror**|Définit le mode passif. Affiche les erreurs uniquement si l'installation échoue. Cette option requiert une intervention de l'utilisateur si l'installation n'a pas réussi.|
|**/showrmui**|S’utilise uniquement avec l’option **/passive** . Affiche un message invitant les utilisateurs à fermer les applications .NET Framework en cours d'exécution. Ce message se comporte de la même manière en mode passif et non passif.|
|**/désinstaller**|Désinstalle le package redistribuable .NET Framework.|

### <a name="supported-languages"></a>Langues prises en charge

Le tableau suivant énumère .NET Packs de langue-cadre qui sont disponibles pour .NET Framework 4.5 et les versions ultérieures.

|LCID|Langue – pays/région|Culture|
|----------|--------------------------------|-------------|
|1025|Arabe - Arabie saoudite|ar|
|1028|Chinois – Traditionnel|zh-Hant|
|1029|Tchèque|cs|
|1030|Danois|da|
|1031|Allemand – Allemagne|de|
|1032|Grec|el|
|1035|Finnois|fi|
|1036|Français – France|fr|
|1037|Hébreu|he|
|1038|Hongrois|hu|
|1040|Italien – Italie|it|
|1041|Japonais|ja|
|1042|Coréen|ko|
|1043|Néerlandais – Pays-Bas|nl|
|1044|Norvégien (bokmål)|non|
|1045|Polonais|pl|
|1046|Portugais – Brésil|pt-br|
|1049|Russe|ru|
|1053|Suédois|sv|
|1055|Turc|tr|
|2052|Chinois – Simplifié|zh-Hans|
|2070|Portugais – Portugal|pt-PT|
|3082|Espagnol - Espagne (moderne)|es|

## <a name="see-also"></a>Voir aussi

- [Guide de déploiement pour les administrateurs](guide-for-administrators.md)
- [Exigences du système](../get-started/system-requirements.md)
- [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [Réduction des redémarrages système lors des installations du .NET Framework 4.5](reducing-system-restarts.md)
- [How to: Get Progress from the .NET Framework 4.5 Installer](how-to-get-progress-from-the-dotnet-installer.md)
