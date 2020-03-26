---
title: Hébergez un contrôle composite WPF dans windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 88efab8adf36989938ba5aa887a28b41eb8820f3
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291620"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Cependant, lorsque vous avez un investissement substantiel dans le code Windows Forms, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] il peut être plus efficace d’étendre votre application Windows Forms existante avec plutôt que de le réécrire à partir de zéro. Un scénario courant est lorsque vous souhaitez intégrer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un ou plusieurs contrôles implémentés avec dans votre application Windows Forms. Pour plus d’informations sur la personnalisation des contrôles WPF, voir [Personnalisation de contrôle](../controls/control-customization.md).  
  
 Ce pas à pas vous permet d’accéder à une application qui héberge un contrôle composite pour effectuer la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saisie des données dans une application Windows Forms. Le contrôle composite est empaqueté dans une DLL. Cette procédure générale peut être étendue à des applications et des contrôles plus complexes. Cette procédure pas à pas est conçue pour être presque identique en apparence et en fonctionnalité à Pas à [pas: Hébergement d’un contrôle composite windows Formes dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). La principale différence est que le scénario d’hébergement est inversé.  
  
 La procédure pas à pas est divisée en deux sections. La première section décrit brièvement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la mise en œuvre du contrôle composite. La deuxième section discute en détail de la façon d’héberger le contrôle composite dans une application Windows Forms, de recevoir des événements du contrôle et d’accéder à certaines propriétés du contrôle.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
- Implémentation du contrôle composite WPF  
  
- Implémentation de l’application hôte Windows Forms  
  
 Pour une liste complète du code des tâches illustrées dans cette procédure pas à pas, voir [Hébergement d’un contrôle composite WPF dans Windows Forms Sample](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Prérequis  

Cette procédure pas à pas nécessite Visual Studio.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implémentation du contrôle composite WPF  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle composite utilisé dans cet exemple est un simple formulaire d’entrée de données qui prend le nom et l’adresse de l’utilisateur. Lorsque l’utilisateur clique sur l’un des deux boutons pour indiquer que la tâche est terminée, le contrôle déclenche un événement personnalisé pour retourner ces informations à l’hôte. L’illustration suivante montre le rendu du contrôle.

 L’image suivante montre un contrôle composite WPF :

 ![Capture d’écran qui montre un simple contrôle WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Création du projet  
 Pour démarrer le projet :  
  
1. Lancez Visual Studio et ouvrez la boîte de dialogue **New Project.**  
  
2. Dans visual C et la catégorie Windows, sélectionnez le modèle **WPF User Control Library.**  
  
3. Nommez le nouveau projet `MyControls`.  
  
4. Pour l’emplacement, spécifiez un dossier `WindowsFormsHostingWpfControl`de haut niveau commodément nommé, tel que . Plus tard, vous placerez l’application hôte dans ce dossier.  
  
5. Cliquez sur **OK** pour créer le projet. Le projet par défaut `UserControl1`contient un seul contrôle nommé .  
  
6. Dans Solution Explorer, `UserControl1` renommez-vous pour `MyControl1`.  
  
 Votre projet doit comporter des références aux DLL système suivantes. Si l’une de ces DLL n’est pas incluse par défaut, ajoutez-la à votre projet.  
  
- PresentationCore  
  
- PresentationFramework  
  
- Système  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Création de l’interface utilisateur  
 Le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pour le contrôle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]composite est implémenté avec . Le contrôle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] composite <xref:System.Windows.Controls.TextBox> se compose de cinq éléments. Chaque <xref:System.Windows.Controls.TextBox> élément a <xref:System.Windows.Controls.TextBlock> un élément associé qui sert d’étiquette. Il ya <xref:System.Windows.Controls.Button> deux éléments en bas, **OK** et **Annuler**. Lorsque l’utilisateur clique sur l’un de ces boutons, le contrôle déclenche un événement personnalisé pour retourner les informations à l’hôte.  
  
