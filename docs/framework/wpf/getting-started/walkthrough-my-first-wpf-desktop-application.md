---
title: Créer une application WPF dans Visual Studio
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: 4919424339df1f8d2c68465bd9f9af42f344fe37
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254072"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Procédure pas à pas : Ma première application de bureau WPF

Cet article explique comment développer une application de bureau Windows Presentation Foundation (WPF) qui comprend les éléments communs à la plupart des applications WPF : Balisage (XAML) Extensible Application Markup Language, code-behind, définitions d’application, contrôles, disposition, liaison de données et styles. Pour développer l’application, vous allez utiliser Visual Studio. 

Cette procédure pas à pas comprend les étapes suivantes :

- Utilisez XAML pour concevoir l’apparence de l’interface utilisateur de l’application.

- Écrivez du code pour générer le comportement de l’application.

- Créez une définition d’application pour gérer l’application.

- Ajoutez des contrôles et créez la disposition pour composer l’interface utilisateur de l’application.

- Créer des styles pour une apparence cohérente dans l’interface utilisateur de l’application.

- Liez l’interface utilisateur aux données, à la fois pour remplir l’interface utilisateur à partir des données et pour maintenir la synchronisation des données et de l’interface utilisateur.

À la fin de la procédure pas à pas, vous aurez créé une application Windows autonome qui permet aux utilisateurs d’afficher les notes de frais pour les personnes sélectionnées. L’application est composée de plusieurs pages WPF qui sont hébergées dans une fenêtre de style navigateur.

> [!TIP]
> L’exemple de code utilisé pour générer cette procédure pas à pas est disponible pour les C# Visual Basic et au niveau de l’exemple de code de l' [application WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Vous pouvez basculer le langage de code de l’exemple de C# code entre et Visual Basic à l’aide de la **\< />** liste déroulante située dans la partie supérieure droite de cet article.

## <a name="prerequisites"></a>Prérequis

- Visual Studio 2017 ou version ultérieure (cet article utilise Visual Studio 2019)

   Pour plus d’informations sur l’installation de la dernière version de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Créer le projet d’application

La première étape consiste à créer l’infrastructure d’application, qui comprend une définition d’application, deux pages et une image.

