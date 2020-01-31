---
title: Héberger un contrôle composite WPF dans Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 05ba8120c90175801aa2cb61499c48133853e8f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794168"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous investissez dans Windows Forms code, il peut être plus efficace d’étendre votre application Windows Forms existante avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plutôt que de la réécrire à partir de zéro. Un scénario courant est lorsque vous souhaitez incorporer un ou plusieurs contrôles implémentés avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans votre application Windows Forms. Pour plus d’informations sur la personnalisation des contrôles WPF, consultez [personnalisation](../controls/control-customization.md)des contrôles.  
  
 Cette procédure pas à pas vous guide à travers une application qui héberge un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle composite pour effectuer une entrée de données dans une application Windows Forms. Le contrôle composite est empaqueté dans une DLL. Cette procédure générale peut être étendue à des applications et des contrôles plus complexes. Cette procédure pas à pas est conçue pour être quasiment identique dans l’apparence et les fonctionnalités de la [procédure pas à pas : Hébergement d’un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). La principale différence est que le scénario d’hébergement est inversé.  
  
 La procédure pas à pas est divisée en deux sections. La première section décrit brièvement l’implémentation du contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. La deuxième section explique en détail comment héberger le contrôle composite dans une application Windows Forms, recevoir des événements du contrôle et accéder à certaines propriétés du contrôle.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
- Implémentation du contrôle composite WPF  
  