#### <a name="basic-layout"></a>Disposition de base  
 Les [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] différents éléments sont <xref:System.Windows.Controls.Grid> contenus dans un élément. Vous pouvez <xref:System.Windows.Controls.Grid> utiliser pour organiser le contenu du contrôle composite `Table` de la même manière que vous utiliseriez un élément en HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a également <xref:System.Windows.Documents.Table> un <xref:System.Windows.Controls.Grid> élément, mais est plus léger et mieux adapté pour les tâches de mise en page simple.  
  
 Le code XAML suivant montre la disposition de base. Ce XAML définit la structure globale du contrôle en spécifiant <xref:System.Windows.Controls.Grid> le nombre de colonnes et de lignes dans l’élément.  
  
 Dans MyControl1.xaml, remplacez le code XAML existant par le code XAML suivant.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Ajout d’éléments TextBlock et TextBox à la grille  
 Vous placez un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] élément dans la <xref:System.Windows.Controls.Grid.RowProperty> grille <xref:System.Windows.Controls.Grid.ColumnProperty> en définissant l’élément et les attributs au numéro de ligne et de colonne approprié. N’oubliez pas que la numérotation des lignes et des colonnes est de base zéro. Vous pouvez avoir une portée d’élément plusieurs colonnes en définissant son <xref:System.Windows.Controls.Grid.ColumnSpanProperty> attribut. Pour plus <xref:System.Windows.Controls.Grid> d’informations sur les éléments, voir [Créer un élément de grille](../controls/how-to-create-a-grid-element.md).  
  
 Le XAML suivant montre le <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBlock> contrôle composite <xref:System.Windows.Controls.Grid.RowProperty> <xref:System.Windows.Controls.Grid.ColumnProperty> et les éléments avec leurs attributs et leurs attributs, qui sont réglés pour placer les éléments correctement dans la grille.  
  
 Dans MyControl1.xaml, ajoutez le XAML suivant dans l’élément. <xref:System.Windows.Controls.Grid>  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Styles des éléments d’interface utilisateur  
 De nombreux éléments du formulaire de saisie de données ont une apparence semblable, ce qui signifie qu’ils ont des paramètres identiques pour plusieurs de leurs propriétés. Plutôt que de définir les attributs de chaque élément <xref:System.Windows.Style> séparément, le précédent XAML utilise des éléments pour définir les paramètres de propriété standard pour les classes d’éléments. Cette approche réduit la complexité du contrôle et permet de modifier l’apparence de plusieurs éléments via un même attribut de style.  
  
 Les <xref:System.Windows.Style> éléments sont <xref:System.Windows.Controls.Grid> contenus <xref:System.Windows.FrameworkElement.Resources%2A> dans la propriété de l’élément, de sorte qu’ils peuvent être utilisés par tous les éléments dans le contrôle. Si un style est nommé, vous l’appliquez à un élément en ajoutant un <xref:System.Windows.Style> élément au nom du style. Les styles qui ne sont pas nommés deviennent le style par défaut de l’élément. Pour plus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’informations sur les styles, voir [Styling et Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Le XAML suivant <xref:System.Windows.Style> montre les éléments pour le contrôle composite. Pour voir comment les styles sont appliqués aux éléments, reportez-vous au code XAML précédent. Par exemple, <xref:System.Windows.Controls.TextBlock> le dernier `inlineText` élément a <xref:System.Windows.Controls.TextBox> le style, et le dernier élément utilise le style par défaut.  
  
 Dans MyControl1.xaml, ajoutez le XAML <xref:System.Windows.Controls.Grid> suivant juste après l’élément de départ.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Ajout des boutons OK et Annuler  
 Les derniers éléments sur le contrôle composite sont les éléments **OK** et **Cancel,** <xref:System.Windows.Controls.Button> qui occupent les deux premières colonnes de la dernière rangée de la <xref:System.Windows.Controls.Grid>. Ces éléments utilisent un `ButtonClicked`gestionnaire d’événements commun, et le style par défaut <xref:System.Windows.Controls.Button> défini dans le XAML précédent.  
  
 Dans MyControl1.xaml, ajoutez le XAML <xref:System.Windows.Controls.TextBox> suivant après le dernier élément. La [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] partie du contrôle composite est maintenant terminée.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implémentation du fichier code-behind  
 Le fichier de code,MyControl1.xaml.cs, implémente trois tâches essentielles :
  
1. La gestion de l’événement qui se produit lorsque l’utilisateur clique sur l’un des boutons  
  
2. Récupère les données <xref:System.Windows.Controls.TextBox> des éléments et les emballe dans un objet d’argument d’événement personnalisé.  
  
3. Soulève l’événement personnalisé, `OnButtonClick` qui informe l’hôte que l’utilisateur est fini et transmet les données à l’hôte.  
  
 Le contrôle expose également plusieurs propriétés de couleur et de police qui vous permettent de modifier l’apparence. Contrairement <xref:System.Windows.Forms.Integration.WindowsFormsHost> à la classe, qui est utilisée <xref:System.Windows.Forms.Integration.ElementHost> pour héberger un <xref:System.Windows.Controls.Panel.Background%2A> contrôle Windows Forms, la classe expose la propriété du contrôle seulement. Pour maintenir la similitude entre cet exemple de code et l’exemple discuté dans [Pas à pas : Héberger un contrôle composite windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), le contrôle expose directement les propriétés restantes.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Structure de base du fichier code-behind  
 Le fichier de code-derrière se `MyControls`compose d’un seul `MyControl1` `MyControlEventArgs`namespace, , qui contiendra deux classes, et .  
  
```csharp  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
```  
  
 La première `MyControl1`classe, , est une classe partielle contenant le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] code qui implémente la fonctionnalité de la définie dans MyControl1.xaml. Lorsque MyControl1.xaml est analysé, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] le est converti à la même classe partielle, et les deux classes partielles sont fusionnées pour former le contrôle compilé. Pour cette raison, le nom de classe du fichier code-behind doit correspondre à celui assigné à MyControl1.xaml, et il doit hériter de l’élément racine du contrôle. La deuxième `MyControlEventArgs`classe, , est une classe d’arguments événementiel qui est utilisé pour renvoyer les données à l’hôte.  
  
 Ouvrez MyControl1.xaml.cs. Modifier la déclaration de classe existante de sorte <xref:System.Windows.Controls.Grid>qu’il a le nom suivant et hérite de .  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Initialisation du contrôle  
 Le code suivant implémente plusieurs tâches de base :  
  
