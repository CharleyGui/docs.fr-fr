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
ms.openlocfilehash: 2657d83f39b60be84846fb784a06e71f6dd46179
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609731"
---
# <a name="how-to-debug-windows-service-applications"></a>Procédure : déboguer les applications de service Windows
Un service doit être exécuté à partir du Gestionnaire de contrôle des services plutôt qu'à partir de Visual Studio. C'est pourquoi le débogage d'un service n'est pas aussi simple que le débogage d'autres types d'applications Visual Studio. Pour déboguer un service, vous devez le démarrer et attacher un débogueur au processus dans lequel il s'exécute. Vous pouvez alors déboguer votre application à l'aide de toutes les fonctionnalités de débogage standard de Visual Studio.  
  
> [!CAUTION]
> Avant de procéder à cet attachement, vérifiez en quoi consiste le processus concerné et pesez bien les conséquences de cette opération qui risque de supprimer le processus. Par exemple, si vous effectuez un attachement au processus WinLogon et que vous interrompez ensuite le débogage, le système s'arrête, car il ne peut pas fonctionner sans WinLogon.  
  
 Vous ne pouvez attacher le débogueur qu'à un service en cours d'exécution. Le processus d'attachement interrompt le fonctionnement actuel de votre service ; il n'a pas pour effet de l'arrêter ni d'en suspendre le traitement. Autrement dit, si votre service est en cours d'exécution lorsque vous commencez le débogage, il se trouve toujours techniquement à l'état Démarré pendant que vous le déboguez, mais son traitement est suspendu.  
  
 Après avoir effectué l'attachement au processus, vous pouvez définir des points d'arrêt et les utiliser pour déboguer votre code. Une fois que vous quittez la boîte de dialogue utilisée pour faire l'attachement au processus, vous êtes en mode débogage. Vous pouvez utiliser le Gestionnaire de contrôle des services pour démarrer, arrêter, interrompre et continuer votre service, en accédant aux points d'arrêt que vous avez définis. Quand le débogage est terminé, vous pouvez supprimer le service factice.  
  
 Cet article décrit le débogage d'un service qui est en cours d'exécution sur l'ordinateur local, mais vous pouvez également déboguer des services Windows qui s'exécutent sur un ordinateur distant. Consultez [débogage distant](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
> Le débogage de la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> peut s'avérer difficile, car le Gestionnaire de contrôle des services impose un délai de 30 secondes pour toute tentative de démarrage d'un service. Pour plus d’informations, consultez [Résolution des problèmes : débogage des services Windows](troubleshooting-debugging-windows-services.md).  
  
> [!WARNING]
> Pour obtenir des informations significatives pour le débogage, le débogueur Visual Studio doit rechercher les fichiers de symboles pour les fichiers binaires qui sont en cours de débogage. Si vous déboguez un service que vous avez généré dans Visual Studio, les fichiers de symboles (fichiers .pdb) se trouvent dans le même dossier que l'exécutable ou la bibliothèque, et le débogueur les charge automatiquement. Si vous déboguez un service que vous n'avez pas généré, vous devez d'abord rechercher des symboles pour le service, puis vous assurer qu'ils sont accessibles par le débogueur. Consultez [Spécifier les fichiers de symboles (.pdb) et les fichiers sources dans le débogueur Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger). Si vous déboguez un processus système ou que vous voulez disposer de symboles pour les appels système dans vos services, vous devez ajouter des serveurs de symboles Microsoft. Consultez [Symboles de débogage](/windows/desktop/DxTechArts/debugging-with-symbols).  
  
### <a name="to-debug-a-service"></a>Pour déboguer un service  
  
1. Générez votre service dans la configuration Debug.  
  
2. Installez votre service. Pour plus d'informations, consultez [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).  
  
3. Démarrez le service à partir du **Gestionnaire de contrôle des services**, à partir de **l’Explorateur de serveurs** ou à partir du code. Pour plus d’informations, consultez [Guide pratique pour démarrer des services](how-to-start-services.md).  
  
4. Démarrez Visual Studio avec des informations d'identification administratives pour pouvoir effectuer un attachement à un processus système.  
  
5. (Facultatif) Dans la barre de menus de Visual Studio, choisissez **Outils**, **Options**. Dans la boîte de dialogue **Options**, choisissez **Débogage**, **Symboles**, cochez la case **Serveurs de symboles Microsoft**, puis choisissez **OK**.  
  
6. Dans la barre de menus, choisissez **Attacher au processus** dans le menu **Débogage** ou **Outils**. (clavier : Ctrl+Alt+H)  
  
     La boîte de dialogue **Processus** s’affiche.  
  
7. Cochez la case **Afficher les processus de tous les utilisateurs**.  
  
8. Dans la section **Processus disponibles**, choisissez le processus de votre service, puis **Attacher**.  
  
    > [!TIP]
    > Le processus porte le même nom que le fichier exécutable de votre service.  
  
     La boîte de dialogue **Attacher au processus** s'affiche.  
  
9. Choisissez les options appropriées, puis **OK** pour fermer la boîte de dialogue.  
  
    > [!NOTE]
    > Vous êtes maintenant en mode débogage.  
  
10. Définissez les points d'arrêt que vous souhaitez utiliser dans votre code.  
  
11. Accédez au Gestionnaire de contrôle des services et manipulez votre service, en envoyant des commandes d'arrêt, d'interruption et de poursuite pour atteindre vos points d'arrêt. Pour plus d’informations sur l’exécution du Gestionnaire de contrôle des services, consultez [Guide pratique pour démarrer des services](how-to-start-services.md). Consultez aussi [Résolution des problèmes : débogage des services Windows](troubleshooting-debugging-windows-services.md).  
  
## <a name="debugging-tips-for-windows-services"></a>Conseils relatifs au débogage des services Windows  
 L'attachement au processus du service vous permet de déboguer le code de ce service dans sa majeure partie mais pas dans sa totalité. Par exemple, comme le service a déjà été démarré, vous ne pouvez pas déboguer de cette façon le code de la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> du service ni celui de la méthode `Main` qui sert à le charger. Pour remédier à cela, vous pouvez créer, dans votre application de service, un deuxième service temporaire servant uniquement à faciliter le débogage. Vous pouvez installer les deux services, puis démarrer ce service factice pour charger le processus du service. Une fois que le service temporaire a démarré le processus, vous pouvez effectuer l’attachement au processus du service à l’aide du menu **Débogage** de Visual Studio.  
  
 Essayez d'ajouter des appels à la méthode <xref:System.Threading.Thread.Sleep%2A> pour retarder l'action jusqu'à ce que vous soyez en mesure d'effectuer l'attachement au processus.  
  
 Essayez de remplacer le programme par une application de console standard. Pour ce faire, réécrivez la méthode `Main` comme suit afin qu'elle puisse s'exécuter à la fois en tant que service Windows et en tant qu'application console, en fonction de la façon dont elle est démarrée.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Procédure : exécution d'un service Windows en tant qu'application console  
  
1. Ajoutez une méthode à votre service qui exécute les méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> :  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. Réécrivez la méthode `Main` suit :  
  
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
  
3. Sous l’onglet **Application** des propriétés du projet, choisissez **Application console** comme **Type de sortie**.  
  
4. Choisissez **Démarrer le débogage** (F5).  
  
5. Pour exécuter à nouveau le programme en tant que service Windows, installez-le et démarrez-le comme vous le faites habituellement pour un service Windows. Il n'est pas nécessaire d'annuler les modifications apportées.  
  
 Dans certains cas, notamment lorsque vous souhaitez déboguer un problème qui se produit uniquement au démarrage du système, vous devez utiliser le débogueur Windows. [Télécharger Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) et consultez [Comment déboguer les services Windows](https://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux applications de service Windows](introduction-to-windows-service-applications.md)
- [Procédure : Installer et désinstaller des services](how-to-install-and-uninstall-services.md)
- [Procédure : démarrer des services](how-to-start-services.md)
- [Déboguer un service](/windows/desktop/Services/debugging-a-service)
