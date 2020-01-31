---
title: Héberger un contrôle composite Windows Forms dans WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 22eb323d1c1921832630d1d1b30463b4ecb7d1fd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794229"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous investissez dans Windows Forms code, il peut être plus efficace de réutiliser au moins une partie de ce code dans votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plutôt que de la réécrire à partir de zéro. Le scénario le plus courant est lorsque vous avez des contrôles de Windows Forms existants. Dans certains cas, il est possible que vous n’ayez même pas accès au code source de ces contrôles. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une procédure simple pour l’hébergement de ces contrôles dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Par exemple, vous pouvez utiliser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour la majeure partie de votre programmation tout en hébergeant vos contrôles de <xref:System.Windows.Forms.DataGridView> spécialisés.  
  
 Cette procédure pas à pas vous guide à travers une application qui héberge un Windows Forms contrôle composite pour effectuer une entrée de données dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le contrôle composite est empaqueté dans une DLL. Cette procédure générale peut être étendue à des applications et des contrôles plus complexes. Cette procédure pas à pas est conçue pour être quasiment identique dans l’apparence et les fonctionnalités de la [procédure pas à pas : Hébergement d’un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). La principale différence est que le scénario d’hébergement est inversé.  
  
 La procédure pas à pas est divisée en deux sections. La première section décrit brièvement l’implémentation du contrôle composite Windows Forms. La deuxième section explique en détail comment héberger le contrôle composite dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], recevoir des événements du contrôle et accéder à certaines propriétés du contrôle.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
- Implémentation du contrôle composite Windows Forms  
  