- Déclare un événement `OnButtonClick`privé, , et `MyControlEventHandler`son délégué associé, .  
  
- Crée plusieurs variables globales privées qui stockent les données de l’utilisateur. Ces données sont exposées via les propriétés correspondantes.  
  
- Implémente `Init`un gestionnaire, pour <xref:System.Windows.FrameworkElement.Loaded> l’événement du contrôle. Ce gestionnaire initialise les variables globales en leur assignant les valeurs définies dans MyControl1.xaml. Pour ce faire, <xref:System.Windows.FrameworkElement.Name%2A> il utilise <xref:System.Windows.Controls.TextBlock> l’attribué à un élément typique, `nameLabel`, pour accéder aux paramètres de propriété de cet élément.  
  
 Supprimez le constructeur existant et ajoutez `MyControl1` le code suivant à votre classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Gestion des événements de clic de bouton  
 L’utilisateur indique que la tâche d’entrée de données est terminée en cliquant soit sur le bouton **OK,** soit sur le bouton **Annuler.** Les deux boutons <xref:System.Windows.Controls.Primitives.ButtonBase.Click> utilisent le `ButtonClicked`même gestionnaire d’événement, . Les deux boutons ont `btnOK` `btnCancel`un nom, ou , qui permet au gestionnaire de `sender` déterminer quel bouton a été cliqué en examinant la valeur de l’argument. Le gestionnaire fait ce qui suit :  
  
- Crée `MyControlEventArgs` un objet qui contient <xref:System.Windows.Controls.TextBox> les données des éléments.  
  
- Si l’utilisateur a cliqué `MyControlEventArgs` sur `IsOK` le `false`bouton **Annuler,** définit la propriété de l’objet vers .  
  
- Soulève `OnButtonClick` l’événement pour indiquer à l’hôte que l’utilisateur est terminé, et transmet les données collectées.  
  
 Ajoutez le code `MyControl1` suivant à `Init` votre classe, après la méthode.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Création de propriétés  
 Le reste de la classe expose simplement les propriétés qui correspondent aux variables globales décrites précédemment. Lorsqu’une propriété change, le setter modifie l’apparence du contrôle en modifiant les propriétés de l’élément correspondant et en mettant à jour les variables globales sous-jacentes.  
  
 Ajoutez le code `MyControl1` suivant à votre classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Renvoi des données à l’hôte  
 Le dernier élément du `MyControlEventArgs` fichier est la classe, qui est utilisée pour renvoyer les données collectées à l’hôte.  
  
 Ajoutez le code `MyControls` suivant à votre espace de nom. L’implémentation est simple et n’est donc pas davantage expliquée.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Générez la solution. La génération produira une DLL nommée MyControls.dll.  
  
