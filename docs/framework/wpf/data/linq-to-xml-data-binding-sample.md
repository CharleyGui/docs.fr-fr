---
title: Exemple de liaison de données LINQ to XML
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920936"
---
# <a name="linq-to-xml-data-binding-sample"></a><span data-ttu-id="b1dd4-102">Exemple de liaison de données LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b1dd4-102">LINQ to XML data binding sample</span></span>

<span data-ttu-id="b1dd4-103">Cet article décrit l’exemple LinqToXmlDataBinding, une application Windows Presentation Foundation (WPF) qui lie des composants d’interface utilisateur à une source de données XML incorporée.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-103">This article describes the LinqToXmlDataBinding sample, a Windows Presentation Foundation (WPF) app that binds user interface components to an embedded XML data source.</span></span>

## <a name="overview"></a><span data-ttu-id="b1dd4-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b1dd4-104">Overview</span></span>

<span data-ttu-id="b1dd4-105">L’exemple LinqToXmlDataBinding est une application Windows Presentation Foundation (WPF) qui contient C# des fichiers sources XAML et.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-105">The LinqToXmlDataBinding sample is a Windows Presentation Foundation (WPF) app that contains C# and XAML source files.</span></span> <span data-ttu-id="b1dd4-106">Un document XML incorporé définit une liste de livres.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-106">An embedded XML document defines a list of books.</span></span> <span data-ttu-id="b1dd4-107">L’application permet à l’utilisateur d’afficher, d’ajouter, de supprimer et de modifier les entrées de livre.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-107">The app enables the user to view, add, delete, and edit the book entries.</span></span>

<span data-ttu-id="b1dd4-108">Il existe deux fichiers sources principaux :</span><span class="sxs-lookup"><span data-stu-id="b1dd4-108">There are two primary source files:</span></span>

- <span data-ttu-id="b1dd4-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) contient le code de déclaration XAML pour l’interface utilisateur de la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) contains the XAML declaration code for the user interface (UI) of the main window.</span></span> <span data-ttu-id="b1dd4-110">Elle contient également une section de ressources de fenêtre qui définit un fournisseur de données et un document XML incorporé pour les listes de livres.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-110">It also contains a window resource section that defines a data provider and an embedded XML document for the book listings.</span></span>

- <span data-ttu-id="b1dd4-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contient les méthodes d’initialisation et de gestion d’événements associées à l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contains the initialization and event-handling methods associated with the UI.</span></span>

<span data-ttu-id="b1dd4-112">La fenêtre principale est composée des quatre sections d'interface utilisateur verticales suivantes :</span><span class="sxs-lookup"><span data-stu-id="b1dd4-112">The main window is divided into the following four vertical UI sections:</span></span>

- <span data-ttu-id="b1dd4-113">**XML** affiche la source XML brute de la liste de livres incorporée.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-113">**XML** displays the raw XML source of the embedded book listing.</span></span>

- <span data-ttu-id="b1dd4-114">**Book List** affiche les entrées de livres au format texte standard et permet à l’utilisateur de sélectionner et de supprimer des entrées.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-114">**Book List** displays the book entries as standard text and enables the user to select and delete individual entries.</span></span>

- <span data-ttu-id="b1dd4-115">**Edit Selected Book** permet à l’utilisateur de modifier les valeurs associées à l’entrée de livre sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-115">**Edit Selected Book** enables the user to edit the values associated with the currently selected book entry.</span></span>

- <span data-ttu-id="b1dd4-116">**Add New Book** permet la création d’une nouvelle entrée de livre sur la base des valeurs entrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-116">**Add New Book** enables the creation of a new book entry based on values entered by the user.</span></span>

## <a name="run-the-sample"></a><span data-ttu-id="b1dd4-117">Exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="b1dd4-117">Run the sample</span></span>

<span data-ttu-id="b1dd4-118">Cette section montre comment créer et générer le projet LinqToXmlDataBinding dans Visual Studio, et comment exécuter l’application LinqToXmlDataBinding Windows Presentation Foundation (WPF) résultante.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-118">This section shows how to create and build the LinqToXmlDataBinding project in Visual Studio, and how to run the resulting LinqToXmlDataBinding Windows Presentation Foundation (WPF) app.</span></span>

### <a name="create-the-project"></a><span data-ttu-id="b1dd4-119">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="b1dd4-119">Create the project</span></span>

