---
title: Mettre en cache les données d’application
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: b7d999f94e2f2ae410a16e537d51c0f890def4e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728061"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="159e9-102">Procédure pas à pas : mise en cache de données d'application dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="159e9-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="159e9-103">La mise en cache vous permet de stocker des données en mémoire pour y accéder rapidement.</span><span class="sxs-lookup"><span data-stu-id="159e9-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="159e9-104">Quand vous accédez à nouveau aux données, les applications peuvent obtenir les données à partir du cache au lieu de devoir les récupérer à partir de la source d’origine.</span><span class="sxs-lookup"><span data-stu-id="159e9-104">When the data is accessed again, applications can get the data from the cache instead of retrieving it from the original source.</span></span> <span data-ttu-id="159e9-105">Cela peut améliorer les performances et la scalabilité.</span><span class="sxs-lookup"><span data-stu-id="159e9-105">This can improve performance and scalability.</span></span> <span data-ttu-id="159e9-106">La mise en cache rend également les données disponibles quand la source de données est temporairement indisponible.</span><span class="sxs-lookup"><span data-stu-id="159e9-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>

 <span data-ttu-id="159e9-107">Le .NET Framework fournit des classes qui vous permettent d’utiliser la mise en cache dans les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="159e9-107">The .NET Framework provides classes that enable you to use caching in .NET Framework applications.</span></span> <span data-ttu-id="159e9-108">Ces classes se trouvent dans l’espace de noms <xref:System.Runtime.Caching>.</span><span class="sxs-lookup"><span data-stu-id="159e9-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="159e9-109">L’espace de noms <xref:System.Runtime.Caching> est une nouveauté du .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="159e9-109">The <xref:System.Runtime.Caching> namespace is new in the .NET Framework 4.</span></span> <span data-ttu-id="159e9-110">Cet espace de noms rend la mise en cache disponible pour toutes les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="159e9-110">This namespace makes caching is available to all .NET Framework applications.</span></span> <span data-ttu-id="159e9-111">Dans les versions précédentes de la .NET Framework, la mise en cache était uniquement disponible dans l’espace de noms <xref:System.Web> et nécessitait donc une dépendance sur les classes ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="159e9-111">In previous versions of the .NET Framework, caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>

 <span data-ttu-id="159e9-112">Cette procédure pas à pas vous montre comment utiliser les fonctionnalités de mise en cache disponibles dans le .NET Framework dans le cadre d’une application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="159e9-112">This walkthrough shows you how to use the caching functionality that is available in the .NET Framework as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="159e9-113">Dans la procédure pas à pas, vous mettez en cache le contenu d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="159e9-113">In the walkthrough, you cache the contents of a text file.</span></span>

 <span data-ttu-id="159e9-114">Cette procédure pas à pas décrit les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="159e9-114">Tasks illustrated in this walkthrough include the following:</span></span>

- <span data-ttu-id="159e9-115">Création d’un projet d’application WPF.</span><span class="sxs-lookup"><span data-stu-id="159e9-115">Creating a WPF application project.</span></span>

- <span data-ttu-id="159e9-116">Ajout d’une référence au .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="159e9-116">Adding a reference to the .NET Framework 4.</span></span>

- <span data-ttu-id="159e9-117">Initialisation d’un cache.</span><span class="sxs-lookup"><span data-stu-id="159e9-117">Initializing a cache.</span></span>

- <span data-ttu-id="159e9-118">Ajout d’une entrée de cache qui contient le contenu d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="159e9-118">Adding a cache entry that contains the contents of a text file.</span></span>

- <span data-ttu-id="159e9-119">Fournir une stratégie d’éviction pour l’entrée du cache.</span><span class="sxs-lookup"><span data-stu-id="159e9-119">Providing an eviction policy for the cache entry.</span></span>

- <span data-ttu-id="159e9-120">Surveillance du chemin d’accès du fichier mis en cache et notification à l’instance du cache des modifications apportées à l’élément analysé.</span><span class="sxs-lookup"><span data-stu-id="159e9-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="159e9-121">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="159e9-121">Prerequisites</span></span>
 <span data-ttu-id="159e9-122">Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="159e9-122">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="159e9-123">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="159e9-123">Visual Studio 2010.</span></span>

