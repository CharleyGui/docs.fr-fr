---
title: Ajouter WCF Web Service Reference
description: Vue d’ensemble de l’outil Microsoft WCF Web Service Reference Provider, qui ajoute des fonctionnalités pour les projets .NET Core et ASP.NET Core, de manière similaire à la fonctionnalité Ajouter une référence de service pour les projets .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: 1f7b1831a956553dbef26f58f4f257c2f3914ede
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400602"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="f48e1-103">Utiliser l’outil WCF Web Service Reference Provider</span><span class="sxs-lookup"><span data-stu-id="f48e1-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="f48e1-104">Au fil des années, de nombreux développeurs Visual Studio ont apprécié le gain de productivité offert par l’outil [**Ajouter une référence de service**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) quand leurs projets .NET Framework avaient besoin d’accéder à des services web.</span><span class="sxs-lookup"><span data-stu-id="f48e1-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="f48e1-105">L’outil **WCF Web Service Reference** est une extension de service connecté de Visual Studio qui fournit une expérience semblable à la fonctionnalité Ajouter une référence de service pour les projets .NET Core et ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f48e1-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="f48e1-106">Cet outil récupère les métadonnées d’un service web dans la solution actuelle sur un emplacement réseau ou dans un fichier WSDL, puis génère un fichier source compatible .NET Core contenant du code de proxy client WCF (Windows Communication Foundation) que vous pouvez utiliser pour accéder au service web.</span><span class="sxs-lookup"><span data-stu-id="f48e1-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f48e1-107">Vous devez référencer des services uniquement à partir d’une source approuvée.</span><span class="sxs-lookup"><span data-stu-id="f48e1-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="f48e1-108">L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.</span><span class="sxs-lookup"><span data-stu-id="f48e1-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f48e1-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f48e1-109">Prerequisites</span></span>