1. <span data-ttu-id="b1dd4-120">Ouvrez Visual Studio et créez une **application WPF** C# nommée **LinqToXmlDataBinding**.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-120">Open Visual Studio and create a C# **WPF App** named **LinqToXmlDataBinding**.</span></span>

   <span data-ttu-id="b1dd4-121">Le projet doit cibler le .NET Framework 3.5 (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="b1dd4-121">The project should target the .NET Framework 3.5 (or later).</span></span>

1. <span data-ttu-id="b1dd4-122">Si elles ne sont pas déjà présentes, ajoutez les références de projet pour les assemblys .NET suivants :</span><span class="sxs-lookup"><span data-stu-id="b1dd4-122">If not already present, add project references for the following .NET assemblies:</span></span>

    - <span data-ttu-id="b1dd4-123">System.Data</span><span class="sxs-lookup"><span data-stu-id="b1dd4-123">System.Data</span></span>
    - <span data-ttu-id="b1dd4-124">System.Data.DataSetExtensions</span><span class="sxs-lookup"><span data-stu-id="b1dd4-124">System.Data.DataSetExtensions</span></span>
    - <span data-ttu-id="b1dd4-125">System.Xml</span><span class="sxs-lookup"><span data-stu-id="b1dd4-125">System.Xml</span></span>
    - <span data-ttu-id="b1dd4-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="b1dd4-126">System.Xml</span></span>

1. <span data-ttu-id="b1dd4-127">Générez la solution en appuyant sur **Ctrl**+**Maj**+**B**, puis exécutez-la en appuyant sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-127">Build the solution by pressing **Ctrl**+**Shift**+**B**, then run it by pressing **F5**.</span></span>

   <span data-ttu-id="b1dd4-128">Le projet doit être compilé sans erreur et exécuté en tant qu'application WPF générique.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-128">The project should compile without errors and run as a generic WPF application.</span></span>

### <a name="add-code"></a><span data-ttu-id="b1dd4-129">Ajouter du code</span><span class="sxs-lookup"><span data-stu-id="b1dd4-129">Add code</span></span>

1. <span data-ttu-id="b1dd4-130">Dans l’**Explorateur de solutions**, renommez le fichier source **Window1.xaml** en **L2XDBForm.xaml**.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-130">In **Solution Explorer**, rename the source file **Window1.xaml** to **L2XDBForm.xaml**.</span></span>

   <span data-ttu-id="b1dd4-131">Le fichier source dépendant Window1.xaml.cs est automatiquement renommé en L2XDBForm.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-131">The dependent source file Window1.xaml.cs is automatically renamed to L2XDBForm.xaml.cs.</span></span>

1. <span data-ttu-id="b1dd4-132">Remplacez le code source trouvé dans le fichier **L2XDBForm. Xaml** par le [code source L2DBForm. Xaml](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="b1dd4-132">Replace the source code found in the file **L2XDBForm.xaml** with the [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="b1dd4-133">Utilisez la vue source XAML pour travailler avec ce fichier.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-133">Use the XAML source view to work with this file.</span></span>

1. <span data-ttu-id="b1dd4-134">De même, remplacez la source dans **L2XDBForm.Xaml.cs** par le [code source L2DBForm.Xaml.cs](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="b1dd4-134">Similarly, replace the source in **L2XDBForm.xaml.cs** with the [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

1. <span data-ttu-id="b1dd4-135">Dans le fichier **app. Xaml**, remplacez toutes les occurrences de la chaîne **Window1. Xaml** par **L2XDBForm. Xaml**.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-135">In the file **App.xaml**, replace all occurrences of the string **Window1.xaml** with **L2XDBForm.xaml**.</span></span>

1. <span data-ttu-id="b1dd4-136">Générez la solution en appuyant sur **Ctrl**+**Maj**+**B**.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-136">Build the solution by pressing **Ctrl**+**Shift**+**B**.</span></span>

### <a name="run-the-app"></a><span data-ttu-id="b1dd4-137">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="b1dd4-137">Run the app</span></span>

<span data-ttu-id="b1dd4-138">L’application LinqToXmlDataBinding permet à l’utilisateur d’afficher et de manipuler une liste de livres stockée en tant qu’élément XML incorporé.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-138">The LinqToXmlDataBinding app enables the user to view and manipulate a list of books that's stored as an embedded XML element.</span></span> <span data-ttu-id="b1dd4-139">Exécutez l’application en appuyant sur **F5** (démarrer le débogage) ou **CTRL**+**F5** (exécuter sans débogage).</span><span class="sxs-lookup"><span data-stu-id="b1dd4-139">Run the app by pressing **F5** (Start Debugging) or **Ctrl**+**F5** (Start Without Debugging).</span></span>

<span data-ttu-id="b1dd4-140">Une fenêtre de programme avec le titre **WPF Data Binding using LINQ to XML** apparaît.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-140">A program window with the title **WPF Data Binding using LINQ to XML** appears.</span></span>

<span data-ttu-id="b1dd4-141">La partie supérieure de l’interface utilisateur affiche le **code XML** brut qui représente la liste de livres.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-141">The top section of the UI displays the raw **XML** that represents the book list.</span></span> <span data-ttu-id="b1dd4-142">Il est affiché à l'aide d'un contrôle <xref:System.Windows.Controls.TextBlock> WPF, qui n'autorise pas d'interaction via le clavier ou la souris.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-142">It is displayed using a WPF <xref:System.Windows.Controls.TextBlock> control, which does not enable interaction through the mouse or keyboard.</span></span>

<span data-ttu-id="b1dd4-143">La deuxième section verticale, libellée **Book List**, affiche les livres sous la forme d’une liste ordonnée en texte brut.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-143">The second vertical section, labeled **Book List**, displays the books as a plain text ordered list.</span></span> <span data-ttu-id="b1dd4-144">Elle utilise un contrôle <xref:System.Windows.Controls.ListBox> qui autorise la sélection via la souris ou le clavier.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-144">It uses a <xref:System.Windows.Controls.ListBox> control that enables selection though the mouse or keyboard.</span></span>

### <a name="add-and-delete-books"></a><span data-ttu-id="b1dd4-145">Ajouter et supprimer des livres</span><span class="sxs-lookup"><span data-stu-id="b1dd4-145">Add and delete books</span></span>

<span data-ttu-id="b1dd4-146">Pour ajouter un nouveau livre à la liste, entrez des valeurs dans les contrôles **ID** et **value** <xref:System.Windows.Controls.TextBox> dans la dernière section, **Add New Book**, puis sélectionnez **Add Book**.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-146">To add a new book to the list, enter values into the **ID** and **Value** <xref:System.Windows.Controls.TextBox> controls in the last section, **Add New Book**, and then select **Add Book**.</span></span> <span data-ttu-id="b1dd4-147">Le livre est ajouté à la liste dans les listes livre et XML.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-147">The book is appended to the list in both the book and XML listings.</span></span> <span data-ttu-id="b1dd4-148">Ce programme ne valide pas les valeurs d'entrée.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-148">This program does not validate input values.</span></span>

<span data-ttu-id="b1dd4-149">Pour supprimer un livre existant de la liste, sélectionnez-le dans la section **Book List** , puis sélectionnez **Remove selected Book**.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-149">To delete an existing book from the list, select it in the **Book List** section, and then select **Remove Selected Book**.</span></span> <span data-ttu-id="b1dd4-150">L’entrée de livre est supprimée du livre et des listes de sources XML brutes.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-150">The book entry is removed from both the book and the raw XML source listings.</span></span>

### <a name="edit-a-book-entry"></a><span data-ttu-id="b1dd4-151">Modifier une entrée de livre</span><span class="sxs-lookup"><span data-stu-id="b1dd4-151">Edit a book entry</span></span>

1. <span data-ttu-id="b1dd4-152">Sélectionnez l’entrée de livre dans la deuxième section **Book List**.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-152">Select the book entry in the second **Book List** section.</span></span>

   <span data-ttu-id="b1dd4-153">Ses valeurs actuelles s’affichent dans la section **modifier le livre sélectionné** .</span><span class="sxs-lookup"><span data-stu-id="b1dd4-153">Its current values are displayed in the **Edit Selected Book** section.</span></span>

1. <span data-ttu-id="b1dd4-154">Modifiez les valeurs à l'aide du clavier.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-154">Edit the values using the keyboard.</span></span> <span data-ttu-id="b1dd4-155">Dès que l’un ou l’autre <xref:System.Windows.Controls.TextBox> contrôle perd le focus, les modifications sont propagées automatiquement à la source XML et aux listes de livres.</span><span class="sxs-lookup"><span data-stu-id="b1dd4-155">As soon as either <xref:System.Windows.Controls.TextBox> control loses focus, changes are automatically propagated to the XML source and book listings.</span></span>