- <span data-ttu-id="159e9-124">Fichier texte qui contient une petite quantité de texte.</span><span class="sxs-lookup"><span data-stu-id="159e9-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="159e9-125">(Le contenu du fichier texte s’affiche dans une boîte de message.) Le code illustré dans la procédure pas à pas suppose que vous travaillez avec le fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="159e9-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>

     `c:\cache\cacheText.txt`

     <span data-ttu-id="159e9-126">Toutefois, vous pouvez utiliser n’importe quel fichier texte et apporter des modifications mineures au code dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="159e9-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>

## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="159e9-127">Création d’un projet d’application WPF</span><span class="sxs-lookup"><span data-stu-id="159e9-127">Creating a WPF Application Project</span></span>
 <span data-ttu-id="159e9-128">Vous allez commencer par créer un projet d’application WPF.</span><span class="sxs-lookup"><span data-stu-id="159e9-128">You will start by creating a WPF application project.</span></span>

#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="159e9-129">Pour créer une application WPF</span><span class="sxs-lookup"><span data-stu-id="159e9-129">To create a WPF application</span></span>

1. <span data-ttu-id="159e9-130">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="159e9-130">Start Visual Studio.</span></span>

2. <span data-ttu-id="159e9-131">Dans le menu **fichier** , cliquez sur **nouveau**, puis sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="159e9-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>

     <span data-ttu-id="159e9-132">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="159e9-132">The **New Project** dialog box is displayed.</span></span>

