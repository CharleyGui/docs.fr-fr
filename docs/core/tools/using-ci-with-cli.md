---
title: Intégration continue (CI) avec des kit SDK .NET Core et des outils
description: Découvrez comment utiliser la kit SDK .NET Core et ses outils sur le serveur de builds avec intégration continue.
ms.date: 05/18/2017
ms.openlocfilehash: 6e23a21dd36422a095e56519c9aa28ce2549f7b2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451036"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Utilisation du SDK et des outils .NET Core avec l’intégration continue

Ce document décrit l’utilisation du SDK .NET Core et de ses outils sur un serveur de builds. L’ensemble d’outils .NET Core fonctionne à la fois de manière interactive, où un développeur saisit des commandes dans une invite de commandes, et de manière automatique, où un serveur d’intégration continue (CI) exécute un script de build. Les commandes, les options, les entrées et les sorties sont identiques, et les seuls éléments que vous fournissez sont un moyen d’acquérir les outils et un système pour générer votre application. Ce document se concentre sur les scénarios d’acquisition d’outils pour l’intégration continue. Il contient également des recommandations sur la façon de concevoir et de structurer vos scripts de build.

## <a name="installation-options-for-ci-build-servers"></a>Options d’installation pour les serveurs de builds avec intégration continue

### <a name="using-the-native-installers"></a>Utilisation de programmes d’installation natifs

Les programmes d’installation natifs sont disponibles pour macOS, Linux et Windows. Les programmes d’installation requièrent un accès administrateur (sudo) au serveur de builds. L’avantage d’utiliser un programme d’installation natif est qu’il installe toutes les dépendances natives requises pour l’exécution des outils. Les programmes d’installation natifs fournissent également une installation du kit SDK à l’échelle du système.

Les utilisateurs de macOS doivent utiliser les programmes d’installation PKG. Sous Linux, vous pouvez utiliser un gestionnaire de package basé sur les flux, tel que apt-get pour Ubuntu ou yum pour CentOS, ou vous pouvez utiliser directement les packages DEB ou RPM. Sous Windows, utilisez le programme d’installation MSI.

