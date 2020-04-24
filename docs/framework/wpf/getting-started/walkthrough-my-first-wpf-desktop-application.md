---
title: Créez votre première application WPF dans Visual Studio 2019 - .NET Framework
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
ms.openlocfilehash: 9381873faa8cca1accf95d823f5183a218d28813
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646414"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>Tutorial: Créez votre première application WPF dans Visual Studio 2019

Cet article vous montre comment développer une application de bureau de la Windows Presentation Foundation (WPF) qui comprend les éléments qui sont communs à la plupart des applications WPF : Marge de balisage extensible d’application (XAML), code-derrière, définitions d’applications, contrôles, mise en page, liaison de données et styles. Pour développer l’application, vous utiliserez Visual Studio.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Créez un projet WPF.
> - Utilisez XAML pour concevoir l’apparence de l’interface utilisateur de l’application (interface utilisateur).
> - Écrivez du code pour construire le comportement de l’application.
> - Créez une définition d’application pour gérer l’application.
> - Ajoutez des commandes et créez la mise en page pour composer l’interface utilisateur de l’application.
> - Créez des styles pour une apparence cohérente tout au long de l’interface utilisateur de l’application.
> - Lier l’interface utilisateur aux données, à la fois pour remplir l’interface utilisateur à partir de données et pour garder les données et l’interface utilisateur synchronisées.

À la fin du tutoriel, vous aurez construit une application Windows autonome qui permet aux utilisateurs de consulter les rapports de dépenses pour certaines personnes. L’application est composée de plusieurs pages WPF qui sont hébergées dans une fenêtre de style navigateur.

