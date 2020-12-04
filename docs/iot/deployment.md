---
title: Déployer des applications .NET sur Raspberry pi
description: Découvrez comment déployer des applications .NET sur Raspberry pi.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96588683"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a>Déployer des applications .NET sur Raspberry pi

Le déploiement d’applications .NET vers Raspberry pi est identique à celui de toute autre plateforme. Votre application peut s’exécuter en mode de déploiement *autonome* ou *dépendant du Framework* . Chaque stratégie présente des avantages. Pour plus d’informations, consultez [vue d’ensemble de la publication d’applications .net](../core/deploying/index.md).

## <a name="deploying-a-framework-dependent-app"></a>Déploiement d’une application dépendante du Framework

Pour déployer votre application comme une application dépendante du Framework, procédez comme suit :

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. Installez .NET sur Raspberry pi à l’aide des [scripts dotnet-install](../core/tools/dotnet-install-script.md). Effectuez les étapes suivantes à partir d’une invite bash sur le Raspberry pi (local ou SSH) :
    1. Exécutez la commande suivante pour installer .NET :

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > Cela installe la dernière version. Si vous avez besoin d’une version spécifique, ajoutez `--version <VERSION>` à la fin, où `<VERSION>` correspond à la version de build spécifique.

    1. Pour simplifier la résolution des chemins d’accès, ajoutez une `DOTNET_ROOT` variable d’environnement et ajoutez le répertoire *. dotnet* à `$PATH` avec les commandes suivantes :

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. Vérifiez l’installation de .NET à l’aide de la commande suivante :

        ```dotnetcli
        dotnet --version
        ```

        Vérifiez que la version affichée correspond à la version que vous avez installée.

1. Publiez l’application sur l’ordinateur de développement comme suit, selon l’environnement de développement.
    - Si vous utilisez **Visual Studio**, [déployez l’application dans un dossier local](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019). Avant la publication, sélectionnez **modifier** dans le résumé du profil de publication et sélectionnez l’onglet **paramètres** . Assurez-vous que le **mode de déploiement** est défini sur dépendant du Framework et que *le* **Runtime cible** est défini sur *portable*.
    - Si vous utilisez l' **interface CLI .net**, utilisez la commande [dotnet Publish](../core/tools/dotnet-publish.md) . Aucun argument supplémentaire n’est requis.

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. À partir d’une invite bash sur le Raspberry pi (local ou SSH), exécutez l’application. Pour ce faire, définissez le dossier de déploiement en tant que répertoire actif et exécutez la commande suivante (où *HelloWorld.dll* est le point d’entrée de l’application) :

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a>Déploiement d’une application autonome

Pour déployer votre application en tant qu’application autonome, procédez comme suit :

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. Publiez l’application sur l’ordinateur de développement comme suit, selon l’environnement de développement.
    - Si vous utilisez **Visual Studio**, [déployez l’application dans un dossier local](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019). Avant la publication, sélectionnez **modifier** dans le résumé du profil de publication et sélectionnez l’onglet **paramètres** . Assurez-vous que le **mode de déploiement** est défini sur *autonome* et que le **Runtime cible** a la valeur *Linux-ARM*.
    - Si vous utilisez l' **interface CLI .net**, utilisez la commande [dotnet Publish](../core/tools/dotnet-publish.md) avec l' `-r linux-arm` argument :

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. À partir d’une invite bash sur le Raspberry pi (local ou SSH), exécutez l’application. Pour ce faire, définissez le répertoire actif sur l’emplacement de déploiement et procédez comme suit :
    1. Attribuez à l’exécutable l’autorisation *Execute* (où `HelloWorld` est le nom du fichier exécutable).

        ```bash
        chmod +x HelloWorld
        ```

    1. Exécutez le fichier exécutable.

        ```bash
        ./HelloWorld
        ```
