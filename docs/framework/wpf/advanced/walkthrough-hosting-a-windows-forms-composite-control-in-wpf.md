---
title: 'Procédure pas à pas : hébergement d’un contrôle composite Windows Forms dans WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: aa971f194b29096245ea8fe94ba96cc5e0cd763b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605498"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Procédure pas à pas : hébergement d’un contrôle composite Windows Forms dans WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez beaucoup investi dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, il peut être plus efficace de réutiliser au moins certains de ce code dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application plutôt que de réécrire de zéro. Le scénario le plus courant est lorsque vous avez des contrôles Windows Forms existants. Dans certains cas, il est possible que vous n’ayez même pas accès au code source de ces contrôles. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Fournit une procédure simple pour l’hébergement de tels contrôles dans un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application. Par exemple, vous pouvez utiliser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour la plupart de votre programmation tout en hébergeant votre spécialisé <xref:System.Windows.Forms.DataGridView> contrôles.  
  
 Cette procédure pas à pas explique comment une application qui héberge un contrôle composite Windows Forms pour effectuer la saisie de données dans un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application. Le contrôle composite est empaqueté dans une DLL. Cette procédure générale peut être étendue à des applications et des contrôles plus complexes. Cette procédure pas à pas est conçu pour être quasiment identique au niveau d’apparence et les fonctionnalités à [procédure pas à pas : Hébergement d’un contrôle Composite WPF dans les Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). La principale différence est que le scénario d’hébergement est inversé.  
  
 La procédure pas à pas est divisée en deux sections. La première section décrit brièvement l’implémentation du contrôle composite Windows Forms. La deuxième section explique en détail comment héberger le contrôle composite dans une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, recevoir des événements à partir du contrôle et accéder à certaines des propriétés du contrôle.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
- Implémentation du contrôle composite Windows Forms  
  
- Implémentation de l’application hôte WPF  
  
 Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle Composite de formulaires Windows dans WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Prérequis  

