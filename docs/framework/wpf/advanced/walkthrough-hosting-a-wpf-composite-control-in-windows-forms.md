---
title: 'Procédure pas à pas : hébergement d’un contrôle composite WPF dans Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: bff89f1d81b16c8c66d73901ef951626f6d2cb9e
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400623"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Procédure pas à pas : hébergement d’un contrôle composite WPF dans Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez un investissement important dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] le code, il peut être plus efficace d’étendre votre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application existante [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec plutôt que de la réécrire à partir de zéro. Un scénario courant est lorsque vous souhaitez incorporer un ou plusieurs contrôles implémentés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec dans votre application Windows Forms. Pour plus d’informations sur la personnalisation des contrôles WPF, consultez [personnalisation](../controls/control-customization.md)des contrôles.  
  
 Cette procédure pas à pas vous guide à travers une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application qui héberge un contrôle composite pour effectuer une entrée de données dans une application Windows Forms. Le contrôle composite est empaqueté dans une DLL. Cette procédure générale peut être étendue à des applications et des contrôles plus complexes. Cette procédure pas à pas est conçue pour être quasiment identique dans l' [apparence et les fonctionnalités de la procédure pas à pas: Hébergement d’un contrôle composite Windows Forms](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)dans WPF. La principale différence est que le scénario d’hébergement est inversé.  
  
 La procédure pas à pas est divisée en deux sections. La première section décrit brièvement l’implémentation du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle composite. La deuxième section explique en détail comment héberger le contrôle composite dans une application Windows Forms, recevoir des événements du contrôle et accéder à certaines propriétés du contrôle.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
- Implémentation du contrôle composite WPF  
  
