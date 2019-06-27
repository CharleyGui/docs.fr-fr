---
title: Vue d'ensemble des boîtes de dialogue
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: 8008feb91a72353a74a647cf79bcecbf7023f962
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410554"
---
# <a name="dialog-boxes-overview"></a>Vue d’ensemble des boîtes de dialogue
Les applications autonomes ont en général une fenêtre principale qui affiche les données principales sur lesquelles l’application fonctionne et expose les fonctionnalités pour traiter ces données via [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] des mécanismes tels que les barres de menus, barres d’outils et barres d’état. Une application non triviale peut également afficher des fenêtres supplémentaires pour effectuer les opérations suivantes :  
  
- Présenter des informations spécifiques aux utilisateurs  
  
- Recueillir des informations auprès des utilisateurs  
  
- Afficher et recueillir des informations  
  
 Ces types de fenêtres sont appelées *boîtes de dialogue*, et il existe deux types : modales et non modales.  
  
 Un *modale* boîte de dialogue est affichée par une fonction quand celle-ci a besoin des données supplémentaires à partir d’un utilisateur pour continuer. Étant donné que la fonction dépend de la boîte de dialogue modale pour recueillir des données, celle-ci empêche également un utilisateur d’activer d’autres fenêtres de l’application pendant qu’elle reste ouverte. Dans la plupart des cas, une boîte de dialogue modale permet à un utilisateur signaler lorsqu’ils ont terminé avec la boîte de dialogue modale en appuyant sur soit un **OK** ou **Annuler** bouton. En appuyant sur la **OK** bouton indique qu’un utilisateur a entré des données et souhaite que la fonction poursuive le traitement de ces données. En appuyant sur la **Annuler** bouton indique qu’un utilisateur veut arrêter la fonction complètement l’exécution. Les exemples les plus courants de boîtes de dialogue modales sont présentés pour ouvrir, enregistrer et imprimer des données.  
  
 Un *non modale* boîte de dialogue, en revanche, n’empêche pas un utilisateur d’activer d’autres fenêtres lorsqu’il est ouvert. Par exemple, si un utilisateur souhaite rechercher des occurrences d’un mot particulier dans un document, une fenêtre principale peut ouvrir une boîte de dialogue pour l’inviter à spécifier le mot qu’il recherche. Puisque rechercher un mot n’empêche pas l’utilisateur de modifier le document, la boîte de dialogue n’a pas besoin d’être modale. Une boîte de dialogue non modale fournit au moins un **fermer** bouton pour fermer la boîte de dialogue et peut fournir des boutons supplémentaires pour exécuter des fonctions spécifiques, comme un **suivant** bouton pour rechercher la correspondance suivante les mots correspond aux critères de recherche d’une recherche de mots.  
  
 Windows Presentation Foundation (WPF) vous permet de créer plusieurs types de boîtes de dialogue, y compris les boîtes de message, les boîtes de dialogue communes et les boîtes de dialogue personnalisées. Cette rubrique présente chaque type et le [exemple de boîte de dialogue](https://go.microsoft.com/fwlink/?LinkID=159984) fournit des exemples correspondants.  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Boîtes de message  
 Un *boîte de message* est une boîte de dialogue qui peut être utilisée pour afficher des informations textuelles et pour permettre aux utilisateurs de prendre des décisions avec des boutons. L’illustration suivante montre une boîte de message qui affiche des informations textuelles, pose une question et fournit à l’utilisateur trois boutons pour répondre à la question.  
  
 ![Une boîte de dialogue de traitement de texte demandant si vous souhaitez enregistrer les modifications dans le document avant que l’application se ferme.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Pour créer une boîte de message, vous utilisez la <xref:System.Windows.MessageBox> classe. <xref:System.Windows.MessageBox> vous permet de configurer le texte du message, un titre, une icône et une boutons, à l’aide de code semblable au suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Pour afficher une boîte de message, vous appelez le `static` <xref:System.Windows.MessageBox.Show%2A> (méthode), comme illustré dans le code suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Quand le code qui affiche une boîte de message doit détecter et traiter la décision de l’utilisateur (quel bouton a été enfoncé), le code peut inspecter le résultat de la boîte de message, comme indiqué dans le code suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Pour plus d’informations sur l’utilisation des boîtes de message, consultez <xref:System.Windows.MessageBox>, [MessageBox, exemple](https://go.microsoft.com/fwlink/?LinkID=160023), et [exemple de boîte de dialogue](https://go.microsoft.com/fwlink/?LinkID=159984).  
  
 Bien que <xref:System.Windows.MessageBox> peut offrir une expérience utilisateur de boîte dialogue simple, l’avantage d’utiliser <xref:System.Windows.MessageBox> qui est le seul type de fenêtre qui peut être affiché par les applications qui s’exécutent dans un bac à sable de sécurité de confiance partielle (consultez [sécurité](../security-wpf.md)), tel que [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 La plupart des boîtes de dialogue affichent et recueillent des données plus complexes que le résultat d’une boîte de message, notamment du texte, une sélection (cases à cocher), une sélection mutuellement exclusive (boutons radio) et une sélection dans une liste (zones de liste, zones de liste modifiable, zones de liste déroulante). Dans ce cas, Windows Presentation Foundation (WPF) fournit plusieurs boîtes de dialogue courantes et vous permet de créer vos propres boîtes de dialogue, bien que leur utilisation soit limitée aux applications qui s’exécutent avec une confiance totale.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Boîtes de dialogue communes  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] implémente diverses boîtes de dialogue réutilisables qui sont communes à toutes les applications, notamment des boîtes de dialogue pour ouvrir, enregistrer et imprimer des fichiers. Ces boîtes de dialogue étant implémentées par le système d’exploitation, elles peuvent être partagées par toutes les applications qui s’exécutent sur le système d’exploitation, ce qui favorise la cohérence de l’expérience utilisateur. Quand les utilisateurs sont habitués à utiliser une boîte de dialogue fournie par le système d’exploitation dans une application, ils n’ont pas besoin d’apprendre à utiliser cette boîte de dialogue dans d’autres applications. Étant donné que ces boîtes de dialogue sont disponibles pour toutes les applications et, car elles permettent de fournir une expérience utilisateur cohérente, elles sont appelées *boîtes de dialogue communes*.  
  
 Windows Presentation Foundation (WPF) encapsule le fichier ouvert, enregistrez le fichier et imprimer des boîtes de dialogue communes et les expose comme des classes managées que vous pouvez utiliser dans des applications autonomes. Cette rubrique fournit une brève présentation de chacune de ces boîtes de dialogue.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Ouvrez la boîte de dialogue fichier  
 La boîte de dialogue d’ouverture de fichier, illustrée ci-dessous, est utilisée par la fonctionnalité d’ouverture de fichier pour récupérer le nom d’un fichier à ouvrir.  
  
 ![Une boîte de dialogue Ouvrir affichant l’emplacement pour récupérer le fichier.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 La boîte de dialogue Ouvrir un fichier est implémentée en tant que le <xref:Microsoft.Win32.OpenFileDialog> classe et se trouve dans le <xref:Microsoft.Win32> espace de noms. Le code suivant montre comment en créer, configurer et afficher une, et comment traiter le résultat.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Pour plus d’informations sur la boîte de dialogue Ouvrir un fichier, consultez <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> peut être utilisé pour récupérer en toute sécurité des noms de fichiers par les applications qui s’exécutent avec une confiance partielle (consultez [sécurité](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Enregistrer le fichier (boîte de dialogue)  
 La boîte de dialogue d’enregistrement de fichier, illustrée ci-dessous, est utilisée par la fonctionnalité d’enregistrement de fichier pour récupérer le nom d’un fichier à enregistrer.  
  
 ![Enregistrer en tant que boîte de dialogue affichant l’emplacement pour enregistrer le fichier.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Le commune d’enregistrement de boîte de dialogue fichier est implémentée en tant que le <xref:Microsoft.Win32.SaveFileDialog> classe et se trouve dans le <xref:Microsoft.Win32> espace de noms. Le code suivant montre comment en créer, configurer et afficher une, et comment traiter le résultat.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Pour plus d’informations sur l’enregistrement de fichier boîte de dialogue, consultez <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Boîte de dialogue Imprimer

La boîte de dialogue d’impression, illustrée ci-dessous, est utilisée par la fonctionnalité d’impression pour choisir et configurer l’imprimante sur laquelle un utilisateur souhaite imprimer des données.  
  
![Capture d’écran qui affiche une boîte de dialogue Imprimer.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
La boîte de dialogue d’impression est implémentée en tant que le <xref:System.Windows.Controls.PrintDialog> classe et se trouve dans le <xref:System.Windows.Controls> espace de noms. Le code suivant montre comment en créer, configurer et afficher une.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Pour plus d’informations sur la boîte de dialogue d’impression, consultez <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Pour obtenir une présentation détaillée de l’impression dans WPF, consultez [vue d’ensemble de l’impression](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Boîtes de dialogue personnalisées

Bien que les boîtes de dialogue communes soient utiles (et doivent être utilisées dans la mesure du possible), elles ne prennent pas en charge les exigences des boîtes de dialogue propres au domaine. Dans ces cas-là, vous devez créer vos propres boîtes de dialogue. Comme nous allons le voir, une boîte de dialogue est une fenêtre avec des comportements spéciaux. <xref:System.Windows.Window> implémente ces comportements et, par conséquent, vous utilisez <xref:System.Windows.Window> pour créer des boîtes de dialogue modales et non modales personnalisées.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Création d’une boîte de dialogue personnalisée modale

Cette rubrique montre comment utiliser <xref:System.Windows.Window> pour créer une implémentation de boîte de dialogue modale classique, à l’aide de la `Margins` boîte de dialogue comme exemple (consultez [exemple de boîte de dialogue](https://go.microsoft.com/fwlink/?LinkID=159984)). Le `Margins` boîte de dialogue est affichée dans la figure suivante.  
  
 ![Une boîte de dialogue marges avec des champs pour définir la marge de gauche, marge supérieure, la marge de droite et marge inférieure.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Configuration d’une boîte de dialogue modale

L’interface utilisateur pour une boîte de dialogue classique comprend les éléments suivants :  
  
- Les différents contrôles nécessaires pour recueillir les données souhaitées  
  
- Un **OK** bouton que les utilisateurs cliquez sur pour fermer la boîte de dialogue, revenir à la fonction et continuent le traitement.  
  
- Un **Annuler** bouton que les utilisateurs cliquent pour fermer la boîte de dialogue et arrêter la traitement de la fonction.  
  
- Un **fermer** bouton dans la barre de titre.  
  
- icône ;  
  
- **Réduire**, **agrandir**, et **restaurer** boutons.  
  
- Un **système** menu pour réduire, agrandir, restaurer et fermer la boîte de dialogue.  
  
- Position au-dessus et dans le centre de la fenêtre qui a ouvert la boîte de dialogue.  
  
- Possibilité d’être redimensionnée lorsque cela est possible pour empêcher la boîte de dialogue est trop petite et pour l’utilisateur avec une taille par défaut utile. Cela nécessite de définir la valeur par défaut et un dimensions minimales.  
  
- La touche ÉCHAP comme un raccourci clavier qui provoque le **Annuler** bouton à enfoncer. Pour cela, définissez la <xref:System.Windows.Controls.Button.IsCancel%2A> propriété de la **Annuler** bouton à `true`.  
  
- La touche entrée (ou retour) comme un raccourci clavier qui provoque le **OK** bouton à enfoncer. Pour cela, définissez la <xref:System.Windows.Controls.Button.IsDefault%2A> propriété de la **OK** bouton `true`.  
  
Le code suivant illustre cette configuration.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
L’expérience utilisateur pour une boîte de dialogue s’étend également à la barre de menus de la fenêtre qui ouvre la boîte de dialogue. Quand un élément de menu exécute une fonction qui nécessite une interaction utilisateur par l’intermédiaire d’une boîte de dialogue pour que la fonction puisse se poursuivre, l’élément de menu de la fonction a des points de suspension dans son en-tête, comme illustré ici.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Quand un élément de menu exécute une fonction qui affiche une boîte de dialogue qui ne nécessite pas d’intervention de l’utilisateur, par exemple une boîte de dialogue À propos, les points de suspension ne sont pas nécessaires.  
  
#### <a name="opening-a-modal-dialog-box"></a>Ouverture d’une boîte de dialogue modale

Une boîte de dialogue apparaît généralement quand un utilisateur sélectionne un élément de menu pour exécuter une fonction propre à un domaine, par exemple pour définir les marges d’un document dans un traitement de texte. Afficher une fenêtre sous forme de boîte de dialogue s’apparente à afficher une fenêtre normale, bien que cela nécessite une configuration supplémentaire propre à la boîte de dialogue. L’ensemble du processus d’instanciation, de configuration et d’ouverture d’une boîte de dialogue est illustré dans le code suivant.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

Ici, le code transmet les informations par défaut (les marges actuelles) à la boîte de dialogue. Il définit également le <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> propriété avec une référence à la fenêtre qui affiche la boîte de dialogue. En règle générale, vous devez toujours définir le propriétaire d’une boîte de dialogue pour fournir des comportements liés à l’état de fenêtre qui sont communes à toutes les boîtes de dialogue (consultez [vue d’ensemble de Windows WPF](wpf-windows-overview.md) pour plus d’informations).

> [!NOTE]
> Vous devez fournir un propriétaire pour prendre en charge d’automation d’interface utilisateur utilisateur pour les boîtes de dialogue (consultez [UI Automation Overview](../../ui-automation/ui-automation-overview.md)).

Une fois la boîte de dialogue est configurée, il s’affiche sous forme modale en appelant le <xref:System.Windows.Window.ShowDialog%2A> (méthode).  
  
#### <a name="validating-user-provided-data"></a>Validation des données fournies par l’utilisateur

Quand une boîte de dialogue est ouverte et que l’utilisateur fournit les données requises, une boîte de dialogue est chargée de vérifier que les données fournies sont valides pour les raisons suivantes :  
  
- Du point de vue de la sécurité, toutes les entrées doivent être validées.  
  
- D’un point de vue propre au domaine, la validation des données empêche que des données erronées soient traitées par le code, ce qui pourrait éventuellement lever des exceptions.  
  
- Du point de vue de l’expérience utilisateur, une boîte de dialogue peut aider les utilisateurs en leur montrant lesquelles des données entrées ne sont pas valides.  
  
- Du point de vue des performances, la validation des données dans une application multicouche peut réduire le nombre d’allers-retours entre le client et les couches Application, en particulier quand l’application est composée de services web ou de bases de données basées sur serveur.  

Pour valider un contrôle dépendant dans WPF, vous devez définir une règle de validation et l’associer à la liaison. Une règle de validation est une classe personnalisée qui dérive de <xref:System.Windows.Controls.ValidationRule>. L’exemple suivant montre une règle de validation, `MarginValidationRule`, qui vérifie qu’une valeur liée est un <xref:System.Double> et se trouve dans une plage spécifiée.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

Dans ce code, la logique de validation d’une règle de validation est implémentée en substituant la <xref:System.Windows.Controls.ValidationRule.Validate%2A> (méthode), qui valide les données et retourne une fonction <xref:System.Windows.Controls.ValidationResult>.  

Pour associer la règle de validation au contrôle dépendant, vous utilisez le balisage suivant.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Une fois que la règle de validation est associée, WPF appliquera automatiquement lorsque les données entrées dans le contrôle dépendant. Lorsqu’un contrôle contient des données non valides, WPF affiche une bordure rouge autour du contrôle non valide, comme indiqué dans l’illustration suivante.  
  
![Une boîte de dialogue marges avec une bordure rouge autour de la valeur de la marge gauche non valide.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF ne limite pas un utilisateur du contrôle non valide jusqu'à ce qu’ils ont entré des données valides. Il s’agit d’un bon comportement pour une boîte de dialogue. En effet, un utilisateur doit pouvoir naviguer librement entre les contrôles d’une boîte de dialogue, que les données soient valides ou non. Toutefois, cela signifie qu’un utilisateur peut entrer des données non valides, puis appuyez sur la **OK** bouton. Pour cette raison, votre code doit également valider tous les contrôles dans une boîte de dialogue boîte lorsque le **OK** bouton est enfoncé en gérant la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Ce code énumère tous les objets de dépendance sur une fenêtre et, si une est non valide (tel que retourné par <xref:System.Windows.Controls.Validation.GetHasError%2A>, le contrôle non valide Obtient le focus, le `IsValid` méthode retourne `false`, et la fenêtre est considérée comme non valide.  
  
Une fois qu’une boîte de dialogue est valide, elle peut être fermée et retourner un résultat en toute sécurité. Dans le cadre du processus de retour, elle doit retourner un résultat à la fonction appelante.  
  
#### <a name="setting-the-modal-dialog-result"></a>Définissez le résultat de la boîte de dialogue modale

Ouverture d’un à l’aide de la boîte de dialogue <xref:System.Windows.Window.ShowDialog%2A> est fondamentalement à appeler une méthode : le code qui a ouvert la boîte de dialogue à l’aide <xref:System.Windows.Window.ShowDialog%2A> attend <xref:System.Windows.Window.ShowDialog%2A> retourne. Lorsque <xref:System.Windows.Window.ShowDialog%2A> retourne, le code qui l’a appelée doit décider s’il faut continuer ou arrêter le traitement, selon si l’utilisateur a appuyé sur le **OK** bouton ou le **Annuler** bouton. Pour faciliter cette décision, la boîte de dialogue doit retourner le choix de l’utilisateur comme un <xref:System.Boolean> valeur retournée à partir de la <xref:System.Windows.Window.ShowDialog%2A> (méthode).  

Lorsque le **OK** bouton est activé, <xref:System.Windows.Window.ShowDialog%2A> doit retourner `true`. Cela s’effectue en définissant le <xref:System.Windows.Window.DialogResult%2A> boîte de propriété de la boîte de dialogue lorsque le **OK** bouton.  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Notez que la définition du <xref:System.Windows.Window.DialogResult%2A> propriété entraîne également la fenêtre se ferme automatiquement, ce qui évite d’avoir à appeler explicitement <xref:System.Windows.Window.Close%2A>.  
  
Lorsque le **Annuler** bouton est activé, <xref:System.Windows.Window.ShowDialog%2A> doit retourner `false`, qui requiert également la définition du <xref:System.Windows.Window.DialogResult%2A> propriété.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Lors d’un bouton <xref:System.Windows.Controls.Button.IsCancel%2A> propriété est définie sur `true` et l’utilisateur appuie sur le **Annuler** bouton ou la touche ÉCHAP, <xref:System.Windows.Window.DialogResult%2A> est automatiquement défini sur `false`. Le balisage suivant a le même effet que le code précédent, sans avoir à gérer le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Une boîte de dialogue retourne automatiquement `false` quand un utilisateur appuie sur le **fermer** situé dans la barre de titre ou choisit le **fermer** élément de menu à partir de la **système** menu.  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Traitement des données retournées à partir d’une boîte de dialogue modale  

Lorsque <xref:System.Windows.Window.DialogResult%2A> est défini par une boîte de dialogue, la fonction qui l’a ouverte peut obtenir le résultat de la boîte de dialogue en inspectant le <xref:System.Windows.Window.DialogResult%2A> propriété lorsque <xref:System.Windows.Window.ShowDialog%2A> retourne.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Si le résultat de la boîte de dialogue est `true`, la fonction qui utilise comme signal pour récupérer et traiter les données fournies par l’utilisateur.  
  
> [!NOTE]
> Après avoir <xref:System.Windows.Window.ShowDialog%2A> a retourné, une boîte de dialogue ne peut pas être rouverte. Au lieu de cela, vous devez créer une nouvelle instance.

Si le résultat de la boîte de dialogue est `false`, la fonction doit terminer le traitement de façon appropriée.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Création d’une boîte de dialogue personnalisée non modale

Une boîte de dialogue non modale, telle que la boîte de dialogue Rechercher affichée ci-dessous, a la même apparence fondamentale que la boîte de dialogue modale.  

![Capture d’écran qui affiche une boîte de dialogue Rechercher.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Toutefois, le comportement est légèrement différent, comme décrit dans les sections suivantes.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Ouverture d’une boîte de dialogue non modale

Une boîte de dialogue non modale est ouverte en appelant le <xref:System.Windows.Window.Show%2A> (méthode).  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Contrairement aux <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> retourne immédiatement. Ainsi, la fenêtre appelante ne peut pas savoir quand la boîte de dialogue non modale est fermée, et ne sait pas quand vérifier le résultat d’une boîte de dialogue ou obtenir des données à partir de la boîte de dialogue pour un traitement ultérieur. Au lieu de cela, la boîte de dialogue doit créer un autre moyen pour retourner des données à la fenêtre appelante en vue de leur traitement.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Traitement des données retournées à partir d’une boîte de dialogue non modale  

Dans cet exemple, le `FindDialogBox` peut retourner un ou plusieurs résultats de recherche à la fenêtre principale, en fonction du texte recherché sans fréquence spécifique. Comme avec une boîte de dialogue modale, une boîte de dialogue non modale peut retourner des résultats à l’aide de propriétés. Toutefois, la fenêtre propriétaire de la boîte de dialogue doit savoir quand vérifier ces propriétés. L’une des solutions consiste à ce que la boîte de dialogue implémente un événement déclenché chaque fois que le texte est trouvé. `FindDialogBox` implémente le `TextFoundEvent` à cet effet, qui nécessite d’abord un délégué.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

À l’aide de la `TextFoundEventHandler` déléguer, `FindDialogBox` implémente le `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

Par conséquent, `Find` peut déclencher l’événement lorsqu’un résultat de recherche est trouvé.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

La fenêtre propriétaire doit ensuite s’inscrire pour cet événement et le gérer.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Fermeture d’une boîte de dialogue non modale

Étant donné que <xref:System.Windows.Window.DialogResult%2A> n’a pas besoin d’être définie, une boîte de dialogue non modale peut être fermée à l’aide du système fournissent des mécanismes, y compris les éléments suivants :  
  
- En cliquant sur le **fermer** bouton dans la barre de titre.  
  
- en appuyant sur Alt+F4 ;  
  
- En choisissant **fermer** à partir de la **système** menu.  
  
Ou bien, votre code peut appeler <xref:System.Windows.Window.Close%2A> lorsque le **fermer** bouton.  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de Popup](../controls/popup-overview.md)
- [Exemple de boîte de dialogue](https://go.microsoft.com/fwlink/?LinkID=159984)