- Implémentation de l’application hôte WPF  
  
 Pour obtenir la liste du code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle composite Windows Forms dans l’exemple WPF](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Prerequisites  

Cette procédure pas à pas nécessite Visual Studio.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implémentation du contrôle composite Windows Forms  
 Le contrôle composite Windows Forms utilisé dans cet exemple est un formulaire de saisie de données simple. Ce formulaire prend le nom et l’adresse de l’utilisateur, puis utilise un événement personnalisé pour retourner ces informations à l’hôte. L’illustration suivante montre le rendu du contrôle.  

 L’illustration suivante montre un contrôle composite Windows Forms :  

 ![Capture d’écran montrant un contrôle de Windows Forms simple.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Création du projet  
 Pour démarrer le projet :  
  
1. Lancez Visual Studio, puis ouvrez la boîte de dialogue **nouveau projet** .  
  
2. Dans la catégorie fenêtre, sélectionnez le modèle **bibliothèque de contrôles Windows Forms** .  
  
3. Nommez le nouveau projet `MyControls`.  
  
4. Pour l’emplacement, spécifiez un dossier de niveau supérieur, tel que `WpfHostingWindowsFormsControl`. Plus tard, vous placerez l’application hôte dans ce dossier.  
  
5. Cliquez sur **OK** pour créer le projet. Le projet par défaut contient un seul contrôle nommé `UserControl1`.  
  
6. Dans Explorateur de solutions, renommez `UserControl1` en `MyControl1`.  
  
 Votre projet doit comporter des références aux DLL système suivantes. Si l’une de ces DLL n’est pas incluse par défaut, ajoutez-la à votre projet.  
  
- System  
  
- System.Data  
  
- System.Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Ajout de contrôles au formulaire  
 Pour ajouter des contrôles au formulaire :  
  
- Ouvrez `MyControl1` dans le concepteur.  
  
 Ajoutez cinq contrôles <xref:System.Windows.Forms.Label> et leurs contrôles <xref:System.Windows.Forms.TextBox> correspondants, dimensionnés et disposés comme dans l’illustration précédente, sur le formulaire. Dans l’exemple, les contrôles <xref:System.Windows.Forms.TextBox> sont nommés :  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 Ajoutez deux contrôles <xref:System.Windows.Forms.Button> étiquetés **OK** et **Annuler**. Dans l’exemple, les noms de bouton sont `btnOK` et `btnCancel`, respectivement.  
  
### <a name="implementing-the-supporting-code"></a>Implémentation du code de prise en charge  
 Ouvrez le formulaire en mode Code. Le contrôle retourne les données collectées à son hôte en déclenchant l’événement `OnButtonClick` personnalisé. Les données sont contenues dans l’objet d’argument d’événement. Le code suivant illustre les déclarations event et delegate.  
  
 Ajoutez le code suivant à la classe `MyControl1` .  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 La classe `MyControlEventArgs` contient les informations à retourner à l’hôte.

 Ajoutez la classe suivante au formulaire.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Quand l’utilisateur clique sur le bouton **OK** ou **Annuler** , les gestionnaires d’événements <xref:System.Windows.Forms.Control.Click> créent un objet `MyControlEventArgs` qui contient les données et déclenche l’événement `OnButtonClick`. La seule différence entre les deux gestionnaires est la propriété `IsOK` de l’argument d’événement. Cette propriété permet à l’hôte de déterminer sur quel bouton l’utilisateur a cliqué. Elle est définie sur `true` pour le bouton **OK** , et `false` pour le bouton **Annuler** . Le code suivant montre les deux gestionnaires de boutons.

 Ajoutez le code suivant à la classe `MyControl1` .

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Attribution d’un nom fort à l’assembly et création de l’assembly
 Pour que cet assembly soit référencé par une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il doit avoir un nom fort. Pour créer un nom fort, créez un fichier de clé avec SN. exe et ajoutez-le à votre projet.

1. Ouvrez une invite de commandes de Visual Studio. Pour ce faire, cliquez sur le menu **Démarrer** , puis sélectionnez **tous les programmes/Microsoft Visual Studio 2010/Visual Studio Tools/invite de commandes Visual Studio**. Une fenêtre de console s’affiche alors avec des variables d’environnement personnalisées.

2. À l’invite de commandes, utilisez la commande `cd` pour accéder au dossier de votre projet.

3. Générez un fichier de clé nommé MyControls.snk en exécutant la commande suivante.

    ```console
    Sn.exe -k MyControls.snk
    ```

4. Pour inclure le fichier de clé dans votre projet, cliquez avec le bouton droit sur le nom du projet dans Explorateur de solutions puis cliquez sur **Propriétés**. Dans le concepteur de projet, cliquez sur l’onglet **signature** , activez la case à cocher **signer l’assembly** , puis accédez à votre fichier de clé.

5. Générez la solution. La génération produira une DLL nommée MyControls.dll.

## <a name="implementing-the-wpf-host-application"></a>Implémentation de l’application hôte WPF
 L’application hôte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour héberger des `MyControl1`. L’application gère l’événement `OnButtonClick` pour recevoir les données du contrôle. Elle contient également une collection de cases d’option qui vous permettent de modifier certaines des propriétés du contrôle à partir de l’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L’illustration suivante montre l’application finale.

L’illustration suivante montre l’application complète, y compris le contrôle incorporé dans l’application WPF :

 ![Capture d’écran montrant un contrôle incorporé dans une page WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Création du projet
 Pour démarrer le projet :

1. Ouvrez Visual Studio, puis sélectionnez **nouveau projet**.

2. Dans la catégorie fenêtre, sélectionnez le modèle **application WPF** .

3. Nommez le nouveau projet `WpfHost`.

4. Pour l’emplacement, spécifiez le même dossier de premier niveau qui contient le projet MyControls.

5. Cliquez sur **OK** pour créer le projet.

 Vous devez également ajouter des références à la DLL qui contient `MyControl1` et d’autres assemblys.

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis sélectionnez **Ajouter une référence**.

2. Cliquez sur l’onglet **Parcourir** et accédez au dossier qui contient MyControls. dll. Pour cette procédure pas à pas, il s’agit du dossier MyControls\bin\Debug.

3. Sélectionnez MyControls. dll, puis cliquez sur **OK**.

4. Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration. dll.

### <a name="implementing-the-basic-layout"></a>Implémentation de la disposition de base
 L' [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l’application hôte est implémentée dans MainWindow. Xaml. Ce fichier contient [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage qui définit la disposition et héberge le contrôle Windows Forms. L’application est divisée en trois sections :

- Le panneau **Propriétés du contrôle** , qui contient une collection de cases d’option que vous pouvez utiliser pour modifier diverses propriétés du contrôle hébergé.

- Les **données du panneau de** configuration, qui contiennent plusieurs éléments <xref:System.Windows.Controls.TextBlock> qui affichent les données retournées par le contrôle hébergé.

- Le contrôle hébergé.

 La disposition de base est indiquée dans le XAML suivant. Le balisage nécessaire pour héberger `MyControl1` est omis dans cet exemple, mais il sera abordé plus tard.

 Remplacez le code XAML de MainWindow.xaml par le code suivant. Si vous utilisez Visual Basic, remplacez la classe par `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 Le premier élément <xref:System.Windows.Controls.StackPanel> contient plusieurs ensembles de contrôles <xref:System.Windows.Controls.RadioButton> qui vous permettent de modifier différentes propriétés par défaut du contrôle hébergé. Qui est suivi d’un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, qui héberge `MyControl1`. L’élément <xref:System.Windows.Controls.StackPanel> final contient plusieurs éléments <xref:System.Windows.Controls.TextBlock> qui affichent les données retournées par le contrôle hébergé. L’ordre des éléments et les paramètres d’attribut <xref:System.Windows.Controls.DockPanel.Dock%2A> et <xref:System.Windows.FrameworkElement.Height%2A> incorporent le contrôle hébergé dans la fenêtre sans espace ni distorsion.

#### <a name="hosting-the-control"></a>Hébergement du contrôle
 La version modifiée suivante du XAML précédent se concentre sur les éléments qui sont nécessaires pour héberger des `MyControl1`.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 L’attribut de mappage de l’espace de noms `xmlns` crée une référence à l’espace de noms `MyControls` qui contient le contrôle hébergé. Ce mappage vous permet de représenter `MyControl1` dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] comme `<mcl:MyControl1>`.

 Dans le code XAML, deux éléments gèrent l’hébergement :

- `WindowsFormsHost` représente l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> qui vous permet d’héberger un contrôle Windows Forms dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

- `mcl:MyControl1`, qui représente `MyControl1`, est ajouté à la collection enfant de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Par conséquent, ce Windows Forms contrôle est restitué dans le cadre de la fenêtre de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et vous pouvez communiquer avec le contrôle à partir de l’application.

### <a name="implementing-the-code-behind-file"></a>Implémentation du fichier code-behind
 Le fichier code-behind, MainWindow. Xaml. vb ou MainWindow.xaml.cs, contient le code procédural qui implémente les fonctionnalités du [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] abordé dans la section précédente. Les tâches principales sont les suivantes :

- Attachement d’un gestionnaire d’événements à l’événement `OnButtonClick` de `MyControl1`.

- Modification de diverses propriétés de `MyControl1`, en fonction de la façon dont la collection de cases d’option est définie.

- Affichage des données collectées par le contrôle

#### <a name="initializing-the-application"></a>Initialisation de l’application
 Le code d’initialisation est contenu dans un gestionnaire d’événements pour l’événement <xref:System.Windows.FrameworkElement.Loaded> de la fenêtre et attache un gestionnaire d’événements à l’événement `OnButtonClick` du contrôle.

 Dans MainWindow. Xaml. vb ou MainWindow.xaml.cs, ajoutez le code suivant à la classe `MainWindow`.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Étant donné que le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] abordé précédemment a ajouté des `MyControl1` à la collection d’éléments enfants de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, vous pouvez effectuer un cast de la <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour récupérer la référence à `MyControl1`. Vous pouvez ensuite utiliser cette référence pour attacher un gestionnaire d’événements à `OnButtonClick`.

 En plus de fournir une référence au contrôle lui-même, <xref:System.Windows.Forms.Integration.WindowsFormsHost> expose un certain nombre de propriétés du contrôle, que vous pouvez manipuler à partir de l’application. Le code d’initialisation affecte ces valeurs aux variables globales privées pour une utilisation ultérieure dans l’application.

 Pour que vous puissiez accéder facilement aux types dans la DLL `MyControls`, ajoutez l’instruction `Imports` ou `using` suivante au début du fichier.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>Gestion de l’événement OnButtonClick
 `MyControl1` déclenche l’événement `OnButtonClick` lorsque l’utilisateur clique sur l’un des boutons du contrôle.

 Ajoutez le code suivant à la classe `MainWindow` .

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Les données dans les zones de texte sont empaquetées dans l’objet `MyControlEventArgs`. Si l’utilisateur clique sur le bouton **OK** , le gestionnaire d’événements extrait les données et les affiche dans le panneau ci-dessous `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Modification des propriétés du contrôle
 L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> expose plusieurs propriétés par défaut du contrôle hébergé. Par conséquent, vous pouvez changer l’apparence du contrôle pour qu’elle corresponde davantage au style de votre application. Les ensembles de cases d’option du panneau gauche permettent à l’utilisateur de modifier plusieurs propriétés de couleur et de police. Chaque ensemble de boutons a un gestionnaire pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, qui détecte les sélections de cases d’option de l’utilisateur et modifie la propriété correspondante sur le contrôle.

 Ajoutez le code suivant à la classe `MainWindow` .

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Générez et exécutez l’application. Ajoutez du texte dans le contrôle composite Windows Forms, puis cliquez sur **OK**. Le texte s’affiche dans les étiquettes. Cliquez sur les différentes cases d’option pour voir l’effet du contrôle.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