> [!TIP]
> L’exemple de code qui est utilisé dans ce tutoriel est disponible à la fois pour Visual Basic et C ' à [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Vous pouvez basculer le langage de code du code de l’échantillon entre C et Visual Basic en utilisant le sélecteur de langue en haut de cette page.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **de développement de bureau .NET** installé.

   Pour plus d’informations sur l’installation de la dernière version de Visual Studio, voir [Install Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Créer le projet d’application

La première étape consiste à créer l’infrastructure d’application, qui comprend une définition d’application, deux pages et une image.

1. Créer un nouveau projet d’application WPF **`ExpenseIt`** dans Visual Basic ou Visual C ' nommé :

   1. Ouvrez Visual Studio et sélectionnez **Créez un nouveau projet** dans le menu Get **started.**

      Le **Dialogue Créer un nouveau projet** s’ouvre.

   2. Dans le **décrocheur de la langue,** sélectionnez soit **C ou** **Visual Basic**.

   3. Sélectionnez le modèle **WPF App (.NET Framework)** et sélectionnez **Ensuite**.

      ![Créer un nouveau dialogue de projet](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      Configurez **votre nouveau dialogue de projet.**

   4. Entrez le **`ExpenseIt`** nom du projet, puis sélectionnez **Créer**.

      ![Configurer un nouveau dialogue de projet](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio crée le projet et ouvre le concepteur pour la fenêtre d’application par défaut nommée **MainWindow.xaml**.

2. Open *Application.xaml* (Visual Basic) ou *App.xaml* (C).

    Ce fichier XAML définit une application WPF et toutes les ressources d’application. Vous utilisez également ce fichier pour spécifier l’interface utilisateur, dans ce cas *MainWindow.xaml*, qui s’affiche automatiquement lorsque l’application commence.

    Votre XAML devrait ressembler à ce qui suit dans Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Et comme ce qui suit dans C:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Ouvert *MainWindow.xaml*.

    Ce fichier XAML est la fenêtre principale de votre application et affiche le contenu créé en pages. La <xref:System.Windows.Window> classe définit les propriétés d’une fenêtre, comme son titre, sa taille ou son icône, et gère des événements tels que la fermeture ou la dissimulation.

4. Modifier <xref:System.Windows.Window> l’élément <xref:System.Windows.Navigation.NavigationWindow>à un , comme indiqué dans le XAML suivant:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Cette application navigue vers différents contenus en fonction de l’entrée de l’utilisateur. C’est pourquoi <xref:System.Windows.Window> le principal doit <xref:System.Windows.Navigation.NavigationWindow>être changé en un . <xref:System.Windows.Navigation.NavigationWindow>hérite de toutes <xref:System.Windows.Window>les propriétés de . L’élément <xref:System.Windows.Navigation.NavigationWindow> dans le fichier XAML <xref:System.Windows.Navigation.NavigationWindow> crée un exemple de la classe. Pour plus d’informations, voir [Aperçu de la navigation](../app-development/navigation-overview.md).

5. Retirez <xref:System.Windows.Controls.Grid> les éléments <xref:System.Windows.Navigation.NavigationWindow> entre les balises.

6. Modifier les propriétés suivantes dans le <xref:System.Windows.Navigation.NavigationWindow> code XAML pour l’élément :

    - Définissez <xref:System.Windows.Window.Title%2A> la`ExpenseIt`propriété à " " .

    - Réglez la <xref:System.Windows.FrameworkElement.Height%2A> propriété à 350 pixels.

    - Réglez la <xref:System.Windows.FrameworkElement.Width%2A> propriété à 500 pixels.

    Votre XAML devrait ressembler à ce qui suit pour Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Et comme ce qui suit pour C:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Ouvrez *MainWindow.xaml.vb* ou *MainWindow.xaml.cs*.

    Ce fichier est un fichier de code-derrière qui contient du code pour gérer les événements déclarés dans *MainWindow.xaml*. Ce fichier contient une classe partielle pour la fenêtre définie en XAML.

8. Si vous utilisez C, changez la `MainWindow` <xref:System.Windows.Navigation.NavigationWindow>classe pour en tirer . (Dans Visual Basic, cela se produit automatiquement lorsque vous changez la fenêtre en XAML.) Votre code CMD devrait maintenant ressembler à ceci :

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Ajouter des fichiers à l’application

Dans cette section, vous allez ajouter deux pages et une image à l’application.

1. Ajoutez une nouvelle page au projet *`ExpenseItHome.xaml`* et nommez-la :

   1. Dans **Solution Explorer**, cliquez **`ExpenseIt`** à droite sur le nœud du projet et choisissez **Ajouter** > **la page**.

   1. Dans le dialogue **Add New Item,** le modèle **Page (WPF)** est déjà sélectionné. Entrez **`ExpenseItHome`** le nom , puis sélectionnez **Ajouter**.

    Cette page est la première page qui s’affiche lorsque l’application est lancée. Il affichera une liste de personnes à choisir, pour afficher un rapport de dépenses pour.

1. Ouvrez *`ExpenseItHome.xaml`*.

1. Réglez <xref:System.Windows.Controls.Page.Title%2A> `ExpenseIt - Home`le à " ".

1. Réglez les `DesignHeight` 350 `DesignWidth` pixels et les 500 pixels.

    Le XAML apparaît maintenant comme suit pour Visual Basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Et comme ce qui suit pour C:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Ouvert *MainWindow.xaml*.

1. Ajoutez <xref:System.Windows.Navigation.NavigationWindow.Source%2A> une propriété <xref:System.Windows.Navigation.NavigationWindow> à l’élément`ExpenseItHome.xaml`et définissez-la à " " "

    Cela *`ExpenseItHome.xaml`* s’établit pour être la première page ouverte lorsque l’application commence.

    Exemple XAML dans Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Et dans C:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Vous pouvez également définir la propriété **Source** dans la catégorie **Divers** de la fenêtre **Propriétés.**
   >
   > ![Propriété source dans la fenêtre de propriétés](./media/properties-source.png)

1. Ajoutez une autre nouvelle page WPF au projet, et *nommez-le ExpenseReportPage.xaml*:

   1. Dans **Solution Explorer**, cliquez **`ExpenseIt`** à droite sur le nœud du projet et choisissez **Ajouter** > **la page**.

   1. Dans le dialogue **Add New Item,** sélectionnez le modèle **De la Page (WPF).** Entrez le nom **ExpenseReportPage**, puis sélectionnez **Ajouter**.

    Cette page affichera le rapport de dépenses **`ExpenseItHome`** pour la personne sélectionnée sur la page.

1. Ouvrez *ExpenseReportPage.xaml*.

1. Réglez <xref:System.Windows.Controls.Page.Title%2A> `ExpenseIt - View Expense`le à " ".

1. Réglez les `DesignHeight` 350 `DesignWidth` pixels et les 500 pixels.

    *ExpenseReportPage.xaml* ressemble maintenant à ce qui suit dans Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Et comme ce qui suit dans C:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Ouvrez *ExpenseItHome.xaml.vb* et *ExpenseReportPage.xaml.vb*, ou *ExpenseItHome.xaml.cs* et *ExpenseReportPage.xaml.cs*.

    Lorsque vous créez un nouveau fichier Page, Visual Studio crée automatiquement son fichier *de code.* Ces fichiers code-behind gèrent la logique pour répondre à une saisie de l’utilisateur.

    Votre code doit ressembler **`ExpenseItHome`** à ce qui suit pour :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    Et comme ce qui suit pour **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Ajoutez une image nommée *watermark.png* au projet. Vous pouvez créer votre propre image, copier le fichier à partir du code de l’échantillon, ou l’obtenir à partir du référentiel [GitHub microsoft/WPF-Samples.](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)

    1. Cliquez à droite sur le nœud du **Shift**+projet et sélectionnez Ajouter > **l’élément existant**, ou appuyez sur Shift **Add****Alt**+**A**.

    2. Dans le dialogue **Ajouter l’élément existant,** définissez le filtre de fichier à **tous les fichiers** ou fichiers **d’image,** naviguez sur le fichier d’image que vous souhaitez utiliser, puis sélectionnez **Ajouter**.

## <a name="build-and-run-the-application"></a>Génération et exécution de l’application

1. Pour créer et exécuter l’application, appuyez sur **F5** ou sélectionnez **Start Debugging** dans le menu **Debug.**

    L’illustration suivante montre <xref:System.Windows.Navigation.NavigationWindow> l’application avec les boutons :

    ![Application après que vous l’avez construit et exécuté.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Fermez l’application pour revenir à Visual Studio.

## <a name="create-the-layout"></a>Créer la mise en page

La mise en page fournit un moyen ordonné de placer des éléments d’interface utilisateur, et gère également la taille et la position de ces éléments lorsqu’une interface utilisateur est resized. En règle générale, vous allez créer une disposition avec l’un des contrôles de disposition suivants :

- <xref:System.Windows.Controls.Canvas>- Définit une zone dans laquelle vous pouvez positionner explicitement les éléments de l’enfant en utilisant des coordonnées relatives à la zone de toile.
- <xref:System.Windows.Controls.DockPanel>- Définit une zone où vous pouvez organiser des éléments d’enfant horizontalement ou verticalement, par rapport à l’autre.
- <xref:System.Windows.Controls.Grid>- Définit une zone flexible de grille qui se compose de colonnes et de rangées.
- <xref:System.Windows.Controls.StackPanel>- Organise des éléments d’enfant en une seule ligne qui peut être orientée horizontalement ou verticalement.
- <xref:System.Windows.Controls.VirtualizingStackPanel>- Organise et virtualise le contenu sur une seule ligne qui est orientée horizontalement ou verticalement.
- <xref:System.Windows.Controls.WrapPanel>- Positionne les éléments de l’enfant en position séquentielle de gauche à droite, brisant le contenu à la ligne suivante au bord de la boîte contenante. La commande subséquente se fait séquentiellement de haut en bas ou de droite à gauche, selon la valeur de la propriété Orientation.

Chacune de ces commandes de mise en page prend en charge un type particulier de mise en page pour ses éléments pour enfants. `ExpenseIt`pages peuvent être resized, et chaque page a des éléments qui sont disposés horizontalement et verticalement aux côtés d’autres éléments. Dans cet exemple, l’est <xref:System.Windows.Controls.Grid> utilisé comme élément de mise en page pour l’application.

> [!TIP]
> Pour plus <xref:System.Windows.Controls.Panel> d’informations sur les éléments, voir [aperçu des panneaux](../controls/panels-overview.md). Pour plus d’informations sur la mise en page, voir [Layout](../advanced/layout.md).

Dans cette section, vous créez une table à colonne unique avec trois lignes et une marge <xref:System.Windows.Controls.Grid> *`ExpenseItHome.xaml`* de 10 pixels en ajoutant des définitions de colonne et de ligne à l’in .

1. Dans *`ExpenseItHome.xaml`*, <xref:System.Windows.FrameworkElement.Margin%2A> mettre la <xref:System.Windows.Controls.Grid> propriété sur l’élément à "10,0,10,10", qui correspond à gauche, en haut, à droite et les marges inférieures:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Vous pouvez également définir les valeurs **de marge** dans la fenêtre **Propriétés,** dans la catégorie **Mise en page** :
   >
   > ![Valeurs de marge dans la fenêtre Propriétés](./media/properties-margin.png)

2. Ajoutez le XAML <xref:System.Windows.Controls.Grid> suivant entre les balises pour créer les définitions de la ligne et de la colonne :

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    Les <xref:System.Windows.Controls.RowDefinition.Height%2A> deux lignes sont <xref:System.Windows.GridLength.Auto%2A>réglées à , ce qui signifie que les lignes sont dimensionnées en fonction du contenu dans les lignes. La <xref:System.Windows.Controls.RowDefinition.Height%2A> valeur <xref:System.Windows.GridUnitType.Star> par défaut est le dimensionnement, ce qui signifie que la hauteur de la rangée est une proportion pondérée de l’espace disponible. Par exemple, si deux <xref:System.Windows.Controls.RowDefinition.Height%2A> rangées ont chacune un de "' , ils ont chacun une hauteur qui est la moitié de l’espace disponible.

    Votre <xref:System.Windows.Controls.Grid> devrait maintenant contenir le XAML suivant:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Ajouter des contrôles

Dans cette section, vous mettrez à jour l’interface utilisateur de la page d’accueil pour afficher une liste de personnes, où vous sélectionnez une personne pour afficher son rapport de dépenses. Les contrôles sont des objets d’interface utilisateur qui permettent aux utilisateurs d’interagir avec votre application. Pour plus d’informations, consultez [Contrôles](../controls/index.md).

Pour créer cette interface utilisateur, vous ajouterez les éléments suivants à *`ExpenseItHome.xaml`*:

- A <xref:System.Windows.Controls.ListBox> (pour la liste des personnes).
- A <xref:System.Windows.Controls.Label> (pour l’en-tête de liste).
- A <xref:System.Windows.Controls.Button> (pour cliquer pour voir le rapport de dépenses pour la personne sélectionnée dans la liste).

Chaque contrôle est placé dans <xref:System.Windows.Controls.Grid> une <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> rangée de la en fixant la propriété ci-jointe. Pour plus d’informations sur les propriétés ci-jointes, voir [Aperçu des propriétés ci-jointes](../advanced/attached-properties-overview.md).

1. Dans *`ExpenseItHome.xaml`*, ajouter le XAML <xref:System.Windows.Controls.Grid> suivant quelque part entre les balises:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Vous pouvez également créer les commandes en les faisant glisser de la fenêtre de la boîte à **outils** sur la fenêtre de conception, puis en définissant leurs propriétés dans la fenêtre **propriétés.**

2. Générez et exécutez l’application.

    L’illustration suivante montre les contrôles que vous avez créés :

![ExpenseIt exemple capture d’écran affichant une liste de noms](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Ajouter une image et un titre

Dans cette section, vous mettrez à jour l’interface utilisateur de la page d’accueil avec une image et un titre de page.

1. Dans *`ExpenseItHome.xaml`*, ajouter une <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> autre <xref:System.Windows.Controls.ColumnDefinition.Width%2A> colonne à l’avec un fixe de 230 pixels:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. Ajouter une autre <xref:System.Windows.Controls.Grid.RowDefinitions%2A>rangée à la , pour un total de quatre rangées:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. Déplacez les commandes vers la <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> deuxième colonne en définissant la propriété à 1 dans chacun des trois contrôles (Border, ListBox et Button).

4. Déplacez chaque contrôle d’affilée <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> en incrémentant sa valeur de 1 pour chacun des trois contrôles (Border, ListBox et Button) et pour l’élément Frontière.

   Le XAML pour les trois contrôles ressemble maintenant à ce qui suit:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Réglez la <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> propriété sur le fichier d’image *watermark.png,* en ajoutant le XAML suivant n’importe où entre les `<Grid>` étiquettes et `</Grid>` les balises :

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Avant <xref:System.Windows.Controls.Border> l’élément, <xref:System.Windows.Controls.Label> ajoutez un avec le contenu "Voir le rapport de dépenses". Cette étiquette est le titre de la page.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Générez et exécutez l’application.

L’illustration suivante montre les résultats de ce que vous venez d’ajouter :

![ExpenseIt exemple capture d’écran montrant le nouveau fond d’image et le titre de la page](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Ajouter du code pour gérer les événements

1. Ajouter *`ExpenseItHome.xaml`* un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gestionnaire d’événements à l’élément. <xref:System.Windows.Controls.Button> Pour plus d’informations, voir [Comment : Créer un gestionnaire d’événement simple.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. *`ExpenseItHome.xaml.vb`* Ouvrez *`ExpenseItHome.xaml.cs`* ou .

3. Ajoutez le code `ExpenseItHome` suivant à la classe pour ajouter un bouton cliquez sur gestionnaire d’événements. Le gestionnaire de l’événement ouvre la page **ExpenseReportPage.**

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Créer l’interface utilisateur pour ExpenseReportPage

*ExpenseReportPage.xaml* affiche le rapport de dépenses pour **`ExpenseItHome`** la personne sélectionnée sur la page. Dans cette section, vous créerez l’interface utilisateur pour **ExpenseReportPage**. Vous ajouterez également des fonds d’arrière-plan et remplirez les couleurs aux différents éléments d’interface utilisateur.

1. Ouvrez *ExpenseReportPage.xaml*.

2. Ajoutez le XAML <xref:System.Windows.Controls.Grid> suivant entre les balises :

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Cette interface utilisateur *`ExpenseItHome.xaml`* est similaire à , sauf <xref:System.Windows.Controls.DataGrid>que les données du rapport est affichée dans un .

3. Générez et exécutez l’application.

4. Sélectionnez le bouton **View.**

    La page de note de frais s’affiche. Notez également que le bouton de navigation arrière est activé.

L’illustration suivante montre les éléments d’interface utilisateur ajoutés à *ExpenseReportPage.xaml*.

![ExpenseIt exemple capture d’écran montrant l’interface utilisateur vient de créer pour le ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Contrôles de style

L’apparition de divers éléments est souvent la même pour tous les éléments du même type dans une interface utilisateur. L’interface utilisateur utilise des [styles](../../../desktop-wpf/fundamentals/styles-templates-overview.md) pour rendre les apparences réutilisables sur plusieurs éléments. La réutilisabilité des styles permet de simplifier la création et la gestion de XAML. Cette section remplace par des styles les attributs d’élément qui ont été définis lors des étapes précédentes.

1. Ouvrez *Application.xaml* ou *App.xaml*.

2. Ajoutez le XAML <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> suivant entre les balises :

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Ce code XAML ajoute les styles suivants :

    - `headerTextStyle`: pour mettre en forme le titre de la page <xref:System.Windows.Controls.Label>.

    - `labelStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Label> .

    - `columnHeaderStyle`: pour mettre en forme <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Border> de l’en-tête de liste.

    - `listHeaderTextStyle`: Pour formater <xref:System.Windows.Controls.Label>l’en-tête de liste .

    - `buttonStyle`: Pour <xref:System.Windows.Controls.Button> formater le on `ExpenseItHome.xaml`.

    Notez que les styles sont <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> des ressources et des enfants de l’élément propriété. À cet emplacement, les styles sont appliqués à tous les éléments d’une application. Par exemple d’utiliser des ressources dans une application .NET, voir [Use Application Resources](../advanced/how-to-use-application-resources.md).

3. Dans *`ExpenseItHome.xaml`*, remplacer <xref:System.Windows.Controls.Grid> tout entre les éléments par le XAML suivant:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Les propriétés qui définissent l’apparence de chaque contrôle, comme <xref:System.Windows.VerticalAlignment> et <xref:System.Windows.Media.FontFamily> , sont supprimées et remplacées lors de l’application de styles. Par exemple, `headerTextStyle` le s’applique au <xref:System.Windows.Controls.Label>« Rapport de dépense de vue ».

4. Ouvrez *ExpenseReportPage.xaml*.

5. Remplacez tout <xref:System.Windows.Controls.Grid> entre les éléments par le XAML suivant :

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Cette XAML ajoute <xref:System.Windows.Controls.Label> des <xref:System.Windows.Controls.Border> styles à la et des éléments.

6. Générez et exécutez l’application. L’apparence de la fenêtre est la même qu’auparavant.

    ![ExpenseIt capture d’écran de l’échantillon avec la même apparence que dans la dernière section.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Fermez l’application pour revenir à Visual Studio.

## <a name="bind-data-to-a-control"></a>Lier les données à un contrôle

Dans cette section, vous allez créer les données XML qui sont liées à divers contrôles.

1. Dans *`ExpenseItHome.xaml`*, après <xref:System.Windows.Controls.Grid> l’élément d’ouverture, ajouter <xref:System.Windows.Data.XmlDataProvider> le XAML suivant pour créer un qui contient les données pour chaque personne:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Les données sont <xref:System.Windows.Controls.Grid> créées comme une ressource. Normalement, ces données seraient chargées comme un fichier, mais pour la simplicité, les données sont ajoutées en ligne.

2. Dans `<Grid.Resources>` l’élément, `<xref:System.Windows.DataTemplate>` ajouter l’élément suivant, qui définit <xref:System.Windows.Controls.ListBox>comment `<XmlDataProvider>` afficher les données dans le , après l’élément:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Pour plus d’informations sur les modèles de données, voir [l’aperçu des données.](../data/data-templating-overview.md)

3. Remplacer l’existant <xref:System.Windows.Controls.ListBox> par le XAML suivant :

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Ce XAML lie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> la <xref:System.Windows.Controls.ListBox> propriété de la source de données <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>et applique le modèle de données comme le .

## <a name="connect-data-to-controls"></a>Connectez les données aux contrôles

Ensuite, vous ajouterez du code pour récupérer le **`ExpenseItHome`** nom sélectionné sur la page et le transmettre au constructeur de **ExpenseReportPage**. **ExpenseReportPage** définit son contexte de données avec l’élément passé, ce à quoi les contrôles définis dans *ExpenseReportPage.xaml* lient.

1. Ouvrez *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.

2. Ajoutez un constructeur qui prend un objet de façon à pouvoir transmettre les données de note de frais de la personne sélectionnée.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. *`ExpenseItHome.xaml.vb`* Ouvrez *`ExpenseItHome.xaml.cs`* ou .

4. Modifier <xref:System.Windows.Controls.Primitives.ButtonBase.Click> le gestionnaire d’événements pour appeler le nouveau constructeur en passant les données de rapport de dépenses de la personne sélectionnée.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Données de style avec modèles de données

Dans cette section, vous mettrez à jour l’interface utilisateur pour chaque élément des listes de données en utilisant des modèles de données.

1. Ouvrez *ExpenseReportPage.xaml*.

2. Lier le contenu des éléments «Nom» et «Département» <xref:System.Windows.Controls.Label> à la propriété de source de données appropriée. Pour plus d’informations sur la liaison des données, voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Après l’élément d’ouverture, <xref:System.Windows.Controls.Grid> ajoutez les modèles de données suivants, qui définissent comment afficher les données du rapport de dépenses :

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Remplacez <xref:System.Windows.Controls.DataGridTextColumn> les <xref:System.Windows.Controls.DataGridTemplateColumn> éléments <xref:System.Windows.Controls.DataGrid> par sous l’élément et appliquez les modèles à eux.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Générez et exécutez l’application.

6. Sélectionnez une personne, puis sélectionnez le bouton **Afficher.**

L’illustration suivante montre `ExpenseIt` les deux pages de l’application avec des contrôles, la mise en page, les styles, la liaison de données et les modèles de données appliqués :

![Les deux pages de l’application montrant la liste des noms et un rapport de dépenses.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Cet échantillon démontre une caractéristique spécifique du WPF et ne suit pas toutes les meilleures pratiques pour des choses comme la sécurité, la localisation et l’accessibilité. Pour une couverture complète de WPF et les meilleures pratiques de développement de l’application .NET, voir les sujets suivants:
>
> - [Accessibilité](../../ui-automation/accessibility-best-practices.md)
> - [Sécurité](../security-wpf.md)
> - [Globalisation et localisation pour WPF](../advanced/wpf-globalization-and-localization-overview.md)
> - [Performances WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Étapes suivantes

Dans ce pas-là, vous avez appris un certain nombre de techniques pour créer une interface utilisateur en utilisant Windows Presentation Foundation (WPF). Vous devez maintenant avoir une compréhension de base des éléments constitutifs d’une application .NET liée aux données. Pour plus d’informations sur les modèles d’architecture et de programmation WPF, consultez les rubriques suivantes :

- [Architecture WPF](../advanced/wpf-architecture.md)
- [Vue d’ensemble XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Aperçu des propriétés de dépendance](../advanced/dependency-properties-overview.md)
- [Mise en page](../advanced/layout.md)

Pour plus d’informations sur la création d’applications, consultez les rubriques suivantes :

- [Développement d’applications](../app-development/index.md)
- [Contrôles](../controls/index.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Graphiques et multimédia](../graphics-multimedia/index.md)
- [Documents dans WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Voir aussi

- [Aperçu des panneaux](../controls/panels-overview.md)
- [Aperçu de la température des données](../data/data-templating-overview.md)
- [Construire une application WPF](../app-development/building-a-wpf-application-wpf.md)
- [Styles et modèles](../controls/styles-and-templates.md)
