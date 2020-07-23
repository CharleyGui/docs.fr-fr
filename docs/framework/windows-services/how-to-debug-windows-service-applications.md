---
title: 'Procédure : déboguer les applications de service Windows'
description: Découvrez comment déboguer des applications de service Windows, qui ne sont pas aussi simples à déboguer que les autres types d’applications Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: fb58f2ff4f480347f0f233ecd9a619cf287cfdfd
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925759"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="5dc6f-103">Procédure : déboguer les applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="5dc6f-103">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="5dc6f-104">Un service doit être exécuté à partir du Gestionnaire de contrôle des services plutôt qu'à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-104">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="5dc6f-105">C'est pourquoi le débogage d'un service n'est pas aussi simple que le débogage d'autres types d'applications Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-105">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="5dc6f-106">Pour déboguer un service, vous devez le démarrer et attacher un débogueur au processus dans lequel il s'exécute.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-106">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="5dc6f-107">Vous pouvez alors déboguer votre application à l'aide de toutes les fonctionnalités de débogage standard de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-107">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5dc6f-108">Avant de procéder à cet attachement, vérifiez en quoi consiste le processus concerné et pesez bien les conséquences de cette opération qui risque de supprimer le processus.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-108">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="5dc6f-109">Par exemple, si vous effectuez un attachement au processus WinLogon et que vous interrompez ensuite le débogage, le système s'arrête, car il ne peut pas fonctionner sans WinLogon.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-109">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="5dc6f-110">Vous ne pouvez attacher le débogueur qu'à un service en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-110">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="5dc6f-111">Le processus d'attachement interrompt le fonctionnement actuel de votre service ; il n'a pas pour effet de l'arrêter ni d'en suspendre le traitement.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-111">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="5dc6f-112">Autrement dit, si votre service est en cours d'exécution lorsque vous commencez le débogage, il se trouve toujours techniquement à l'état Démarré pendant que vous le déboguez, mais son traitement est suspendu.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-112">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="5dc6f-113">Après avoir effectué l'attachement au processus, vous pouvez définir des points d'arrêt et les utiliser pour déboguer votre code.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-113">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="5dc6f-114">Une fois que vous quittez la boîte de dialogue utilisée pour faire l'attachement au processus, vous êtes en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-114">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="5dc6f-115">Vous pouvez utiliser le Gestionnaire de contrôle des services pour démarrer, arrêter, interrompre et continuer votre service, en accédant aux points d'arrêt que vous avez définis.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-115">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="5dc6f-116">Quand le débogage est terminé, vous pouvez supprimer le service factice.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-116">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="5dc6f-117">Cet article décrit le débogage d'un service qui est en cours d'exécution sur l'ordinateur local, mais vous pouvez également déboguer des services Windows qui s'exécutent sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-117">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="5dc6f-118">Consultez [débogage distant](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-118">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5dc6f-119">Le débogage de la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> peut s'avérer difficile, car le Gestionnaire de contrôle des services impose un délai de 30 secondes pour toute tentative de démarrage d'un service.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-119">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="5dc6f-120">Pour plus d’informations, consultez [Résolution des problèmes : débogage des services Windows](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-120">For more information, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="5dc6f-121">Pour obtenir des informations significatives pour le débogage, le débogueur Visual Studio doit rechercher les fichiers de symboles pour les fichiers binaires qui sont en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-121">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="5dc6f-122">Si vous déboguez un service que vous avez généré dans Visual Studio, les fichiers de symboles (fichiers .pdb) se trouvent dans le même dossier que l'exécutable ou la bibliothèque, et le débogueur les charge automatiquement.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-122">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="5dc6f-123">Si vous déboguez un service que vous n'avez pas généré, vous devez d'abord rechercher des symboles pour le service, puis vous assurer qu'ils sont accessibles par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-123">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="5dc6f-124">Consultez [Spécifier les fichiers de symboles (.pdb) et les fichiers sources dans le débogueur Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-124">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="5dc6f-125">Si vous déboguez un processus système ou que vous voulez disposer de symboles pour les appels système dans vos services, vous devez ajouter des serveurs de symboles Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-125">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="5dc6f-126">Consultez [Symboles de débogage](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-126">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="5dc6f-127">Pour déboguer un service</span><span class="sxs-lookup"><span data-stu-id="5dc6f-127">To debug a service</span></span>  
  
1. <span data-ttu-id="5dc6f-128">Générez votre service dans la configuration Debug.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-128">Build your service in the Debug configuration.</span></span>  
  
2. <span data-ttu-id="5dc6f-129">Installez votre service.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-129">Install your service.</span></span> <span data-ttu-id="5dc6f-130">Pour plus d'informations, consultez [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-130">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
3. <span data-ttu-id="5dc6f-131">Démarrez le service à partir du **Gestionnaire de contrôle des services**, à partir de **l’Explorateur de serveurs** ou à partir du code.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-131">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="5dc6f-132">Pour plus d’informations, consultez [Guide pratique pour démarrer des services](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-132">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>  
  
4. <span data-ttu-id="5dc6f-133">Démarrez Visual Studio avec des informations d'identification administratives pour pouvoir effectuer un attachement à un processus système.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-133">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5. <span data-ttu-id="5dc6f-134">(Facultatif) Dans la barre de menus de Visual Studio, choisissez **Outils**, **Options**.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-134">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="5dc6f-135">Dans la boîte de dialogue **Options**, choisissez **Débogage**, **Symboles**, cochez la case **Serveurs de symboles Microsoft**, puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-135">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6. <span data-ttu-id="5dc6f-136">Dans la barre de menus, choisissez **Attacher au processus** dans le menu **Débogage** ou **Outils**.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-136">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="5dc6f-137">(clavier : Ctrl+Alt+H)</span><span class="sxs-lookup"><span data-stu-id="5dc6f-137">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="5dc6f-138">La boîte de dialogue **Processus** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-138">The **Processes** dialog box appears.</span></span>  
  
7. <span data-ttu-id="5dc6f-139">Cochez la case **Afficher les processus de tous les utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-139">Select the **Show processes from all users** check box.</span></span>  
  
8. <span data-ttu-id="5dc6f-140">Dans la section **Processus disponibles**, choisissez le processus de votre service, puis **Attacher**.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-140">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="5dc6f-141">Le processus porte le même nom que le fichier exécutable de votre service.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-141">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="5dc6f-142">La boîte de dialogue **Attacher au processus** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-142">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="5dc6f-143">Choisissez les options appropriées, puis **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-143">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5dc6f-144">Vous êtes maintenant en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-144">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="5dc6f-145">Définissez les points d'arrêt que vous souhaitez utiliser dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-145">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="5dc6f-146">Accédez au Gestionnaire de contrôle des services et manipulez votre service, en envoyant des commandes d'arrêt, d'interruption et de poursuite pour atteindre vos points d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-146">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="5dc6f-147">Pour plus d’informations sur l’exécution du Gestionnaire de contrôle des services, consultez [Guide pratique pour démarrer des services](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-147">For more information about running the Services Control Manager, see [How to: Start Services](how-to-start-services.md).</span></span> <span data-ttu-id="5dc6f-148">Consultez aussi [Résolution des problèmes : débogage des services Windows](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-148">Also, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="5dc6f-149">Conseils relatifs au débogage des services Windows</span><span class="sxs-lookup"><span data-stu-id="5dc6f-149">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="5dc6f-150">L'attachement au processus du service vous permet de déboguer le code de ce service dans sa majeure partie mais pas dans sa totalité.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-150">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="5dc6f-151">Par exemple, comme le service a déjà été démarré, vous ne pouvez pas déboguer de cette façon le code de la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> du service ni celui de la méthode `Main` qui sert à le charger.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-151">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="5dc6f-152">Pour remédier à cela, vous pouvez créer, dans votre application de service, un deuxième service temporaire servant uniquement à faciliter le débogage.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-152">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="5dc6f-153">Vous pouvez installer les deux services, puis démarrer ce service factice pour charger le processus du service.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-153">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="5dc6f-154">Une fois que le service temporaire a démarré le processus, vous pouvez effectuer l’attachement au processus du service à l’aide du menu **Débogage** de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-154">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="5dc6f-155">Essayez d'ajouter des appels à la méthode <xref:System.Threading.Thread.Sleep%2A> pour retarder l'action jusqu'à ce que vous soyez en mesure d'effectuer l'attachement au processus.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-155">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="5dc6f-156">Essayez de remplacer le programme par une application de console standard.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-156">Try changing the program to a regular console application.</span></span> <span data-ttu-id="5dc6f-157">Pour ce faire, réécrivez la méthode `Main` comme suit afin qu'elle puisse s'exécuter à la fois en tant que service Windows et en tant qu'application console, en fonction de la façon dont elle est démarrée.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-157">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="5dc6f-158">Procédure : exécution d'un service Windows en tant qu'application console</span><span class="sxs-lookup"><span data-stu-id="5dc6f-158">How to: Run a Windows Service as a console application</span></span>  
  
1. <span data-ttu-id="5dc6f-159">Ajoutez une méthode à votre service qui exécute les méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> :</span><span class="sxs-lookup"><span data-stu-id="5dc6f-159">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. <span data-ttu-id="5dc6f-160">Réécrivez la méthode `Main` suit :</span><span class="sxs-lookup"><span data-stu-id="5dc6f-160">Rewrite the `Main` method as follows:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        if (Environment.UserInteractive)  
        {  
            MyNewService service1 = new MyNewService(args);  
            service1.TestStartupAndStop(args);  
        }  
        else  
        {  
            // Put the body of your old Main method here.  
        }  
    }
    ```  
  
3. <span data-ttu-id="5dc6f-161">Sous l’onglet **Application** des propriétés du projet, choisissez **Application console** comme **Type de sortie**.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-161">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4. <span data-ttu-id="5dc6f-162">Choisissez **Démarrer le débogage** (F5).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-162">Choose **Start Debugging** (F5).</span></span>  
  
5. <span data-ttu-id="5dc6f-163">Pour exécuter à nouveau le programme en tant que service Windows, installez-le et démarrez-le comme vous le faites habituellement pour un service Windows.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-163">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="5dc6f-164">Il n'est pas nécessaire d'annuler les modifications apportées.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-164">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="5dc6f-165">Dans certains cas, notamment lorsque vous souhaitez déboguer un problème qui se produit uniquement au démarrage du système, vous devez utiliser le débogueur Windows.</span><span class="sxs-lookup"><span data-stu-id="5dc6f-165">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="5dc6f-166">[Télécharger Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) et consultez [Comment déboguer les services Windows](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="5dc6f-166">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc6f-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dc6f-167">See also</span></span>

- [<span data-ttu-id="5dc6f-168">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="5dc6f-168">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="5dc6f-169">Procédure : Installer et désinstaller des services</span><span class="sxs-lookup"><span data-stu-id="5dc6f-169">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="5dc6f-170">Procédure : démarrer des services</span><span class="sxs-lookup"><span data-stu-id="5dc6f-170">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="5dc6f-171">Déboguer un service</span><span class="sxs-lookup"><span data-stu-id="5dc6f-171">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
