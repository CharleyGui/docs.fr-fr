---
title: 'Procédure pas à pas : mise en cache des données d’application dans une application WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 4ee973eb5a81a6428ee5a5fcfc00e28425ff2a44
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457517"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="e3515-102">Procédure pas à pas : mise en cache des données d’application dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="e3515-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="e3515-103">La mise en cache vous permet de stocker des données en mémoire pour y accéder rapidement.</span><span class="sxs-lookup"><span data-stu-id="e3515-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="e3515-104">Quand vous accédez à nouveau aux données, les applications peuvent obtenir les données à partir du cache au lieu de devoir les récupérer à partir de la source d’origine.</span><span class="sxs-lookup"><span data-stu-id="e3515-104">When the data is accessed again, applications can get the data from the cache instead of retrieving it from the original source.</span></span> <span data-ttu-id="e3515-105">Cela peut améliorer les performances et la scalabilité.</span><span class="sxs-lookup"><span data-stu-id="e3515-105">This can improve performance and scalability.</span></span> <span data-ttu-id="e3515-106">La mise en cache rend également les données disponibles quand la source de données est temporairement indisponible.</span><span class="sxs-lookup"><span data-stu-id="e3515-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>

 <span data-ttu-id="e3515-107">Le .NET Framework fournit des classes qui vous permettent d’utiliser la mise en cache dans les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e3515-107">The .NET Framework provides classes that enable you to use caching in .NET Framework applications.</span></span> <span data-ttu-id="e3515-108">Ces classes se trouvent dans le <xref:System.Runtime.Caching> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e3515-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
