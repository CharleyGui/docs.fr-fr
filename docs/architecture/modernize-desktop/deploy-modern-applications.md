---
title: Déploiement d’applications de bureau modernes
description: Tout ce que vous devez savoir sur le déploiement d’applications de bureau modernes.
ms.date: 05/12/2020
ms.openlocfilehash: ba47f09b27adf270734bbfff285fe44dd4175d29
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615852"
---
# <a name="deploying-modern-desktop-applications"></a>Déploiement d’applications de bureau modernes

Lorsque vous développez des applications de bureau, il est important de tenir compte de la façon dont votre application va être empaquetée et déployée sur les ordinateurs des utilisateurs. Le problème de l’empaquetage, du déploiement et de l’installation est qu’il se trouve généralement dans le cadre des professionnels de l’informatique, qui s’occupent de choses différentes que les développeurs.

Aujourd’hui, nous nous sommes familiers du concept DevOps, où les développeurs et les professionnels de l’informatique travaillent étroitement pour déplacer des applications vers leurs environnements de production. Mais si vous êtes dans la bataille du Bureau depuis plus de 10 ans, vous avez peut-être vu l’histoire suivante. Une équipe de développeurs travaille difficilement pour répondre aux échéances du projet. Les utilisateurs professionnels sont nerveux, car ils ont besoin du système qui travaille sur les ordinateurs de plusieurs utilisateurs pour exécuter l’entreprise. Sur « D-Day », le chef de projet vérifie avec chaque développeur que son code fonctionne correctement et que tout est parfait, afin qu’il puisse être livré. L’équipe du package est ensuite chargée de générer le programme d’installation de l’application, de la distribuer à chaque ordinateur utilisateur et à un ensemble d’utilisateurs de test d’exécuter l’application. Bien, elles essaient, car avant d’illustrer une interface utilisateur, l’application lève une exception qui indique « méthode ~ de l’objet ~ échec ». La panique commence par l’air et une brève investigation pointe vers un développeur jeune et fatigué qui a introduit un contrôle tiers, qui a certainement « fonctionné sur l’ordinateur de développement ».

L’installation d’applications de bureau a traditionnellement été un cauchemar pour deux raisons principales :

- Absence de culture de collaboration étroite entre les équipes de développement et informatiques.
- Il n’y a pas d’empaquetage solide et de technologie de déploiement que nous pouvons créer.

En fait, nous sommes à l’esprit que, parfois, vous regrettez l’installation d’une application, car :

- Cela finit par avoir des effets secondaires indésirables sur votre ordinateur.
- Certaines applications qui ont été installées précédemment cessent de fonctionner.

En outre, vous ne pouvez pas simplement restaurer le système à son état d’origine en désinstallant l’application. Nous sommes tellement utilisés pour vivre cette situation et nous avons des termes tels que « l’enfer des DLL » ou « Winrot ».

Dans ce chapitre, nous aborderons MSIX. MSIX est la toute nouvelle technologie de Microsoft qui tente de capturer le meilleur des technologies précédentes pour fournir une base solide pour la technologie d’empaquetage du futur.

Qu’est-ce qu’une technologie de Packaging doit faire avec modernisation ? Eh bien, il s’avère que l’empaquetage est fondamental pour l’informatique d’entreprise avec un grand nombre d’argent investi. La modernisation n’est pas uniquement liée à l’utilisation des dernières technologies. Elle est également liée à la réduction du délai de commercialisation à partir du moment où une exigence métier est définie jusqu’à ce que votre entreprise remette la fonctionnalité à votre client.

## <a name="the-modern-application-lifecycle"></a>Cycle de vie des applications modernes

Aujourd’hui, les développeurs écrivent et génèrent le code d’une application, puis transmettent les ressources générées aux professionnels de l’informatique. Ensuite, les professionnels de l’informatique reconfigurent l’application et la reconditionnent, généralement dans un fichier MSI ou plus récemment, dans un format d’empaquetage App-V. L’application est ensuite déployée via différents canaux et outils. L’un des principaux problèmes de cette approche est communément appelé « empaquetage ». Le problème est que ce cycle se répète chaque fois qu’une mise à jour d’application ou une mise à jour du système d’exploitation.

Vous pouvez voir le processus reflété sur l’image suivante :