3. <span data-ttu-id="159e9-133">Sous **modèles installés**, sélectionnez le langage de programmation que vous souhaitez utiliser (**Visual Basic** ou **C#visuel**).</span><span class="sxs-lookup"><span data-stu-id="159e9-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>

4. <span data-ttu-id="159e9-134">Dans la boîte de dialogue **nouveau projet** , sélectionnez **application WPF**.</span><span class="sxs-lookup"><span data-stu-id="159e9-134">In the **New Project** dialog box, select **WPF Application**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="159e9-135">Si vous ne voyez pas le modèle d' **application WPF** , assurez-vous que vous ciblez une version du .NET Framework qui prend en charge WPF.</span><span class="sxs-lookup"><span data-stu-id="159e9-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the .NET Framework that supports WPF.</span></span> <span data-ttu-id="159e9-136">Dans la boîte de dialogue **nouveau projet** , sélectionnez .NET Framework 4 dans la liste.</span><span class="sxs-lookup"><span data-stu-id="159e9-136">In the **New Project** dialog box, select .NET Framework 4 from the list.</span></span>

5. <span data-ttu-id="159e9-137">Dans la zone de texte **nom** , entrez un nom pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="159e9-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="159e9-138">Par exemple, vous pouvez entrer **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="159e9-138">For example, you can enter **WPFCaching**.</span></span>

6. <span data-ttu-id="159e9-139">Cochez la case **Créer le répertoire pour la solution**.</span><span class="sxs-lookup"><span data-stu-id="159e9-139">Select the **Create directory for solution** check box.</span></span>

7. <span data-ttu-id="159e9-140">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="159e9-140">Click **OK**.</span></span>

     <span data-ttu-id="159e9-141">Le Concepteur WPF s’ouvre en mode **création** et affiche le fichier MainWindow. Xaml.</span><span class="sxs-lookup"><span data-stu-id="159e9-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="159e9-142">Visual Studio crée le dossier **My Project** , le fichier application. xaml et le fichier MainWindow. Xaml.</span><span class="sxs-lookup"><span data-stu-id="159e9-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="159e9-143">Ciblage de la .NET Framework et ajout d’une référence aux assemblys de mise en cache</span><span class="sxs-lookup"><span data-stu-id="159e9-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>
 <span data-ttu-id="159e9-144">Par défaut, les applications WPF ciblent le profil client .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="159e9-144">By default, WPF applications target the .NET Framework 4 Client Profile.</span></span> <span data-ttu-id="159e9-145">Pour utiliser l’espace de noms <xref:System.Runtime.Caching> dans une application WPF, l’application doit cibler le .NET Framework 4 (et non le .NET Framework 4 Client Profile) et doit inclure une référence à l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="159e9-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the .NET Framework 4 (not the .NET Framework 4 Client Profile) and must include a reference to the namespace.</span></span>

 <span data-ttu-id="159e9-146">Par conséquent, l’étape suivante consiste à modifier le .NET Framework cible et à ajouter une référence à l’espace de noms <xref:System.Runtime.Caching>.</span><span class="sxs-lookup"><span data-stu-id="159e9-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="159e9-147">La procédure de modification de la .NET Framework cible est différente dans un projet Visual Basic et dans un C# projet visuel.</span><span class="sxs-lookup"><span data-stu-id="159e9-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="159e9-148">Pour modifier le .NET Framework cible dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="159e9-148">To change the target .NET Framework in Visual Basic</span></span>

1. <span data-ttu-id="159e9-149">Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="159e9-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>

     <span data-ttu-id="159e9-150">La fenêtre Propriétés de l’application s’affiche.</span><span class="sxs-lookup"><span data-stu-id="159e9-150">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="159e9-151">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="159e9-151">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="159e9-152">En bas de la fenêtre, cliquez sur **Options avancées de compilation...** .</span><span class="sxs-lookup"><span data-stu-id="159e9-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>

     <span data-ttu-id="159e9-153">La boîte de dialogue **Paramètres avancés du compilateur** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="159e9-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>

4. <span data-ttu-id="159e9-154">Dans la liste **Framework cible (toutes les configurations)** , sélectionnez .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="159e9-154">In the **Target framework (all configurations)** list, select .NET Framework 4.</span></span> <span data-ttu-id="159e9-155">(Ne sélectionnez pas .NET Framework 4 Client Profile.)</span><span class="sxs-lookup"><span data-stu-id="159e9-155">(Do not select .NET Framework 4 Client Profile.)</span></span>

5. <span data-ttu-id="159e9-156">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="159e9-156">Click **OK**.</span></span>

     <span data-ttu-id="159e9-157">La boîte de dialogue **Modification du Framework cible** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="159e9-157">The **Target Framework Change** dialog box is displayed.</span></span>

6. <span data-ttu-id="159e9-158">Dans la boîte de dialogue **modification du Framework cible** , cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="159e9-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>

     <span data-ttu-id="159e9-159">Le projet est fermé, puis rouvert.</span><span class="sxs-lookup"><span data-stu-id="159e9-159">The project is closed and is then reopened.</span></span>

7. <span data-ttu-id="159e9-160">Ajoutez une référence à l’assembly de mise en cache en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="159e9-160">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="159e9-161">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="159e9-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="159e9-162">Sélectionnez l’onglet **.net** , sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="159e9-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="159e9-163">Pour modifier le .NET Framework cible dans un projet C# visuel</span><span class="sxs-lookup"><span data-stu-id="159e9-163">To change the target .NET Framework in a Visual C# project</span></span>

1. <span data-ttu-id="159e9-164">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="159e9-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>

     <span data-ttu-id="159e9-165">La fenêtre Propriétés de l’application s’affiche.</span><span class="sxs-lookup"><span data-stu-id="159e9-165">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="159e9-166">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="159e9-166">Click the **Application** tab.</span></span>

3. <span data-ttu-id="159e9-167">Dans la liste **Framework cible** , sélectionnez .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="159e9-167">In the **Target framework** list, select .NET Framework 4.</span></span> <span data-ttu-id="159e9-168">(Ne sélectionnez pas **.NET Framework 4 Client Profile**.)</span><span class="sxs-lookup"><span data-stu-id="159e9-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>

4. <span data-ttu-id="159e9-169">Ajoutez une référence à l’assembly de mise en cache en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="159e9-169">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="159e9-170">Cliquez avec le bouton droit sur le dossier **références** , puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="159e9-170">Right-click the **References** folder and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="159e9-171">Sélectionnez l’onglet **.net** , sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="159e9-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="159e9-172">Ajout d’un bouton à la fenêtre WPF</span><span class="sxs-lookup"><span data-stu-id="159e9-172">Adding a Button to the WPF Window</span></span>
 <span data-ttu-id="159e9-173">Ensuite, vous allez ajouter un contrôle Button et créer un gestionnaire d’événements pour l’événement `Click` du bouton.</span><span class="sxs-lookup"><span data-stu-id="159e9-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="159e9-174">Plus tard, vous ajouterez le code à. ainsi, lorsque vous cliquerez sur le bouton, le contenu du fichier texte sera mis en cache et affiché.</span><span class="sxs-lookup"><span data-stu-id="159e9-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>

#### <a name="to-add-a-button-control"></a><span data-ttu-id="159e9-175">Pour ajouter un contrôle Button</span><span class="sxs-lookup"><span data-stu-id="159e9-175">To add a button control</span></span>

1. <span data-ttu-id="159e9-176">Dans **Explorateur de solutions**, double-cliquez sur le fichier MainWindow. XAML pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="159e9-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>

2. <span data-ttu-id="159e9-177">À partir de la **boîte à outils**, sous **contrôles WPF communs**, faites glisser un contrôle `Button` vers la fenêtre de `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="159e9-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>

3. <span data-ttu-id="159e9-178">Dans la fenêtre **Propriétés** , affectez à la propriété `Content` du contrôle `Button` la valeur récupérer dans le **cache**.</span><span class="sxs-lookup"><span data-stu-id="159e9-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>

## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="159e9-179">Initialisation du cache et mise en cache d’une entrée</span><span class="sxs-lookup"><span data-stu-id="159e9-179">Initializing the Cache and Caching an Entry</span></span>
 <span data-ttu-id="159e9-180">Ensuite, vous allez ajouter le code pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="159e9-180">Next, you will add the code to perform the following tasks:</span></span>

- <span data-ttu-id="159e9-181">Créez une instance de la classe cache, autrement dit, vous allez instancier un nouvel objet <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="159e9-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>

- <span data-ttu-id="159e9-182">Spécifiez que le cache utilise un objet <xref:System.Runtime.Caching.HostFileChangeMonitor> pour surveiller les modifications dans le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="159e9-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>

- <span data-ttu-id="159e9-183">Lit le fichier texte et met en cache son contenu en tant qu’entrée de cache.</span><span class="sxs-lookup"><span data-stu-id="159e9-183">Read the text file and cache its contents as a cache entry.</span></span>

- <span data-ttu-id="159e9-184">Affichez le contenu du fichier texte mis en cache.</span><span class="sxs-lookup"><span data-stu-id="159e9-184">Display the contents of the cached text file.</span></span>

#### <a name="to-create-the-cache-object"></a><span data-ttu-id="159e9-185">Pour créer l’objet cache</span><span class="sxs-lookup"><span data-stu-id="159e9-185">To create the cache object</span></span>

1. <span data-ttu-id="159e9-186">Double-cliquez sur le bouton que vous venez d’ajouter afin de créer un gestionnaire d’événements dans le fichier MainWindow.xaml.cs ou MainWindow. Xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="159e9-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>

2. <span data-ttu-id="159e9-187">En haut du fichier (avant la déclaration de classe), ajoutez les instructions `Imports` (Visual Basic) ou `using` (C#) suivantes :</span><span class="sxs-lookup"><span data-stu-id="159e9-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. <span data-ttu-id="159e9-188">Dans le gestionnaire d’événements, ajoutez le code suivant pour instancier l’objet cache :</span><span class="sxs-lookup"><span data-stu-id="159e9-188">In the event handler, add the following code to instantiate the cache object:</span></span>

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <span data-ttu-id="159e9-189">La classe <xref:System.Runtime.Caching.ObjectCache> est une classe intégrée qui fournit un cache d’objets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="159e9-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>

4. <span data-ttu-id="159e9-190">Ajoutez le code suivant pour lire le contenu d’une entrée de cache nommée `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="159e9-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. <span data-ttu-id="159e9-191">Ajoutez le code suivant pour vérifier si l’entrée de cache nommée `filecontents` existe :</span><span class="sxs-lookup"><span data-stu-id="159e9-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     <span data-ttu-id="159e9-192">Si l’entrée de cache spécifiée n’existe pas, vous devez lire le fichier texte et l’ajouter en tant qu’entrée de cache au cache.</span><span class="sxs-lookup"><span data-stu-id="159e9-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>

6. <span data-ttu-id="159e9-193">Dans le bloc `if/then`, ajoutez le code suivant pour créer un nouvel objet <xref:System.Runtime.Caching.CacheItemPolicy> qui spécifie que l’entrée de cache expire au bout de 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="159e9-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     <span data-ttu-id="159e9-194">Si aucune information d’éviction ou d’expiration n’est fournie, la valeur par défaut est <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, ce qui signifie que les entrées du cache n’expirent jamais en fonction d’une heure absolue.</span><span class="sxs-lookup"><span data-stu-id="159e9-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="159e9-195">Au lieu de cela, les entrées de cache expirent uniquement en cas de sollicitation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="159e9-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="159e9-196">En guise de meilleure pratique, vous devez toujours fournir explicitement une expiration absolue ou décalée.</span><span class="sxs-lookup"><span data-stu-id="159e9-196">As a best practice, you should always explicitly provide either an absolute or a sliding expiration.</span></span>

7. <span data-ttu-id="159e9-197">Dans le bloc `if/then` et après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour créer une collection pour les chemins d’accès aux fichiers que vous souhaitez analyser, et pour ajouter le chemin d’accès du fichier texte à la collection :</span><span class="sxs-lookup"><span data-stu-id="159e9-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > <span data-ttu-id="159e9-198">Si le fichier texte que vous souhaitez utiliser n’est pas `c:\cache\cacheText.txt`, spécifiez le chemin d’accès du fichier texte que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="159e9-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>

8. <span data-ttu-id="159e9-199">Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour ajouter un nouvel objet <xref:System.Runtime.Caching.HostFileChangeMonitor> à la collection d’analyses de modification pour l’entrée de cache :</span><span class="sxs-lookup"><span data-stu-id="159e9-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <span data-ttu-id="159e9-200">L’objet <xref:System.Runtime.Caching.HostFileChangeMonitor> surveille le chemin d’accès du fichier texte et avertit le cache si des modifications se produisent.</span><span class="sxs-lookup"><span data-stu-id="159e9-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="159e9-201">Dans cet exemple, l’entrée de cache expire si le contenu du fichier est modifié.</span><span class="sxs-lookup"><span data-stu-id="159e9-201">In this example, the cache entry will expire if the content of the file changes.</span></span>

9. <span data-ttu-id="159e9-202">Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour lire le contenu du fichier texte :</span><span class="sxs-lookup"><span data-stu-id="159e9-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     <span data-ttu-id="159e9-203">L’horodateur de la date et de l’heure est ajouté afin que vous puissiez voir à quel moment l’entrée du cache expire.</span><span class="sxs-lookup"><span data-stu-id="159e9-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>

10. <span data-ttu-id="159e9-204">Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour insérer le contenu du fichier dans l’objet cache en tant qu’instance de <xref:System.Runtime.Caching.CacheItem> :</span><span class="sxs-lookup"><span data-stu-id="159e9-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     <span data-ttu-id="159e9-205">Vous spécifiez des informations sur la façon dont l’entrée du cache doit être supprimée en passant l’objet <xref:System.Runtime.Caching.CacheItemPolicy> que vous avez créé précédemment en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="159e9-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>

11. <span data-ttu-id="159e9-206">Après le bloc `if/then`, ajoutez le code suivant pour afficher le contenu du fichier mis en cache dans une boîte de message :</span><span class="sxs-lookup"><span data-stu-id="159e9-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. <span data-ttu-id="159e9-207">Dans le menu **générer** , cliquez sur **générer WPFCaching** pour générer votre projet.</span><span class="sxs-lookup"><span data-stu-id="159e9-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>

## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="159e9-208">Test de la mise en cache dans l’application WPF</span><span class="sxs-lookup"><span data-stu-id="159e9-208">Testing Caching in the WPF Application</span></span>
 <span data-ttu-id="159e9-209">Vous pouvez à présent tester l’application.</span><span class="sxs-lookup"><span data-stu-id="159e9-209">You can now test the application.</span></span>

#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="159e9-210">Pour tester la mise en cache dans l’application WPF</span><span class="sxs-lookup"><span data-stu-id="159e9-210">To test caching in the WPF application</span></span>

1. <span data-ttu-id="159e9-211">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="159e9-211">Press CTRL+F5 to run the application.</span></span>

     <span data-ttu-id="159e9-212">La fenêtre `MainWindow` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="159e9-212">The `MainWindow` window is displayed.</span></span>

2. <span data-ttu-id="159e9-213">Cliquez sur **récupérer le cache**.</span><span class="sxs-lookup"><span data-stu-id="159e9-213">Click **Get Cache**.</span></span>

     <span data-ttu-id="159e9-214">Le contenu mis en cache à partir du fichier texte s’affiche dans une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="159e9-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="159e9-215">Notez l’horodateur du fichier.</span><span class="sxs-lookup"><span data-stu-id="159e9-215">Notice the timestamp on the file.</span></span>

3. <span data-ttu-id="159e9-216">Fermez la boîte de message, puis cliquez à nouveau sur **récupérer le cache** .</span><span class="sxs-lookup"><span data-stu-id="159e9-216">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="159e9-217">L’horodateur est inchangé.</span><span class="sxs-lookup"><span data-stu-id="159e9-217">The timestamp is unchanged.</span></span> <span data-ttu-id="159e9-218">Cela indique que le contenu mis en cache est affiché.</span><span class="sxs-lookup"><span data-stu-id="159e9-218">This indicates the cached content is displayed.</span></span>

4. <span data-ttu-id="159e9-219">Attendez au moins 10 secondes, puis cliquez à nouveau sur **obtenir le cache** .</span><span class="sxs-lookup"><span data-stu-id="159e9-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>

     <span data-ttu-id="159e9-220">Cette fois, un nouvel horodateur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="159e9-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="159e9-221">Cela indique que la stratégie laisse l’entrée de cache expirer et que le nouveau contenu mis en cache est affiché.</span><span class="sxs-lookup"><span data-stu-id="159e9-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>

5. <span data-ttu-id="159e9-222">Dans un éditeur de texte, ouvrez le fichier texte que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="159e9-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="159e9-223">N’apportez aucune modification pour le moment.</span><span class="sxs-lookup"><span data-stu-id="159e9-223">Do not make any changes yet.</span></span>

6. <span data-ttu-id="159e9-224">Fermez la boîte de message, puis cliquez à nouveau sur **récupérer le cache** .</span><span class="sxs-lookup"><span data-stu-id="159e9-224">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="159e9-225">Remarquez l’horodatage.</span><span class="sxs-lookup"><span data-stu-id="159e9-225">Notice the timestamp again.</span></span>

7. <span data-ttu-id="159e9-226">Apportez une modification au fichier texte, puis enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="159e9-226">Make a change to the text file and then save the file.</span></span>

8. <span data-ttu-id="159e9-227">Fermez la boîte de message, puis cliquez à nouveau sur **récupérer le cache** .</span><span class="sxs-lookup"><span data-stu-id="159e9-227">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="159e9-228">Cette boîte de message contient le contenu mis à jour à partir du fichier texte et un nouvel horodateur.</span><span class="sxs-lookup"><span data-stu-id="159e9-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="159e9-229">Cela indique que l’analyse de la modification du fichier hôte a expulsé l’entrée du cache immédiatement lorsque vous avez modifié le fichier, même si le délai d’expiration absolu n’a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="159e9-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>

    > [!NOTE]
    > <span data-ttu-id="159e9-230">Vous pouvez augmenter le temps d’éviction à 20 secondes ou plus afin de laisser plus de temps à apporter une modification dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="159e9-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>

## <a name="code-example"></a><span data-ttu-id="159e9-231">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="159e9-231">Code Example</span></span>
 <span data-ttu-id="159e9-232">Une fois que vous avez terminé cette procédure pas à pas, le code pour le projet que vous avez créé ressemble à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="159e9-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="159e9-233">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="159e9-233">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [<span data-ttu-id="159e9-234">Mise en cache dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="159e9-234">Caching in .NET Framework Applications</span></span>](../../performance/caching-in-net-framework-applications.md)
