---
title: Dépannage 'Cette application n’a pas pu être lancée'
description: Apprenez ce qu’il faut faire si vous voyez une boîte de dialogue « Cette application ne pourrait pas être lancée ».
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965904"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="d7918-103">Dépannage d’un message d’erreur « Cette application ne pouvait pas être lancé »</span><span class="sxs-lookup"><span data-stu-id="d7918-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="d7918-104">Les applications qui sont développées pour le cadre .NET exigent généralement qu’une version spécifique du cadre .NET soit installée sur votre système.</span><span class="sxs-lookup"><span data-stu-id="d7918-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="d7918-105">Dans certains cas, vous pouvez essayer d’exécuter une application sans une version installée ou la version attendue du cadre .NET présent.</span><span class="sxs-lookup"><span data-stu-id="d7918-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="d7918-106">Cela produit souvent une boîte de dialogue d’erreur comme ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="d7918-106">This often produces an error dialog box like the following:</span></span>

![Impossible de démarrer cette application](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="d7918-108">Cela indique généralement l’une des conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7918-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="d7918-109">Une installation cadre .NET sur votre système est devenue corrompue.</span><span class="sxs-lookup"><span data-stu-id="d7918-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="d7918-110">La version du cadre .NET nécessaire à votre application ne peut pas être détectée.</span><span class="sxs-lookup"><span data-stu-id="d7918-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="d7918-111">Pour résoudre ce problème afin que vous puissiez exécuter votre demande, faites ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d7918-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="d7918-112">Télécharger le [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="d7918-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="d7918-113">L’outil s’exécute automatiquement lorsque le téléchargement se termine.</span><span class="sxs-lookup"><span data-stu-id="d7918-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="d7918-114">Si l’outil de réparation cadre .NET recommande toute action supplémentaire, comme celles indiquées dans le chiffre suivant, **sélectionnez Next**.</span><span class="sxs-lookup"><span data-stu-id="d7918-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Changements recommandés](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="d7918-116">Les outils de réparation cadre .NET affichent une boîte de dialogue indiquée dans le chiffre suivant pour indiquer que les changements sont complets.</span><span class="sxs-lookup"><span data-stu-id="d7918-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="d7918-117">Laissez la boîte de dialogue ouverte pendant que vous essayez de réexécuter votre demande.</span><span class="sxs-lookup"><span data-stu-id="d7918-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="d7918-118">Cela devrait réussir si l’outil de réparation cadre .NET a identifié et corrigé une installation cadre .NET corrompue.</span><span class="sxs-lookup"><span data-stu-id="d7918-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Changements recommandés](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="d7918-120">Si votre application s’exécute avec succès, sélectionnez le bouton **Finition.**</span><span class="sxs-lookup"><span data-stu-id="d7918-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="d7918-121">Sinon, sélectionnez le bouton **Suivant.**</span><span class="sxs-lookup"><span data-stu-id="d7918-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="d7918-122">Si vous avez sélectionné le bouton **Suivant,** l’outil de réparation cadre .NET affiche une boîte de dialogue comme ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="d7918-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="d7918-123">Sélectionnez le bouton **Finition** pour envoyer des informations diagnostiques à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d7918-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Incapable de résoudre le problème](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="d7918-125">Si vous ne pouvez toujours pas exécuter l’application, installez la dernière version du cadre .NET pris en charge par votre version de Windows, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d7918-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="d7918-126">Version de Windows</span><span class="sxs-lookup"><span data-stu-id="d7918-126">Windows version</span></span>|<span data-ttu-id="d7918-127">.NET Installation-cadre</span><span class="sxs-lookup"><span data-stu-id="d7918-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="d7918-128">Mise à jour anniversaire de Windows 10 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="d7918-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="d7918-129">.NET Cadre 4.8 Runtime</span><span class="sxs-lookup"><span data-stu-id="d7918-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="d7918-130">Windows 10, Windows 10 Novembre Mise à jour</span><span class="sxs-lookup"><span data-stu-id="d7918-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="d7918-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="d7918-131">.NET Framework 4.6.2</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |<span data-ttu-id="d7918-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d7918-132">Windows 8.1</span></span>|[<span data-ttu-id="d7918-133">.NET Cadre 4.8 Runtime</span><span class="sxs-lookup"><span data-stu-id="d7918-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="d7918-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d7918-134">Windows 8</span></span>|[<span data-ttu-id="d7918-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="d7918-135">.NET Framework 4.6.1</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |<span data-ttu-id="d7918-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d7918-136">Windows 7 SP1</span></span>|[<span data-ttu-id="d7918-137">.NET Cadre 4.8 Runtime</span><span class="sxs-lookup"><span data-stu-id="d7918-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="d7918-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="d7918-138">Windows Vista SP2</span></span>|[<span data-ttu-id="d7918-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="d7918-139">.NET Framework 4.6</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > <span data-ttu-id="d7918-140">.NET Framework 4.8 est préinstallé sur Windows 10 mai 2019 Mise à jour.</span><span class="sxs-lookup"><span data-stu-id="d7918-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="d7918-141">Tentative de lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="d7918-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="d7918-142">Dans certains cas, vous pouvez voir une boîte de dialogue comme ce qui suit, qui vous demande d’installer le cadre .NET 3.5.</span><span class="sxs-lookup"><span data-stu-id="d7918-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="d7918-143">Sélectionnez **Télécharger et installer cette fonctionnalité** pour installer le cadre .NET 3.5, puis lancez l’application à nouveau.</span><span class="sxs-lookup"><span data-stu-id="d7918-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Incapable de résoudre le problème](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="d7918-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7918-145">See also</span></span>

- [<span data-ttu-id="d7918-146">Configuration requise du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d7918-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="d7918-147">Guide d’installation du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d7918-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="d7918-148">Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d7918-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
