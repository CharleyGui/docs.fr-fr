---
title: 'Comment : installer et désinstaller des services Windows'
description: Consultez Comment installer et désinstaller des services Windows. Si vous développez un service Windows avec .NET, vous pouvez utiliser InstallUtil.exe ou PowerShell.
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 883b587a7ef60bc686d6f453c775f6651f0ccb7f
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063820"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="9eadd-104">Comment : installer et désinstaller des services Windows</span><span class="sxs-lookup"><span data-stu-id="9eadd-104">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="9eadd-105">Si vous développez un service Windows avec l' .NET Framework, vous pouvez installer rapidement votre application de service à l’aide de l’utilitaire de ligne de commande [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) ou de [PowerShell](/powershell/scripting/overview).</span><span class="sxs-lookup"><span data-stu-id="9eadd-105">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="9eadd-106">Les développeurs qui souhaitent libérer un service Windows que les utilisateurs peuvent installer et désinstaller peuvent utiliser l’ensemble d’outils [WiX](https://wixtoolset.org/) gratuit ou des outils commerciaux comme [Advanced installer](https://www.advancedinstaller.com/), [InstallShield](https://www.revenera.com/install/products/installshield.html), etc.</span><span class="sxs-lookup"><span data-stu-id="9eadd-106">Developers who want to release a Windows service that users can install and uninstall can use the free [WiX Toolset](https://wixtoolset.org/) or commercial tools like [Advanced Installer](https://www.advancedinstaller.com/), [InstallShield](https://www.revenera.com/install/products/installshield.html), or others.</span></span> <span data-ttu-id="9eadd-107">Pour plus d’informations, consultez [créer un package d’installation (Windows Desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="9eadd-107">For more information, see [Create an installer package (Windows desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