- Implémentation de l’application hôte Windows Forms  
  
 Pour obtenir la liste du code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle composite WPF dans Windows Forms exemple](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Prérequis  

Cette procédure pas à pas nécessite Visual Studio.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implémentation du contrôle composite WPF  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle composite utilisé dans cet exemple est un formulaire de saisie de données simple qui prend le nom et l’adresse de l’utilisateur. Lorsque l’utilisateur clique sur l’un des deux boutons pour indiquer que la tâche est terminée, le contrôle déclenche un événement personnalisé pour retourner ces informations à l’hôte. L’illustration suivante montre le rendu du contrôle. 

 L’illustration suivante montre un contrôle composite WPF: 

 ![Capture d’écran montrant un contrôle WPF simple.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Création du projet  
 Pour démarrer le projet :  
  
1. Lancer [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]et ouvrir la boîte **de dialogue Nouveau projet** .  
  
2. Dans Visual C# et la catégorie Windows, sélectionnez le modèle **bibliothèque de contrôles utilisateur WPF** .  
  
3. Nommez le nouveau projet `MyControls`.  
  
4. Pour l’emplacement, spécifiez un dossier de niveau supérieur nommé facilement, tel que `WindowsFormsHostingWpfControl`. Plus tard, vous placerez l’application hôte dans ce dossier.  
  
5. Cliquez sur **OK** pour créer le projet. Le projet par défaut contient un seul contrôle `UserControl1`nommé.  
  
6. Dans Explorateur de solutions, `UserControl1` renommez `MyControl1`-le.  
  
 Votre projet doit comporter des références aux DLL système suivantes. Si l’une de ces DLL n’est pas incluse par défaut, ajoutez-la à votre projet.  
  
- PresentationCore  
  
- PresentationFramework  
  
- Système  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Création de l’interface utilisateur  
 Le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] du contrôle composite est implémenté avec [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Le contrôle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] composite se compose <xref:System.Windows.Controls.TextBox> de cinq éléments. Chaque <xref:System.Windows.Controls.TextBox> élément a un élément <xref:System.Windows.Controls.TextBlock> associé qui sert d’étiquette. Il y a <xref:System.Windows.Controls.Button> deux éléments en bas, **OK** et **Annuler**. Lorsque l’utilisateur clique sur l’un de ces boutons, le contrôle déclenche un événement personnalisé pour retourner les informations à l’hôte.  
  
#### <a name="basic-layout"></a>Disposition de base  
 Les différents [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments sont contenus dans un <xref:System.Windows.Controls.Grid> élément. Vous pouvez utiliser <xref:System.Windows.Controls.Grid> pour réorganiser le contenu du contrôle composite à peu près de la même façon que `Table` vous utiliseriez un élément en html. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]possède également un <xref:System.Windows.Documents.Table> élément, mais <xref:System.Windows.Controls.Grid> est plus léger et mieux adapté aux tâches de disposition simples.  
  
 Le code XAML suivant montre la disposition de base. Ce code XAML définit la structure globale du contrôle en spécifiant le nombre de colonnes et de lignes <xref:System.Windows.Controls.Grid> dans l’élément.  
  
 Dans MyControl1.xaml, remplacez le code XAML existant par le code XAML suivant.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Ajout d’éléments TextBlock et TextBox à la grille  
 Vous placez un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] élément dans la grille en définissant les attributs <xref:System.Windows.Controls.Grid.RowProperty> et <xref:System.Windows.Controls.Grid.ColumnProperty> de l’élément sur le numéro de ligne et de colonne approprié. N’oubliez pas que la numérotation des lignes et des colonnes est de base zéro. Vous pouvez avoir un élément qui s’étend sur plusieurs colonnes <xref:System.Windows.Controls.Grid.ColumnSpanProperty> en définissant son attribut. Pour plus d’informations <xref:System.Windows.Controls.Grid> sur les éléments, consultez [créer un élément Grid](../controls/how-to-create-a-grid-element.md).  
  
 Le code XAML suivant montre les éléments et <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBlock> du contrôle composite <xref:System.Windows.Controls.Grid.RowProperty> avec <xref:System.Windows.Controls.Grid.ColumnProperty> leurs attributs et, qui sont définis pour placer correctement les éléments dans la grille.  
  
 Dans MyControl1. xaml, ajoutez le code XAML suivant dans <xref:System.Windows.Controls.Grid> l’élément.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Styles des éléments d’interface utilisateur  
 De nombreux éléments du formulaire de saisie de données ont une apparence semblable, ce qui signifie qu’ils ont des paramètres identiques pour plusieurs de leurs propriétés. Au lieu de définir séparément les attributs de chaque élément, le code <xref:System.Windows.Style> XAML précédent utilise des éléments pour définir des paramètres de propriété standard pour les classes d’éléments. Cette approche réduit la complexité du contrôle et permet de modifier l’apparence de plusieurs éléments via un même attribut de style.  
  
 Les <xref:System.Windows.Style> éléments sont contenus dans la <xref:System.Windows.Controls.Grid> propriété de <xref:System.Windows.FrameworkElement.Resources%2A> l’élément, de sorte qu’ils peuvent être utilisés par tous les éléments du contrôle. Si un style est nommé, vous l’appliquez à un élément en ajoutant un <xref:System.Windows.Style> ensemble d’éléments au nom du style. Les styles qui ne sont pas nommés deviennent le style par défaut de l’élément. Pour plus d’informations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sur les styles, consultez [stylisation et création de modèles](../controls/styling-and-templating.md).  
  
 Le code XAML suivant montre <xref:System.Windows.Style> les éléments du contrôle composite. Pour voir comment les styles sont appliqués aux éléments, reportez-vous au code XAML précédent. Par exemple, le dernier <xref:System.Windows.Controls.TextBlock> élément a le `inlineText` style, et le dernier <xref:System.Windows.Controls.TextBox> élément utilise le style par défaut.  
  
 Dans MyControl1. xaml, ajoutez le code XAML suivant juste après <xref:System.Windows.Controls.Grid> l’élément Start.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Ajout des boutons OK et Annuler  
 Les éléments finaux sur le contrôle composite sont les éléments **OK** et **Cancel** <xref:System.Windows.Controls.Button> , qui occupent les deux premières colonnes <xref:System.Windows.Controls.Grid>de la dernière ligne de. Ces éléments utilisent un gestionnaire d’événements communs `ButtonClicked`,, et le <xref:System.Windows.Controls.Button> style par défaut défini dans le XAML précédent.  
  
 Dans MyControl1. xaml, ajoutez le code XAML suivant après le <xref:System.Windows.Controls.TextBox> dernier élément. La [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] partie du contrôle composite est maintenant terminée.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implémentation du fichier code-behind  
 Le fichier code-behind, MyControl1.xaml.cs, implémente trois tâches essentielles:
  
