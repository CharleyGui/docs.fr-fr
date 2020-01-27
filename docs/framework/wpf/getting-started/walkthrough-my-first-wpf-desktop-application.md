---
title: Créer votre première application WPF dans Visual Studio 2019-.NET Framework
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 232605850c65aebd9aafdc9b76c90af42f2c901c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746978"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>Didacticiel : créer votre première application WPF dans Visual Studio 2019

Cet article vous montre comment développer une application de bureau Windows Presentation Foundation (WPF) qui comprend les éléments communs à la plupart des applications WPF : balisage XAML Extensible Application Markup Language (XAML), code-behind, définitions d’application, contrôles, disposition, liaison de données et styles. Pour développer l’application, vous allez utiliser Visual Studio. 

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
>
> - Créez un projet WPF.
> - Utilisez XAML pour concevoir l’apparence de l’interface utilisateur de l’application.
> - Écrivez du code pour générer le comportement de l’application.
> - Créez une définition d’application pour gérer l’application.
> - Ajoutez des contrôles et créez la disposition pour composer l’interface utilisateur de l’application.
> - Créer des styles pour une apparence cohérente dans l’interface utilisateur de l’application.
> - Liez l’interface utilisateur aux données, à la fois pour remplir l’interface utilisateur à partir des données et pour maintenir la synchronisation des données et de l’interface utilisateur.

À la fin du didacticiel, vous aurez créé une application Windows autonome qui permet aux utilisateurs d’afficher les notes de frais pour les personnes sélectionnées. L’application est composée de plusieurs pages WPF qui sont hébergées dans une fenêtre de style navigateur.

> [!TIP]
> L’exemple de code utilisé dans ce didacticiel est disponible pour les Visual Basic et C# dans le [didacticiel exemple de code d’application WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Vous pouvez basculer le langage de code de l’exemple de C# code entre et Visual Basic à l’aide du sélecteur de langue en haut de cette page.

## <a name="prerequisites"></a>Prerequisites

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement .net Desktop** installée.

   Pour plus d’informations sur l’installation de la dernière version de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Créer le projet d’application

La première étape consiste à créer l’infrastructure d’application, qui comprend une définition d’application, deux pages et une image.