> [!WARNING]
> <span data-ttu-id="9eadd-108">Si vous voulez désinstaller un service de votre ordinateur, ne suivez pas les étapes décrites dans cet article.</span><span class="sxs-lookup"><span data-stu-id="9eadd-108">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="9eadd-109">Au lieu de cela, déterminez quel programme ou package logiciel a installé le service, puis choisissez **Applications** dans les paramètres pour désinstaller ce programme.</span><span class="sxs-lookup"><span data-stu-id="9eadd-109">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="9eadd-110">Notez que de nombreux services font partie intégrante de Windows. Si vous les supprimez, vous pouvez rendre le système instable.</span><span class="sxs-lookup"><span data-stu-id="9eadd-110">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="9eadd-111">Pour utiliser les étapes décrites dans cet article, vous devez d’abord ajouter un programme d’installation de service à votre service Windows.</span><span class="sxs-lookup"><span data-stu-id="9eadd-111">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="9eadd-112">Pour plus d’informations, consultez [procédure pas à pas : création d’une application de service Windows](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="9eadd-112">For more information, see [Walkthrough: Creating a Windows service app](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="9eadd-113">Vous ne pouvez pas exécuter les projets de service Windows directement à partir de l’environnement de développement Visual Studio en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="9eadd-113">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="9eadd-114">Avant de pouvoir exécuter le projet, vous devez installer le service dans le projet.</span><span class="sxs-lookup"><span data-stu-id="9eadd-114">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="9eadd-115">Vous pouvez utiliser l’**Explorateur de serveurs** pour vérifier que vous avez bien installé ou désinstallé le service.</span><span class="sxs-lookup"><span data-stu-id="9eadd-115">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="9eadd-116">Pour plus d’informations, consultez [Guide pratique pour utiliser l’Explorateur de serveurs dans Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9eadd-116">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="9eadd-117">Installer votre service manuellement à l’aide de l’utilitaire InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="9eadd-117">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="9eadd-118">Dans le menu **Démarrer** , sélectionnez le répertoire **Visual \<*version*> Studio** , puis sélectionnez \*\*invite de commandes développeur pour vs \<*version*> \*\*.</span><span class="sxs-lookup"><span data-stu-id="9eadd-118">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="9eadd-119">L’invite de commandes développeur pour Visual Studio s’affiche.</span><span class="sxs-lookup"><span data-stu-id="9eadd-119">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="9eadd-120">Accédez au répertoire dans lequel se trouve le fichier exécutable compilé de votre projet.</span><span class="sxs-lookup"><span data-stu-id="9eadd-120">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="9eadd-121">Exécutez *InstallUtil.exe* à partir de l’invite de commandes avec le fichier exécutable de votre projet en guise de paramètre :</span><span class="sxs-lookup"><span data-stu-id="9eadd-121">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="9eadd-122">Si vous utilisez l’invite de commandes développeur pour Visual Studio, *InstallUtil.exe* doit se trouver dans le chemin système.</span><span class="sxs-lookup"><span data-stu-id="9eadd-122">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="9eadd-123">Si ce n’est pas le cas, vous pouvez l’ajouter au chemin ou utiliser le chemin complet pour l’appeler.</span><span class="sxs-lookup"><span data-stu-id="9eadd-123">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="9eadd-124">Cet outil est installé avec le .NET Framework dans \*%windir%\Microsoft.NET\Framework [64] \\<framework_version \> \*.</span><span class="sxs-lookup"><span data-stu-id="9eadd-124">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="9eadd-125">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9eadd-125">For example:</span></span>
     - <span data-ttu-id="9eadd-126">Pour la version 32 bits de .NET Framework 4 ou 4.5 et ultérieur, si votre répertoire d’installation Windows est *C:\Windows*, le chemin par défaut est *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="9eadd-126">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="9eadd-127">Pour la version 64 bits de .NET Framework 4 ou 4.5 et ultérieur, le chemin par défaut est *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="9eadd-127">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="9eadd-128">Désinstaller manuellement votre service à l’aide de l’utilitaire InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="9eadd-128">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="9eadd-129">Dans le menu **Démarrer** , sélectionnez le répertoire **Visual \<*version*> Studio** , puis sélectionnez \*\*invite de commandes développeur pour vs \<*version*> \*\*.</span><span class="sxs-lookup"><span data-stu-id="9eadd-129">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="9eadd-130">L’invite de commandes développeur pour Visual Studio s’affiche.</span><span class="sxs-lookup"><span data-stu-id="9eadd-130">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="9eadd-131">Exécutez *InstallUtil.exe* à partir de l’invite de commandes avec la sortie de votre projet en guise de paramètre :</span><span class="sxs-lookup"><span data-stu-id="9eadd-131">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="9eadd-132">Après avoir supprimé l’exécutable d’un service, il est possible que ce service soit toujours présent dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="9eadd-132">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="9eadd-133">Si c’est le cas, utilisez la commande [sc delete](/windows-server/administration/windows-commands/sc-delete) pour supprimer l’entrée du service dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="9eadd-133">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="9eadd-134">Installer votre service manuellement à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9eadd-134">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="9eadd-135">Dans le menu **Démarrer** , sélectionnez le répertoire **Windows PowerShell** , puis sélectionnez **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="9eadd-135">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="9eadd-136">Accédez au répertoire dans lequel se trouve le fichier exécutable compilé de votre projet.</span><span class="sxs-lookup"><span data-stu-id="9eadd-136">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="9eadd-137">Exécutez l’applet de commande [**New-service**](/powershell/module/microsoft.powershell.management/new-service) avec avec la sortie de votre projet et un nom de service comme paramètres :</span><span class="sxs-lookup"><span data-stu-id="9eadd-137">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="9eadd-138">Désinstaller manuellement votre service à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9eadd-138">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="9eadd-139">Dans le menu **Démarrer** , sélectionnez le répertoire **Windows PowerShell** , puis sélectionnez **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="9eadd-139">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="9eadd-140">Exécutez l’applet de commande [**Remove-service**](/powershell/module/microsoft.powershell.management/remove-service) avec le nom de votre service comme paramètre :</span><span class="sxs-lookup"><span data-stu-id="9eadd-140">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="9eadd-141">Après avoir supprimé l’exécutable d’un service, il est possible que ce service soit toujours présent dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="9eadd-141">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="9eadd-142">Si c’est le cas, utilisez la commande [sc delete](/windows-server/administration/windows-commands/sc-delete) pour supprimer l’entrée du service dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="9eadd-142">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="9eadd-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eadd-143">See also</span></span>

- [<span data-ttu-id="9eadd-144">Présentation des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="9eadd-144">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="9eadd-145">Comment : créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="9eadd-145">How to: Create Windows services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="9eadd-146">Comment : ajouter des programmes d’installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="9eadd-146">How to: Add installers to your service application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="9eadd-147">Installutil.exe (outil d’installation)</span><span class="sxs-lookup"><span data-stu-id="9eadd-147">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
