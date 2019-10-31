---
title: Résolution des problèmes « cette application n’a pas pu être démarrée »
description: Découvrez comment faire si la boîte de dialogue « cette application n’a pas pu être démarrée » s’affiche.
ms.date: 09/05/2019
ms.openlocfilehash: 2140ab38c29d610634f71305c4337c324e0550d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092048"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="fb8a9-103">Résolution des problèmes liés à un message d’erreur « cette application n’a pas pu être démarrée »</span><span class="sxs-lookup"><span data-stu-id="fb8a9-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="fb8a9-104">Les applications développées pour le .NET Framework requièrent généralement qu’une version spécifique du .NET Framework soit installée sur votre système.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="fb8a9-105">Dans certains cas, vous pouvez essayer d’exécuter une application sans version installée ou avec la version attendue du .NET Framework présent.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="fb8a9-106">Cela génère souvent une boîte de dialogue d’erreur semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="fb8a9-106">This often produces an error dialog box like the following:</span></span>

![Impossible de démarrer cette application](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="fb8a9-108">Cela indique généralement l’une des conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb8a9-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="fb8a9-109">Une installation .NET Framework sur votre système a été endommagée.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="fb8a9-110">La version du .NET Framework nécessaire à votre application ne peut pas être détectée.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="fb8a9-111">Pour résoudre ce problème afin de pouvoir exécuter votre application, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fb8a9-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="fb8a9-112">Téléchargez l' [outil de réparation .NET Framework (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="fb8a9-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="fb8a9-113">L’outil s’exécute automatiquement une fois le téléchargement terminé.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="fb8a9-114">Si l’outil de réparation .NET Framework recommande des actions supplémentaires, comme celles figurant dans l’illustration suivante, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Changements recommandés](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="fb8a9-116">Le .NET Framework outils de réparation affiche une boîte de dialogue illustrée dans la figure suivante pour indiquer que les modifications sont terminées.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="fb8a9-117">Laissez la boîte de dialogue ouverte pendant que vous essayez de réexécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="fb8a9-118">Cette opération doit être effectuée si l’outil de réparation .NET Framework a identifié et corrigé une installation endommagée de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Changements recommandés](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="fb8a9-120">Si votre application s’exécute correctement, sélectionnez le bouton **Terminer** .</span><span class="sxs-lookup"><span data-stu-id="fb8a9-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="fb8a9-121">Dans le cas contraire, sélectionnez le bouton **suivant** .</span><span class="sxs-lookup"><span data-stu-id="fb8a9-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="fb8a9-122">Si vous avez sélectionné le bouton **suivant** , l’outil de réparation .NET Framework affiche une boîte de dialogue semblable à la suivante.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="fb8a9-123">Sélectionnez le bouton **Terminer** pour envoyer des informations de diagnostic à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Impossible de résoudre le problème](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="fb8a9-125">Si vous ne pouvez toujours pas exécuter l’application, installez la version la plus récente du .NET Framework pris en charge par votre version de Windows, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="fb8a9-126">Version Windows</span><span class="sxs-lookup"><span data-stu-id="fb8a9-126">Windows version</span></span>|<span data-ttu-id="fb8a9-127">Installation de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb8a9-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="fb8a9-128">Mise à jour anniversaire Windows 10 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="fb8a9-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="fb8a9-129">.NET Framework 4,8 Runtime</span><span class="sxs-lookup"><span data-stu-id="fb8a9-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="fb8a9-130">Windows 10, mise à jour de novembre de Windows 10</span><span class="sxs-lookup"><span data-stu-id="fb8a9-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="fb8a9-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="fb8a9-131">.NET Framework 4.6.2</span></span>](https://www.microsoft.com/download/details.aspx?id=53345)|
   |<span data-ttu-id="fb8a9-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="fb8a9-132">Windows 8.1</span></span>|[<span data-ttu-id="fb8a9-133">.NET Framework 4,8 Runtime</span><span class="sxs-lookup"><span data-stu-id="fb8a9-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="fb8a9-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="fb8a9-134">Windows 8</span></span>|[<span data-ttu-id="fb8a9-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fb8a9-135">.NET Framework 4.6.1</span></span>](https://www.microsoft.com/download/details.aspx?id=49981)|
   |<span data-ttu-id="fb8a9-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="fb8a9-136">Windows 7 SP1</span></span>|[<span data-ttu-id="fb8a9-137">.NET Framework 4,8 Runtime</span><span class="sxs-lookup"><span data-stu-id="fb8a9-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="fb8a9-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="fb8a9-138">Windows Vista SP2</span></span>|[<span data-ttu-id="fb8a9-139">.NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="fb8a9-139">.NET Framework 4.6</span></span>](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   > <span data-ttu-id="fb8a9-140">.NET Framework 4,8 est préinstallé sur la mise à jour de Windows 10 mai 2019.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="fb8a9-141">Essayez de lancer l’application.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="fb8a9-142">Dans certains cas, une boîte de dialogue semblable à la suivante s’affiche, vous demandant d’installer le .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="fb8a9-143">Sélectionnez **Télécharger et installer cette fonctionnalité** pour installer le .NET Framework 3,5, puis relancez l’application.</span><span class="sxs-lookup"><span data-stu-id="fb8a9-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Impossible de résoudre le problème](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="fb8a9-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb8a9-145">See also</span></span>

- [<span data-ttu-id="fb8a9-146">Configuration système requise pour .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb8a9-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="fb8a9-147">Guide d’installation de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb8a9-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="fb8a9-148">Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb8a9-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
