---
title: Déboguer des applications .NET sur Raspberry pi
description: Découvrez comment déboguer des applications .NET sur Raspberry pi et des appareils similaires.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
zone_pivot_groups: ide-set-one
ms.openlocfilehash: 7b9872304ee53071452772e3da02081a7def4d80
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "96588570"
---
# <a name="debug-net-apps-on-raspberry-pi"></a>Déboguer des applications .NET sur Raspberry pi

Le débogage d’applications .NET exécutées sur des appareils IoT basés sur ARM comme Raspberry pi présente un défi unique. Il est possible de développer des applications .NET sur des appareils ARM. Toutefois, OmniSharp, qui est requis pour déboguer des applications .NET en dehors de Visual Studio, n’est pas compatible avec les appareils ARM. Par conséquent, les applications doivent être déboguées à distance à partir d’une plateforme compatible.

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a>Déboguer à partir de Visual Studio Code (multiplateforme)

Le débogage de .NET sur Raspberry pi à partir de Visual Studio Code nécessite des étapes de configuration sur Raspberry pi et dans le fichier du projet *launch.js* .

### <a name="enable-ssh-on-the-raspberry-pi"></a>Activer SSH sur le Raspberry pi

SSH est requis pour le débogage distant. Pour activer SSH, [reportez-vous à *activer SSH* dans la documentation Raspberry pi](https://www.raspberrypi.org/documentation/remote-access/ssh/) <span class="docon docon-navigate-external x-hidden-focus"></span> .

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a>Installer le Débogueur distant Visual Studio sur Raspberry pi

Dans une console bash sur le Raspberry pi (localement ou via SSH), procédez comme suit :

1. Exécutez la commande suivante pour télécharger et installer le Débogueur distant Visual Studio sur le Raspberry pi :

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. Le débogueur requiert l’exécution de en tant que `root` . Par défaut, n' `root` a pas de mot de passe sur Raspberry pi. Définissez un mot de passe pour `root` en exécutant la commande suivante et en suivant les invites.

    ```bash
    sudo passwd root
    ```

1. Visual Studio Code utilise le protocole SSH pour déboguer à distance. Pour des raisons de sécurité, `root` n’est pas autorisé à se connecter par le biais de ssh par défaut. Pour permettre `root` à de se connecter via SSH, procédez comme suit :

    1. Exécutez la commande suivante pour ouvrir */etc/ssh/sshd_config* dans [nano](https://www.nano-editor.org/docs.php) <span class="docon docon-navigate-external x-hidden-focus"></span> .

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. Appuyez sur <kbd>CTRL + W</kbd> et recherchez **PermitRootLogin**.
    1. Supprimez les marques de commentaire de la ligne avec **PermitRootLogin** si nécessaire.
    1. Modifiez la ligne comme suit :

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > S’il n’y a aucune ligne **PermitRootLogin** dans */etc/ssh/sshd_config*, ajoutez une nouvelle ligne avec la valeur indiquée ci-dessus.

    1. Appuyez sur <kbd>CTRL + X</kbd> pour quitter et enregistrer vos chances. Quand vous êtes invité à **enregistrer la mémoire tampon modifiée ?**, appuyez sur <kbd>Y</kbd> pour confirmer. Appuyez sur <kbd>entrée</kbd> pour confirmer le remplacement du fichier d’origine.
    1. Redémarrez Raspberry pi en exécutant la commande suivante :

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a>launch.jsdu programme d’installation dans Visual Studio Code

Ajoutez une configuration de lancement à lalaunch.jsdu projet *sur*. Si le projet n’a pas de *launch.jssur* le fichier, ajoutez-en un en basculant vers l’onglet **exécuter** , en sélectionnant **créer un launch.jssur le fichier**, puis en sélectionnant **.net** ou **.net Core** dans la boîte de dialogue.

La nouvelle configuration de *launch.jssur* doit se présenter comme suit :

```json
"configurations": [
    {
        "name": ".NET Core Launch (remote console)",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "/home/pi/.dotnet/dotnet",
        "args": ["/home/pi/sample/Sample.dll"],
        "cwd": "/home/pi/sample",
        "stopAtEntry": false,
        "console": "internalConsole",
        "pipeTransport": {
            "pipeCwd": "${workspaceFolder}",
            "pipeProgram": "C:\\Program Files\\PuTTY\\PLINK.EXE",
            "pipeArgs": [
                "-pw",
                "P@ssw0rd",
                "root@raspberrypi"
            ],
            "debuggerPath": "/home/pi/vsdbg/vsdbg"
        }
    },
```

Notez les points suivants :

- `program` est le chemin d’accès au Runtime .NET sur le pi.
- `args` est le chemin d’accès à l’assembly à déboguer sur pi.
- `cwd` Répertoire de travail à utiliser lors du lancement de l’application sur le pi.
- `pipeProgram` est le chemin d’accès à un client SSH sur l’ordinateur local.
- `pipeArgs` paramètres à transmettre au client SSH. Veillez à spécifier le paramètre de mot de passe, ainsi que l' `root` utilisateur au format `<user>@<hostname>` .

> [!IMPORTANT]
> L’exemple ci-dessus utilise *Plink*, un composant du client SSH [Putty](https://www.ssh.com/ssh/putty/) <span class="docon docon-navigate-external x-hidden-focus"></span> . [OpenSSH](https://www.openssh.com/) <span class="docon docon-navigate-external x-hidden-focus"></span> , qui est inclus dans les versions récentes de Windows et Linux, peut être utilisé à la place. Toutefois, OpenSSH ne prend pas en charge l’envoi de mots de passe en tant que paramètre de ligne de commande. Pour utiliser OpenSSH, [configurez votre Raspberry pi pour l’accès SSH avec mot de passe](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md) <span class="docon docon-navigate-external x-hidden-focus"></span> .

### <a name="deploy-the-app"></a>Déployer l’application

Déployez l’application comme décrit dans [déployer des applications .net vers Raspberry pi](deployment.md). Assurez-vous que le chemin de déploiement est le même que celui spécifié dans le `cwd` paramètre de la *launch.jssur* la configuration.

### <a name="launch-the-debugger"></a>Lancez le débogueur

Sous l’onglet **exécuter** , sélectionnez la configuration de **lancement de .net Core (console distante)** et sélectionnez **Démarrer le débogage**. L’application démarre sur le Raspberry pi. Le débogueur peut être utilisé pour définir des points d’arrêt, inspecter les variables locales, et bien plus encore.

## <a name="references"></a>References

[Débogage à distance avec vs code sur Windows sur un Raspberry pi à l’aide de .net Core sur ARM](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)<span class="docon docon-navigate-external x-hidden-focus"></span>

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a>Déboguer à partir de Visual Studio sur Windows

Visual Studio peut déboguer des applications .NET sur des appareils distants via SSH. Aucune configuration spécialisée n’est requise sur l’appareil. Pour plus d’informations sur l’utilisation de Visual Studio pour déboguer .NET à distance, consultez [Déboguer à distance .net sur Linux à l’aide de SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).

::: zone-end
