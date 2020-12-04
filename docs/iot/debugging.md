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
# <a name="debug-net-apps-on-raspberry-pi"></a><span data-ttu-id="b6db6-103">Déboguer des applications .NET sur Raspberry pi</span><span class="sxs-lookup"><span data-stu-id="b6db6-103">Debug .NET apps on Raspberry Pi</span></span>

<span data-ttu-id="b6db6-104">Le débogage d’applications .NET exécutées sur des appareils IoT basés sur ARM comme Raspberry pi présente un défi unique.</span><span class="sxs-lookup"><span data-stu-id="b6db6-104">Debugging .NET apps running on ARM-based IoT devices like Raspberry Pi presents a unique challenge.</span></span> <span data-ttu-id="b6db6-105">Il est possible de développer des applications .NET sur des appareils ARM.</span><span class="sxs-lookup"><span data-stu-id="b6db6-105">It is possible to develop .NET apps on ARM devices.</span></span> <span data-ttu-id="b6db6-106">Toutefois, OmniSharp, qui est requis pour déboguer des applications .NET en dehors de Visual Studio, n’est pas compatible avec les appareils ARM.</span><span class="sxs-lookup"><span data-stu-id="b6db6-106">However, OmniSharp, which is required for debugging .NET apps outside of Visual Studio, is not compatible with ARM devices.</span></span> <span data-ttu-id="b6db6-107">Par conséquent, les applications doivent être déboguées à distance à partir d’une plateforme compatible.</span><span class="sxs-lookup"><span data-stu-id="b6db6-107">As a result, apps must be debugged remotely from a compatible platform.</span></span>

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a><span data-ttu-id="b6db6-108">Déboguer à partir de Visual Studio Code (multiplateforme)</span><span class="sxs-lookup"><span data-stu-id="b6db6-108">Debug from Visual Studio Code (cross-platform)</span></span>

<span data-ttu-id="b6db6-109">Le débogage de .NET sur Raspberry pi à partir de Visual Studio Code nécessite des étapes de configuration sur Raspberry pi et dans le fichier du projet *launch.js* .</span><span class="sxs-lookup"><span data-stu-id="b6db6-109">Debugging .NET on Raspberry Pi from Visual Studio Code requires configuration steps on the Raspberry Pi and in the project's *launch.json* file.</span></span>

### <a name="enable-ssh-on-the-raspberry-pi"></a><span data-ttu-id="b6db6-110">Activer SSH sur le Raspberry pi</span><span class="sxs-lookup"><span data-stu-id="b6db6-110">Enable SSH on the Raspberry Pi</span></span>