Cette procédure pas à pas nécessite Visual Studio.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implémentation du contrôle composite Windows Forms  
 Le contrôle composite Windows Forms utilisé dans cet exemple est un formulaire de saisie de données simple. Ce formulaire prend le nom et l’adresse de l’utilisateur, puis utilise un événement personnalisé pour retourner ces informations à l’hôte. L’illustration suivante montre le rendu du contrôle.  

 L’illustration suivante montre un contrôle composite Windows Forms :  

 ![Capture d’écran montrant un contrôle Windows Forms simple.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Création du projet  
 Pour démarrer le projet :  
  
1. Lancez [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], puis ouvrez le **nouveau projet** boîte de dialogue.  
  
2. Dans la catégorie fenêtre, sélectionnez le **bibliothèque de contrôles Windows Forms** modèle.  
  
3. Nommez le nouveau projet `MyControls`.  
  
4. Pour l’emplacement, spécifiez un dossier à la racine, tel que `WpfHostingWindowsFormsControl`. Plus tard, vous placerez l’application hôte dans ce dossier.  
  
5. Cliquez sur **OK** pour créer le projet. Le projet par défaut contienne un seul contrôle nommé `UserControl1`.  
  
6. Dans l’Explorateur de solutions, renommez `UserControl1` à `MyControl1`.  
  
 Votre projet doit comporter des références aux DLL système suivantes. Si l’une de ces DLL n’est pas incluse par défaut, ajoutez-la à votre projet.  
  
- Système  
  
- System.Data  
  
- System.Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Ajout de contrôles au formulaire  
 Pour ajouter des contrôles au formulaire :  
  
- Ouvrez `MyControl1` dans le concepteur.  
  
 Ajoutez cinq <xref:System.Windows.Forms.Label> contrôles et leurs correspondant <xref:System.Windows.Forms.TextBox> contrôles, dimensionnés et organisés comme elles se trouvent dans l’illustration précédente, dans le formulaire. Dans l’exemple, le <xref:System.Windows.Forms.TextBox> contrôles sont nommés :  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 Ajoutez deux <xref:System.Windows.Forms.Button> contrôles étiquetés **OK** et **Annuler**. Dans l’exemple, les noms de bouton sont `btnOK` et `btnCancel`, respectivement.  
  
### <a name="implementing-the-supporting-code"></a>Implémentation du code de prise en charge  
 Ouvrez le formulaire en mode Code. Le contrôle retourne les données collectées à son hôte en déclenchant personnalisé `OnButtonClick` événement. Les données sont contenues dans l’objet d’argument d’événement. Le code suivant illustre les déclarations event et delegate.  
  
 Ajoutez le code suivant à la classe `MyControl1` .  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 Le `MyControlEventArgs` classe contient les informations à retourner à l’hôte.

 Ajoutez la classe suivante au formulaire.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Lorsque l’utilisateur clique sur le **OK** ou **Annuler** bouton, le <xref:System.Windows.Forms.Control.Click> créer des gestionnaires d’événements une `MyControlEventArgs` objet qui contient les données et déclenche le `OnButtonClick` événement. La seule différence entre les deux gestionnaires est l’argument d’événement `IsOK` propriété. Cette propriété permet à l’hôte de déterminer sur quel bouton l’utilisateur a cliqué. Il est défini sur `true` pour le **OK** bouton, et `false` pour le **Annuler** bouton. Le code suivant montre les deux gestionnaires de boutons.

 Ajoutez le code suivant à la classe `MyControl1` .

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Attribution d’un nom fort à l’assembly et création de l’assembly
 Pour cet assembly soit référencé par une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, il doit avoir un nom fort. Pour créer un nom fort, créez un fichier de clé avec Sn.exe et ajoutez-le à votre projet.

1. Ouvrez une invite de commandes [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Pour ce faire, cliquez sur le **Démarrer** menu, puis sélectionnez **tous les programmes/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio invite de commandes**. Une fenêtre de console s’affiche alors avec des variables d’environnement personnalisées.

2. À l’invite de commande, utilisez le `cd` commande pour accéder à votre dossier de projet.

3. Générez un fichier de clé nommé MyControls.snk en exécutant la commande suivante.

    ```
    Sn.exe -k MyControls.snk
    ```

4. Pour inclure le fichier de clé dans votre projet, cliquez sur le nom du projet dans l’Explorateur de solutions, puis sur **propriétés**. Dans le Concepteur de projets, cliquez sur le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher, puis accédez à votre fichier de clé.

5. Générez la solution. La génération produira une DLL nommée MyControls.dll.

## <a name="implementing-the-wpf-host-application"></a>Implémentation de l’application hôte WPF
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] héberger l’application utilise le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle à héberger `MyControl1`. L’application gère le `OnButtonClick` événement pour recevoir les données à partir du contrôle. Il possède également une collection de cases d’option qui vous permettent de modifier certaines propriétés du contrôle à partir de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application. L’illustration suivante montre l’application finale.

L’illustration suivante montre l’application complète, y compris le contrôle incorporé dans l’application WPF :

 ![Capture d’écran montrant un contrôle incorporé dans une page WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Création du projet
 Pour démarrer le projet :

1. Ouvrez [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], puis sélectionnez **nouveau projet**.

2. Dans la catégorie fenêtre, sélectionnez le **Application WPF** modèle.

3. Nommez le nouveau projet `WpfHost`.

4. Pour l’emplacement, spécifiez le même dossier de premier niveau qui contient le projet MyControls.

5. Cliquez sur **OK** pour créer le projet.

 Vous devez également ajouter des références à la DLL qui contient `MyControl1` et d’autres assemblys.

1. Cliquez sur le nom du projet dans l’Explorateur de solutions et sélectionnez **ajouter une référence**.

2. Cliquez sur le **Parcourir** onglet et accédez au dossier qui contient MyControls.dll. Pour cette procédure pas à pas, il s’agit du dossier MyControls\bin\Debug.

3. Sélectionnez MyControls.dll, puis cliquez sur **OK**.

4. Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.

### <a name="implementing-the-basic-layout"></a>Implémentation de la disposition de base
 Le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l’hôte de l’application est implémentée dans MainWindow.xaml. Ce fichier contient [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage qui définit la disposition et héberge le contrôle Windows Forms. L’application est divisée en trois sections :

- Le **propriétés de contrôle** panneau, qui constituée une collection de cases d’option que vous pouvez utiliser pour modifier différentes propriétés du contrôle hébergé.

- Le **données à partir du contrôle** panneau, qui contient plusieurs <xref:System.Windows.Controls.TextBlock> les éléments qui affichent les données retournées par le contrôle hébergé.

- Le contrôle hébergé.

 La disposition de base est indiquée dans le XAML suivant. Le balisage qui est nécessaire pour héberger `MyControl1` est omis à partir de cet exemple, mais sera abordé plus tard.

 Remplacez le code XAML de MainWindow.xaml par le code suivant. Si vous utilisez Visual Basic, remplacez la classe par `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 La première <xref:System.Windows.Controls.StackPanel> élément contient plusieurs jeux de <xref:System.Windows.Controls.RadioButton> contrôles qui vous permettent de modifier différentes propriétés par défaut du contrôle hébergé. Qui est suivie d’un <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément, quels sont les hôtes `MyControl1`. La dernière <xref:System.Windows.Controls.StackPanel> élément contient plusieurs <xref:System.Windows.Controls.TextBlock> les éléments qui affichent les données retournées par le contrôle hébergé. Le classement des éléments et les <xref:System.Windows.Controls.DockPanel.Dock%2A> et <xref:System.Windows.FrameworkElement.Height%2A> paramètres d’attribut incorporent le contrôle hébergé sur la fenêtre sans espace ni distorsion.

#### <a name="hosting-the-control"></a>Hébergement du contrôle
 La version modifiée suivante de le XAML précédent se concentre sur les éléments qui sont nécessaires à l’hôte `MyControl1`.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 Le `xmlns` attribut de mappage d’espace de noms crée une référence à la `MyControls` espace de noms qui contient le contrôle hébergé. Ce mappage vous permet de représenter `MyControl1` dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] comme `<mcl:MyControl1>`.

 Dans le code XAML, deux éléments gèrent l’hébergement :

- `WindowsFormsHost` représente le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément qui vous permet d’héberger un contrôle Windows Forms dans un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.

- `mcl:MyControl1`, qui représente `MyControl1`, est ajouté à la <xref:System.Windows.Forms.Integration.WindowsFormsHost> collection enfant de l’élément. Par conséquent, ce contrôle Windows Forms est rendu dans le cadre de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fenêtre et vous pouvez communiquer avec le contrôle de l’application.

### <a name="implementing-the-code-behind-file"></a>Implémentation du fichier code-behind
 Le fichier code-behind, MainWindow.xaml.vb ou MainWindow.xaml.cs, contient le code procédural qui implémente les fonctionnalités de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] décrits dans la section précédente. Les tâches principales sont les suivantes :

- Attachement d’un gestionnaire d’événements `MyControl1`de `OnButtonClick` événements.

- Modification des différentes propriétés de `MyControl1`, en fonction de la définition de la collection de cases d’option.

- Affichage des données collectées par le contrôle

#### <a name="initializing-the-application"></a>Initialisation de l’application
 Le code d’initialisation est contenu dans un gestionnaire d’événements de la fenêtre <xref:System.Windows.FrameworkElement.Loaded> événement et attache un gestionnaire d’événements pour le contrôle `OnButtonClick` événement.

 Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, ajoutez le code suivant à la `MainWindow` classe.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Étant donné que le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] abordé précédemment ajoutait `MyControl1` à la <xref:System.Windows.Forms.Integration.WindowsFormsHost> collection d’éléments enfants de l’élément, vous pouvez effectuer un cast le <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> pour obtenir la référence à `MyControl1`. Vous pouvez ensuite utiliser cette référence pour attacher un gestionnaire d’événements `OnButtonClick`.

 En plus de fournir une référence au contrôle lui-même, <xref:System.Windows.Forms.Integration.WindowsFormsHost> expose un certain nombre de propriétés du contrôle, que vous pouvez manipuler à partir de l’application. Le code d’initialisation affecte ces valeurs aux variables globales privées pour une utilisation ultérieure dans l’application.

 Afin que vous puissiez accéder facilement les types dans les `MyControls` DLL, ajoutez le code suivant `Imports` ou `using` instruction au début du fichier.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>Gestion de l’événement OnButtonClick
 `MyControl1` déclenche le `OnButtonClick` événement lorsque l’utilisateur clique sur un des boutons du contrôle.

 Ajoutez le code suivant à la classe `MainWindow` .

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Les données dans les zones de texte sont compressées dans le `MyControlEventArgs` objet. Si l’utilisateur clique sur le **OK** bouton, le Gestionnaire d’événements extrait les données et l’affiche dans le panneau ci-dessous `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Modification des propriétés du contrôle
 Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément expose plusieurs propriétés de valeur par défaut du contrôle hébergé. Par conséquent, vous pouvez changer l’apparence du contrôle pour qu’elle corresponde davantage au style de votre application. Les ensembles de cases d’option du panneau gauche permettent à l’utilisateur de modifier plusieurs propriétés de couleur et de police. Chaque ensemble de boutons possède un gestionnaire pour le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement, qui détecte les sélections de cases d’option de l’utilisateur et modifie la propriété correspondante sur le contrôle.

 Ajoutez le code suivant à la classe `MainWindow` .

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Générez et exécutez l’application. Ajouter du texte dans le contrôle composite Windows Forms, puis sur **OK**. Le texte s’affiche dans les étiquettes. Cliquez sur les différentes cases d’option pour voir l’effet du contrôle.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Procédure pas à pas : Hébergement d’un contrôle de formulaires Windows dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d’un contrôle Composite WPF dans les Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