- Implémentation de l’application hôte Windows Forms  
  
 Pour obtenir la liste du code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle composite WPF dans Windows Forms exemple](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Prerequisites  

Cette procédure pas à pas nécessite Visual Studio.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implémentation du contrôle composite WPF  
 Le contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisé dans cet exemple est un formulaire de saisie de données simple qui prend le nom et l’adresse de l’utilisateur. Lorsque l’utilisateur clique sur l’un des deux boutons pour indiquer que la tâche est terminée, le contrôle déclenche un événement personnalisé pour retourner ces informations à l’hôte. L’illustration suivante montre le rendu du contrôle. 

 L’illustration suivante montre un contrôle composite WPF : 

 ![Capture d’écran montrant un contrôle WPF simple.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Création du projet  
 Pour démarrer le projet :  
  
1. Lancez Visual Studio, puis ouvrez la boîte de dialogue **nouveau projet** .  
  
2. Dans Visual C# et la catégorie Windows, sélectionnez le modèle **bibliothèque de contrôles utilisateur WPF** .  
  
3. Nommez le nouveau projet `MyControls`.  
  
4. Pour l’emplacement, spécifiez un dossier de niveau supérieur, tel que `WindowsFormsHostingWpfControl`. Plus tard, vous placerez l’application hôte dans ce dossier.  
  
5. Cliquez sur **OK** pour créer le projet. Le projet par défaut contient un seul contrôle nommé `UserControl1`.  
  
6. Dans Explorateur de solutions, renommez `UserControl1` en `MyControl1`.  
  
 Votre projet doit comporter des références aux DLL système suivantes. Si l’une de ces DLL n’est pas incluse par défaut, ajoutez-la à votre projet.  
  
- PresentationCore  
  
- PresentationFramework  
  
- System  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Création de l’interface utilisateur  
 La [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pour le contrôle composite est implémentée avec [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de contrôle composite se compose de cinq éléments <xref:System.Windows.Controls.TextBox>. Chaque élément <xref:System.Windows.Controls.TextBox> est associé à un élément <xref:System.Windows.Controls.TextBlock> qui sert d’étiquette. Il y a deux éléments <xref:System.Windows.Controls.Button> en bas, **OK** et **Annuler**. Lorsque l’utilisateur clique sur l’un de ces boutons, le contrôle déclenche un événement personnalisé pour retourner les informations à l’hôte.  
  
#### <a name="basic-layout"></a>Disposition de base  
 Les différents éléments de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sont contenus dans un élément <xref:System.Windows.Controls.Grid>. Vous pouvez utiliser <xref:System.Windows.Controls.Grid> pour réorganiser le contenu du contrôle composite à peu près de la même façon que vous utiliseriez un élément `Table` en HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a également un élément <xref:System.Windows.Documents.Table>, mais <xref:System.Windows.Controls.Grid> est plus léger et mieux adapté aux tâches de disposition simples.  
  
 Le code XAML suivant montre la disposition de base. Ce code XAML définit la structure globale du contrôle en spécifiant le nombre de colonnes et de lignes dans l’élément <xref:System.Windows.Controls.Grid>.  
  
 Dans MyControl1.xaml, remplacez le code XAML existant par le code XAML suivant.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Ajout d’éléments TextBlock et TextBox à la grille  
 Vous placez un élément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans la grille en affectant aux attributs <xref:System.Windows.Controls.Grid.RowProperty> et <xref:System.Windows.Controls.Grid.ColumnProperty> de l’élément le numéro de ligne et de colonne approprié. N’oubliez pas que la numérotation des lignes et des colonnes est de base zéro. Vous pouvez avoir un élément qui s’étend sur plusieurs colonnes en définissant son attribut <xref:System.Windows.Controls.Grid.ColumnSpanProperty>. Pour plus d’informations sur les éléments de <xref:System.Windows.Controls.Grid>, consultez [créer un élément Grid](../controls/how-to-create-a-grid-element.md).  
  
 Le code XAML suivant montre les éléments <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.TextBlock> du contrôle composite avec leurs attributs <xref:System.Windows.Controls.Grid.RowProperty> et <xref:System.Windows.Controls.Grid.ColumnProperty>, qui sont définis pour placer correctement les éléments dans la grille.  
  
 Dans MyControl1. xaml, ajoutez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Styles des éléments d’interface utilisateur  
 De nombreux éléments du formulaire de saisie de données ont une apparence semblable, ce qui signifie qu’ils ont des paramètres identiques pour plusieurs de leurs propriétés. Au lieu de définir séparément les attributs de chaque élément, le code XAML précédent utilise <xref:System.Windows.Style> éléments pour définir des paramètres de propriété standard pour les classes d’éléments. Cette approche réduit la complexité du contrôle et permet de modifier l’apparence de plusieurs éléments via un même attribut de style.  
  
 Les éléments <xref:System.Windows.Style> sont contenus dans la propriété <xref:System.Windows.FrameworkElement.Resources%2A> de l’élément <xref:System.Windows.Controls.Grid>, de sorte qu’ils peuvent être utilisés par tous les éléments du contrôle. Si un style est nommé, vous l’appliquez à un élément en ajoutant un <xref:System.Windows.Style> élément défini sur le nom du style. Les styles qui ne sont pas nommés deviennent le style par défaut de l’élément. Pour plus d’informations sur les styles de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Le code XAML suivant montre les éléments de <xref:System.Windows.Style> pour le contrôle composite. Pour voir comment les styles sont appliqués aux éléments, reportez-vous au code XAML précédent. Par exemple, le dernier élément <xref:System.Windows.Controls.TextBlock> a le style `inlineText` et le dernier élément <xref:System.Windows.Controls.TextBox> utilise le style par défaut.  
  
 Dans MyControl1. xaml, ajoutez le code XAML suivant juste après l’élément de début <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Ajout des boutons OK et Annuler  
 Les éléments finaux sur le contrôle composite sont les éléments **OK** et **Cancel**<xref:System.Windows.Controls.Button>, qui occupent les deux premières colonnes de la dernière ligne du <xref:System.Windows.Controls.Grid>. Ces éléments utilisent un gestionnaire d’événements communs, `ButtonClicked`et le style de <xref:System.Windows.Controls.Button> par défaut défini dans le XAML précédent.  
  
 Dans MyControl1. xaml, ajoutez le code XAML suivant après le dernier élément <xref:System.Windows.Controls.TextBox>. La [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] partie du contrôle composite est maintenant terminée.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implémentation du fichier code-behind  
 Le fichier code-behind, MyControl1.xaml.cs, implémente trois tâches essentielles :
  
1. La gestion de l’événement qui se produit lorsque l’utilisateur clique sur l’un des boutons  
  
2. Récupère les données des éléments de <xref:System.Windows.Controls.TextBox> et les empaquette dans un objet d’argument d’événement personnalisé.  
  
3. Déclenche l’événement de `OnButtonClick` personnalisé, qui avertit l’hôte que l’utilisateur a terminé et transmet les données à l’hôte.  
  
 Le contrôle expose également plusieurs propriétés de couleur et de police qui vous permettent de modifier l’apparence. Contrairement à la classe <xref:System.Windows.Forms.Integration.WindowsFormsHost>, qui est utilisée pour héberger un contrôle Windows Forms, la classe <xref:System.Windows.Forms.Integration.ElementHost> expose uniquement la propriété <xref:System.Windows.Controls.Panel.Background%2A> du contrôle. Pour maintenir la similarité entre cet exemple de code et l’exemple abordé dans [procédure pas à pas : Hébergement d’un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), le contrôle expose directement les propriétés restantes.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Structure de base du fichier code-behind  
 Le fichier code-behind se compose d’un espace de noms unique, `MyControls`, qui contient deux classes, `MyControl1` et `MyControlEventArgs`.  
  
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
  
 La première classe, `MyControl1`, est une classe partielle contenant le code qui implémente les fonctionnalités de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] définie dans MyControl1. Xaml. Lorsque MyControl1. xaml est analysé, le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est converti en la même classe partielle, et les deux classes partielles sont fusionnées pour former le contrôle compilé. Pour cette raison, le nom de classe du fichier code-behind doit correspondre à celui assigné à MyControl1.xaml, et il doit hériter de l’élément racine du contrôle. La deuxième classe, `MyControlEventArgs`, est une classe d’arguments d’événement qui est utilisée pour renvoyer les données à l’hôte.  
  
 Ouvrez MyControl1.xaml.cs. Modifiez la déclaration de classe existante afin qu’elle porte le nom suivant et hérite de <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Initialisation du contrôle  
 Le code suivant implémente plusieurs tâches de base :  
  
- Déclare un événement privé, `OnButtonClick`et son délégué associé, `MyControlEventHandler`.  
  
- Crée plusieurs variables globales privées qui stockent les données de l’utilisateur. Ces données sont exposées via les propriétés correspondantes.  
  
- Implémente un gestionnaire, `Init`, pour l’événement <xref:System.Windows.FrameworkElement.Loaded> du contrôle. Ce gestionnaire initialise les variables globales en leur assignant les valeurs définies dans MyControl1.xaml. Pour ce faire, il utilise la <xref:System.Windows.FrameworkElement.Name%2A> affectée à un élément de <xref:System.Windows.Controls.TextBlock> typique, `nameLabel`, pour accéder aux paramètres de propriété de cet élément.  
  
 Supprimez le constructeur existant et ajoutez le code suivant à votre classe `MyControl1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Gestion des événements de clic de bouton  
 L’utilisateur indique que la tâche de saisie de données est terminée en cliquant sur le bouton **OK** ou sur le bouton **Annuler** . Les deux boutons utilisent le même <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gestionnaire d’événements, `ButtonClicked`. Les deux boutons ont un nom, `btnOK` ou `btnCancel`, qui permet au gestionnaire de déterminer le bouton sur lequel l’utilisateur a cliqué en examinant la valeur de l’argument `sender`. Le gestionnaire fait ce qui suit :  
  
- Crée un objet `MyControlEventArgs` qui contient les données à partir des éléments <xref:System.Windows.Controls.TextBox>.  
  
- Si l’utilisateur a cliqué sur le bouton **Annuler** , affecte à la propriété `IsOK` de l’objet `MyControlEventArgs` la valeur `false`.  
  
- Déclenche l’événement `OnButtonClick` pour indiquer à l’hôte que l’utilisateur a terminé et passe les données collectées.  
  
 Ajoutez le code suivant à votre classe `MyControl1`, après la méthode `Init`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Création de propriétés  
 Le reste de la classe expose simplement les propriétés qui correspondent aux variables globales décrites précédemment. Lorsqu’une propriété change, le setter modifie l’apparence du contrôle en modifiant les propriétés de l’élément correspondant et en mettant à jour les variables globales sous-jacentes.  
  
 Ajoutez le code suivant à votre classe `MyControl1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Renvoi des données à l’hôte  
 Le dernier composant du fichier est la classe `MyControlEventArgs`, qui est utilisée pour renvoyer les données collectées à l’hôte.  
  
 Ajoutez le code suivant à votre espace de noms `MyControls`. L’implémentation est simple et n’est donc pas davantage expliquée.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Générez la solution. La génération produira une DLL nommée MyControls.dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implémentation de l’application hôte Windows Forms  
 L’application hôte Windows Forms utilise un objet <xref:System.Windows.Forms.Integration.ElementHost> pour héberger le contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L’application gère l’événement `OnButtonClick` pour recevoir les données du contrôle composite. L’application comprend également un ensemble de cases d’option que vous pouvez utiliser pour modifier l’apparence du contrôle. L’illustration suivante présente l’application.  

L’illustration suivante montre un contrôle composite WPF hébergé dans une application Windows Forms»  

 ![Scteenshot qui affiche un contrôle Windows Form hébergeant Avalon.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Création du projet  
 Pour démarrer le projet :  
  
1. Lancez Visual Studio, puis ouvrez la boîte de dialogue **nouveau projet** .  
  
2. Dans Visual C# et la catégorie Windows, sélectionnez le modèle d' **application Windows Forms** .  
  
3. Nommez le nouveau projet `WFHost`.  
  
4. Pour l’emplacement, spécifiez le même dossier de premier niveau qui contient le projet MyControls.  
  
5. Cliquez sur **OK** pour créer le projet.  
  
 Vous devez également ajouter des références à la DLL qui contient `MyControl1` et d’autres assemblys.  
  
1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis sélectionnez **Ajouter une référence**.  
  
2. Cliquez sur l’onglet **Parcourir** et accédez au dossier qui contient MyControls. dll. Pour cette procédure pas à pas, il s’agit du dossier MyControls\bin\Debug.  
  
3. Sélectionnez MyControls. dll, puis cliquez sur **OK**.  
  
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
  
3. Dans l’angle supérieur droit du formulaire, ajoutez un contrôle <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> pour contenir le contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
4. Ajoutez les contrôles <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> suivants au formulaire.  
  
    |Name|Text|  
    |----------|----------|  
    |groupBox1|Background Color|  
    |groupBox2|Couleur de premier plan|  
    |groupBox3|Font Size|  
    |groupBox4|Famille de polices|  
    |groupBox5|Font Style|  
    |groupBox6|Épaisseur de police|  
    |groupBox7|Données du contrôle|  
  
5. Ajoutez les contrôles <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> suivants aux contrôles <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>.  
  
    |GroupBox|Name|Text|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|D'origine|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|D'origine|  
    |groupBox2|radioForegroundRed|Rouge|  
    |groupBox2|radioForegroundYellow|Jaune|  
    |groupBox3|radioSizeOriginal|D'origine|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|D'origine|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normale|  
    |groupBox5|radioStyleItalic|Caractères italiques|  
    |groupBox6|radioWeightOriginal|D'origine|  
    |groupBox6|radioWeightBold|Gras|  
  
6. Ajoutez les contrôles <xref:System.Windows.Forms.Label?displayProperty=nameWithType> suivants au dernier <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Ces contrôles affichent les données retournées par le contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    |GroupBox|Name|Text|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nom :|  
    |groupBox7|lblAddress|Adresse :|  
    |groupBox7|lblCity|Ville :|  
    |groupBox7|lblState|État :|  
    |groupBox7|lblZip|Code postal :|  
  
### <a name="initializing-the-form"></a>Initialisation du formulaire  
 En général, vous implémentez le code d’hébergement dans le gestionnaire d’événements <xref:System.Windows.Forms.Form.Load> du formulaire. Le code suivant illustre le gestionnaire d’événements <xref:System.Windows.Forms.Form.Load>, un gestionnaire pour l’événement <xref:System.Windows.FrameworkElement.Loaded> du contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des déclarations pour plusieurs variables globales qui sont utilisées ultérieurement.  
  
 Dans la Concepteur Windows Forms, double-cliquez sur le formulaire pour créer un gestionnaire d’événements <xref:System.Windows.Forms.Form.Load>. En haut de Form1.cs, ajoutez les instructions `using` suivantes.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Remplacez le contenu de la classe de `Form1` existante par le code suivant.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 La méthode `Form1_Load` dans le code précédent montre la procédure générale pour l’hébergement d’un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
1. Créez un objet de <xref:System.Windows.Forms.Integration.ElementHost>.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle la valeur <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3. Ajoutez le contrôle <xref:System.Windows.Forms.Integration.ElementHost> à la collection de <xref:System.Windows.Forms.Control.Controls%2A> du contrôle <xref:System.Windows.Forms.Panel>.  
  
4. Créez une instance du contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
5. Hébergez le contrôle composite sur le formulaire en assignant le contrôle à la propriété <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  
  
 Les deux lignes restantes de la méthode `Form1_Load` attachent des gestionnaires à deux événements de contrôle :  
  
- `OnButtonClick` est un événement personnalisé déclenché par le contrôle composite lorsque l’utilisateur clique sur le bouton **OK** ou **Annuler** . Vous gérez l’événement pour obtenir la réponse de l’utilisateur et pour collecter les données spécifiées par l’utilisateur.  
  
- <xref:System.Windows.FrameworkElement.Loaded> est un événement standard déclenché par un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lorsqu’il est entièrement chargé. L’événement est utilisé ici, parce que l’exemple doit initialiser plusieurs variables globales à l’aide de propriétés du contrôle. Au moment de l’événement <xref:System.Windows.Forms.Form.Load> du formulaire, le contrôle n’est pas entièrement chargé et ces valeurs sont toujours définies sur `null`. Vous devez attendre que l’événement <xref:System.Windows.FrameworkElement.Loaded> du contrôle se produise avant de pouvoir accéder à ces propriétés.  
  
 Le gestionnaire d’événements <xref:System.Windows.FrameworkElement.Loaded> est illustré dans le code précédent. Le gestionnaire de `OnButtonClick` est abordé dans la section suivante.  
  
### <a name="handling-onbuttonclick"></a>Handling OnButtonClick  
 L’événement `OnButtonClick` se produit lorsque l’utilisateur clique sur le bouton **OK** ou **Annuler** .  
  
 Le gestionnaire d’événements vérifie le champ `IsOK` de l’argument d’événement pour déterminer le bouton sur lequel l’utilisateur a cliqué. Les variables de *données* `lbl`correspondent aux contrôles <xref:System.Windows.Forms.Label> abordés précédemment. Si l’utilisateur clique sur le bouton **OK** , les données des contrôles de <xref:System.Windows.Controls.TextBox> du contrôle sont assignées au contrôle <xref:System.Windows.Forms.Label> correspondant. Si l’utilisateur clique sur **Annuler**, les valeurs de <xref:System.Windows.Forms.Label.Text%2A> sont définies sur les chaînes par défaut.  
  
 Ajoutez le code du gestionnaire d’événements Click du bouton suivant à la classe `Form1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Générez et exécutez l’application. Ajoutez du texte dans le contrôle composite WPF, puis cliquez sur **OK**. Le texte s’affiche dans les étiquettes. À ce stade, le code n’a pas été ajouté pour gérer les cases d’option.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modification de l’apparence du contrôle  
 Les contrôles <xref:System.Windows.Forms.RadioButton> du formulaire permettent à l’utilisateur de modifier les couleurs de premier plan et d’arrière-plan du contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ainsi que plusieurs propriétés de police. La couleur d’arrière-plan est exposée par l’objet <xref:System.Windows.Forms.Integration.ElementHost>. Les propriétés restantes sont exposées comme des propriétés personnalisées du contrôle.  
  
 Double-cliquez sur chaque contrôle <xref:System.Windows.Forms.RadioButton> du formulaire pour créer des gestionnaires d’événements <xref:System.Windows.Forms.RadioButton.CheckedChanged>. Remplacez les gestionnaires d’événements <xref:System.Windows.Forms.RadioButton.CheckedChanged> par le code suivant.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Générez et exécutez l’application. Cliquez sur les différentes cases d’option pour voir l’effet du contrôle composite WPF.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : hébergement d’un contrôle composite 3-D WPF dans les Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
