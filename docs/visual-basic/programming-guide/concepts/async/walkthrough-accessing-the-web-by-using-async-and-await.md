---
title: 'Procédure pas à pas : accès au Web avec Async et Await'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 41ededd4d4335b78b8d7a33e8fe387c7d632cbee
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400743"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="254f1-102">Procédure pas à pas : accès au web avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="254f1-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="254f1-103">Vous pouvez écrire des programmes asynchrones plus facilement et intuitivement en utilisant les fonctionnalités async/await.</span><span class="sxs-lookup"><span data-stu-id="254f1-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="254f1-104">Vous pouvez écrire du code asynchrone qui ressemble au code synchrone et laisser le compilateur gérer les difficiles fonctions de rappel et continuations qu’implique généralement le code asynchrone.</span><span class="sxs-lookup"><span data-stu-id="254f1-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="254f1-105">Pour plus d’informations sur la fonctionnalité Async, consultez [programmation asynchrone avec Async et await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="254f1-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="254f1-106">Cette procédure pas à pas commence avec une application Windows Presentation Foundation (WPF) synchrone qui additionne le nombre d’octets figurant dans une liste de sites web.</span><span class="sxs-lookup"><span data-stu-id="254f1-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="254f1-107">La procédure pas à pas convertit ensuite l’application en solution asynchrone en utilisant les nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="254f1-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="254f1-108">Si vous ne souhaitez pas générer les applications vous-même, vous pouvez télécharger « Exemple Async : Accès à la procédure web (C# et Visual Basic) » à partir des [exemples de code de développeur](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="254f1-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="254f1-109">Dans cette procédure pas à pas, vous effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="254f1-109">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="254f1-110">Créer une application WPF</span><span class="sxs-lookup"><span data-stu-id="254f1-110">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="254f1-111">Concevoir une simple fenêtre MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="254f1-111">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="254f1-112">Ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="254f1-112">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="254f1-113">Ajouter les instructions Imports nécessaires</span><span class="sxs-lookup"><span data-stu-id="254f1-113">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="254f1-114">Créer une application synchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-114">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="254f1-115">Tester la solution synchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-115">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="254f1-116">Convertir GetURLContents en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-116">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="254f1-117">Convertir SumPageSizes en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-117">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="254f1-118">Convertir startButton_Click en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-118">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="254f1-119">Tester la solution asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-119">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="254f1-120">Remplacer la méthode GetURLContentsAsync par une méthode .NET Framework</span><span class="sxs-lookup"><span data-stu-id="254f1-120">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="254f1-121">Consultez la section [exemple](#example) pour obtenir un exemple asynchrone complet.</span><span class="sxs-lookup"><span data-stu-id="254f1-121">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="254f1-122">Prérequis</span><span class="sxs-lookup"><span data-stu-id="254f1-122">Prerequisites</span></span>

<span data-ttu-id="254f1-123">Visual Studio 2012 ou version ultérieure doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="254f1-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="254f1-124">Pour plus d’informations, consultez la page [téléchargements](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="254f1-124">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="254f1-125">Créer une application WPF</span><span class="sxs-lookup"><span data-stu-id="254f1-125">Create a WPF application</span></span>

1. <span data-ttu-id="254f1-126">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="254f1-126">Start Visual Studio.</span></span>

2. <span data-ttu-id="254f1-127">Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="254f1-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="254f1-128">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="254f1-128">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="254f1-129">Dans le volet **modèles installés** , choisissez Visual Basic, puis choisissez **application WPF** dans la liste des types de projets.</span><span class="sxs-lookup"><span data-stu-id="254f1-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="254f1-130">Dans la zone de texte **Nom**, entrez `AsyncExampleWPF`, puis choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="254f1-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="254f1-131">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="254f1-131">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="254f1-132">Concevoir une simple fenêtre MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="254f1-132">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="254f1-133">Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="254f1-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="254f1-134">Si la fenêtre **Boîte à outils** n’est pas visible, ouvrez le menu **Affichage**, puis choisissez **Boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="254f1-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="254f1-135">Ajoutez un contrôle **Button** et un contrôle **TextBox** à la fenêtre **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="254f1-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="254f1-136">Mettez en surbrillance le contrôle **TextBox** et, dans la fenêtre **Propriétés**, définissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="254f1-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="254f1-137">Affectez la valeur `resultsTextBox` à la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="254f1-137">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="254f1-138">Affectez la valeur 250 à la propriété **Height**.</span><span class="sxs-lookup"><span data-stu-id="254f1-138">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="254f1-139">Affectez la valeur 500 à la propriété **Width**.</span><span class="sxs-lookup"><span data-stu-id="254f1-139">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="254f1-140">Sous l’onglet **Texte**, spécifiez une police à espacement fixe, comme Lucida Console ou Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="254f1-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="254f1-141">Mettez en surbrillance le contrôle **Button** et, dans la fenêtre **Propriétés**, définissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="254f1-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="254f1-142">Affectez la valeur `startButton` à la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="254f1-142">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="254f1-143">Remplacez la valeur **Button** de la propriété **Content** par **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="254f1-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="254f1-144">Placez la zone de texte et le bouton de manière à ce qu’ils apparaissent tous les deux dans la fenêtre **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="254f1-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="254f1-145">Pour plus d’informations sur le concepteur XAML WPF, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="254f1-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="254f1-146">Ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="254f1-146">Add a reference</span></span>

1. <span data-ttu-id="254f1-147">Dans l’**Explorateur de solutions**, mettez en surbrillance le nom de votre projet.</span><span class="sxs-lookup"><span data-stu-id="254f1-147">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="254f1-148">Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="254f1-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="254f1-149">La boîte de dialogue **Gestionnaire de références** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="254f1-149">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="254f1-150">En haut de la boîte de dialogue, vérifiez que votre projet cible .NET Framework 4.5 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="254f1-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="254f1-151">Dans la zone **Assemblys**, choisissez **Framework** s’il n’est pas déjà sélectionné.</span><span class="sxs-lookup"><span data-stu-id="254f1-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="254f1-152">Dans la liste de noms, cochez la case **System.Net.Http**.</span><span class="sxs-lookup"><span data-stu-id="254f1-152">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="254f1-153">Choisissez le bouton **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="254f1-153">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="254f1-154">Ajouter les instructions Imports nécessaires</span><span class="sxs-lookup"><span data-stu-id="254f1-154">Add necessary Imports statements</span></span>

1. <span data-ttu-id="254f1-155">Dans **Explorateur de solutions**, ouvrez le menu contextuel de MainWindow. Xaml. vb, puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="254f1-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="254f1-156">Ajoutez les `Imports` instructions suivantes en haut du fichier de code, si elles ne sont pas déjà présentes.</span><span class="sxs-lookup"><span data-stu-id="254f1-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="254f1-157">Créer une application synchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-157">Create a synchronous application</span></span>

1. <span data-ttu-id="254f1-158">Dans la fenêtre de conception, MainWindow. xaml, double-cliquez sur le bouton **Démarrer** pour créer le `startButton_Click` Gestionnaire d’événements dans MainWindow. Xaml. vb.</span><span class="sxs-lookup"><span data-stu-id="254f1-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="254f1-159">Dans MainWindow. Xaml. vb, copiez le code suivant dans le corps de `startButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="254f1-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="254f1-160">Le code appelle la méthode qui pilote l'application, `SumPageSizes`, et affiche un message quand le contrôle redevient `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="254f1-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="254f1-161">Le code de la solution synchrone contient les quatre méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="254f1-161">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="254f1-162">`SumPageSizes`, qui obtient la liste des URL des pages web à partir de `SetUpURLList`, puis qui appelle `GetURLContents` et `DisplayResults` pour traiter chaque URL.</span><span class="sxs-lookup"><span data-stu-id="254f1-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="254f1-163">`SetUpURLList`, qui dresse et retourne la liste des adresses web.</span><span class="sxs-lookup"><span data-stu-id="254f1-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="254f1-164">`GetURLContents`, qui télécharge le contenu de chaque site web et retourne le contenu sous la forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="254f1-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="254f1-165">`DisplayResults`, qui affiche le nombre d'octets dans le tableau d'octets pour chaque URL.</span><span class="sxs-lookup"><span data-stu-id="254f1-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="254f1-166">Copiez les quatre méthodes suivantes, puis collez-les sous le `startButton_Click` Gestionnaire d’événements dans MainWindow. Xaml. vb :</span><span class="sxs-lookup"><span data-stu-id="254f1-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="254f1-167">Tester la solution synchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-167">Test the synchronous solution</span></span>

1. <span data-ttu-id="254f1-168">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="254f1-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="254f1-169">Une sortie semblable à la liste suivante doit apparaître :</span><span class="sxs-lookup"><span data-stu-id="254f1-169">Output that resembles the following list should appear:</span></span>

    ```console
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
    msdn.microsoft.com                                            33964
    msdn.microsoft.com/library/hh290136.aspx               225793
    msdn.microsoft.com/library/ee256749.aspx               143577
    msdn.microsoft.com/library/hh290138.aspx               237372
    msdn.microsoft.com/library/hh290140.aspx               128279
    msdn.microsoft.com/library/dd470362.aspx               157649
    msdn.microsoft.com/library/aa578028.aspx               204457
    msdn.microsoft.com/library/ms404677.aspx               176405
    msdn.microsoft.com/library/ff730837.aspx               143474

    Total bytes returned:  1834802

    Control returned to startButton_Click.
    ```

    <span data-ttu-id="254f1-170">Notez que quelques secondes suffisent pour afficher les nombres.</span><span class="sxs-lookup"><span data-stu-id="254f1-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="254f1-171">Pendant ce temps, le thread d'interface utilisateur est bloqué alors qu'il attend que les ressources demandées se téléchargent.</span><span class="sxs-lookup"><span data-stu-id="254f1-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="254f1-172">Par conséquent, vous ne pouvez pas déplacer, agrandir, réduire ni même fermer la fenêtre d’affichage une fois que vous avez choisi le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="254f1-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="254f1-173">Ces efforts échouent jusqu'à ce que les nombres d'octets commencent à apparaître.</span><span class="sxs-lookup"><span data-stu-id="254f1-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="254f1-174">Si un site web ne répond pas, vous n'avez aucune indication précise sur le site en question qui a échoué.</span><span class="sxs-lookup"><span data-stu-id="254f1-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="254f1-175">Il est même difficile d'arrêter l'attente et de fermer le programme.</span><span class="sxs-lookup"><span data-stu-id="254f1-175">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="254f1-176">Convertir GetURLContents en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-176">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="254f1-177">Pour convertir la solution synchrone en solution asynchrone, le meilleur point de départ est de faire en sorte `GetURLContents` que les appels à la <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> méthode et à la <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> méthode se trouvent là où l’application accède au Web.</span><span class="sxs-lookup"><span data-stu-id="254f1-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="254f1-178">Le .NET Framework facilite la conversion en fournissant des versions asynchrones des deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="254f1-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="254f1-179">Pour plus d'informations sur les méthodes utilisées dans `GetURLContents`, consultez <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="254f1-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="254f1-180">Quand vous suivez les étapes décrites dans cette procédure pas à pas, plusieurs erreurs de compilation apparaissent.</span><span class="sxs-lookup"><span data-stu-id="254f1-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="254f1-181">Vous pouvez les ignorer et poursuivre la procédure.</span><span class="sxs-lookup"><span data-stu-id="254f1-181">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="254f1-182">Remplacez la méthode appelée à la troisième ligne de `GetURLContents` dont la valeur est `GetResponse` par la méthode <xref:System.Net.WebRequest.GetResponseAsync%2A> asynchrone basée sur les tâches.</span><span class="sxs-lookup"><span data-stu-id="254f1-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="254f1-183">`GetResponseAsync` retourne un <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="254f1-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="254f1-184">Dans ce cas, la *variable de retour de tâche*, `TResult` , est de type <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="254f1-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="254f1-185">La tâche est une promesse de produire un objet `WebResponse` réel une fois que les données demandées ont été téléchargées et que la tâche s'est exécutée entièrement.</span><span class="sxs-lookup"><span data-stu-id="254f1-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="254f1-186">Pour récupérer la `WebResponse` valeur de la tâche, appliquez un opérateur [await](../../../language-reference/operators/await-operator.md) à l’appel à `GetResponseAsync` , comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="254f1-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="254f1-187">L’opérateur `Await` suspend l’exécution de la méthode actuelle, `GetURLContents`, jusqu’à ce que la tâche attendue soit terminée.</span><span class="sxs-lookup"><span data-stu-id="254f1-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="254f1-188">Entre-temps, le contrôle retourne à l'appelant de la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="254f1-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="254f1-189">Dans cet exemple, la méthode actuelle est `GetURLContents` et l'appelant est `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="254f1-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="254f1-190">Quand la tâche est terminée, l'objet `WebResponse` promis est produit sous forme de valeur de la tâche attendue et assigné à la variable `response`.</span><span class="sxs-lookup"><span data-stu-id="254f1-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="254f1-191">L'instruction précédente peut être divisée en deux instructions suivantes pour clarifier ce qui se passe.</span><span class="sxs-lookup"><span data-stu-id="254f1-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="254f1-192">L'appel à `webReq.GetResponseAsync` retourne un `Task(Of WebResponse)` ou `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="254f1-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="254f1-193">Un `Await` opérateur est ensuite appliqué à la tâche pour récupérer la `WebResponse` valeur.</span><span class="sxs-lookup"><span data-stu-id="254f1-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="254f1-194">Si votre méthode async a un travail à effectuer qui ne dépend pas de l'achèvement de la tâche, elle peut poursuivre ce travail entre ces deux instructions, après l'appel à la méthode async et avant l'application de l'opérateur await.</span><span class="sxs-lookup"><span data-stu-id="254f1-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="254f1-195">Pour obtenir des exemples, consultez [Comment : effectuer plusieurs requêtes Web en parallèle en utilisant Async et await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) et [Comment : étendre la procédure pas à pas Async à l’aide de Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="254f1-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="254f1-196">Comme vous avez ajouté l’opérateur `Await` à l’étape précédente, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="254f1-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="254f1-197">L’opérateur peut être utilisé uniquement dans les méthodes marquées avec le modificateur [Async](../../../language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="254f1-197">The operator can be used only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="254f1-198">Ignorez l'erreur quand que vous répétez les étapes de conversion pour remplacer l'appel à `CopyTo` par un appel à `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="254f1-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="254f1-199">Remplacez le nom de la méthode appelée par <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="254f1-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="254f1-200">La méthode `CopyTo` ou `CopyToAsync` copie les octets dans son argument, `content`, et ne retourne pas de valeur significative.</span><span class="sxs-lookup"><span data-stu-id="254f1-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="254f1-201">Dans la version synchrone, l'appel à `CopyTo` est une simple instruction qui ne retourne aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="254f1-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="254f1-202">La version asynchrone, `CopyToAsync`, retourne un <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="254f1-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="254f1-203">La tâche fonctionne comme Task(void) et permet à la méthode d'être attendue.</span><span class="sxs-lookup"><span data-stu-id="254f1-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="254f1-204">Appliquez `Await` ou `await` à l'appel à `CopyToAsync`, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="254f1-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="254f1-205">L'instruction précédente abrège les deux lignes de code suivantes.</span><span class="sxs-lookup"><span data-stu-id="254f1-205">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="254f1-206">Tout ce qui reste à faire dans `GetURLContents` consiste à adapter la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="254f1-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="254f1-207">Vous pouvez utiliser l' `Await` opérateur uniquement dans les méthodes marquées avec le modificateur [Async](../../../language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="254f1-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="254f1-208">Ajoutez le modificateur pour marquer la méthode en tant que *méthode async*, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="254f1-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="254f1-209">Le type de retour d’une méthode Async peut uniquement être <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="254f1-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="254f1-210">En Visual Basic, la méthode doit être un `Function` qui retourne un `Task` ou `Task(Of T)`, ou la méthode doit être un `Sub`.</span><span class="sxs-lookup"><span data-stu-id="254f1-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="254f1-211">En règle générale, une `Sub` méthode est utilisée uniquement dans un gestionnaire d’événements Async, où `Sub` est requis.</span><span class="sxs-lookup"><span data-stu-id="254f1-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="254f1-212">Dans d’autres cas, vous utilisez `Task(T)` si la méthode terminée a une instruction [Return](../../../language-reference/statements/return-statement.md) qui retourne une valeur de type T et que vous utilisez `Task` si la méthode terminée ne retourne pas de valeur significative.</span><span class="sxs-lookup"><span data-stu-id="254f1-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="254f1-213">Pour plus d’informations, consultez [types de retour Async (Visual Basic)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="254f1-213">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

    <span data-ttu-id="254f1-214">La méthode `GetURLContents` comporte une instruction return et l'instruction retourne un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="254f1-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="254f1-215">Ainsi, le type de retour de la version asynchrone est Task(T), où T est un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="254f1-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="254f1-216">Apportez les modifications suivantes dans la signature de la méthode :</span><span class="sxs-lookup"><span data-stu-id="254f1-216">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="254f1-217">Remplacez le type de retour par `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="254f1-217">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="254f1-218">Par convention, les méthodes asynchrones portent des noms qui se terminent par « Async ». Renommez alors la méthode `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="254f1-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="254f1-219">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="254f1-219">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="254f1-220">Avec ces quelques modifications, la conversion de `GetURLContents` en méthode asynchrone est terminée.</span><span class="sxs-lookup"><span data-stu-id="254f1-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="254f1-221">Convertir SumPageSizes en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-221">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="254f1-222">Répétez les étapes de la procédure précédente pour `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="254f1-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="254f1-223">Tout d'abord, modifiez l'appel à `GetURLContents` en appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="254f1-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="254f1-224">Remplacez le nom de la méthode appelée `GetURLContents` par `GetURLContentsAsync`, si vous ne l'avez pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="254f1-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="254f1-225">Appliquez `Await` à la tâche que `GetURLContentsAsync` retourne pour obtenir la valeur du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="254f1-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="254f1-226">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="254f1-226">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="254f1-227">L'instruction précédente abrège les deux lignes de code suivantes.</span><span class="sxs-lookup"><span data-stu-id="254f1-227">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="254f1-228">Apportez les modifications suivantes dans la signature de la méthode :</span><span class="sxs-lookup"><span data-stu-id="254f1-228">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="254f1-229">Marquez la méthode avec le modificateur `Async`.</span><span class="sxs-lookup"><span data-stu-id="254f1-229">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="254f1-230">Ajoutez « Async » au nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="254f1-230">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="254f1-231">Il n’existe aucune variable de retour de tâche, T, cette fois, car `SumPageSizesAsync` ne retourne pas de valeur pour t. (la méthode n’a aucune `Return` instruction.) Toutefois, la méthode doit retourner un `Task` pour pouvoir être attendu.</span><span class="sxs-lookup"><span data-stu-id="254f1-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="254f1-232">Par conséquent, remplacez le type de méthode par `Sub` `Function` .</span><span class="sxs-lookup"><span data-stu-id="254f1-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="254f1-233">Le type de retour de la fonction est `Task`.</span><span class="sxs-lookup"><span data-stu-id="254f1-233">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="254f1-234">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="254f1-234">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="254f1-235">La conversion de `SumPageSizes` en `SumPageSizesAsync` est terminée.</span><span class="sxs-lookup"><span data-stu-id="254f1-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="254f1-236">Convertir startButton_Click en méthode asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-236">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="254f1-237">Dans le gestionnaire d'événements, remplacez le nom de la méthode appelée `SumPageSizes` par `SumPageSizesAsync`, si vous ne l'avez pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="254f1-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="254f1-238">Étant donné que `SumPageSizesAsync` est une méthode async, modifiez le code dans le gestionnaire d'événements de sorte à attendre le résultat.</span><span class="sxs-lookup"><span data-stu-id="254f1-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="254f1-239">L'appel à `SumPageSizesAsync` reflète l'appel à `CopyToAsync` dans `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="254f1-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="254f1-240">L'appel retourne un `Task`, et non un `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="254f1-240">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="254f1-241">Comme dans les procédures précédentes, vous pouvez convertir l'appel à l'aide d'une ou deux instructions.</span><span class="sxs-lookup"><span data-stu-id="254f1-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="254f1-242">Le code suivant illustre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="254f1-242">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="254f1-243">Pour empêcher une nouvelle entrée accidentelle de l’opération, ajoutez l’instruction suivante en haut de `startButton_Click` pour désactiver le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="254f1-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="254f1-244">Vous pouvez réactiver le bouton à la fin du gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="254f1-244">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="254f1-245">Pour plus d’informations sur la réentrance, consultez [gestion de la réentrance dans les applications Async (Visual Basic)](handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="254f1-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="254f1-246">Enfin, ajoutez le modificateur `Async` à la déclaration pour que le gestionnaire d’événements puisse attendre `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="254f1-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="254f1-247">En règle générale, les noms des gestionnaires d'événements ne sont pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="254f1-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="254f1-248">Le type de retour n’est pas remplacé par `Task` car les gestionnaires d’événements doivent être `Sub` des procédures dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="254f1-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="254f1-249">La conversion du projet depuis un traitement synchrone vers un traitement asynchrone est terminée.</span><span class="sxs-lookup"><span data-stu-id="254f1-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="254f1-250">Tester la solution asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-250">Test the asynchronous solution</span></span>

1. <span data-ttu-id="254f1-251">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="254f1-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="254f1-252">Une sortie semblable à la sortie de la solution synchrone doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="254f1-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="254f1-253">En revanche, observez les différences ci-après.</span><span class="sxs-lookup"><span data-stu-id="254f1-253">However, notice the following differences.</span></span>

    - <span data-ttu-id="254f1-254">Les résultats ne se produisent pas tous en même temps, une fois le traitement terminé.</span><span class="sxs-lookup"><span data-stu-id="254f1-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="254f1-255">Par exemple, les deux programmes contiennent une ligne dans `startButton_Click` qui efface la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="254f1-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="254f1-256">L’objectif est d’effacer la zone de texte entre les exécutions si vous choisissez le bouton **Démarrer** une deuxième fois, une fois qu’un jeu de résultats est apparu.</span><span class="sxs-lookup"><span data-stu-id="254f1-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="254f1-257">Dans la version synchrone, la zone de texte s’efface juste avant que les nombres n’apparaissent pour la deuxième fois, quand les téléchargements sont terminés et que le thread d’interface utilisateur est libre d’effectuer autre chose.</span><span class="sxs-lookup"><span data-stu-id="254f1-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="254f1-258">Dans la version asynchrone, la zone de texte s’efface immédiatement après avoir choisi le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="254f1-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="254f1-259">Plus important encore, le thread d'interface utilisateur n'est pas bloqué pendant les téléchargements.</span><span class="sxs-lookup"><span data-stu-id="254f1-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="254f1-260">Vous pouvez déplacer ou redimensionner la fenêtre pendant le téléchargement, la comptabilisation et l'affichage des ressources web.</span><span class="sxs-lookup"><span data-stu-id="254f1-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="254f1-261">Si l’un des sites web est lent ou ne répond pas, vous pouvez annuler l’opération en choisissant le bouton **Fermer** (le x dans le champ rouge situé dans le coin supérieur droit).</span><span class="sxs-lookup"><span data-stu-id="254f1-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="254f1-262">Remplacer la méthode GetURLContentsAsync par une méthode .NET Framework</span><span class="sxs-lookup"><span data-stu-id="254f1-262">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="254f1-263">Le .NET Framework fournit de nombreuses méthodes Async que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="254f1-263">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="254f1-264">L’une d’entre elles, la <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> méthode, fait exactement ce dont vous avez besoin pour cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="254f1-264">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="254f1-265">Vous pouvez l'utiliser à la place de la méthode `GetURLContentsAsync` que vous avez créée précédemment.</span><span class="sxs-lookup"><span data-stu-id="254f1-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="254f1-266">La première étape consiste à créer un <xref:System.Net.Http.HttpClient> objet dans la `SumPageSizesAsync` méthode.</span><span class="sxs-lookup"><span data-stu-id="254f1-266">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="254f1-267">Ajoutez la déclaration suivante au début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="254f1-267">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="254f1-268">Dans `SumPageSizesAsync,`, remplacez l'appel à votre méthode `GetURLContentsAsync` par un appel à la méthode `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="254f1-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="254f1-269">Supprimez ou commentez la méthode `GetURLContentsAsync` que vous avez écrite.</span><span class="sxs-lookup"><span data-stu-id="254f1-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="254f1-270">Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="254f1-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="254f1-271">Le comportement de cette version du projet doit correspondre à celui décrit par la procédure « Pour tester la solution asynchrone » mais avec encore moins d'efforts de votre part.</span><span class="sxs-lookup"><span data-stu-id="254f1-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="254f1-272">Exemple</span><span class="sxs-lookup"><span data-stu-id="254f1-272">Example</span></span>

<span data-ttu-id="254f1-273">Voici l’exemple complet de la solution asynchrone convertie qui utilise la `GetURLContentsAsync` méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="254f1-273">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="254f1-274">Remarquez qu’il ressemble fortement à la solution synchrone d’origine.</span><span class="sxs-lookup"><span data-stu-id="254f1-274">Notice that it strongly resembles the original, synchronous solution.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

<span data-ttu-id="254f1-275">Le code suivant inclut l'exemple complet de la solution qui utilise la méthode `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="254f1-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a><span data-ttu-id="254f1-276">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="254f1-276">See also</span></span>

- [<span data-ttu-id="254f1-277">Exemple Async : Accès à la procédure web (C# et Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="254f1-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="254f1-278">Await (opérateur)</span><span class="sxs-lookup"><span data-stu-id="254f1-278">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
- [<span data-ttu-id="254f1-279">Asynchrone</span><span class="sxs-lookup"><span data-stu-id="254f1-279">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="254f1-280">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="254f1-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="254f1-281">Types de retour Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="254f1-281">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="254f1-282">Programmation asynchrone basée sur les tâches (TAP)</span><span class="sxs-lookup"><span data-stu-id="254f1-282">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="254f1-283">Guide pratique : étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="254f1-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="254f1-284">Guide pratique : effectuer plusieurs requêtes web en parallèle avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="254f1-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