<a name="winforms_host_section"></a>
## <a name="implementing-the-windows-forms-host-application"></a>Implémentation de l’application hôte Windows Forms  
 L’application d’hôte <xref:System.Windows.Forms.Integration.ElementHost> Windows Forms [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise un objet pour héberger le contrôle composite. L’application gère `OnButtonClick` l’événement pour recevoir les données du contrôle composite. L’application dispose également d’un ensemble de boutons d’option que vous pouvez utiliser pour modifier l’apparence du contrôle. L’illustration suivante présente l’application.  

L’image suivante montre un contrôle composite WPF hébergé dans une application Windows Forms"  

 ![Capture d’écran qui montre un formulaire Windows Hébergeant le contrôle Avalon.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Création du projet  
 Pour démarrer le projet :  
  
1. Lancez Visual Studio et ouvrez la boîte de dialogue **New Project.**  
  
2. Dans la catégorie Visual C et Windows, sélectionnez le modèle **d’application des formulaires Windows.**  
  
3. Nommez le nouveau projet `WFHost`.  
  
4. Pour l’emplacement, spécifiez le même dossier de premier niveau qui contient le projet MyControls.  
  
5. Cliquez sur **OK** pour créer le projet.  
  
 Vous devez également ajouter des références `MyControl1` à la DLL qui contient et d’autres assemblages.  
  
1. Cliquez à droite sur le nom du projet dans Solution Explorer, et sélectionnez **Ajouter référence**.  
  
2. Cliquez sur l’onglet **Parcourir,** et naviguez vers le dossier qui contient MyControls.dll. Pour cette procédure pas à pas, il s’agit du dossier MyControls\bin\Debug.  
  
3. Sélectionnez MyControls.dll, puis cliquez **sur OK**.  
  
4. Ajoutez les références aux assemblys suivants.  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - System.Xaml  
  
    - WindowsBase  
  
    - WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implémentation de l’interface utilisateur de l’application  
 L’interface utilisateur de l’application Windows Forms contient plusieurs contrôles permettant d’interagir avec le contrôle composite WPF.  
  
1. Ouvrez Form1 dans le Concepteur Windows Forms.  
  
2. Agrandissez le formulaire pour qu’il puisse contenir tous les contrôles.  
  
3. Dans le coin supérieur droit de <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> la forme, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ajoutez un contrôle pour maintenir le contrôle composite.  
  
4. Ajoutez les <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> commandes suivantes au formulaire.  
  
    |Nom|Texte|  
    |----------|----------|  
    |groupBox1|Couleur d’arrière-plan|  
    |groupBox2|Couleur de premier plan|  
    |groupBox3|Taille de police|  
    |groupBox4|Famille de polices|  
    |groupBox5|Style|  
    |groupBox6|Épaisseur de police|  
    |groupBox7|Données du contrôle|  
  
5. Ajoutez les <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> commandes <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> suivantes aux commandes.  
  
    |GroupBox|Nom|Texte|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Original|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|Original|  
    |groupBox2|radioForegroundRed|Rouge|  
    |groupBox2|radioForegroundYellow|Jaune|  
    |groupBox3|radioSizeOriginal|Original|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Original|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normal|  
    |groupBox5|radioStyleItalic|Italique|  
    |groupBox6|radioWeightOriginal|Original|  
    |groupBox6|radioWeightBold|Gras|  
  
6. Ajouter les <xref:System.Windows.Forms.Label?displayProperty=nameWithType> commandes suivantes <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>à la dernière . Ces contrôles affichent les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] données retournées par le contrôle composite.  
  
    |GroupBox|Nom|Texte|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nom :|  
    |groupBox7|lblAddress|Adresse :|  
    |groupBox7|lblCity|Ville :|  
    |groupBox7|lblState|État :|  
    |groupBox7|lblZip|Code postal :|  
  
### <a name="initializing-the-form"></a>Initialisation du formulaire  
 Vous implémentez généralement le <xref:System.Windows.Forms.Form.Load> code d’hébergement dans le gestionnaire d’événement du formulaire. Le code suivant <xref:System.Windows.Forms.Form.Load> montre le gestionnaire [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’événements, <xref:System.Windows.FrameworkElement.Loaded> un gestionnaire pour l’événement du contrôle composite, et des déclarations pour plusieurs variables globales qui sont utilisées plus tard.  
  
 Dans le concepteur de formulaires Windows, <xref:System.Windows.Forms.Form.Load> cliquez deux fois sur le formulaire pour créer un gestionnaire d’événements. Au sommet de Form1.cs, ajoutez les `using` déclarations suivantes.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Remplacez le contenu `Form1` de la classe existante par le code suivant.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 La `Form1_Load` méthode du code précédent montre la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procédure générale d’hébergement d’un contrôle :  
  
1. Créez un objet <xref:System.Windows.Forms.Integration.ElementHost>.  
  
2. Définissez la <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>du contrôle à .  
  
3. Ajoutez <xref:System.Windows.Forms.Integration.ElementHost> le contrôle <xref:System.Windows.Forms.Panel> à <xref:System.Windows.Forms.Control.Controls%2A> la collection du contrôle.  
  
4. Créez une instance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du contrôle.  
  
5. Hébergez le contrôle composite sur le formulaire <xref:System.Windows.Forms.Integration.ElementHost> en <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> attribuant le contrôle à la propriété du contrôle.  
  
 Les deux autres `Form1_Load` lignes de la méthode attachent les gestionnaires à deux événements de contrôle :  
  
- `OnButtonClick`est un événement personnalisé qui est tiré par le contrôle composite lorsque l’utilisateur clique sur le bouton **OK** ou **Annuler.** Vous gérez l’événement pour obtenir la réponse de l’utilisateur et pour collecter les données spécifiées par l’utilisateur.  
  
- <xref:System.Windows.FrameworkElement.Loaded>est un événement standard qui [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est soulevé par un contrôle quand il est entièrement chargé. L’événement est utilisé ici, parce que l’exemple doit initialiser plusieurs variables globales à l’aide de propriétés du contrôle. Au moment de l’événement du <xref:System.Windows.Forms.Form.Load> formulaire, le contrôle n’est `null`pas entièrement chargé et ces valeurs sont toujours définies à . Vous devez attendre jusqu’à <xref:System.Windows.FrameworkElement.Loaded> ce que l’événement du contrôle se produise avant de pouvoir accéder à ces propriétés.  
  
 Le <xref:System.Windows.FrameworkElement.Loaded> gestionnaire d’événements est indiqué dans le code précédent. Le `OnButtonClick` gestionnaire est discuté dans la section suivante.  
  
### <a name="handling-onbuttonclick"></a>Handling OnButtonClick  
 L’événement `OnButtonClick` se produit lorsque l’utilisateur clique sur le bouton **OK** ou **Annuler.**  
  
 Le gestionnaire de l’événement `IsOK` vérifie le champ de l’argument de l’événement pour déterminer quel bouton a été cliqué. Les `lbl`variables *de* <xref:System.Windows.Forms.Label> données correspondent aux contrôles qui ont été discutés plus tôt. Si l’utilisateur clique sur le bouton **OK,** les données des contrôles du <xref:System.Windows.Controls.TextBox> contrôle sont attribuées au contrôle correspondant. <xref:System.Windows.Forms.Label> Si l’utilisateur **Cancel**clique <xref:System.Windows.Forms.Label.Text%2A> Annuler , les valeurs sont définies aux chaînes par défaut.  
  
 Ajoutez le code de gestionnaire `Form1` d’événements suivant à la classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Générez et exécutez l’application. Ajouter un peu de texte dans le contrôle composite WPF, puis cliquez **sur OK**. Le texte s’affiche dans les étiquettes. À ce stade, le code n’a pas été ajouté pour gérer les cases d’option.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modification de l’apparence du contrôle  
 Les <xref:System.Windows.Forms.RadioButton> contrôles sur le formulaire permettront [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’utilisateur de changer les couleurs de premier plan et de fond du contrôle composite ainsi que plusieurs propriétés de police. La couleur de fond <xref:System.Windows.Forms.Integration.ElementHost> est exposée par l’objet. Les propriétés restantes sont exposées comme des propriétés personnalisées du contrôle.  
  
 Double-cliquez <xref:System.Windows.Forms.RadioButton> sur chaque contrôle <xref:System.Windows.Forms.RadioButton.CheckedChanged> sur le formulaire pour créer des gestionnaires d’événements. Remplacez <xref:System.Windows.Forms.RadioButton.CheckedChanged> les gestionnaires d’événements par le code suivant.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Générez et exécutez l’application. Cliquez sur les différentes cases d’option pour voir l’effet du contrôle composite WPF.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Procédure pas à pas : hébergement d’un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d’un contrôle composite WPF 3D dans les formulaires Windows](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
