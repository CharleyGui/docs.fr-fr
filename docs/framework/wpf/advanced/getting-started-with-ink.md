---
title: Créer InkCanvas dans Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: b8087d6db04f7024b9ee48f28002bee04045a14b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737886"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="952a0-102">Prise en main de l’encre dans WPF</span><span class="sxs-lookup"><span data-stu-id="952a0-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="952a0-103">Windows Presentation Foundation (WPF) dispose d’une fonctionnalité d’encre qui facilite l’incorporation de l’encre numérique dans votre application.</span><span class="sxs-lookup"><span data-stu-id="952a0-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="952a0-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="952a0-104">Prerequisites</span></span>

<span data-ttu-id="952a0-105">Pour utiliser les exemples suivants, commencez par installer [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="952a0-105">To use the following examples, first install [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="952a0-106">Il permet également de savoir comment écrire des applications WPF de base.</span><span class="sxs-lookup"><span data-stu-id="952a0-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="952a0-107">Pour obtenir de l’aide sur la prise en main de WPF, consultez [procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="952a0-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="952a0-108">Démarrage rapide de la</span><span class="sxs-lookup"><span data-stu-id="952a0-108">Quick Start</span></span>

<span data-ttu-id="952a0-109">Cette section vous aide à écrire une application WPF simple qui collecte de l’encre.</span><span class="sxs-lookup"><span data-stu-id="952a0-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="952a0-110">Vous avez de l’encre ?</span><span class="sxs-lookup"><span data-stu-id="952a0-110">Got Ink?</span></span>

<span data-ttu-id="952a0-111">Pour créer une application WPF qui prend en charge l’encre :</span><span class="sxs-lookup"><span data-stu-id="952a0-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="952a0-112">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="952a0-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="952a0-113">Créez une **application WPF**.</span><span class="sxs-lookup"><span data-stu-id="952a0-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="952a0-114">Dans la boîte de dialogue **nouveau projet** , développez la catégorie **installé** > **Visual C#**  ou **Visual Basic** > **Bureau Windows** .</span><span class="sxs-lookup"><span data-stu-id="952a0-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="952a0-115">Ensuite, sélectionnez le modèle application **WPF (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="952a0-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="952a0-116">Entrez un nom, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="952a0-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="952a0-117">Visual Studio crée le projet, et *MainWindow. Xaml* s’ouvre dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="952a0-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="952a0-118">Tapez `<InkCanvas/>` entre les balises `<Grid>`.</span><span class="sxs-lookup"><span data-stu-id="952a0-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![Concepteur XAML avec balise InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="952a0-120">Appuyez sur **F5** pour lancer votre application dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="952a0-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="952a0-121">À l’aide d’un stylet ou d’une souris, écrivez **Hello World** dans la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="952a0-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="952a0-122">Vous avez écrit l’équivalent de l’encre d’une application « Hello World » avec seulement 12 séquences de touches !</span><span class="sxs-lookup"><span data-stu-id="952a0-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="952a0-123">Agrémentez votre application</span><span class="sxs-lookup"><span data-stu-id="952a0-123">Spice Up Your App</span></span>

<span data-ttu-id="952a0-124">Nous allons tirer parti de certaines fonctionnalités de WPF.</span><span class="sxs-lookup"><span data-stu-id="952a0-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="952a0-125">Remplacez tout ce qui se trouve entre les balises d’ouverture et de fermeture \<fenêtre > par le balisage suivant :</span><span class="sxs-lookup"><span data-stu-id="952a0-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

<span data-ttu-id="952a0-126">Ce code XAML crée un arrière-plan de pinceau dégradé sur votre surface d’encrage.</span><span class="sxs-lookup"><span data-stu-id="952a0-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![Couleurs de dégradé sur la surface d’entrée manuscrite dans l’application WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="952a0-128">Ajouter du code derrière le XAML</span><span class="sxs-lookup"><span data-stu-id="952a0-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="952a0-129">Bien que XAML facilite la conception de l’interface utilisateur, toute application réelle doit ajouter du code pour gérer les événements.</span><span class="sxs-lookup"><span data-stu-id="952a0-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="952a0-130">Voici un exemple simple qui effectue un zoom avant sur l’encre en réponse à un clic droit à partir d’une souris.</span><span class="sxs-lookup"><span data-stu-id="952a0-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="952a0-131">Définissez le gestionnaire de `MouseRightButtonUp` dans votre code XAML :</span><span class="sxs-lookup"><span data-stu-id="952a0-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="952a0-132">Dans **Explorateur de solutions**, développez MainWindow. xaml et ouvrez le fichier code-behind (MainWindow.Xaml.cs ou MainWindow. Xaml. vb).</span><span class="sxs-lookup"><span data-stu-id="952a0-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="952a0-133">Ajoutez le code de gestionnaire d’événements suivant :</span><span class="sxs-lookup"><span data-stu-id="952a0-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="952a0-134">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="952a0-134">Run the application.</span></span> <span data-ttu-id="952a0-135">Ajoutez de l’encre, puis cliquez avec le bouton droit avec la souris ou effectuez une pression et une pression équivalente avec un stylet.</span><span class="sxs-lookup"><span data-stu-id="952a0-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="952a0-136">L’affichage effectue un zoom avant chaque fois que vous cliquez avec le bouton droit de la souris.</span><span class="sxs-lookup"><span data-stu-id="952a0-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="952a0-137">Utiliser le code de procédure au lieu de XAML</span><span class="sxs-lookup"><span data-stu-id="952a0-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="952a0-138">Vous pouvez accéder à toutes les fonctionnalités WPF à partir du code procédural.</span><span class="sxs-lookup"><span data-stu-id="952a0-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="952a0-139">Suivez ces étapes pour créer une application « Hello Ink World » pour WPF qui n’utilise pas du tout XAML.</span><span class="sxs-lookup"><span data-stu-id="952a0-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="952a0-140">Créez un projet d’application console dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="952a0-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="952a0-141">Dans la boîte de dialogue **nouveau projet** , développez la catégorie **installé** > **Visual C#**  ou **Visual Basic** > **Bureau Windows** .</span><span class="sxs-lookup"><span data-stu-id="952a0-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="952a0-142">Ensuite, sélectionnez le modèle application **console (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="952a0-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="952a0-143">Entrez un nom, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="952a0-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="952a0-144">Collez le code suivant dans le fichier Program.cs ou Program. vb :</span><span class="sxs-lookup"><span data-stu-id="952a0-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="952a0-145">Ajoutez des références aux assemblys PresentationCore, PresentationFramework et WindowsBase en cliquant avec le bouton droit sur **références** dans **Explorateur de solutions** et en choisissant **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="952a0-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![Gestionnaire de références avec PresentationCore et PresentationFramework](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. <span data-ttu-id="952a0-147">Générez l’application en appuyant sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="952a0-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="952a0-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="952a0-148">See also</span></span>

- [<span data-ttu-id="952a0-149">Encre numérique</span><span class="sxs-lookup"><span data-stu-id="952a0-149">Digital Ink</span></span>](digital-ink.md)
- [<span data-ttu-id="952a0-150">Collecte d'encre</span><span class="sxs-lookup"><span data-stu-id="952a0-150">Collecting Ink</span></span>](collecting-ink.md)
- [<span data-ttu-id="952a0-151">Reconnaissance d'écriture manuscrite</span><span class="sxs-lookup"><span data-stu-id="952a0-151">Handwriting Recognition</span></span>](handwriting-recognition.md)
- [<span data-ttu-id="952a0-152">Stockage de l’encre</span><span class="sxs-lookup"><span data-stu-id="952a0-152">Storing Ink</span></span>](storing-ink.md)