1. Créez un projet d’application WPF dans Visual Basic ou un C# visuel **`ExpenseIt`** nommé :

   1. Ouvrez Visual Studio et sélectionnez **créer un nouveau projet** dans le menu **Démarrer** .

      La boîte de dialogue **créer un nouveau projet** s’ouvre.

   2. Dans la liste déroulante langue **C#** , sélectionnez ou **Visual Basic**.
      
   3. Sélectionnez le modèle **application WPF (.NET Framework)** , puis sélectionnez **suivant**. 
     
      ![Boîte de dialogue créer un nouveau projet](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      La boîte de dialogue **configurer votre nouveau projet** s’ouvre.

   4. Entrez le nom **`ExpenseIt`** du projet, puis sélectionnez **créer**.

      ![Boîte de dialogue Configurer un nouveau projet](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio crée le projet et ouvre le concepteur pour la fenêtre d’application par défaut nommée **MainWindow. Xaml**.

2. Ouvrez *application. Xaml* (Visual Basic) ou *app. Xaml* (C#).

    Ce fichier XAML définit une application WPF et toutes les ressources d’application. Vous utilisez également ce fichier pour spécifier l’interface utilisateur, dans ce cas, *MainWindow. Xaml*, qui s’affiche automatiquement au démarrage de l’application.

    Votre code XAML doit ressembler à ce qui suit dans Visual Basic :

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Et de la façon suivante C#dans :

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Ouvrez *MainWindow. Xaml*.

    Ce fichier XAML est la fenêtre principale de votre application et affiche le contenu créé dans les pages. La <xref:System.Windows.Window> classe définit les propriétés d’une fenêtre, telles que son titre, sa taille ou son icône, et gère les événements, tels que la fermeture ou le masquage.

4. Remplacez l' <xref:System.Windows.Window> élément par un <xref:System.Windows.Navigation.NavigationWindow>, comme indiqué dans le code XAML suivant :

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Cette application accède à un contenu différent en fonction de l’entrée de l’utilisateur. C’est la raison pour <xref:System.Windows.Window> laquelle le principal doit être remplacé <xref:System.Windows.Navigation.NavigationWindow>par un. <xref:System.Windows.Navigation.NavigationWindow>hérite de toutes les propriétés <xref:System.Windows.Window>de. L' <xref:System.Windows.Navigation.NavigationWindow> élément dans le fichier XAML crée une instance de la <xref:System.Windows.Navigation.NavigationWindow> classe. Pour plus d’informations, consultez [vue d’ensemble](../app-development/navigation-overview.md)de la navigation.

5. Supprimez <xref:System.Windows.Controls.Grid> les éléments entre les <xref:System.Windows.Navigation.NavigationWindow> balises.

6. Modifiez les propriétés suivantes dans le code XAML pour l' <xref:System.Windows.Navigation.NavigationWindow> élément :

    - Affectez <xref:System.Windows.Window.Title%2A> à la propriété`ExpenseIt`la valeur "".

    - Affectez <xref:System.Windows.FrameworkElement.Height%2A> à la propriété la valeur 350 pixels.

    - Affectez <xref:System.Windows.FrameworkElement.Width%2A> à la propriété la valeur 500 pixels.

    Votre code XAML doit ressembler à ce qui suit pour Visual Basic :

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Et comme suit pour C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Ouvrez *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs*.

    Ce fichier est un fichier code-behind qui contient le code permettant de gérer les événements déclarés dans *MainWindow. Xaml*. Ce fichier contient une classe partielle pour la fenêtre définie en XAML.

8. Si vous utilisez C#, modifiez la classe `MainWindow` pour qu’elle dérive de. <xref:System.Windows.Navigation.NavigationWindow> (Dans Visual Basic, cela se produit automatiquement lorsque vous modifiez la fenêtre en XAML.) Votre C# code doit maintenant ressembler à ceci :

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Ajouter des fichiers à l’application

Dans cette section, vous allez ajouter deux pages et une image à l’application.

1. Ajoutez une nouvelle page au projet et nommez- *`ExpenseItHome.xaml`* la :

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit **`ExpenseIt`** sur le nœud du projet et choisissez **Ajouter** > une**page**.

   1. Dans la boîte de dialogue **Ajouter un nouvel élément** , le modèle **page (WPF)** est déjà sélectionné. Entrez le nom **`ExpenseItHome`** , puis sélectionnez **Ajouter**.

    Cette page est la première page qui s’affiche lorsque l’application est lancée. Elle affiche une liste des personnes à sélectionner, pour afficher une note de frais pour.

1. Ouvrez *`ExpenseItHome.xaml`* .

1. Affectez <xref:System.Windows.Controls.Page.Title%2A> à la`ExpenseIt - Home`valeur «».

1. Définissez sur 350 pixels `DesignWidth` et sur 500 pixels. `DesignHeight`

    Le code XAML se présente désormais comme suit pour Visual Basic :

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Et comme suit pour C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Ouvrez *MainWindow. Xaml*.

1. Ajoutez une <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriété à l' <xref:System.Windows.Navigation.NavigationWindow> élément et affectez-lui`ExpenseItHome.xaml`la valeur "".

    Cela définit *`ExpenseItHome.xaml`* la première page ouverte au démarrage de l’application. 

    Exemple de code XAML dans Visual Basic :

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Et en C# :

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Vous pouvez également définir la propriété **source** dans la catégorie **divers** de la fenêtre **Propriétés** .
   >
   > ![Propriété source dans Fenêtre Propriétés](./media/properties-source.png)

1. Ajoutez une autre nouvelle page WPF au projet et nommez-la *ExpenseReportPage. Xaml*::

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit **`ExpenseIt`** sur le nœud du projet et choisissez **Ajouter** > une**page**.

   1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle **page (WPF)** . Entrez le nom **ExpenseReportPage**, puis sélectionnez **Ajouter**.

    Cette page affiche la note de frais de la personne sélectionnée sur la **`ExpenseItHome`** page.

1. Ouvrez *ExpenseReportPage.xaml*.

1. Affectez <xref:System.Windows.Controls.Page.Title%2A> à la`ExpenseIt - View Expense`valeur «».

1. Définissez sur 350 pixels `DesignWidth` et sur 500 pixels. `DesignHeight` 

    *ExpenseReportPage. Xaml* ressemble maintenant à ce qui suit dans Visual Basic :

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Et de la façon suivante C#dans :

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Ouvrez *ExpenseItHome. Xaml. vb* et *ExpenseReportPage. Xaml. vb*, ou *ExpenseItHome.Xaml.cs* et *ExpenseReportPage.Xaml.cs*.

    Lorsque vous créez un nouveau fichier d’échange, Visual Studio crée automatiquement son fichier *code-behind* . Ces fichiers code-behind gèrent la logique pour répondre à une saisie de l’utilisateur.

    Votre code doit ressembler à ce **`ExpenseItHome`** qui suit pour :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    Et comme suit pour **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Ajoutez une image nommée *Watermark. png* au projet. Vous pouvez créer votre propre image, copier le fichier à partir de l’exemple de code ou l’afficher [ici](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).

    1. Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter** > un**élément existant**, ou appuyez sur **MAJ**+**ALT**+**A**.

    2. Dans la boîte de dialogue **Ajouter un élément existant** , définissez le filtre de fichiers sur **tous les fichiers** ou **fichiers image**, accédez au fichier image que vous souhaitez utiliser, puis sélectionnez **Ajouter**.

## <a name="build-and-run-the-application"></a>Générez et exécutez l'application.

1. Pour générer et exécuter l’application, appuyez sur **F5** ou sélectionnez **Démarrer le débogage** dans le menu **Déboguer** .

    L’illustration suivante montre l’application avec les <xref:System.Windows.Navigation.NavigationWindow> boutons :

    ![Application après l’avoir générée et exécutée.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Fermez l’application pour revenir à Visual Studio.

## <a name="create-the-layout"></a>Créer la disposition

La disposition fournit un moyen ordonné de placer des éléments d’interface utilisateur, et gère également la taille et la position de ces éléments quand une interface utilisateur est redimensionnée. En règle générale, vous allez créer une disposition avec l’un des contrôles de disposition suivants :

- <xref:System.Windows.Controls.Canvas>-Définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants à l’aide de coordonnées relatives à la zone de canevas.
- <xref:System.Windows.Controls.DockPanel>: Définit une zone dans laquelle vous pouvez réorganiser les éléments enfants horizontalement ou verticalement, l’un par rapport à l’autre.
- <xref:System.Windows.Controls.Grid>-Définit une zone de grille flexible composée de colonnes et de lignes.
- <xref:System.Windows.Controls.StackPanel>-Réorganise les éléments enfants en une seule ligne qui peut être orientée horizontalement ou verticalement.
- <xref:System.Windows.Controls.VirtualizingStackPanel>-Réorganise et virtualise le contenu sur une seule ligne orientée horizontalement ou verticalement.
- <xref:System.Windows.Controls.WrapPanel>-Positionne les éléments enfants dans un ordre séquentiel de gauche à droite, en fractionnant le contenu à la ligne suivante au bord de la zone conteneur. Le classement suivant se produit de manière séquentielle de haut en bas ou de droite à gauche, selon la valeur de la propriété orientation.

Chacun de ces contrôles de disposition prend en charge un type particulier de disposition pour ses éléments enfants. `ExpenseIt`les pages peuvent être redimensionnées et chaque page possède des éléments disposés horizontalement et verticalement en même temps que d’autres éléments. Dans cet exemple, <xref:System.Windows.Controls.Grid> est utilisé comme élément de disposition pour l’application.

> [!TIP]
> Pour plus d’informations <xref:System.Windows.Controls.Panel> sur les éléments, consultez [vue d’ensemble des panneaux](../controls/panels-overview.md). Pour plus d’informations sur la disposition, consultez [disposition](../advanced/layout.md).

Dans cette section, vous créez une table à une seule colonne avec trois lignes et une marge de 10 pixels en ajoutant des définitions de colonne et <xref:System.Windows.Controls.Grid> de *`ExpenseItHome.xaml`* ligne au dans.

1. Dans *`ExpenseItHome.xaml`* , affectez <xref:System.Windows.FrameworkElement.Margin%2A> à la propriété <xref:System.Windows.Controls.Grid> de l’élément la valeur « 10, 0, 10, 10 », qui correspond aux marges gauche, haut, droit et bas :

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Vous pouvez également définir les valeurs de **marge** dans la fenêtre **Propriétés** , sous la catégorie **disposition** :
   >
   > ![Valeurs de marge dans Fenêtre Propriétés](./media/properties-margin.png)

2. Ajoutez le code XAML suivant entre <xref:System.Windows.Controls.Grid> les balises pour créer les définitions de ligne et de colonne :

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    La <xref:System.Windows.Controls.RowDefinition.Height%2A> valeur de deux lignes est définie <xref:System.Windows.GridLength.Auto%2A>sur, ce qui signifie que les lignes sont dimensionnées en fonction du contenu des lignes. La valeur <xref:System.Windows.Controls.RowDefinition.Height%2A> par <xref:System.Windows.GridUnitType.Star> défaut est le dimensionnement, ce qui signifie que la hauteur de ligne est une proportion pondérée de l’espace disponible. Par exemple, si deux lignes ont chacune <xref:System.Windows.Controls.RowDefinition.Height%2A> une de « * », elles ont chacune une hauteur qui correspond à la moitié de l’espace disponible.

    Votre <xref:System.Windows.Controls.Grid> doit maintenant contenir le code XAML suivant :

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Ajouter des contrôles

Dans cette section, vous allez mettre à jour l’interface utilisateur de la page d’origine pour afficher une liste de personnes, dans laquelle vous sélectionnez une personne pour afficher son rapport de frais. Les contrôles sont des objets d’interface utilisateur qui permettent aux utilisateurs d’interagir avec votre application. Pour plus d’informations, consultez [Contrôles](../controls/index.md).

Pour créer cette interface utilisateur, vous allez ajouter les éléments suivants *`ExpenseItHome.xaml`* à :

- A <xref:System.Windows.Controls.ListBox> (pour la liste des personnes).
- <xref:System.Windows.Controls.Label> (Pour l’en-tête de liste).
- A <xref:System.Windows.Controls.Button> (pour afficher la note de frais de la personne sélectionnée dans la liste).

Chaque contrôle est placé dans une ligne du <xref:System.Windows.Controls.Grid> en définissant la <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriété jointe. Pour plus d’informations sur les propriétés jointes, consultez [vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).

1. Dans *`ExpenseItHome.xaml`* , ajoutez le code XAML suivant entre les <xref:System.Windows.Controls.Grid> balises :

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Vous pouvez également créer les contrôles en les faisant glisser de la fenêtre **boîte à outils** vers la fenêtre de conception, puis en définissant leurs propriétés dans la fenêtre **Propriétés** .

2. Générez et exécutez l’application.

    L’illustration suivante montre les contrôles que vous avez créés :

![Exemple d’instantané ExpenseIt l’affichage d’une liste de noms](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Ajouter une image et un titre

Dans cette section, vous allez mettre à jour l’interface utilisateur de la page d’hébergement avec une image et un titre de page.

1. Dans *`ExpenseItHome.xaml`* , ajoutez une autre colonne <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> au avec un 230 <xref:System.Windows.Controls.ColumnDefinition.Width%2A> pixels au fixe :

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Ajoutez une autre ligne au <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, pour un total de quatre lignes :

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Déplacez les contrôles vers la deuxième colonne en affectant <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> à la propriété la valeur 1 dans chacun des trois contrôles (Border, ListBox et Button).

4. Déplacez chaque contrôle d’une ligne vers le haut en <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> incrémentant sa valeur de 1 pour chacun des trois contrôles (Border, ListBox et Button) et pour l’élément Border.

   Le code XAML des trois contrôles se présente désormais comme suit :

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Définissez la <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> propriété sur le fichier image *Watermark. png* , en ajoutant le code XAML suivant entre les `<Grid>` balises et `</Grid>` :

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Avant l' <xref:System.Windows.Controls.Border> élément, ajoutez un <xref:System.Windows.Controls.Label> avec le contenu « afficher la note de frais ». Cette étiquette est le titre de la page.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Générez et exécutez l’application.

L’illustration suivante montre les résultats de ce que vous venez d’ajouter :

![Capture d’écran de l’exemple ExpenseIt le nouvel arrière-plan d’image et le titre de la page](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Ajouter du code pour gérer les événements

1. Dans *`ExpenseItHome.xaml`* , ajoutez un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gestionnaire d’événements à <xref:System.Windows.Controls.Button> l’élément. Pour plus d'informations, voir [Procédure : Créez un gestionnaire](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))d’événements simple.

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Ouvrez *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .

3. Ajoutez le code suivant à la `ExpenseItHome` classe pour ajouter un gestionnaire d’événements de clic sur un bouton. Le gestionnaire d’événements ouvre la page **ExpenseReportPage** .

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Créer l’interface utilisateur pour ExpenseReportPage

*ExpenseReportPage. Xaml* affiche la note de frais pour la personne sélectionnée sur la **`ExpenseItHome`** page. Dans cette section, vous allez créer l’interface utilisateur pour **ExpenseReportPage**. Vous ajouterez également des couleurs d’arrière-plan et de remplissage aux différents éléments de l’interface utilisateur.

1. Ouvrez *ExpenseReportPage.xaml*.

2. Ajoutez le code XAML suivant entre <xref:System.Windows.Controls.Grid> les balises :

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Cette interface utilisateur est similaire *`ExpenseItHome.xaml`* à, sauf que les données de rapport s' <xref:System.Windows.Controls.DataGrid>affichent dans un.

3. Générez et exécutez l’application.

4. Sélectionnez le bouton **Afficher** .

    La page de note de frais s’affiche. Notez également que le bouton de navigation précédent est activé.

L’illustration suivante montre les éléments d’interface utilisateur ajoutés à *ExpenseReportPage. Xaml*.

![Exemple de capture d’écran expenseux montrant l’interface utilisateur qui vient d’être créée pour ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Contrôles de style

L’apparence de différents éléments est souvent la même pour tous les éléments du même type dans une interface utilisateur. L’interface utilisateur utilise des [styles](../controls/styling-and-templating.md) pour rendre les apparences réutilisables sur plusieurs éléments. La réutilisabilité des styles permet de simplifier la création et la gestion XAML. Cette section remplace par des styles les attributs d’élément qui ont été définis lors des étapes précédentes.

1. Ouvrez *application. Xaml* ou *app. Xaml*.

2. Ajoutez le code XAML suivant entre <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> les balises :

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Ce code XAML ajoute les styles suivants :

    - `headerTextStyle`: Pour mettre en forme le <xref:System.Windows.Controls.Label>titre de la page.

    - `labelStyle`: Pour mettre en <xref:System.Windows.Controls.Label> forme les contrôles.

    - `columnHeaderStyle`: Pour mettre en <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>forme le.

    - `listHeaderStyle`: Pour mettre en forme les <xref:System.Windows.Controls.Border> contrôles d’en-tête de liste.

    - `listHeaderTextStyle`: Pour mettre en forme l' <xref:System.Windows.Controls.Label>en-tête de liste.

    - `buttonStyle`: Pour mettre en <xref:System.Windows.Controls.Button> `ExpenseItHome.xaml`forme le.

    Notez que les styles sont des ressources et des enfants <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> de l’élément Property. À cet emplacement, les styles sont appliqués à tous les éléments d’une application. Pour obtenir un exemple d’utilisation de ressources dans une application .NET, consultez [utiliser des ressources d’application](../advanced/how-to-use-application-resources.md).

3. Dans *`ExpenseItHome.xaml`* , remplacez tout ce qui <xref:System.Windows.Controls.Grid> se trouve entre les éléments par le code XAML suivant :

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Les propriétés qui définissent l’apparence de chaque contrôle, comme <xref:System.Windows.VerticalAlignment> et <xref:System.Windows.Media.FontFamily> , sont supprimées et remplacées lors de l’application de styles. Par exemple, l `headerTextStyle` 'est appliqué à l' « afficher la <xref:System.Windows.Controls.Label>note de frais ».

4. Ouvrez *ExpenseReportPage.xaml*.

5. Remplacez tout ce qui <xref:System.Windows.Controls.Grid> se trouve entre les éléments par le code XAML suivant :

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Ce code XAML ajoute des styles <xref:System.Windows.Controls.Label> aux <xref:System.Windows.Controls.Border> éléments et.

6. Générez et exécutez l’application. L’apparence de la fenêtre est la même que précédemment.

    ![Exemple de capture d’écran ExpenseIt avec la même apparence que dans la dernière section.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Fermez l’application pour revenir à Visual Studio.

## <a name="bind-data-to-a-control"></a>Lier des données à un contrôle

Dans cette section, vous allez créer les données XML liées à différents contrôles.

1. Dans *`ExpenseItHome.xaml`* , après l’élément <xref:System.Windows.Controls.Grid> d’ouverture, ajoutez le code XAML suivant pour <xref:System.Windows.Data.XmlDataProvider> créer un qui contient les données pour chaque personne :

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Les données sont créées en tant <xref:System.Windows.Controls.Grid> que ressource. Normalement, ces données sont chargées en tant que fichier, mais pour des raisons de simplicité, les données sont ajoutées Inline.

2. Dans l' `<Grid.Resources>` élément, ajoutez l’élément `<xref:System.Windows.DataTemplate>` suivant, qui définit comment afficher les données dans le <xref:System.Windows.Controls.ListBox>, après l' `<XmlDataProvider>` élément :

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Pour plus d’informations sur les modèles de données, consultez [vue d’ensemble](../data/data-templating-overview.md)des modèles de données.

3. Remplacez le existant <xref:System.Windows.Controls.ListBox> par le code XAML suivant :

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Ce code XAML lie la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété <xref:System.Windows.Controls.ListBox> de à la source de données et applique <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>le modèle de données en tant que.

## <a name="connect-data-to-controls"></a>Connecter des données à des contrôles

Ensuite, vous allez ajouter du code pour récupérer le nom qui est sélectionné dans **`ExpenseItHome`** la page et le passer au constructeur de **ExpenseReportPage**. **ExpenseReportPage** définit son contexte de données avec l’élément passé, à savoir à quoi les contrôles définis dans *ExpenseReportPage. Xaml* se lient.

1. Ouvrez *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.

2. Ajoutez un constructeur qui prend un objet de façon à pouvoir transmettre les données de note de frais de la personne sélectionnée.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Ouvrez *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .

4. Modifiez le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gestionnaire d’événements pour appeler le nouveau constructeur en passant les données de la note de frais de la personne sélectionnée.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Données de style avec des modèles de données

Dans cette section, vous allez mettre à jour l’interface utilisateur pour chaque élément des listes liées aux données à l’aide de modèles de données.

1. Ouvrez *ExpenseReportPage.xaml*.

2. Liez le contenu des éléments « Name » et « Department » <xref:System.Windows.Controls.Label> à la propriété de source de données appropriée. Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Après l’élément <xref:System.Windows.Controls.Grid> d’ouverture, ajoutez les modèles de données suivants, qui définissent comment afficher les données de note de frais :

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Remplacez les <xref:System.Windows.Controls.DataGridTextColumn> éléments par <xref:System.Windows.Controls.DataGridTemplateColumn> sous l' <xref:System.Windows.Controls.DataGrid> élément et appliquez-leur les modèles.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Générez et exécutez l’application.

6. Sélectionnez une personne, puis cliquez sur le bouton **Afficher** .

L’illustration suivante montre les deux pages de `ExpenseIt` l’application avec les contrôles, la disposition, les styles, la liaison de données et les modèles de données appliqués :

![Les deux pages de l’application indiquent la liste des noms et une note de frais.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Cet exemple illustre une fonctionnalité spécifique de WPF et ne suit pas toutes les méthodes recommandées pour la sécurité, la localisation et l’accessibilité. Pour une couverture complète de WPF et des meilleures pratiques en matière de développement d’applications .NET, consultez les rubriques suivantes :
>
> - [Accessibilité](../../ui-automation/accessibility-best-practices.md)
>
> - [Sécurité](../security-wpf.md)
>
> - [Globalisation et localisation pour WPF](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [Performances WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Étapes suivantes

Dans cette procédure pas à pas, vous avez appris un certain nombre de techniques pour la création d’une interface utilisateur à l’aide d’Windows Presentation Foundation (WPF). Vous devez maintenant avoir une compréhension de base des blocs de construction d’une application .NET liée aux données. Pour plus d’informations sur les modèles d’architecture et de programmation WPF, consultez les rubriques suivantes :

- [Architecture WPF](../advanced/wpf-architecture.md)
- [Vue d’ensemble du langage XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Vue d’ensemble des propriétés de dépendance](../advanced/dependency-properties-overview.md)
- [Disposition](../advanced/layout.md)

Pour plus d’informations sur la création d’applications, consultez les rubriques suivantes :

- [Développement d’applications](../app-development/index.md)
- [Contrôles](../controls/index.md)
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Graphiques et multimédia](../graphics-multimedia/index.md)
- [Documents dans WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des panneaux](../controls/panels-overview.md)
- [Vue d’ensemble des modèles de données](../data/data-templating-overview.md)
- [Générer une application WPF](../app-development/building-a-wpf-application-wpf.md)
- [Styles et modèles](../controls/styles-and-templates.md)