1. La gestion de l’événement qui se produit lorsque l’utilisateur clique sur l’un des boutons  
  
2. Récupère les données des <xref:System.Windows.Controls.TextBox> éléments et les empaquette dans un objet d’argument d’événement personnalisé.  
  
3. Déclenche l’événement `OnButtonClick` personnalisé, qui avertit l’hôte que l’utilisateur a terminé et transmet les données à l’hôte.  
  
 Le contrôle expose également plusieurs propriétés de couleur et de police qui vous permettent de modifier l’apparence. Contrairement à <xref:System.Windows.Forms.Integration.WindowsFormsHost> la classe, qui est utilisée pour héberger un contrôle Windows Forms <xref:System.Windows.Forms.Integration.ElementHost> , la classe expose uniquement <xref:System.Windows.Controls.Panel.Background%2A> la propriété du contrôle. Pour maintenir la similarité entre cet exemple de code et l’exemple abordé dans [procédure pas à pas: L’hébergement d’un contrôle composite](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)Windows Forms dans WPF, le contrôle expose directement les propriétés restantes.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Structure de base du fichier code-behind  
 Le fichier code-behind se compose d’un espace de `MyControls`noms unique,, qui contient deux `MyControl1` classes `MyControlEventArgs`, et.  
  
```  
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
  
 La première classe, `MyControl1`, est une classe partielle contenant le code qui implémente les fonctionnalités [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du défini dans MyControl1. Xaml. Lorsque MyControl1. xaml est analysé, le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est converti en la même classe partielle, et les deux classes partielles sont fusionnées pour former le contrôle compilé. Pour cette raison, le nom de classe du fichier code-behind doit correspondre à celui assigné à MyControl1.xaml, et il doit hériter de l’élément racine du contrôle. La deuxième classe, `MyControlEventArgs`, est une classe d’arguments d’événement qui est utilisée pour renvoyer les données à l’hôte.  
  
 Ouvrez MyControl1.xaml.cs. Modifiez la déclaration de classe existante afin qu’elle porte le nom suivant et hérite <xref:System.Windows.Controls.Grid>de.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Initialisation du contrôle  
 Le code suivant implémente plusieurs tâches de base :  
  
- Déclare un événement privé, `OnButtonClick`, et son `MyControlEventHandler`délégué associé.  
  
- Crée plusieurs variables globales privées qui stockent les données de l’utilisateur. Ces données sont exposées via les propriétés correspondantes.  
  
- Implémente un gestionnaire, `Init`, pour l’événement du <xref:System.Windows.FrameworkElement.Loaded> contrôle. Ce gestionnaire initialise les variables globales en leur assignant les valeurs définies dans MyControl1.xaml. Pour ce faire, il utilise le <xref:System.Windows.FrameworkElement.Name%2A> assigné à un élément <xref:System.Windows.Controls.TextBlock> standard, `nameLabel`, pour accéder aux paramètres de propriété de cet élément.  
  
 Supprimez le constructeur existant et ajoutez le code suivant à `MyControl1` votre classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Gestion des événements de clic de bouton  
 L’utilisateur indique que la tâche de saisie de données est terminée en cliquant sur le bouton **OK** ou sur le bouton **Annuler** . Les deux boutons utilisent le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> même gestionnaire d' `ButtonClicked`événements,. Les deux boutons ont un nom `btnOK` , `btnCancel`ou, qui permet au gestionnaire de déterminer le bouton sur lequel l’utilisateur a cliqué en examinant la valeur de l' `sender` argument. Le gestionnaire fait ce qui suit :  
  
- Crée un `MyControlEventArgs` objet qui contient les données <xref:System.Windows.Controls.TextBox> à partir des éléments.  
  
- Si l’utilisateur a cliqué sur le bouton **Annuler** , affecte `MyControlEventArgs` la valeur `IsOK` à `false`la propriété de l’objet.  
  
- Déclenche l' `OnButtonClick` événement pour indiquer à l’hôte que l’utilisateur a terminé et passe les données collectées.  
  
 Ajoutez le code suivant à votre `MyControl1` classe, après la `Init` méthode.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Création de propriétés  
 Le reste de la classe expose simplement les propriétés qui correspondent aux variables globales décrites précédemment. Lorsqu’une propriété change, le setter modifie l’apparence du contrôle en modifiant les propriétés de l’élément correspondant et en mettant à jour les variables globales sous-jacentes.  
  
 Ajoutez le code suivant à votre `MyControl1` classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Renvoi des données à l’hôte  
 Le dernier composant du fichier est la `MyControlEventArgs` classe, qui est utilisée pour renvoyer les données collectées à l’hôte.  
  
 Ajoutez le code suivant à votre `MyControls` espace de noms. L’implémentation est simple et n’est donc pas davantage expliquée.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Générez la solution. La génération produira une DLL nommée MyControls.dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implémentation de l’application hôte Windows Forms  
 L’application hôte Windows Forms utilise un <xref:System.Windows.Forms.Integration.ElementHost> objet pour héberger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contrôle composite. L’application gère l' `OnButtonClick` événement pour recevoir les données du contrôle composite. L’application comprend également un ensemble de cases d’option que vous pouvez utiliser pour modifier l’apparence du contrôle. L’illustration suivante présente l’application.  

L’illustration suivante montre un contrôle composite WPF hébergé dans une application Windows Forms»  

 ![Scteenshot qui affiche un contrôle Windows Form hébergeant Avalon.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Création du projet  
 Pour démarrer le projet :  
  
1. Lancer [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]et ouvrir la boîte **de dialogue Nouveau projet** .  
  
2. Dans Visual C# et la catégorie Windows, sélectionnez le modèle d' **application Windows Forms** .  
  
3. Nommez le nouveau projet `WFHost`.  
  
4. Pour l’emplacement, spécifiez le même dossier de premier niveau qui contient le projet MyControls.  
  
5. Cliquez sur **OK** pour créer le projet.  
  
 Vous devez également ajouter des références à la dll qui contient `MyControl1` et d’autres assemblys.  
  
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
  
3. Dans l’angle supérieur droit du formulaire, ajoutez un <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> contrôle pour contenir le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle composite.  
  
4. Ajoutez les contrôles <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> suivants au formulaire.  
  
    |Nom|Texte|  
    |----------|----------|  
    |groupBox1|Couleur d'arrière-plan|  
    |groupBox2|Couleur de premier plan|  
    |groupBox3|Taille de police|  
    |groupBox4|Famille de polices|  
    |groupBox5|Style|  
    |groupBox6|Épaisseur de police|  
    |groupBox7|Données du contrôle|  
  
5. Ajoutez les contrôles <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> suivants <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> aux contrôles.  
  
    |GroupBox|Nom|Texte|  
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
    |groupBox5|radioStyleItalic|Italique|  
    |groupBox6|radioWeightOriginal|D'origine|  
    |groupBox6|radioWeightBold|Gras|  
  
6. Ajoutez les contrôles <xref:System.Windows.Forms.Label?displayProperty=nameWithType> suivants au dernier. <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> Ces contrôles affichent les données retournées par le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle composite.  
  
    |GroupBox|Nom|Texte|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Nom :|  
    |groupBox7|lblAddress|Adresse :|  
    |groupBox7|lblCity|Ville :|  
    |groupBox7|lblState|État :|  
    |groupBox7|lblZip|Code postal :|  
  
### <a name="initializing-the-form"></a>Initialisation du formulaire  
 En général, vous implémentez le code d’hébergement <xref:System.Windows.Forms.Form.Load> dans le gestionnaire d’événements du formulaire. Le code suivant montre le <xref:System.Windows.Forms.Form.Load> gestionnaire d’événements, un gestionnaire pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’événement du <xref:System.Windows.FrameworkElement.Loaded> contrôle composite et des déclarations pour plusieurs variables globales qui sont utilisées ultérieurement.  
  
 Dans la Concepteur Windows Forms, double-cliquez sur le formulaire pour créer <xref:System.Windows.Forms.Form.Load> un gestionnaire d’événements. En haut de Form1.cs, ajoutez les instructions suivantes `using` .  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Remplacez le contenu de la classe `Form1` existante par le code suivant.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 La `Form1_Load` méthode dans le code précédent montre la procédure générale pour l’hébergement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’un contrôle:  
  
1. Créez un nouvel <xref:System.Windows.Forms.Integration.ElementHost> objet.  
  
2. Affectez à <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>la <xref:System.Windows.Forms.Control.Dock%2A> propriété du contrôle la valeur.  
  
3. Ajoutez le <xref:System.Windows.Forms.Integration.ElementHost> contrôle à la <xref:System.Windows.Forms.Panel> collection du <xref:System.Windows.Forms.Control.Controls%2A> contrôle.  
  
4. Créez une instance du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle.  
  
5. Hébergez le contrôle composite sur le formulaire en assignant le <xref:System.Windows.Forms.Integration.ElementHost> contrôle à <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> la propriété du contrôle.  
  
 Les deux lignes restantes `Form1_Load` de la méthode associent des gestionnaires à deux événements de contrôle:  
  
- `OnButtonClick`est un événement personnalisé déclenché par le contrôle composite lorsque l’utilisateur clique sur le bouton **OK** ou **Annuler** . Vous gérez l’événement pour obtenir la réponse de l’utilisateur et pour collecter les données spécifiées par l’utilisateur.  
  
- <xref:System.Windows.FrameworkElement.Loaded>est un événement standard déclenché par un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle lorsqu’il est entièrement chargé. L’événement est utilisé ici, parce que l’exemple doit initialiser plusieurs variables globales à l’aide de propriétés du contrôle. Au moment de l’événement du <xref:System.Windows.Forms.Form.Load> formulaire, le contrôle n’est pas entièrement chargé et ces valeurs ont toujours la `null`valeur. Vous devez attendre que l’événement du <xref:System.Windows.FrameworkElement.Loaded> contrôle se produise avant de pouvoir accéder à ces propriétés.  
  
 Le <xref:System.Windows.FrameworkElement.Loaded> gestionnaire d’événements est illustré dans le code précédent. Le `OnButtonClick` gestionnaire est abordé dans la section suivante.  
  
### <a name="handling-onbuttonclick"></a>Handling OnButtonClick  
 L' `OnButtonClick` événement se produit lorsque l’utilisateur clique sur le bouton **OK** ou **Annuler** .  
  
 Le gestionnaire d’événements vérifie le champ de `IsOK` l’argument d’événement pour déterminer le bouton sur lequel l’utilisateur a cliqué. Les `lbl` *variables de données* correspondent aux contrôlesdécritsprécédemment.<xref:System.Windows.Forms.Label> Si l’utilisateur clique sur le bouton **OK** , les données des contrôles <xref:System.Windows.Controls.TextBox> du contrôle sont assignées <xref:System.Windows.Forms.Label> au contrôle correspondant. Si l’utilisateur clique sur **Annuler**, les <xref:System.Windows.Forms.Label.Text%2A> valeurs sont définies sur les chaînes par défaut.  
  
 Ajoutez le code du gestionnaire d’événements Click du bouton `Form1` suivant à la classe.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Générez et exécutez l’application. Ajoutez du texte dans le contrôle composite WPF, puis cliquez sur **OK**. Le texte s’affiche dans les étiquettes. À ce stade, le code n’a pas été ajouté pour gérer les cases d’option.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Modification de l’apparence du contrôle  
 Les <xref:System.Windows.Forms.RadioButton> contrôles sur le formulaire permettent à l’utilisateur de modifier les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] couleurs de premier plan et d’arrière-plan du contrôle composite, ainsi que plusieurs propriétés de police. La couleur d’arrière-plan est <xref:System.Windows.Forms.Integration.ElementHost> exposée par l’objet. Les propriétés restantes sont exposées comme des propriétés personnalisées du contrôle.  
  
 Double-cliquez sur <xref:System.Windows.Forms.RadioButton> chaque contrôle du formulaire pour créer <xref:System.Windows.Forms.RadioButton.CheckedChanged> des gestionnaires d’événements. Remplacez les <xref:System.Windows.Forms.RadioButton.CheckedChanged> gestionnaires d’événements par le code suivant.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Générez et exécutez l’application. Cliquez sur les différentes cases d’option pour voir l’effet du contrôle composite WPF.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Procédure pas à pas : Hébergement d’un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d’un contrôle composite 3D WPF dans Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