>  <span data-ttu-id="e3515-109">Le <xref:System.Runtime.Caching> espace de noms est une nouveauté de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e3515-109">The <xref:System.Runtime.Caching> namespace is new in the .NET Framework 4.</span></span> <span data-ttu-id="e3515-110">Cet espace de noms rend la mise en cache est disponible pour toutes les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e3515-110">This namespace makes caching is available to all .NET Framework applications.</span></span> <span data-ttu-id="e3515-111">Dans les versions précédentes du .NET Framework, la mise en cache était disponible uniquement dans le <xref:System.Web> espace de noms et nécessitait donc une dépendance vis-à-vis des classes ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e3515-111">In previous versions of the .NET Framework, caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>

 <span data-ttu-id="e3515-112">Cette procédure pas à pas vous montre comment utiliser la fonctionnalité de mise en cache est disponible dans le .NET Framework en tant que partie d’un [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="e3515-112">This walkthrough shows you how to use the caching functionality that is available in the .NET Framework as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="e3515-113">Dans la procédure pas à pas, vous mettre en cache le contenu d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e3515-113">In the walkthrough, you cache the contents of a text file.</span></span>

 <span data-ttu-id="e3515-114">Cette procédure pas à pas décrit les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="e3515-114">Tasks illustrated in this walkthrough include the following:</span></span>

- <span data-ttu-id="e3515-115">Création d’un projet d’application WPF.</span><span class="sxs-lookup"><span data-stu-id="e3515-115">Creating a WPF application project.</span></span>

- <span data-ttu-id="e3515-116">Ajout d’une référence vers le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e3515-116">Adding a reference to the .NET Framework 4.</span></span>

- <span data-ttu-id="e3515-117">Initialisation d’un cache.</span><span class="sxs-lookup"><span data-stu-id="e3515-117">Initializing a cache.</span></span>

- <span data-ttu-id="e3515-118">Ajout d’une entrée de cache qui contient le contenu d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e3515-118">Adding a cache entry that contains the contents of a text file.</span></span>

- <span data-ttu-id="e3515-119">En fournissant une stratégie d’éviction de l’entrée de cache.</span><span class="sxs-lookup"><span data-stu-id="e3515-119">Providing an eviction policy for the cache entry.</span></span>

- <span data-ttu-id="e3515-120">Analyse le chemin d’accès du fichier mis en cache et l’informant de l’instance de cache des modifications apportées à l’élément analysé.</span><span class="sxs-lookup"><span data-stu-id="e3515-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e3515-121">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e3515-121">Prerequisites</span></span>
 <span data-ttu-id="e3515-122">Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e3515-122">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="e3515-123">Microsoft Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="e3515-123">Microsoft Visual Studio 2010.</span></span>

- <span data-ttu-id="e3515-124">Un fichier texte qui contient une petite quantité de texte.</span><span class="sxs-lookup"><span data-stu-id="e3515-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="e3515-125">(Vous afficherez le contenu du fichier texte dans une boîte de message.) Le code illustré dans la procédure pas à pas suppose que vous travaillez avec le fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="e3515-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>

     `c:\cache\cacheText.txt`

     <span data-ttu-id="e3515-126">Toutefois, vous pouvez utiliser n’importe quel fichier texte et apporter des modifications mineures au code dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="e3515-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>

## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="e3515-127">Création d’un projet d’Application WPF</span><span class="sxs-lookup"><span data-stu-id="e3515-127">Creating a WPF Application Project</span></span>
 <span data-ttu-id="e3515-128">Vous commencerez par créer un projet d’application WPF.</span><span class="sxs-lookup"><span data-stu-id="e3515-128">You will start by creating a WPF application project.</span></span>

#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="e3515-129">Pour créer une application WPF</span><span class="sxs-lookup"><span data-stu-id="e3515-129">To create a WPF application</span></span>

1. <span data-ttu-id="e3515-130">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3515-130">Start Visual Studio.</span></span>

2. <span data-ttu-id="e3515-131">Dans le **fichier** menu, cliquez sur **New**, puis cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="e3515-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>

     <span data-ttu-id="e3515-132">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e3515-132">The **New Project** dialog box is displayed.</span></span>

3. <span data-ttu-id="e3515-133">Sous **modèles installés**, sélectionnez le langage de programmation que vous souhaitez utiliser (**Visual Basic** ou **Visual C#** ).</span><span class="sxs-lookup"><span data-stu-id="e3515-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>

4. <span data-ttu-id="e3515-134">Dans le **nouveau projet** boîte de dialogue, sélectionnez **Application WPF**.</span><span class="sxs-lookup"><span data-stu-id="e3515-134">In the **New Project** dialog box, select **WPF Application**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e3515-135">Si vous ne voyez pas le **Application WPF** modèle, assurez-vous que vous ciblez une version du .NET Framework qui prend en charge de WPF.</span><span class="sxs-lookup"><span data-stu-id="e3515-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the .NET Framework that supports WPF.</span></span> <span data-ttu-id="e3515-136">Dans le **nouveau projet** boîte de dialogue, sélectionnez .NET Framework 4 dans la liste.</span><span class="sxs-lookup"><span data-stu-id="e3515-136">In the **New Project** dialog box, select .NET Framework 4 from the list.</span></span>

5. <span data-ttu-id="e3515-137">Dans le **nom** texte, entrez un nom pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="e3515-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="e3515-138">Par exemple, vous pouvez entrer **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="e3515-138">For example, you can enter **WPFCaching**.</span></span>

6. <span data-ttu-id="e3515-139">Cochez la case **Créer le répertoire pour la solution**.</span><span class="sxs-lookup"><span data-stu-id="e3515-139">Select the **Create directory for solution** check box.</span></span>

7. <span data-ttu-id="e3515-140">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e3515-140">Click **OK**.</span></span>

     <span data-ttu-id="e3515-141">Le Concepteur WPF s’ouvre dans **conception** afficher et affiche le fichier MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="e3515-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="e3515-142">Visual Studio crée le **mon projet** dossier, le fichier Application.xaml et le fichier MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="e3515-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="e3515-143">Ciblage du .NET Framework et l’ajout d’une référence aux assemblys de mise en cache</span><span class="sxs-lookup"><span data-stu-id="e3515-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>
 <span data-ttu-id="e3515-144">Par défaut, les applications WPF ciblent le [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3515-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="e3515-145">Pour utiliser le <xref:System.Runtime.Caching> espace de noms dans une application WPF, l’application doit cibler le .NET Framework 4 (pas le [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) et doit inclure une référence à l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e3515-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the .NET Framework 4 (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>

 <span data-ttu-id="e3515-146">Par conséquent, l’étape suivante consiste à modifier la cible de .NET Framework et ajoutez une référence à la <xref:System.Runtime.Caching> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e3515-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
>  <span data-ttu-id="e3515-147">La procédure de modification de la cible de .NET Framework est différente dans un projet Visual Basic et dans un projet Visual c#.</span><span class="sxs-lookup"><span data-stu-id="e3515-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="e3515-148">Pour modifier la cible du .NET Framework dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3515-148">To change the target .NET Framework in Visual Basic</span></span>

1. <span data-ttu-id="e3515-149">Dans **l’Explorateur de Solutions**, cliquez sur le nom de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e3515-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>

     <span data-ttu-id="e3515-150">La fenêtre Propriétés de l’application s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e3515-150">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="e3515-151">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="e3515-151">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="e3515-152">En bas de la fenêtre, cliquez sur **Options avancées de compilation...** .</span><span class="sxs-lookup"><span data-stu-id="e3515-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>

     <span data-ttu-id="e3515-153">Le **paramètres avancés du compilateur** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e3515-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>

4. <span data-ttu-id="e3515-154">Dans le **framework cible (toutes les configurations)** , sélectionnez .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e3515-154">In the **Target framework (all configurations)** list, select .NET Framework 4.</span></span> <span data-ttu-id="e3515-155">(Ne sélectionnez pas [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="e3515-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>

5. <span data-ttu-id="e3515-156">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e3515-156">Click **OK**.</span></span>

     <span data-ttu-id="e3515-157">La boîte de dialogue **Modification du Framework cible** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e3515-157">The **Target Framework Change** dialog box is displayed.</span></span>

6. <span data-ttu-id="e3515-158">Dans le **modification du Framework cible** boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="e3515-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>

     <span data-ttu-id="e3515-159">Le projet est fermé et est ensuite rouvert.</span><span class="sxs-lookup"><span data-stu-id="e3515-159">The project is closed and is then reopened.</span></span>

7. <span data-ttu-id="e3515-160">Ajoutez une référence à l’assembly de mise en cache en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="e3515-160">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="e3515-161">Dans **l’Explorateur de solutions**, cliquez sur le nom du projet, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="e3515-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="e3515-162">Sélectionnez le **.NET** onglet, sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e3515-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="e3515-163">Pour modifier la cible de .NET Framework dans un projet Visual c#</span><span class="sxs-lookup"><span data-stu-id="e3515-163">To change the target .NET Framework in a Visual C# project</span></span>

1. <span data-ttu-id="e3515-164">Dans **l’Explorateur de solutions**, cliquez sur le nom de projet, puis sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e3515-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>

     <span data-ttu-id="e3515-165">La fenêtre Propriétés de l’application s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e3515-165">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="e3515-166">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="e3515-166">Click the **Application** tab.</span></span>

3. <span data-ttu-id="e3515-167">Dans le **framework cible** , sélectionnez .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e3515-167">In the **Target framework** list, select .NET Framework 4.</span></span> <span data-ttu-id="e3515-168">(Ne sélectionnez pas **.NET Framework 4 Client Profile**.)</span><span class="sxs-lookup"><span data-stu-id="e3515-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>

4. <span data-ttu-id="e3515-169">Ajoutez une référence à l’assembly de mise en cache en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="e3515-169">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="e3515-170">Cliquez sur le **références** dossier, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="e3515-170">Right-click the **References** folder and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="e3515-171">Sélectionnez le **.NET** onglet, sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e3515-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="e3515-172">Ajout d’un bouton dans la fenêtre WPF</span><span class="sxs-lookup"><span data-stu-id="e3515-172">Adding a Button to the WPF Window</span></span>
 <span data-ttu-id="e3515-173">Ensuite, vous ajoutez un contrôle button et créerez un gestionnaire d’événements du bouton `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="e3515-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="e3515-174">Plus tard, vous allez ajouter de code lorsque vous cliquez sur le bouton, le contenu du fichier texte est mis en cache et affiché.</span><span class="sxs-lookup"><span data-stu-id="e3515-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>

#### <a name="to-add-a-button-control"></a><span data-ttu-id="e3515-175">Pour ajouter un contrôle de bouton</span><span class="sxs-lookup"><span data-stu-id="e3515-175">To add a button control</span></span>

1. <span data-ttu-id="e3515-176">Dans **l’Explorateur de solutions**, double-cliquez sur le fichier MainWindow.xaml pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="e3515-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>

2. <span data-ttu-id="e3515-177">À partir de la **boîte à outils**, sous **des contrôles WPF communs**, faites glisser un `Button` le contrôle à la `MainWindow` fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e3515-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>

3. <span data-ttu-id="e3515-178">Dans le **propriétés** fenêtre, définissez la `Content` propriété de la `Button` le contrôle à **Cache obtenir**.</span><span class="sxs-lookup"><span data-stu-id="e3515-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>

## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="e3515-179">L’initialisation du Cache et la mise en cache une entrée</span><span class="sxs-lookup"><span data-stu-id="e3515-179">Initializing the Cache and Caching an Entry</span></span>
 <span data-ttu-id="e3515-180">Ensuite, vous allez ajouter le code pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="e3515-180">Next, you will add the code to perform the following tasks:</span></span>

- <span data-ttu-id="e3515-181">Créez une instance de la classe de cache, c'est-à-dire instancier un nouvel <xref:System.Runtime.Caching.MemoryCache> objet.</span><span class="sxs-lookup"><span data-stu-id="e3515-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>

- <span data-ttu-id="e3515-182">Spécifiez que le cache utilise un <xref:System.Runtime.Caching.HostFileChangeMonitor> objet à surveiller les modifications dans le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e3515-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>

- <span data-ttu-id="e3515-183">Lire le fichier texte et mettre en cache son contenu comme une entrée de cache.</span><span class="sxs-lookup"><span data-stu-id="e3515-183">Read the text file and cache its contents as a cache entry.</span></span>

- <span data-ttu-id="e3515-184">Afficher le contenu du fichier texte mis en cache.</span><span class="sxs-lookup"><span data-stu-id="e3515-184">Display the contents of the cached text file.</span></span>

#### <a name="to-create-the-cache-object"></a><span data-ttu-id="e3515-185">Pour créer l’objet de cache</span><span class="sxs-lookup"><span data-stu-id="e3515-185">To create the cache object</span></span>

1. <span data-ttu-id="e3515-186">Double-cliquez sur le bouton que vous venez d’ajouter pour créer un gestionnaire d’événements dans le fichier MainWindow.xaml.cs ou MainWindow.Xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="e3515-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>

2. <span data-ttu-id="e3515-187">En haut du fichier (avant la déclaration de classe), ajoutez le code suivant `Imports` (Visual Basic) ou `using` instructions (c#) :</span><span class="sxs-lookup"><span data-stu-id="e3515-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. <span data-ttu-id="e3515-188">Dans le Gestionnaire d’événements, ajoutez le code suivant pour instancier l’objet de cache :</span><span class="sxs-lookup"><span data-stu-id="e3515-188">In the event handler, add the following code to instantiate the cache object:</span></span>

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <span data-ttu-id="e3515-189">Le <xref:System.Runtime.Caching.ObjectCache> est une classe intégrée qui fournit un cache d’objets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="e3515-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>

4. <span data-ttu-id="e3515-190">Ajoutez le code suivant pour lire le contenu d’une entrée de cache nommé `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="e3515-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. <span data-ttu-id="e3515-191">Ajoutez le code suivant pour vérifier si l’entrée de cache nommé `filecontents` existe :</span><span class="sxs-lookup"><span data-stu-id="e3515-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     <span data-ttu-id="e3515-192">Si l’entrée de cache spécifiée n’existe pas, vous devez lire le fichier texte et ajouter une entrée du cache dans le cache.</span><span class="sxs-lookup"><span data-stu-id="e3515-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>

6. <span data-ttu-id="e3515-193">Dans le `if/then` bloquer, ajoutez le code suivant pour créer une nouvelle <xref:System.Runtime.Caching.CacheItemPolicy> objet qui spécifie que l’entrée de cache expire après 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="e3515-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     <span data-ttu-id="e3515-194">Si aucune information d’éviction ou d’expiration est fournie, la valeur par défaut est <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, ce qui signifie que les entrées du cache n’expirent jamais en uniquement sur une heure absolue.</span><span class="sxs-lookup"><span data-stu-id="e3515-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="e3515-195">Au lieu de cela, les entrées du cache expirent uniquement en cas de sollicitation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e3515-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="e3515-196">Comme meilleure pratique, vous devez toujours explicitement fournir une expiration décalée ou absolu.</span><span class="sxs-lookup"><span data-stu-id="e3515-196">As a best practice, you should always explicitly provide either an absolute or a sliding expiration.</span></span>

7. <span data-ttu-id="e3515-197">À l’intérieur de la `if/then` bloquer et la suite du code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour créer une collection pour les chemins d’accès de fichier que vous voulez surveiller et pour ajouter le chemin d’accès du fichier texte à la collection :</span><span class="sxs-lookup"><span data-stu-id="e3515-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    >  <span data-ttu-id="e3515-198">Si le fichier texte que vous souhaitez utiliser n’est pas `c:\cache\cacheText.txt`, spécifiez le chemin d’accès où le fichier texte que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e3515-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>

8. <span data-ttu-id="e3515-199">Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour ajouter un nouveau <xref:System.Runtime.Caching.HostFileChangeMonitor> surveille d’objet à la collection de modification pour l’entrée de cache :</span><span class="sxs-lookup"><span data-stu-id="e3515-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <span data-ttu-id="e3515-200">Le <xref:System.Runtime.Caching.HostFileChangeMonitor> objet surveille le chemin d’accès du fichier texte et notifie le cache si des modifications interviennent.</span><span class="sxs-lookup"><span data-stu-id="e3515-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="e3515-201">Dans cet exemple, l’entrée de cache expire si le contenu du fichier change.</span><span class="sxs-lookup"><span data-stu-id="e3515-201">In this example, the cache entry will expire if the content of the file changes.</span></span>

9. <span data-ttu-id="e3515-202">Suite du code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour lire le contenu du fichier texte :</span><span class="sxs-lookup"><span data-stu-id="e3515-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     <span data-ttu-id="e3515-203">L’horodatage de date et d’heure est ajoutée afin que vous serez en mesure de voir quand l’entrée de cache expire.</span><span class="sxs-lookup"><span data-stu-id="e3515-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>

10. <span data-ttu-id="e3515-204">Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour insérer le contenu du fichier dans l’objet cache comme un <xref:System.Runtime.Caching.CacheItem> instance :</span><span class="sxs-lookup"><span data-stu-id="e3515-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     <span data-ttu-id="e3515-205">Vous spécifiez des informations sur le mode de suppression de l’entrée de cache en passant le <xref:System.Runtime.Caching.CacheItemPolicy> objet que vous avez créé précédemment en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="e3515-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>

11. <span data-ttu-id="e3515-206">Après le `if/then` bloquer, ajoutez le code suivant pour afficher le contenu du fichier mis en cache dans une boîte de message :</span><span class="sxs-lookup"><span data-stu-id="e3515-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. <span data-ttu-id="e3515-207">Dans le **Build** menu, cliquez sur **générer WPFCaching** pour générer votre projet.</span><span class="sxs-lookup"><span data-stu-id="e3515-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>

## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="e3515-208">Test de la mise en cache dans l’Application WPF</span><span class="sxs-lookup"><span data-stu-id="e3515-208">Testing Caching in the WPF Application</span></span>
 <span data-ttu-id="e3515-209">Vous pouvez maintenant tester l’application.</span><span class="sxs-lookup"><span data-stu-id="e3515-209">You can now test the application.</span></span>

#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="e3515-210">Pour tester la mise en cache dans l’application WPF</span><span class="sxs-lookup"><span data-stu-id="e3515-210">To test caching in the WPF application</span></span>

1. <span data-ttu-id="e3515-211">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="e3515-211">Press CTRL+F5 to run the application.</span></span>

     <span data-ttu-id="e3515-212">Le `MainWindow` fenêtre s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e3515-212">The `MainWindow` window is displayed.</span></span>

2. <span data-ttu-id="e3515-213">Cliquez sur **obtenir Cache**.</span><span class="sxs-lookup"><span data-stu-id="e3515-213">Click **Get Cache**.</span></span>

     <span data-ttu-id="e3515-214">Le contenu mis en cache à partir du fichier texte est affiché dans une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="e3515-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="e3515-215">Notez l’horodatage sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="e3515-215">Notice the timestamp on the file.</span></span>

3. <span data-ttu-id="e3515-216">Fermez la boîte de message, puis **Cache obtenir** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="e3515-216">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="e3515-217">L’horodatage est inchangé.</span><span class="sxs-lookup"><span data-stu-id="e3515-217">The timestamp is unchanged.</span></span> <span data-ttu-id="e3515-218">Cela indique que le contenu mis en cache s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e3515-218">This indicates the cached content is displayed.</span></span>

4. <span data-ttu-id="e3515-219">Attendez au moins 10 secondes, puis **Cache obtenir** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="e3515-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>

     <span data-ttu-id="e3515-220">Cette fois, un nouvel horodatage s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e3515-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="e3515-221">Cela indique que la stratégie permettre l’entrée de cache expire et que le nouveau contenu mis en cache est affiché.</span><span class="sxs-lookup"><span data-stu-id="e3515-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>

5. <span data-ttu-id="e3515-222">Dans un éditeur de texte, ouvrez le fichier texte que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="e3515-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="e3515-223">N’apportez pas encore de modifications.</span><span class="sxs-lookup"><span data-stu-id="e3515-223">Do not make any changes yet.</span></span>

6. <span data-ttu-id="e3515-224">Fermez la boîte de message, puis **Cache obtenir** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="e3515-224">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="e3515-225">Notez à nouveau l’horodatage.</span><span class="sxs-lookup"><span data-stu-id="e3515-225">Notice the timestamp again.</span></span>

7. <span data-ttu-id="e3515-226">Apportez une modification dans le fichier texte, puis enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="e3515-226">Make a change to the text file and then save the file.</span></span>

8. <span data-ttu-id="e3515-227">Fermez la boîte de message, puis **Cache obtenir** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="e3515-227">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="e3515-228">Cette boîte de message contient le contenu mis à jour à partir du fichier texte et un nouveau horodatage.</span><span class="sxs-lookup"><span data-stu-id="e3515-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="e3515-229">Cela indique que l’Analyseur de modification de fichier hôte supprimé l’entrée du cache immédiatement lorsque vous avez modifié le fichier, même si le délai d’expiration absolue n’a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="e3515-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e3515-230">Vous pouvez augmenter le temps d’éviction à 20 secondes ou plus pour permettre plus de temps pour vous apporter une modification dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="e3515-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>

## <a name="code-example"></a><span data-ttu-id="e3515-231">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="e3515-231">Code Example</span></span>
 <span data-ttu-id="e3515-232">Une fois que vous avez terminé cette procédure pas à pas, le code pour le projet que vous avez créé doit ressembler à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e3515-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e3515-233">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3515-233">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [<span data-ttu-id="e3515-234">Mise en cache dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e3515-234">Caching in .NET Framework Applications</span></span>](../../performance/caching-in-net-framework-applications.md)