![Diagramme montrant le cycle de vie informatique moderne](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

Les entreprises ont besoin d’un moyen de casser ce cycle de Packaging en trois cycles indépendants :

- Mises à jour de système d’exploitation
- Mises à jour d’application
- Personnalisation

![Diagramme montrant le cycle vertueux moderne](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

Le diagramme précédent montre que vous pouvez :

- Mettez à jour le système d’exploitation sous-jacent sans avoir à reconditionner vos applications.
- Activez les personnalisations sans avoir à reconditionner le package de développement d’origine.

Cette modification radicale nous amène au nouveau cycle de vie informatique moderne, tel qu’indiqué dans l’image suivante :

![Diagramme montrant le cycle de vie de l’application à l’aide des outils Microsoft](./media/deploy-modern-applications/microsoft-it-tools.png)

Les développeurs créent l’application et génèrent un package MSIX que les professionnels de l’informatique peuvent utiliser et configurer sans avoir à reconditionner. Avec la technologie MSIX, Microsoft a créé des outils pour lui permettre de personnaliser et de configurer des packages sans réintégration.

## <a name="msix-the-next-generation-of-deployment"></a>MSIX : la prochaine génération de déploiement

Avant MSIX, plusieurs technologies de Packaging étaient disponibles, comme les assistants d’installation, MSI, ClickOnce, App-V et les scripts. Chacune de ces technologies a ses propres forces et Microsoft a décidé de choisir le meilleur de tout pour créer des MSIX. MSIX repose sur les fondements de ces technologies existantes qui sélectionnent le meilleur de chacun :

- App-V = \> conteneur
- ClickOnce = \> mise à jour automatique
- MSI = \> facile à distribuer

Avec MSIX, vous bénéficiez d’une technologie de programme d’installation avec toutes ces fonctionnalités.

![Diagramme montrant les différentes technologies qui ont eu un impact sur la création de MSIX](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a>Avantages de MSIX

#### <a name="never-regret-installing-an-app"></a>Vous ne regrettez pas l’installation d’une application

MSIX fournit un déploiement prévisible, fiable et sécurisé. La méthode déclarative contenue dans le manifeste du package permet au système d’exploitation d’effectuer le suivi de chaque ressource dont votre application a besoin. Il fournit également une véritable désinstallation propre sans effets secondaires.

#### <a name="disk-space-optimization"></a>Optimisation de l’espace disque

MSIX est optimisé pour réduire l’encombrement qu’une application a sur l’espace disque de l’utilisateur. Il crée un stockage d’instance unique de vos fichiers. Autrement dit, si vous avez deux packages différents avec la même DLL, la DLL n’est pas installée deux fois. La plateforme s’occupe de ce problème, car elle connaît tous les fichiers qu’une application particulière a installés grâce à sa nature déclarative. Elle vous permet également d’avoir différentes versions d’une DLL qui fonctionnent côte à côte.

Avec l’utilisation de packages de ressources, vous pouvez facilement créer des applications multilingues et le système d’exploitation s’occupe de l’installation de celles qui sont utilisées.

#### <a name="network-optimization"></a>Optimisation du réseau

MSIX détecte les différences sur les fichiers au niveau du bloc d’octets, ce qui active une fonctionnalité appelée mises à jour différentielles. Cela signifie que seuls les blocs d’octets mis à jour sont téléchargés sur les mises à jour d’application.

![Diagramme qui montre comment MSIX gère les mises à jour différentielles](./media/deploy-modern-applications/msix-managing-updates.png)

Avec l’installation de streaming, l’utilisateur peut rapidement commencer à travailler sur votre application, tandis que d’autres parties de l’application sont téléchargées en arrière-plan. Cette fonctionnalité contribue à une expérience attrayante pour vos utilisateurs.

Avec la fonctionnalité de packages facultatives, vous obtenez une composante de votre déploiement d’application, afin de pouvoir les télécharger si nécessaire.

#### <a name="simple-packaging-and-deployment"></a>Empaquetage et déploiement simples

Le AppManifest déclare le contrôle de version, le ciblage de périphérique et l’identification de manière standard pour chaque application. Il fournit également un moyen de signer vos ressources en fournissant une base solide de sécurité.

#### <a name="os-managed"></a>Géré par le système d’exploitation

Le système d’exploitation gère tous les processus d’installation, de mise à jour et de suppression d’une application. Les applications sont installées par utilisateur, mais ne sont téléchargées qu’une seule fois, ce qui réduit l’encombrement du disque. Microsoft travaille sur la fourniture de l’expérience MSIX sur Windows 7.

#### <a name="windows-provides-integrity-for-the-app"></a>Windows fournit l’intégrité de l’application

Avec l’utilisation de signatures numériques, vous pouvez vous assurer que vous n’installez pas une application à partir de sources non approuvées. MSIX empêche également la falsification en raison des éléments suivants :

- Il conserve un enregistrement des hachages de fichier.
- Elle détecte si un fichier a été modifié après l’installation.

#### <a name="works-for-the-entire-app-catalog"></a>Fonctionne pour l’intégralité du catalogue d’applications

L’un des aspects les plus intéressants de MSIX est qu’il fonctionne pour l’intégralité du catalogue d’applications, Windows Forms, WPF, MFC/ATL, Delphi, même si vous souhaitez effectuer un déploiement xCopy, ClickOnce ou accéder au magasin, vous pouvez utiliser le même package MSIX.

### <a name="tools"></a>Outils

#### <a name="windows-application-packaging-project"></a>Projet de création de package d’application Windows

Vous pouvez utiliser le **Projet d’empaquetage d’applications Windows** dans Visual Studio afin de générer un package pour votre application de bureau. Vous pouvez ensuite publier ce package sur le Microsoft Store ou le chargement sur un ou plusieurs PC.

#### <a name="msix-packaging-tool"></a>Outil d’empaquetage MSIX

L’outil MSIX Packaging Tool vous permet de générer un nouveau package pour vos applications Win32 au format MSIX. Il offre à la fois une interface utilisateur interactive et une ligne de commande pour les conversions et vous donne la possibilité de convertir une application sans avoir le code source.

![Outil d’empaquetage MSIX](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a>Framework de prise en charge de package

L’infrastructure de prise en charge des packages est un kit Open source qui vous permet d’appliquer des correctifs à votre application Win32 existante lorsque vous n’avez pas accès au code source, afin qu’il puisse s’exécuter dans un conteneur MSIX. Le Framework de prise en charge de package aide votre application à respecter les bonnes pratiques de l’environnement d’exécution moderne.

#### <a name="app-installer"></a>Programme d’installation d’application

Le programme d’installation de l’application permet d’installer les applications Windows 10 en double-cliquant sur le package d’application. Cela signifie que les utilisateurs n’ont pas besoin d’utiliser PowerShell ou d’autres outils de développement pour déployer des applications Windows 10. Le programme d’installation de l’application peut également installer une application à partir du Web, des packages facultatifs et des jeux associés.

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a>Comment créer un package MSIX à partir d’une application de bureau Win32 existante

Passons en revue le processus de création d’un package MSIX à partir d’une application Win32 existante. Dans cet exemple, nous allons utiliser une application Windows Forms.

Pour commencer, ajoutez un nouveau projet à votre solution, sélectionnez le projet de création de packages d’applications Windows et donnez-lui un nom.

![Ajout d’un nouveau projet d’empaquetage d’applications Windows](./media/deploy-modern-applications/add-packaging-project.png)

Vous verrez la structure du projet de Packaging et vous noterez un dossier spécial appelé *applications*. À l’intérieur de ce dossier, vous pouvez spécifier les applications que vous souhaitez inclure dans le package. Il peut être supérieur à un.

![Structure du projet de Packaging](./media/deploy-modern-applications/packaging-project.png)

Cliquez avec le bouton droit sur le dossier *applications* et sélectionnez le projet Windows Forms que vous souhaitez empaqueter à partir de la solution Visual Studio.

![Ajout du projet Windows Forms au projet d’empaquetage](./media/deploy-modern-applications/add-winforms-project.png)

À ce stade, vous pouvez compiler et générer le package, mais examinons quelques éléments. Pour une meilleure expérience utilisateur, Visual Studio peut générer automatiquement toutes les ressources visuelles dont une application moderne a besoin pour gérer les icônes et les éléments multimédias de mosaïques pour la barre de vignette et le menu Démarrer. Ouvrez le fichier *Package. appxmanifest* pour accéder au concepteur de manifeste. Vous pouvez ensuite générer toutes les ressources visuelles d’une image donnée présentes sur votre projet en cliquant simplement sur **créer**.

![Capture d’écran du concepteur de manifeste dans Visual Studio](./media/deploy-modern-applications/manifest-designer.png)

Si vous ouvrez le code du fichier *Package. appxmanifest* , vous pouvez voir quelques éléments intéressants.

Juste sous `<Package>` , il y a un `<Identity>` nœud. C’est ici que votre application empaquetée va récupérer son identité, qui sera gérée par le système d’exploitation.

![Nœud d’identité](./media/deploy-modern-applications/identity-node.png)

Dans le `<Capabilities>` nœud, vous pouvez trouver toutes les exigences dont l’application a besoin, en faisant particulièrement attention au `<rescap:Capability Name="runFullTrust" \>` , qui indique au système d’exploitation d’exécuter l’application en mode de confiance totale dans la mesure où il s’agit d’une application Win32.

![Nœud fonctionnalités](./media/deploy-modern-applications/capabilities-node.png)

Définissez le projet de Packaging comme projet de démarrage pour la solution et sélectionnez *exécuter*. Cela va à :

- Compilez l’application Windows Forms.
- Créez un package MSIX à partir des résultats de la génération.
- Déployez les packages.
- Installez-la localement sur l’ordinateur de développement.
- Lancer l’application.

![Notre application installée](./media/deploy-modern-applications/our-installed-application.png)

Avec cela, vous bénéficiez de l’expérience d’installation et de désinstallation propre que MSIX fournit entièrement intégré à Windows 10.

La dernière étape concerne la façon dont vous déployez le package MSIX sur un autre ordinateur.

Cliquez avec le bouton droit sur le projet Packaging, sélectionnez le menu **Store** , puis sélectionnez l’option **créer des packages d’application** .

Ensuite, vous pouvez choisir entre la création d’un package à charger dans le magasin ou la création de packages pour chargement. Dans la plupart des scénarios de modernisation, vous choisirez de **créer des packages pour chargement**.

![Configuration des packages](./media/deploy-modern-applications/configuring-packages.png)

Vous pouvez sélectionner les différentes architectures que vous souhaitez cibler, car vous pouvez inclure autant de que vous le souhaitez dans le même package MSIX.

La dernière étape consiste à déclarer où vous souhaitez déployer les ressources d’installation finales.

![Configurer les paramètres de mise à jour](./media/deploy-modern-applications/configure-update-settings.png)

Vous pouvez choisir d’utiliser un serveur Web d’un chemin d’accès UNC partagé sur vos serveurs de fichiers d’entreprise. Faites attention aux paramètres pour spécifier la façon dont vous souhaitez mettre à jour votre application. Nous allons aborder les mises à jour d’application dans la section suivante.

Pour obtenir un guide pas à pas détaillé, consultez [empaqueter une application de bureau à partir du code source à l’aide de Visual Studio](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).

## <a name="auto-updates-in-msix"></a>Mises à jour automatiques dans MSIX

Le Windows Store dispose d’un mécanisme de mise à jour remarquable utilisant Windows Update. Dans la plupart des scénarios d’entreprise, vous n’utilisez pas le Windows Store pour distribuer vos applications de bureau. Par conséquent, vous avez besoin d’un moyen similaire pour configurer des mises à jour pour votre application et les tirer à vos utilisateurs.

À l’aide d’une combinaison de fonctionnalités Windows 10 et de packages MSIX, vous pouvez fournir une grande expérience de mise à jour à vos utilisateurs. En fait, l’utilisateur n’a pas besoin d’être technique du tout, tout en continuant à bénéficier d’une expérience de mise à jour d’application transparente.

Vous pouvez configurer vos mises à jour pour interagir avec l’utilisateur de deux manières différentes :

- Mises à jour demandées par l’utilisateur : le système d’exploitation affiche une interface utilisateur intéressante générée automatiquement pour informer l’utilisateur de l’installation de l’application. Il génère cette interface utilisateur en fonction des propriétés que vous spécifiez sur vos fichiers d’installation.

- Mises à jour silencieuses en arrière-plan. Avec cette option, vos utilisateurs n’ont pas besoin de connaître les mises à jour.

Vous pouvez également configurer le moment où vous souhaitez effectuer des mises à jour, lorsque l’application démarre ou régulièrement. Grâce aux fonctionnalités de chargement indépendant, vous pouvez même recevoir ces mises à jour pendant l’exécution de l’application.

Lorsque vous utilisez ce type de déploiement, un fichier spécial est créé, appelé *. appinstaller*. Ce fichier simple contient les sections suivantes :

- Emplacement du fichier *. appinstaller*
- Propriétés principales du package MSIX de l’application
- Comportement de mise à jour

![fichier. appinstaller](./media/deploy-modern-applications/appinstaller-file.png)

En association avec ce fichier, Microsoft a conçu un protocole d’URL spécial pour lancer le processus d’installation à partir d’un lien :

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

Ce protocole fonctionne sur tous les navigateurs et lance le processus d’installation avec une expérience utilisateur exceptionnelle sur Windows 10. Étant donné que le système d’exploitation gère le processus d’installation, il est conscient de l’emplacement à partir duquel cette application a été installée et effectue le suivi de tous les fichiers affectés par le processus.

MSIX crée une interface utilisateur pour l’installation, en présentant automatiquement certaines propriétés du package. Cela permet une expérience d’installation commune pour chaque application.

Une fois que vous avez généré le nouveau package MSIX et que vous l’avez déplacé vers le serveur de déploiement, il vous suffit de modifier le fichier *. appinstaller* pour refléter ces modifications, principalement la version et le chemin d’accès au nouveau fichier MSIX. La prochaine fois que l’utilisateur lance l’application, le système va détecter la modification et télécharger les fichiers pour la nouvelle version en arrière-plan. Une fois cette opération effectuée, l’installation s’exécutera sur le nouveau lancement de l’application de manière transparente pour votre utilisateur.

>[!div class="step-by-step"]
>[Précédent](example-migration.md)