1. Créez un projet d’application WPF dans Visual Basic ou un C# visuel nommé **`ExpenseIt`** :

   1. Ouvrez Visual Studio et sélectionnez **créer un nouveau projet** dans le menu **Démarrer** .

      La boîte de dialogue **créer un nouveau projet** s’ouvre.

   2. Dans la liste déroulante langue **C#** , sélectionnez ou **Visual Basic**.
      
   3. Sélectionnez le modèle **application WPF (.NET Framework)** , puis sélectionnez **suivant**. 
     
      ![Boîte de dialogue créer un nouveau projet](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      La boîte de dialogue **configurer votre nouveau projet** s’ouvre.

   4. Entrez le nom du projet **`ExpenseIt`** puis sélectionnez **créer**.

      ![Boîte de dialogue Configurer un nouveau projet](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio crée le projet et ouvre le concepteur pour la fenêtre d’application par défaut nommée **MainWindow. Xaml**.

2. Ouvrez *application. Xaml* (Visual Basic) ou *app. Xaml* (C#).

    Ce fichier XAML définit une application WPF et toutes les ressources d’application. Vous utilisez également ce fichier pour spécifier l’interface utilisateur, dans ce cas, *MainWindow. Xaml*, qui s’affiche automatiquement au démarrage de l’application.

    Votre code XAML doit ressembler à ce qui suit dans Visual Basic :

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Et de la façon suivante C#dans :

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Ouvrez *MainWindow. Xaml*.

    Ce fichier XAML est la fenêtre principale de votre application et affiche le contenu créé dans les pages. La classe <xref:System.Windows.Window> définit les propriétés d’une fenêtre, telles que son titre, sa taille ou son icône, et gère les événements, tels que la fermeture ou le masquage.

4. Remplacez l’élément <xref:System.Windows.Window> par un <xref:System.Windows.Navigation.NavigationWindow>, comme indiqué dans le code XAML suivant :

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Cette application accède à un contenu différent en fonction de l’entrée de l’utilisateur. C’est la raison pour laquelle le <xref:System.Windows.Window> principal doit être remplacé par un <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> hérite de toutes les propriétés de <xref:System.Windows.Window>. L’élément <xref:System.Windows.Navigation.NavigationWindow> dans le fichier XAML crée une instance de la classe <xref:System.Windows.Navigation.NavigationWindow>. Pour plus d’informations, consultez [vue d’ensemble](../app-development/navigation-overview.md)de la navigation.

5. Supprimez les éléments <xref:System.Windows.Controls.Grid> entre les balises <xref:System.Windows.Navigation.NavigationWindow>.

6. Modifiez les propriétés suivantes dans le code XAML pour l’élément <xref:System.Windows.Navigation.NavigationWindow> :

    - Affectez à la propriété <xref:System.Windows.Window.Title%2A> la valeur «`ExpenseIt`».

    - Affectez à la propriété <xref:System.Windows.FrameworkElement.Height%2A> la valeur 350 pixels.

    - Affectez à la propriété <xref:System.Windows.FrameworkElement.Width%2A> la valeur 500 pixels.

    Votre code XAML doit ressembler à ce qui suit pour Visual Basic :

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Et comme suit pour C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Ouvrez *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs*.

    Ce fichier est un fichier code-behind qui contient le code permettant de gérer les événements déclarés dans *MainWindow. Xaml*. Ce fichier contient une classe partielle pour la fenêtre définie en XAML.

8. Si vous utilisez C#, modifiez la classe `MainWindow` à dériver de <xref:System.Windows.Navigation.NavigationWindow>. (Dans Visual Basic, cela se produit automatiquement lorsque vous modifiez la fenêtre en XAML.) Votre C# code doit maintenant ressembler à ceci :

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Ajouter des fichiers à l’application

Dans cette section, vous allez ajouter deux pages et une image à l’application.

1. Ajoutez une nouvelle page au projet et nommez-la *`ExpenseItHome.xaml`* :

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet **`ExpenseIt`** et choisissez **Ajouter** une **page** > .

   1. Dans la boîte de dialogue **Ajouter un nouvel élément** , le modèle **page (WPF)** est déjà sélectionné. Entrez le nom **`ExpenseItHome`** , puis sélectionnez **Ajouter**.

    Cette page est la première page qui s’affiche lorsque l’application est lancée. Elle affiche une liste des personnes à sélectionner, pour afficher une note de frais pour.

1. Ouvrez *`ExpenseItHome.xaml`* .

1. Définissez le <xref:System.Windows.Controls.Page.Title%2A> sur «`ExpenseIt - Home`».

1. Définissez le `DesignHeight` sur 350 pixels et le `DesignWidth` sur 500 pixels.

    Le code XAML se présente désormais comme suit pour Visual Basic :

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Et comme suit pour C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Ouvrez *MainWindow. Xaml*.

1. Ajoutez une propriété <xref:System.Windows.Navigation.NavigationWindow.Source%2A> à l’élément <xref:System.Windows.Navigation.NavigationWindow> et affectez-lui la valeur «`ExpenseItHome.xaml`».

    Cela définit *`ExpenseItHome.xaml`* comme étant la première page ouverte au démarrage de l’application. 

    Exemple de code XAML dans Visual Basic :

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Et en c# :

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Vous pouvez également définir la propriété **source** dans la catégorie **divers** de la fenêtre **Propriétés** .
   >
   > ![Propriété source dans Fenêtre Propriétés](./media/properties-source.png)

1. Ajoutez une autre nouvelle page WPF au projet et nommez-la *ExpenseReportPage. Xaml*::

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet **`ExpenseIt`** et choisissez **Ajouter** une **page** > .

   1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle **page (WPF)** . Entrez le nom **ExpenseReportPage**, puis sélectionnez **Ajouter**.

    Cette page affiche la note de frais de la personne sélectionnée sur la page **`ExpenseItHome`** .

1. Ouvrez *ExpenseReportPage.xaml*.

1. Définissez le <xref:System.Windows.Controls.Page.Title%2A> sur «`ExpenseIt - View Expense`».

1. Définissez le `DesignHeight` sur 350 pixels et le `DesignWidth` sur 500 pixels. 

    *ExpenseReportPage. Xaml* ressemble maintenant à ce qui suit dans Visual Basic :

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Et de la façon suivante C#dans :

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Ouvrez *ExpenseItHome. Xaml. vb* et *ExpenseReportPage. Xaml. vb*, ou *ExpenseItHome.Xaml.cs* et *ExpenseReportPage.Xaml.cs*.

    Lorsque vous créez un nouveau fichier d’échange, Visual Studio crée automatiquement son fichier *code-behind* . Ces fichiers code-behind gèrent la logique pour répondre à une saisie de l’utilisateur.

    Votre code doit ressembler à ce qui suit pour **`ExpenseItHome`** :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    Et comme suit pour **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Ajoutez une image nommée *Watermark. png* au projet. Vous pouvez créer votre propre image, copier le fichier à partir de l’exemple de code ou l’extraire à partir du référentiel GitHub [Microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) .

    1. Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **ajouter** > **élément existant**, ou appuyez sur **MAJ**+**ALT**+**A**.

    2. Dans la boîte de dialogue **Ajouter un élément existant** , définissez le filtre de fichiers sur **tous les fichiers** ou **fichiers image**, accédez au fichier image que vous souhaitez utiliser, puis sélectionnez **Ajouter**.

## <a name="build-and-run-the-application"></a>Générez et exécutez l'application.

1. Pour générer et exécuter l’application, appuyez sur **F5** ou sélectionnez **Démarrer le débogage** dans le menu **Déboguer** .

    L’illustration suivante montre l’application avec les boutons <xref:System.Windows.Navigation.NavigationWindow> :

    ![Application après l’avoir générée et exécutée.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Fermez l’application pour revenir à Visual Studio.

## <a name="create-the-layout"></a>Créer la disposition

La disposition fournit un moyen ordonné de placer des éléments d’interface utilisateur, et gère également la taille et la position de ces éléments quand une interface utilisateur est redimensionnée. En règle générale, vous allez créer une disposition avec l’un des contrôles de disposition suivants :

- <xref:System.Windows.Controls.Canvas> : définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants à l’aide de coordonnées relatives à la zone de canevas.
- <xref:System.Windows.Controls.DockPanel> : définit une zone dans laquelle vous pouvez réorganiser les éléments enfants horizontalement ou verticalement, l’un par rapport à l’autre.
- <xref:System.Windows.Controls.Grid> : définit une zone de grille flexible composée de colonnes et de lignes.
- <xref:System.Windows.Controls.StackPanel> : réorganise les éléments enfants sur une seule ligne qui peut être orientée horizontalement ou verticalement.
- <xref:System.Windows.Controls.VirtualizingStackPanel> : réorganise et virtualise le contenu sur une seule ligne orientée horizontalement ou verticalement.
- <xref:System.Windows.Controls.WrapPanel> place les éléments enfants dans un ordre séquentiel de gauche à droite, en fractionnant le contenu à la ligne suivante au bord de la zone conteneur. Le classement suivant se produit de manière séquentielle de haut en bas ou de droite à gauche, selon la valeur de la propriété orientation.

Chacun de ces contrôles de disposition prend en charge un type particulier de disposition pour ses éléments enfants. `ExpenseIt` pages peuvent être redimensionnées et chaque page possède des éléments disposés horizontalement et verticalement avec d’autres éléments. Dans cet exemple, la <xref:System.Windows.Controls.Grid> est utilisée comme élément de disposition pour l’application.

> [!TIP]
> Pour plus d’informations sur les éléments de <xref:System.Windows.Controls.Panel>, consultez [vue d’ensemble des panneaux](../controls/panels-overview.md). Pour plus d’informations sur la disposition, consultez [disposition](../advanced/layout.md).

Dans cette section, vous créez une table à une seule colonne avec trois lignes et une marge de 10 pixels en ajoutant des définitions de colonne et de ligne au <xref:System.Windows.Controls.Grid> dans *`ExpenseItHome.xaml`* .

1. Dans *`ExpenseItHome.xaml`* , définissez la propriété <xref:System.Windows.FrameworkElement.Margin%2A> de l’élément <xref:System.Windows.Controls.Grid> sur « 10, 0, 10, 10 », ce qui correspond aux marges gauche, haut, droit et bas :

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Vous pouvez également définir les valeurs de **marge** dans la fenêtre **Propriétés** , sous la catégorie **disposition** :
   >
   > ![Valeurs de marge dans Fenêtre Propriétés](./media/properties-margin.png)

2. Ajoutez le code XAML suivant entre les balises <xref:System.Windows.Controls.Grid> pour créer les définitions de ligne et de colonne :

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    La <xref:System.Windows.Controls.RowDefinition.Height%2A> de deux lignes est définie sur <xref:System.Windows.GridLength.Auto%2A>, ce qui signifie que les lignes sont dimensionnées en fonction du contenu des lignes. La <xref:System.Windows.Controls.RowDefinition.Height%2A> par défaut est <xref:System.Windows.GridUnitType.Star> le dimensionnement, ce qui signifie que la hauteur de ligne est une proportion pondérée de l’espace disponible. Par exemple, si deux lignes ont une <xref:System.Windows.Controls.RowDefinition.Height%2A> de « * », elles ont chacune une hauteur qui correspond à la moitié de l’espace disponible.

    Votre <xref:System.Windows.Controls.Grid> doit maintenant contenir le code XAML suivant :

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Ajouter des contrôles

Dans cette section, vous allez mettre à jour l’interface utilisateur de la page d’origine pour afficher une liste de personnes, dans laquelle vous sélectionnez une personne pour afficher son rapport de frais. Les contrôles sont des objets d’interface utilisateur qui permettent aux utilisateurs d’interagir avec votre application. Pour plus d’informations, consultez [Contrôles](../controls/index.md).

Pour créer cette interface utilisateur, vous allez ajouter les éléments suivants à *`ExpenseItHome.xaml`* :

- <xref:System.Windows.Controls.ListBox> (pour la liste des personnes).
- <xref:System.Windows.Controls.Label> (pour l’en-tête de liste).
- Un <xref:System.Windows.Controls.Button> (Cliquer pour afficher la note de frais de la personne sélectionnée dans la liste).

Chaque contrôle est placé dans une ligne du <xref:System.Windows.Controls.Grid> en définissant la propriété jointe <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>. Pour plus d’informations sur les propriétés jointes, consultez [vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).

1. Dans *`ExpenseItHome.xaml`* , ajoutez le code XAML suivant entre les balises <xref:System.Windows.Controls.Grid> :

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Vous pouvez également créer les contrôles en les faisant glisser de la fenêtre **boîte à outils** vers la fenêtre de conception, puis en définissant leurs propriétés dans la fenêtre **Propriétés** .

2. Générez et exécutez l’application.

    L’illustration suivante montre les contrôles que vous avez créés :

![Exemple d’instantané ExpenseIt l’affichage d’une liste de noms](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Ajouter une image et un titre

Dans cette section, vous allez mettre à jour l’interface utilisateur de la page d’hébergement avec une image et un titre de page.

1. Dans *`ExpenseItHome.xaml`* , ajoutez une autre colonne au <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> avec un <xref:System.Windows.Controls.ColumnDefinition.Width%2A> fixe de 230 pixels :

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Ajoutez une autre ligne au <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, pour un total de quatre lignes :

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Déplacez les contrôles vers la deuxième colonne en affectant à la propriété <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> la valeur 1 dans chacun des trois contrôles (Border, ListBox et Button).

4. Déplacez chaque contrôle d’une ligne vers le haut en incrémentant sa valeur <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> de 1 pour chacun des trois contrôles (Border, ListBox et Button) et pour l’élément Border.

   Le code XAML des trois contrôles se présente désormais comme suit :

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Définissez la propriété <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> sur le fichier image *Watermark. png* , en ajoutant le code XAML suivant entre les balises `<Grid>` et `</Grid>` :

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Avant l’élément <xref:System.Windows.Controls.Border>, ajoutez un <xref:System.Windows.Controls.Label> avec le contenu « afficher la note de frais ». Cette étiquette est le titre de la page.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Générez et exécutez l’application.

L’illustration suivante montre les résultats de ce que vous venez d’ajouter :

![Capture d’écran de l’exemple ExpenseIt le nouvel arrière-plan d’image et le titre de la page](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Ajouter du code pour gérer les événements

1. Dans *`ExpenseItHome.xaml`* , ajoutez un gestionnaire d’événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> à l’élément <xref:System.Windows.Controls.Button>. Pour plus d’informations, consultez [Comment : créer un gestionnaire d’événements simple](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Ouvrez *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .

3. Ajoutez le code suivant à la classe `ExpenseItHome` pour ajouter un gestionnaire d’événements de clic sur un bouton. Le gestionnaire d’événements ouvre la page **ExpenseReportPage** .

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Créer l’interface utilisateur pour ExpenseReportPage

*ExpenseReportPage. Xaml* affiche la note de frais pour la personne sélectionnée sur la page **`ExpenseItHome`** . Dans cette section, vous allez créer l’interface utilisateur pour **ExpenseReportPage**. Vous ajouterez également des couleurs d’arrière-plan et de remplissage aux différents éléments de l’interface utilisateur.

1. Ouvrez *ExpenseReportPage.xaml*.

2. Ajoutez le code XAML suivant entre les balises <xref:System.Windows.Controls.Grid> :

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Cette interface utilisateur est similaire à *`ExpenseItHome.xaml`* , à l’exception des données de rapport qui s’affichent dans une <xref:System.Windows.Controls.DataGrid>.

3. Générez et exécutez l’application.

4. Sélectionnez le bouton **Afficher** .

    La page de note de frais s’affiche. Notez également que le bouton de navigation précédent est activé.

L’illustration suivante montre les éléments d’interface utilisateur ajoutés à *ExpenseReportPage. Xaml*.

![Exemple de capture d’écran expenseux montrant l’interface utilisateur qui vient d’être créée pour ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Contrôles de style

L’apparence de différents éléments est souvent la même pour tous les éléments du même type dans une interface utilisateur. L’interface utilisateur utilise des [styles](../controls/styling-and-templating.md) pour rendre les apparences réutilisables sur plusieurs éléments. La réutilisabilité des styles permet de simplifier la création et la gestion XAML. Cette section remplace par des styles les attributs d’élément qui ont été définis lors des étapes précédentes.

1. Ouvrez *application. Xaml* ou *app. Xaml*.

2. Ajoutez le code XAML suivant entre les balises <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> :

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Ce code XAML ajoute les styles suivants :

    - `headerTextStyle`: pour mettre en forme le titre de la page <xref:System.Windows.Controls.Label>.

    - `labelStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Label> .

    - `columnHeaderStyle`: pour mettre en forme <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Border> de l’en-tête de liste.

    - `listHeaderTextStyle`: pour mettre en forme l’en-tête de liste <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: pour mettre en forme le <xref:System.Windows.Controls.Button> sur `ExpenseItHome.xaml`.

    Notez que les styles sont des ressources et des enfants de l’élément de propriété <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. À cet emplacement, les styles sont appliqués à tous les éléments d’une application. Pour obtenir un exemple d’utilisation de ressources dans une application .NET, consultez [utiliser des ressources d’application](../advanced/how-to-use-application-resources.md).

3. Dans *`ExpenseItHome.xaml`* , remplacez tout ce qui se trouve entre les éléments <xref:System.Windows.Controls.Grid> par le code XAML suivant :

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Les propriétés qui définissent l’apparence de chaque contrôle, comme <xref:System.Windows.VerticalAlignment> et <xref:System.Windows.Media.FontFamily> , sont supprimées et remplacées lors de l’application de styles. Par exemple, le `headerTextStyle` est appliqué à la <xref:System.Windows.Controls.Label>« afficher le rapport des dépenses ».

4. Ouvrez *ExpenseReportPage.xaml*.

5. Remplacez tout ce qui se trouve entre les éléments <xref:System.Windows.Controls.Grid> par le code XAML suivant :

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Ce code XAML ajoute des styles aux éléments <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.Border>.

6. Générez et exécutez l’application. L’apparence de la fenêtre est la même que précédemment.

    ![Exemple de capture d’écran ExpenseIt avec la même apparence que dans la dernière section.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Fermez l’application pour revenir à Visual Studio.

## <a name="bind-data-to-a-control"></a>Lier des données à un contrôle

Dans cette section, vous allez créer les données XML liées à différents contrôles.

1. Dans *`ExpenseItHome.xaml`* , après l’élément <xref:System.Windows.Controls.Grid> ouvrant, ajoutez le code XAML suivant pour créer un <xref:System.Windows.Data.XmlDataProvider> qui contient les données pour chaque personne :

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Les données sont créées en tant que ressource <xref:System.Windows.Controls.Grid>. Normalement, ces données sont chargées en tant que fichier, mais pour des raisons de simplicité, les données sont ajoutées Inline.

2. Dans l’élément `<Grid.Resources>`, ajoutez l’élément `<xref:System.Windows.DataTemplate>` suivant, qui définit comment afficher les données dans le <xref:System.Windows.Controls.ListBox>, après l’élément `<XmlDataProvider>` :

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Pour plus d’informations sur les modèles de données, consultez [vue d’ensemble](../data/data-templating-overview.md)des modèles de données.

3. Remplacez le <xref:System.Windows.Controls.ListBox> existant par le code XAML suivant :

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Ce code XAML lie la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> du <xref:System.Windows.Controls.ListBox> à la source de données et applique le modèle de données en tant que <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Connecter des données à des contrôles

Ensuite, vous allez ajouter du code pour récupérer le nom sélectionné dans la page **`ExpenseItHome`** et le passer au constructeur de **ExpenseReportPage**. **ExpenseReportPage** définit son contexte de données avec l’élément passé, à savoir à quoi les contrôles définis dans *ExpenseReportPage. Xaml* se lient.

1. Ouvrez *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.

2. Ajoutez un constructeur qui prend un objet de façon à pouvoir transmettre les données de note de frais de la personne sélectionnée.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Ouvrez *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .

4. Modifiez le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> pour appeler le nouveau constructeur en passant les données de la note de frais de la personne sélectionnée.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Données de style avec des modèles de données

Dans cette section, vous allez mettre à jour l’interface utilisateur pour chaque élément des listes liées aux données à l’aide de modèles de données.

1. Ouvrez *ExpenseReportPage.xaml*.

2. Liez le contenu des éléments de <xref:System.Windows.Controls.Label> « Name » et « Department » à la propriété de source de données appropriée. Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Après l’élément d’ouverture <xref:System.Windows.Controls.Grid>, ajoutez les modèles de données suivants, qui définissent comment afficher les données de note de frais :

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Remplacez les éléments <xref:System.Windows.Controls.DataGridTextColumn> par des <xref:System.Windows.Controls.DataGridTemplateColumn> sous l’élément <xref:System.Windows.Controls.DataGrid> et appliquez-leur les modèles.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Générez et exécutez l’application.

6. Sélectionnez une personne, puis cliquez sur le bouton **Afficher** .

L’illustration suivante montre les deux pages de l’application `ExpenseIt` avec les contrôles, la disposition, les styles, la liaison de données et les modèles de données appliqués :

![Les deux pages de l’application indiquent la liste des noms et une note de frais.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Cet exemple illustre une fonctionnalité spécifique de WPF et ne suit pas toutes les méthodes recommandées pour la sécurité, la localisation et l’accessibilité. Pour une couverture complète de WPF et des meilleures pratiques en matière de développement d’applications .NET, consultez les rubriques suivantes :
>
> - [Accessibilité](../../ui-automation/accessibility-best-practices.md)
> - [Security](../security-wpf.md)
> - [Globalisation et localisation pour WPF](../advanced/wpf-globalization-and-localization-overview.md)
> - [Performances WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Étapes suivantes :

Dans cette procédure pas à pas, vous avez appris un certain nombre de techniques pour la création d’une interface utilisateur à l’aide d’Windows Presentation Foundation (WPF). Vous devez maintenant avoir une compréhension de base des blocs de construction d’une application .NET liée aux données. Pour plus d’informations sur les modèles d’architecture et de programmation WPF, consultez les rubriques suivantes :

- [Architecture WPF](../advanced/wpf-architecture.md)
- [Vue d’ensemble du langage XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Vue d’ensemble des propriétés de dépendance](../advanced/dependency-properties-overview.md)
- [Disposition](../advanced/layout.md)

Pour plus d’informations sur la création d’applications, consultez les rubriques suivantes :

- [Développement d’applications](../app-development/index.md)
- [Contrôles](../controls/index.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Graphiques et multimédia](../graphics-multimedia/index.md)
- [Documents dans WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des panneaux](../controls/panels-overview.md)
- [Vue d’ensemble des modèles de données](../data/data-templating-overview.md)
- [Générer une application WPF](../app-development/building-a-wpf-application-wpf.md)
- [Styles et modèles](../controls/styles-and-templates.md)