<span data-ttu-id="b6db6-111">SSH est requis pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="b6db6-111">SSH is required for remote debugging.</span></span> <span data-ttu-id="b6db6-112">Pour activer SSH, [reportez-vous à *activer SSH* dans la documentation Raspberry pi](https://www.raspberrypi.org/documentation/remote-access/ssh/) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="b6db6-112">To enable SSH, [refer to *Enable SSH* in the Raspberry Pi documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a><span data-ttu-id="b6db6-113">Installer le Débogueur distant Visual Studio sur Raspberry pi</span><span class="sxs-lookup"><span data-stu-id="b6db6-113">Install the Visual Studio Remote Debugger on the Raspberry Pi</span></span>

<span data-ttu-id="b6db6-114">Dans une console bash sur le Raspberry pi (localement ou via SSH), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6db6-114">Within a Bash console on the Raspberry Pi (either locally or via SSH), complete the following steps:</span></span>

1. <span data-ttu-id="b6db6-115">Exécutez la commande suivante pour télécharger et installer le Débogueur distant Visual Studio sur le Raspberry pi :</span><span class="sxs-lookup"><span data-stu-id="b6db6-115">Execute the following command to download and install the Visual Studio Remote Debugger on the Raspberry Pi:</span></span>

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. <span data-ttu-id="b6db6-116">Le débogueur requiert l’exécution de en tant que `root` .</span><span class="sxs-lookup"><span data-stu-id="b6db6-116">The debugger requires running as `root`.</span></span> <span data-ttu-id="b6db6-117">Par défaut, n' `root` a pas de mot de passe sur Raspberry pi.</span><span class="sxs-lookup"><span data-stu-id="b6db6-117">By default, `root` has no password on Raspberry Pi.</span></span> <span data-ttu-id="b6db6-118">Définissez un mot de passe pour `root` en exécutant la commande suivante et en suivant les invites.</span><span class="sxs-lookup"><span data-stu-id="b6db6-118">Set a password for `root` by executing the following command and following the prompts.</span></span>

    ```bash
    sudo passwd root
    ```

1. <span data-ttu-id="b6db6-119">Visual Studio Code utilise le protocole SSH pour déboguer à distance.</span><span class="sxs-lookup"><span data-stu-id="b6db6-119">Visual Studio Code uses the SSH protocol to debug remotely.</span></span> <span data-ttu-id="b6db6-120">Pour des raisons de sécurité, `root` n’est pas autorisé à se connecter par le biais de ssh par défaut.</span><span class="sxs-lookup"><span data-stu-id="b6db6-120">For security purposes, `root` is not permitted to log on via SSH by default.</span></span> <span data-ttu-id="b6db6-121">Pour permettre `root` à de se connecter via SSH, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6db6-121">To enable `root` to log on via SSH, complete the following steps:</span></span>

    1. <span data-ttu-id="b6db6-122">Exécutez la commande suivante pour ouvrir */etc/ssh/sshd_config* dans [nano](https://www.nano-editor.org/docs.php) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="b6db6-122">Execute the following command to open */etc/ssh/sshd_config* in [nano](https://www.nano-editor.org/docs.php) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <span data-ttu-id="b6db6-123">Appuyez sur <kbd>CTRL + W</kbd> et recherchez **PermitRootLogin**.</span><span class="sxs-lookup"><span data-stu-id="b6db6-123">Press <kbd>Ctrl+W</kbd> and search for **PermitRootLogin**.</span></span>
    1. <span data-ttu-id="b6db6-124">Supprimez les marques de commentaire de la ligne avec **PermitRootLogin** si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b6db6-124">Uncomment the line with **PermitRootLogin** if needed.</span></span>
    1. <span data-ttu-id="b6db6-125">Modifiez la ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6db6-125">Change the line to read as follows:</span></span>

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > <span data-ttu-id="b6db6-126">S’il n’y a aucune ligne **PermitRootLogin** dans */etc/ssh/sshd_config*, ajoutez une nouvelle ligne avec la valeur indiquée ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="b6db6-126">If there is no **PermitRootLogin** line in */etc/ssh/sshd_config*, add a new line with the value shown above.</span></span>

    1. <span data-ttu-id="b6db6-127">Appuyez sur <kbd>CTRL + X</kbd> pour quitter et enregistrer vos chances.</span><span class="sxs-lookup"><span data-stu-id="b6db6-127">Press <kbd>Ctrl+X</kbd> to exit and save your chances.</span></span> <span data-ttu-id="b6db6-128">Quand vous êtes invité à **enregistrer la mémoire tampon modifiée ?**, appuyez sur <kbd>Y</kbd> pour confirmer.</span><span class="sxs-lookup"><span data-stu-id="b6db6-128">When prompted **Save modified buffer?**, press <kbd>Y</kbd> to confirm.</span></span> <span data-ttu-id="b6db6-129">Appuyez sur <kbd>entrée</kbd> pour confirmer le remplacement du fichier d’origine.</span><span class="sxs-lookup"><span data-stu-id="b6db6-129">Press <kbd>Enter</kbd> to confirm overwriting the original file.</span></span>
    1. <span data-ttu-id="b6db6-130">Redémarrez Raspberry pi en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b6db6-130">Reboot the Raspberry Pi by executing the following command:</span></span>

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a><span data-ttu-id="b6db6-131">launch.jsdu programme d’installation dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b6db6-131">Setup launch.json in Visual Studio Code</span></span>

<span data-ttu-id="b6db6-132">Ajoutez une configuration de lancement à lalaunch.jsdu projet *sur*.</span><span class="sxs-lookup"><span data-stu-id="b6db6-132">Add a launch configuration to the project's *launch.json*.</span></span> <span data-ttu-id="b6db6-133">Si le projet n’a pas de *launch.jssur* le fichier, ajoutez-en un en basculant vers l’onglet **exécuter** , en sélectionnant **créer un launch.jssur le fichier**, puis en sélectionnant **.net** ou **.net Core** dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b6db6-133">If the project doesn't have a *launch.json* file, add one by switching to the **Run** tab, selecting **create a launch.json file**, and selecting **.NET** or **.NET Core** in the dialog.</span></span>

<span data-ttu-id="b6db6-134">La nouvelle configuration de *launch.jssur* doit se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="b6db6-134">The new configuration in *launch.json* should look similar to this:</span></span>

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

<span data-ttu-id="b6db6-135">Notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="b6db6-135">Notice the following:</span></span>

- <span data-ttu-id="b6db6-136">`program` est le chemin d’accès au Runtime .NET sur le pi.</span><span class="sxs-lookup"><span data-stu-id="b6db6-136">`program` is the path to the .NET runtime on the Pi.</span></span>
- <span data-ttu-id="b6db6-137">`args` est le chemin d’accès à l’assembly à déboguer sur pi.</span><span class="sxs-lookup"><span data-stu-id="b6db6-137">`args` is the path to the assembly to debug on the Pi.</span></span>
- <span data-ttu-id="b6db6-138">`cwd` Répertoire de travail à utiliser lors du lancement de l’application sur le pi.</span><span class="sxs-lookup"><span data-stu-id="b6db6-138">`cwd` is the working directory to use when launching the app on the Pi.</span></span>
- <span data-ttu-id="b6db6-139">`pipeProgram` est le chemin d’accès à un client SSH sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b6db6-139">`pipeProgram` is the path to an SSH client on the local machine.</span></span>
- <span data-ttu-id="b6db6-140">`pipeArgs` paramètres à transmettre au client SSH.</span><span class="sxs-lookup"><span data-stu-id="b6db6-140">`pipeArgs` are the parameters to be passed to the SSH client.</span></span> <span data-ttu-id="b6db6-141">Veillez à spécifier le paramètre de mot de passe, ainsi que l' `root` utilisateur au format `<user>@<hostname>` .</span><span class="sxs-lookup"><span data-stu-id="b6db6-141">Be sure to specify the password parameter, as well as the `root` user in the format `<user>@<hostname>`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6db6-142">L’exemple ci-dessus utilise *Plink*, un composant du client SSH [Putty](https://www.ssh.com/ssh/putty/) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="b6db6-142">The above example uses *plink*, a component of the [PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span> SSH client.</span></span> <span data-ttu-id="b6db6-143">[OpenSSH](https://www.openssh.com/) <span class="docon docon-navigate-external x-hidden-focus"></span> , qui est inclus dans les versions récentes de Windows et Linux, peut être utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="b6db6-143">[OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span>, which is included in recent versions of Windows and Linux, may be used instead.</span></span> <span data-ttu-id="b6db6-144">Toutefois, OpenSSH ne prend pas en charge l’envoi de mots de passe en tant que paramètre de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b6db6-144">However, OpenSSH doesn't support sending passwords as a command-line parameter.</span></span> <span data-ttu-id="b6db6-145">Pour utiliser OpenSSH, [configurez votre Raspberry pi pour l’accès SSH avec mot de passe](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="b6db6-145">To use OpenSSH, [configure your Raspberry Pi for passwordless SSH access](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

### <a name="deploy-the-app"></a><span data-ttu-id="b6db6-146">Déployer l’application</span><span class="sxs-lookup"><span data-stu-id="b6db6-146">Deploy the app</span></span>

<span data-ttu-id="b6db6-147">Déployez l’application comme décrit dans [déployer des applications .net vers Raspberry pi](deployment.md).</span><span class="sxs-lookup"><span data-stu-id="b6db6-147">Deploy the app as described in [Deploy .NET apps to Raspberry Pi](deployment.md).</span></span> <span data-ttu-id="b6db6-148">Assurez-vous que le chemin de déploiement est le même que celui spécifié dans le `cwd` paramètre de la *launch.jssur* la configuration.</span><span class="sxs-lookup"><span data-stu-id="b6db6-148">Ensure the deployment path is the same path specified in the `cwd` parameter in the *launch.json* configuration.</span></span>

### <a name="launch-the-debugger"></a><span data-ttu-id="b6db6-149">Lancez le débogueur</span><span class="sxs-lookup"><span data-stu-id="b6db6-149">Launch the debugger</span></span>

<span data-ttu-id="b6db6-150">Sous l’onglet **exécuter** , sélectionnez la configuration de **lancement de .net Core (console distante)** et sélectionnez **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="b6db6-150">On the **Run** tab, select the **.NET Core Launch (remote console)** configuration and select **Start Debugging**.</span></span> <span data-ttu-id="b6db6-151">L’application démarre sur le Raspberry pi.</span><span class="sxs-lookup"><span data-stu-id="b6db6-151">The app launches on the Raspberry Pi.</span></span> <span data-ttu-id="b6db6-152">Le débogueur peut être utilisé pour définir des points d’arrêt, inspecter les variables locales, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="b6db6-152">The debugger may be used to set breakpoints, inspect locals, and more.</span></span>

## <a name="references"></a><span data-ttu-id="b6db6-153">References</span><span class="sxs-lookup"><span data-stu-id="b6db6-153">References</span></span>

<span data-ttu-id="b6db6-154">[Débogage à distance avec vs code sur Windows sur un Raspberry pi à l’aide de .net Core sur ARM](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="b6db6-154">[Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a><span data-ttu-id="b6db6-155">Déboguer à partir de Visual Studio sur Windows</span><span class="sxs-lookup"><span data-stu-id="b6db6-155">Debug from Visual Studio on Windows</span></span>

<span data-ttu-id="b6db6-156">Visual Studio peut déboguer des applications .NET sur des appareils distants via SSH.</span><span class="sxs-lookup"><span data-stu-id="b6db6-156">Visual Studio can debug .NET apps on remote devices via SSH.</span></span> <span data-ttu-id="b6db6-157">Aucune configuration spécialisée n’est requise sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="b6db6-157">No specialized configuration is required on the device.</span></span> <span data-ttu-id="b6db6-158">Pour plus d’informations sur l’utilisation de Visual Studio pour déboguer .NET à distance, consultez [Déboguer à distance .net sur Linux à l’aide de SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="b6db6-158">For details on using Visual Studio to debug .NET remotely, see [Remote debug .NET on Linux using SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span></span>

::: zone-end