- <span data-ttu-id="f48e1-110">[Visual Studio 2017 version 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="f48e1-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="f48e1-111">Comment utiliser l’extension</span><span class="sxs-lookup"><span data-stu-id="f48e1-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="f48e1-112">L’option **WCF Web Service Reference** s’applique aux projets créés à l’aide des modèles de projet suivants :</span><span class="sxs-lookup"><span data-stu-id="f48e1-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="f48e1-113">**Visual C#**  >  **.Net Core**</span><span class="sxs-lookup"><span data-stu-id="f48e1-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="f48e1-114">**Visual C#**  >  **.NET standard**</span><span class="sxs-lookup"><span data-stu-id="f48e1-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="f48e1-115">**Visual C#**  >  **Web**  >  **Application Web ASP.net Core**</span><span class="sxs-lookup"><span data-stu-id="f48e1-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="f48e1-116">Prenant le modèle de projet **Application web ASP.NET Core** en guise d’exemple, cet article explique comment ajouter une référence de service WCF au projet :</span><span class="sxs-lookup"><span data-stu-id="f48e1-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="f48e1-117">Dans l’Explorateur de solutions, double-cliquez sur le nœud du projet **Services connectés** (pour un projet .NET Core ou .NET Standard, cette option est disponible quand vous cliquez avec le bouton droit sur le nœud **Dépendances** du projet dans l’Explorateur de solutions).</span><span class="sxs-lookup"><span data-stu-id="f48e1-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="f48e1-118">La page **Services connectés** s’affiche, comme illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="f48e1-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Onglet Services connectés de Visual Studio pour .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="f48e1-120">Dans la page **Services connectés** , cliquez sur **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="f48e1-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="f48e1-121">L’Assistant **Configurer la référence de services web WCF** apparaît :</span><span class="sxs-lookup"><span data-stu-id="f48e1-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Onglet Point de terminaison de service Visual Studio pour .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="f48e1-123">Sélectionnez un service.</span><span class="sxs-lookup"><span data-stu-id="f48e1-123">Select a service.</span></span>

    <span data-ttu-id="f48e1-124">3a.</span><span class="sxs-lookup"><span data-stu-id="f48e1-124">3a.</span></span> <span data-ttu-id="f48e1-125">Plusieurs options de recherche de services sont disponibles dans l’Assistant **Configurer la référence de services web WCF** :</span><span class="sxs-lookup"><span data-stu-id="f48e1-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="f48e1-126">Pour rechercher parmi les services définis dans la solution actuelle, cliquez sur le bouton **Découvrir**.</span><span class="sxs-lookup"><span data-stu-id="f48e1-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="f48e1-127">Pour rechercher parmi les services hébergés à une adresse spécifiée, entrez une URL de service dans la zone **Adresse** , puis cliquez sur le bouton **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="f48e1-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="f48e1-128">Pour sélectionner un fichier WSDL qui contient les informations de métadonnées de service web, cliquez sur le bouton **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="f48e1-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="f48e1-129">3b.</span><span class="sxs-lookup"><span data-stu-id="f48e1-129">3b.</span></span> <span data-ttu-id="f48e1-130">Sélectionnez le service dans la liste des résultats de recherche dans la zone **Services**.</span><span class="sxs-lookup"><span data-stu-id="f48e1-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="f48e1-131">Si nécessaire, entrez l’espace de noms du code généré dans la zone de texte **Espace de noms** correspondante.</span><span class="sxs-lookup"><span data-stu-id="f48e1-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="f48e1-132">3c.</span><span class="sxs-lookup"><span data-stu-id="f48e1-132">3c.</span></span> <span data-ttu-id="f48e1-133">Cliquez sur le bouton **Suivant** pour ouvrir les pages **Options du type de données** et **Options du client**.</span><span class="sxs-lookup"><span data-stu-id="f48e1-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="f48e1-134">Vous pouvez aussi cliquer sur le bouton **Terminer** pour utiliser les options par défaut.</span><span class="sxs-lookup"><span data-stu-id="f48e1-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="f48e1-135">Le formulaire **Options du type de données** vous permet d’affiner les paramètres de configuration de référence de service générés :</span><span class="sxs-lookup"><span data-stu-id="f48e1-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Onglet Options du type de données Visual Studio pour .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="f48e1-137">La case à cocher **Réutiliser les types dans les assemblys référencés** est utile quand les types de données nécessaires pour la génération du code de référence de service sont définis dans l’un des assemblys référencés de votre projet.</span><span class="sxs-lookup"><span data-stu-id="f48e1-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="f48e1-138">Il est important de réutiliser ces types de données existants pour éviter les conflits de type au moment de la compilation ou les problèmes au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f48e1-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="f48e1-139">Il peut y avoir un délai pendant le chargement des informations de type, en fonction du nombre de dépendances du projet et d’autres facteurs de performances système.</span><span class="sxs-lookup"><span data-stu-id="f48e1-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="f48e1-140">Le bouton **Terminer** est désactivé pendant le chargement, sauf si la case **Réutiliser les types dans les assemblys référencés** est cochée.</span><span class="sxs-lookup"><span data-stu-id="f48e1-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="f48e1-141">Cliquez sur **Terminer** quand vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="f48e1-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="f48e1-142">Lors de l’affichage de la progression, l’outil :</span><span class="sxs-lookup"><span data-stu-id="f48e1-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="f48e1-143">Télécharge les métadonnées à partir du service WCF.</span><span class="sxs-lookup"><span data-stu-id="f48e1-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="f48e1-144">Génère le code de référence de service dans un fichier nommé *reference.cs* et l’ajoute à votre projet sous le nœud **Services connectés**.</span><span class="sxs-lookup"><span data-stu-id="f48e1-144">Generates the service reference code in a file named *reference.cs* , and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="f48e1-145">Met à jour le fichier projet (.csproj) avec les références de package NuGet nécessaires pour la compilation et l’exécution sur la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="f48e1-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Fenêtre de progression Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="f48e1-147">Une fois ces processus terminés, vous pouvez créer une instance du type de client WCF généré et appeler les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="f48e1-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="f48e1-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f48e1-148">See also</span></span>

- [<span data-ttu-id="f48e1-149">Prise en main des applications Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f48e1-149">Get started with Windows Communication Foundation applications</span></span>](../../framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="f48e1-150">Services de Windows Communication Foundation et services de données WCF dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f48e1-150">Windows Communication Foundation services and WCF data services in Visual Studio</span></span>](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [<span data-ttu-id="f48e1-151">Fonctionnalités prises en charge par WCF sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="f48e1-151">WCF supported features on .NET Core</span></span>](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a><span data-ttu-id="f48e1-152">Commentaires et questions</span><span class="sxs-lookup"><span data-stu-id="f48e1-152">Feedback & questions</span></span>

<span data-ttu-id="f48e1-153">Si vous avez des commentaires sur les produits, signalez-le auprès de la [communauté des développeurs](https://aka.ms/feedback/report?space=61) à l’aide de l’outil [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) .</span><span class="sxs-lookup"><span data-stu-id="f48e1-153">If you have any product feedback, report it at [Developer Community](https://aka.ms/feedback/report?space=61) using the [Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) tool.</span></span>

## <a name="release-notes"></a><span data-ttu-id="f48e1-154">Notes de publication</span><span class="sxs-lookup"><span data-stu-id="f48e1-154">Release notes</span></span>

- <span data-ttu-id="f48e1-155">Pour obtenir des informations à jour sur les versions, notamment les problèmes connus, consultez les [Notes de publication](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md).</span><span class="sxs-lookup"><span data-stu-id="f48e1-155">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