Les fichiers binaires stables les plus récents se trouvent sous [Téléchargements .NET](https://dotnet.microsoft.com/download). Si vous souhaitez utiliser les outils en version préliminaire les plus récents (et potentiellement instables), utilisez les liens fournis dans le [référentiel GitHub dotnet/core-sdk](https://github.com/dotnet/core-sdk#installers-and-binaries). Pour les distributions Linux, des archives `tar.gz` (également appelées `tarballs`) sont disponibles ; utilisez les scripts d’installation dans les archives pour installer .NET Core.

### <a name="using-the-installer-script"></a>Utilisation du script d’installation

L’utilisation du script d’installation permet une installation non administrative sur votre serveur de builds, ainsi qu’une automatisation facile pour obtenir les outils. Le script se charge de télécharger les outils et de les extraire dans un emplacement par défaut ou spécifié. Vous pouvez également spécifier la version des outils que vous souhaitez installer et si vous voulez installer le kit SDK complet ou uniquement le runtime partagé.

Le script d’installation est automatisé pour s’exécuter au début de la génération afin de récupérer et d’installer la version nécessaire du kit SDK. La *version souhaitée* est la version du kit SDK dont vos projets ont besoin pour être générés. Le script vous permet d’installer le kit SDK dans un répertoire local sur le serveur, d’exécuter les outils à partir de l’emplacement d’installation, puis de nettoyer (ou de laisser le service d’intégration continue nettoyer) une fois la génération terminée. Cela fournit à l’ensemble de votre processus de génération l’encapsulation et l’isolation requises. La documentation de référence sur le script d’installation est disponible dans l’article [dotnet-install](dotnet-install-script.md).

> [!NOTE]
> **Azure DevOps Services**
>
> Lorsque vous utilisez le script d’installation, les dépendances natives ne sont pas installées automatiquement. Vous devez installer les dépendances natives si le système d’exploitation ne les possède pas. Pour plus d’informations, consultez [.net Core Dependencies and Requirements](../install/dependencies.md).

## <a name="ci-setup-examples"></a>Exemples de configuration de l’intégration continue

Cette section décrit une configuration manuelle à l’aide d’un script PowerShell ou bash, et contient la description de plusieurs solutions d’intégration continue SaaS (logiciel en tant que service). Les solutions d’intégration continue SaaS traitées sont [CI Travis](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/) et [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

### <a name="manual-setup"></a>Configuration manuelle

Chaque service SaaS dispose de ses propres méthodes pour créer et configurer un processus de génération. Si vous utilisez une solution SaaS différente de celles répertoriées ou si vous avez besoin d’une personnalisation qui va au-delà de la prise en charge prédéfinie, vous devez effectuer une configuration manuelle.

En règle générale, une configuration manuelle vous oblige à acquérir une version des outils (ou les versions les plus récentes des outils générées de nuit) et à exécuter votre script de build. Vous pouvez utiliser un script PowerShell ou bash pour orchestrer les commandes .NET Core ou vous pouvez utiliser un fichier projet qui décrit le processus de génération. La [section sur l’orchestration](#orchestrating-the-build) fournit plus de détails sur ces options.

Après avoir créé un script qui exécute une configuration manuelle du serveur de builds CI, utilisez-le sur votre machine de développement afin de générer votre code localement à des fins de test. Après avoir confirmé que le script s’exécute correctement localement, déployez-le sur votre serveur de builds CI. Un script PowerShell relativement simple illustre comment obtenir le kit SDK .NET Core et l’installer sur un serveur de builds Windows :

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

Vous fournissez l’implémentation pour votre processus de génération à la fin du script. Le script acquiert les outils, puis exécute votre processus de génération. Pour les ordinateurs UNIX, le script bash suivant effectue les actions décrites dans le script PowerShell de la même manière :

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a>Travis CI

Vous pouvez configurer [CI Travis](https://travis-ci.org/) pour installer le kit SDK .NET Core à l’aide du langage `csharp` et de la clé `dotnet`. Pour plus d’informations, consultez les documents officiels sur CI Travis sous [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) (Générer un projet C#, F# ou Visual Basic). Remarque : lorsque vous accédez aux informations sur CI Travis, l’identificateur de langage `language: csharp` entretenu par la communauté fonctionne pour tous les langages .NET, notamment F# et Mono.

CI Travis exécute à la fois les travaux macOS et Linux dans une *matrice de builds*, où vous spécifiez une combinaison de runtime, d’environnement et d’exclusions/inclusions pour couvrir les combinaisons de build pour votre application. Pour plus d’informations, consultez l’article [Personnalisation de la build](https://docs.travis-ci.com/user/customizing-the-build) dans la documentation CI Travis. Les outils MSBuild incluent les runtimes LTS (1.0.x) et Current (1.1.x) dans le package ; donc, en installant le kit SDK, vous recevez tout ce dont vous avez besoin pour la génération.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) installe le kit SDK .NET Core 1.0.1 avec l’image de travail de la build `Visual Studio 2017`. D’autres images de la build avec différentes versions du SDK .NET Core sont disponibles. Pour plus d’informations, consultez l’[exemple appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) et l’article [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) dans la documentation AppVeyor.

Les fichiers binaires du kit SDK .NET Core sont téléchargés et décompressés dans un sous-répertoire à l’aide du script d’installation, puis ils sont ajoutés à la variable d’environnement `PATH`. Ajoutez une matrice de builds pour exécuter des tests d’intégration avec plusieurs versions du SDK .NET Core :

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Azure DevOps Services

Configurez Azure DevOps Services pour générer des projets .NET Core à l’aide de l’une des méthodes suivantes :

1. Exécutez le script à partir de [l’étape de configuration manuelle](#manual-setup) en utilisant vos commandes.
1. Créez une build composée de plusieurs tâches de build intégrées Azure DevOps Services qui sont configurées pour utiliser les outils .NET Core.

Les deux solutions sont valides. À l’aide d’un script de configuration manuelle, vous contrôlez la version des outils que vous recevez, car vous les téléchargez dans le cadre de la génération. La build est exécutée à partir d’un script que vous devez créer. Cet article couvre uniquement l’option manuelle. Pour plus d’informations sur la composition d’une build avec les tâches de génération Azure DevOps Services, consultez la documentation [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

Pour utiliser un script de configuration manuelle dans Azure DevOps Services, créez une nouvelle définition de build et spécifiez le script à exécuter pour l’étape de génération. Cette opération est possible grâce à l’interface utilisateur Azure DevOps Services :

1. Commencez par créer une nouvelle définition de build. Lorsque vous atteignez l’écran qui vous permet de définir le type de build que vous souhaitez créer, sélectionnez l’option **Empty** (Vide).

   ![Sélection d’une définition de build vide](./media/using-ci-with-cli/select-empty-build-definition.png)

1. Après avoir configuré le référentiel à générer, vous êtes dirigé vers les définitions de la build. Sélectionnez **Ajouter une étape de build** :

   ![Ajout d’une étape de build](./media/using-ci-with-cli/add-build-step.png)

1. Le **catalogue de tâches** s’affiche. Le catalogue contient les tâches que vous utilisez dans la build. Étant donné que vous avez un script, sélectionnez le bouton **Ajouter** pour **PowerShell : exécuter un script PowerShell**.

   ![Ajout d’une étape de script PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. Configurez l’étape de build. Ajoutez le script à partir du référentiel que vous générez :

   ![Spécification du script PowerShell à exécuter](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Orchestration de la build

Ce document décrit principalement comment obtenir les outils .NET Core et configurer différents services d’intégration continue sans fournir d’informations sur la façon d’orchestrer ou de *réellement générer* votre code avec .NET Core. Les choix sur la façon de structurer le processus de génération dépendent de nombreux facteurs qui ne peuvent pas être traités ici d’une manière générale. Pour plus d’informations sur l’orchestration de vos builds avec chaque technologie, explorez les ressources et les exemples fournis dans la documentation de [CI Travis](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/) et [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

L’utilisation directe de MSBuild ou l’utilisation des commandes de ligne de commande .NET Core constituent les deux méthodes générales que vous utilisez afin de structurer le processus de génération pour le code .NET Core à l’aide des outils .NET Core. La méthode que vous choisissez dépend de votre niveau d’assurance et des compromis en matière de complexité. MSBuild vous permet d’exprimer votre processus de génération sous la forme de tâches et de cibles, mais vous devez vous familiariser avec la syntaxe de fichier projet MSBuild complexe. L’utilisation des outils de ligne de commande .NET Core est peut-être plus simple, mais vous devez écrire une logique d’orchestration dans un langage de script comme `bash` ou PowerShell.

## <a name="see-also"></a>Voir aussi

- [Téléchargements .NET - Linux](https://dotnet.microsoft.com/download?initial-os=linux)
