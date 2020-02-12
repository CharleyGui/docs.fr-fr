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
ms.openlocfilehash: bce2eed5f0e78c16b85b399e588c3d0d68ce7cb7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123712"
---
# <a name="dialog-boxes-overview"></a>Vue d’ensemble des boîtes de dialogue
En général, les applications autonomes ont une fenêtre principale qui affiche les données principales sur lesquelles l’application s’exécute et expose les fonctionnalités permettant de traiter ces données par le biais de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mécanismes tels que des barres de menus, des barres d’outils et des barres d’État. Une application non triviale peut également afficher des fenêtres supplémentaires pour effectuer les opérations suivantes :  
  
- Présenter des informations spécifiques aux utilisateurs  
  
- Recueillir des informations auprès des utilisateurs  
  
- Afficher et recueillir des informations  
  
 Ces types de fenêtres sont appelés *boîtes de dialogue*et il existe deux types : modal et non modal.  
  
 Une boîte de dialogue *modale* est affichée par une fonction quand la fonction a besoin de données supplémentaires d’un utilisateur pour continuer. Étant donné que la fonction dépend de la boîte de dialogue modale pour recueillir des données, celle-ci empêche également un utilisateur d’activer d’autres fenêtres de l’application pendant qu’elle reste ouverte. Dans la plupart des cas, une boîte de dialogue modale permet à un utilisateur de signaler une fois qu’il a fini d’utiliser la boîte de dialogue modale en appuyant sur un bouton **OK** ou **Annuler** . Le fait d’appuyer sur le bouton **OK** indique qu’un utilisateur a entré des données et souhaite que la fonction continue le traitement avec ces données. Appuyez sur le bouton **Annuler** pour indiquer qu’un utilisateur souhaite empêcher la fonction de s’exécuter entièrement. Les exemples les plus courants de boîtes de dialogue modales sont présentés pour ouvrir, enregistrer et imprimer des données.  
  
 En revanche, une boîte de dialogue non *modale* n’empêche pas un utilisateur d’activer d’autres fenêtres pendant qu’elle est ouverte. Par exemple, si un utilisateur souhaite rechercher des occurrences d’un mot particulier dans un document, une fenêtre principale peut ouvrir une boîte de dialogue pour l’inviter à spécifier le mot qu’il recherche. Puisque rechercher un mot n’empêche pas l’utilisateur de modifier le document, la boîte de dialogue n’a pas besoin d’être modale. Une boîte de dialogue non modale au moins fournit un bouton **Fermer** pour fermer la boîte de dialogue, et peut fournir des boutons supplémentaires pour exécuter des fonctions spécifiques, comme un bouton **suivant** pour rechercher le mot suivant qui correspond aux critères de recherche d’une recherche de mots.  
  
 Windows Presentation Foundation (WPF) vous permet de créer plusieurs types de boîtes de dialogue, notamment des boîtes de message, des boîtes de dialogue communes et des boîtes de dialogue personnalisées. Cette rubrique décrit chaque, et l' [exemple de boîte de dialogue](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) fournit des exemples correspondants.  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Boîtes de message  
 Une *boîte de message* est une boîte de dialogue qui peut être utilisée pour afficher des informations textuelles et permettre aux utilisateurs de prendre des décisions avec des boutons. L’illustration suivante montre une boîte de message qui affiche des informations textuelles, pose une question et fournit à l’utilisateur trois boutons pour répondre à la question.  
  
 ![Une boîte de dialogue traitement de texte vous demandant si vous souhaitez enregistrer les modifications apportées au document avant la fermeture de l’application.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Pour créer une boîte de message, vous utilisez la classe <xref:System.Windows.MessageBox>. <xref:System.Windows.MessageBox> vous permet de configurer le texte de la boîte de message, le titre, l’icône et les boutons à l’aide d’un code similaire à ce qui suit.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Pour afficher une boîte de message, vous appelez la méthode `static`<xref:System.Windows.MessageBox.Show%2A>, comme illustré dans le code suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Quand le code qui affiche une boîte de message doit détecter et traiter la décision de l’utilisateur (quel bouton a été enfoncé), le code peut inspecter le résultat de la boîte de message, comme indiqué dans le code suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Pour plus d’informations sur l’utilisation des boîtes de message, consultez exemple de <xref:System.Windows.MessageBox>, [MessageBox](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)et de [boîte de dialogue](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).  
  
 Bien que <xref:System.Windows.MessageBox> puisse offrir une expérience utilisateur simple de boîte de dialogue, l’avantage de l’utilisation de <xref:System.Windows.MessageBox> est que est le seul type de fenêtre qui peut être affiché par les applications qui s’exécutent dans un bac à sable (sandbox) de sécurité de confiance partielle (voir [sécurité](../security-wpf.md)), telles que les applications de navigateur XAML (XBAP).  
  
 La plupart des boîtes de dialogue affichent et recueillent des données plus complexes que le résultat d’une boîte de message, notamment du texte, une sélection (cases à cocher), une sélection mutuellement exclusive (boutons radio) et une sélection dans une liste (zones de liste, zones de liste modifiable, zones de liste déroulante). Pour ces, Windows Presentation Foundation (WPF) fournit plusieurs boîtes de dialogue communes et vous permet de créer vos propres boîtes de dialogue, bien que l’utilisation de soit limitée aux applications qui s’exécutent avec un niveau de confiance totale.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Boîtes de dialogue communes  
 Windows implémente une variété de boîtes de dialogue réutilisables communes à toutes les applications, y compris les boîtes de dialogue permettant d’ouvrir des fichiers, d’enregistrer des fichiers et d’imprimer. Ces boîtes de dialogue étant implémentées par le système d’exploitation, elles peuvent être partagées par toutes les applications qui s’exécutent sur le système d’exploitation, ce qui favorise la cohérence de l’expérience utilisateur. Quand les utilisateurs sont habitués à utiliser une boîte de dialogue fournie par le système d’exploitation dans une application, ils n’ont pas besoin d’apprendre à utiliser cette boîte de dialogue dans d’autres applications. Étant donné que ces boîtes de dialogue sont disponibles pour toutes les applications et qu’elles permettent d’offrir une expérience utilisateur cohérente, elles sont appelées *boîtes de dialogue communes*.  
  
 Windows Presentation Foundation (WPF) encapsule les boîtes de dialogue courantes ouvrir un fichier, enregistrer le fichier et imprimer et les expose en tant que classes managées que vous pouvez utiliser dans des applications autonomes. Cette rubrique fournit une brève présentation de chacune de ces boîtes de dialogue.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Boîte de dialogue Ouvrir un fichier  
 La boîte de dialogue d’ouverture de fichier, illustrée ci-dessous, est utilisée par la fonctionnalité d’ouverture de fichier pour récupérer le nom d’un fichier à ouvrir.  
  
 ![Boîte de dialogue ouverte qui indique l’emplacement de récupération du fichier.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 La boîte de dialogue Common Open file est implémentée en tant que classe <xref:Microsoft.Win32.OpenFileDialog> et se trouve dans l’espace de noms <xref:Microsoft.Win32>. Le code suivant montre comment en créer, configurer et afficher une, et comment traiter le résultat.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Pour plus d’informations sur la boîte de dialogue Ouvrir un fichier, consultez <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog> peut être utilisé pour récupérer en toute sécurité des noms de fichiers par des applications qui s’exécutent avec une confiance partielle (voir [sécurité](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Enregistrer le fichier (boîte de dialogue)  
 La boîte de dialogue d’enregistrement de fichier, illustrée ci-dessous, est utilisée par la fonctionnalité d’enregistrement de fichier pour récupérer le nom d’un fichier à enregistrer.  
  
 ![Une boîte de dialogue Enregistrer sous indique l’emplacement d’enregistrement du fichier.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 La boîte de dialogue fichier d’enregistrement commun est implémentée en tant que classe <xref:Microsoft.Win32.SaveFileDialog> et se trouve dans l’espace de noms <xref:Microsoft.Win32>. Le code suivant montre comment en créer, configurer et afficher une, et comment traiter le résultat.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Pour plus d’informations sur la boîte de dialogue Enregistrer le fichier, consultez <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Boîte de dialogue Imprimer

La boîte de dialogue d’impression, illustrée ci-dessous, est utilisée par la fonctionnalité d’impression pour choisir et configurer l’imprimante sur laquelle un utilisateur souhaite imprimer des données.  
  
![Capture d’écran montrant une boîte de dialogue Imprimer.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
La boîte de dialogue d’impression courante est implémentée en tant que classe <xref:System.Windows.Controls.PrintDialog> et se trouve dans l’espace de noms <xref:System.Windows.Controls>. Le code suivant montre comment en créer, configurer et afficher une.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Pour plus d’informations sur la boîte de dialogue Imprimer, consultez <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Pour plus d’informations sur l’impression dans WPF, consultez [vue d’ensemble de l’impression](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Boîtes de dialogue personnalisées

Bien que les boîtes de dialogue communes soient utiles (et doivent être utilisées dans la mesure du possible), elles ne prennent pas en charge les exigences des boîtes de dialogue propres au domaine. Dans ces cas-là, vous devez créer vos propres boîtes de dialogue. Comme nous allons le voir, une boîte de dialogue est une fenêtre avec des comportements spéciaux. <xref:System.Windows.Window> implémente ces comportements et, par conséquent, vous utilisez <xref:System.Windows.Window> pour créer des boîtes de dialogue modales personnalisées et non modales.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Création d’une boîte de dialogue personnalisée modale

Cette rubrique montre comment utiliser <xref:System.Windows.Window> pour créer une implémentation de boîte de dialogue modale standard, à l’aide de la boîte de dialogue `Margins` comme exemple (consultez exemple de [boîte de dialogue](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)). La boîte de dialogue `Margins` est présentée dans la figure suivante.  
  
 ![Boîte de dialogue marges avec des champs pour définir la marge de gauche, la marge supérieure, la marge droite et la marge inférieure.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Configuration d’une boîte de dialogue modale

L’interface utilisateur pour une boîte de dialogue classique comprend les éléments suivants :  
  
- Les différents contrôles nécessaires pour recueillir les données souhaitées  
  
- Un bouton **OK** sur lequel les utilisateurs cliquent pour fermer la boîte de dialogue, revenir à la fonction et continuer le traitement.  
  
- Bouton **Annuler** sur lequel les utilisateurs cliquent pour fermer la boîte de dialogue et empêcher la fonction d’effectuer un traitement supplémentaire.  
  
- Bouton **Fermer** dans la barre de titre.  
  
- icône ;  
  
- Boutons de **réduction**, d' **agrandissement**et de **restauration** .  
  
- Menu **système** pour réduire, agrandir, restaurer et fermer la boîte de dialogue.  
  
- Position au-dessus et au centre de la fenêtre qui A ouvert la boîte de dialogue.  
  
- Possibilité de redimensionner si possible pour empêcher la boîte de dialogue d’être trop petite et de fournir à l’utilisateur une taille par défaut utile. Pour cela, vous devez définir les dimensions par défaut et les dimensions minimales.  
  
- Touche Échap comme raccourci clavier qui entraîne l’activation du bouton **Annuler** . Pour ce faire, définissez la propriété <xref:System.Windows.Controls.Button.IsCancel%2A> du bouton **Annuler** sur `true`.  
  
- Touche entrée (ou retour) sous la forme d’un raccourci clavier qui entraîne l’appui sur le bouton **OK** . Pour ce faire, définissez la propriété <xref:System.Windows.Controls.Button.IsDefault%2A> du bouton **OK** `true`.  
  
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

Ici, le code passe les informations par défaut (les marges actuelles) à la boîte de dialogue. Il définit également la propriété <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> avec une référence à la fenêtre qui présente la boîte de dialogue. En général, vous devez toujours définir le propriétaire d’une boîte de dialogue pour fournir les comportements liés à l’état de la fenêtre qui sont communs à toutes les boîtes de dialogue (consultez [vue d’ensemble des fenêtres WPF](wpf-windows-overview.md) pour plus d’informations).

> [!NOTE]
> Vous devez fournir un propriétaire pour prendre en charge l’automatisation de l’interface utilisateur pour les boîtes de dialogue (consultez [vue d’ensemble d’UI Automation](../../ui-automation/ui-automation-overview.md)).

Une fois la boîte de dialogue configurée, elle s’affiche de façon modale en appelant la méthode <xref:System.Windows.Window.ShowDialog%2A>.  
  
#### <a name="validating-user-provided-data"></a>Validation des données fournies par l’utilisateur

Quand une boîte de dialogue est ouverte et que l’utilisateur fournit les données requises, une boîte de dialogue est chargée de vérifier que les données fournies sont valides pour les raisons suivantes :  
  
- Du point de vue de la sécurité, toutes les entrées doivent être validées.  
  
- D’un point de vue propre au domaine, la validation des données empêche que des données erronées soient traitées par le code, ce qui pourrait éventuellement lever des exceptions.  
  
- Du point de vue de l’expérience utilisateur, une boîte de dialogue peut aider les utilisateurs en leur montrant lesquelles des données entrées ne sont pas valides.  
  
- Du point de vue des performances, la validation des données dans une application multicouche peut réduire le nombre d’allers-retours entre le client et les couches Application, en particulier quand l’application est composée de services web ou de bases de données basées sur serveur.  

Pour valider un contrôle lié dans WPF, vous devez définir une règle de validation et l’associer à la liaison. Une règle de validation est une classe personnalisée qui dérive de <xref:System.Windows.Controls.ValidationRule>. L’exemple suivant montre une règle de validation, `MarginValidationRule`, qui vérifie qu’une valeur liée est un <xref:System.Double> et se trouve dans une plage spécifiée.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

Dans ce code, la logique de validation d’une règle de validation est implémentée en remplaçant la méthode <xref:System.Windows.Controls.ValidationRule.Validate%2A>, qui valide les données et retourne un <xref:System.Windows.Controls.ValidationResult>approprié.  

Pour associer la règle de validation au contrôle dépendant, vous utilisez le balisage suivant.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Une fois la règle de validation associée, WPF l’applique automatiquement lorsque les données sont entrées dans le contrôle lié. Lorsqu’un contrôle contient des données non valides, WPF affiche une bordure rouge autour du contrôle non valide, comme indiqué dans l’illustration suivante.  
  
![Boîte de dialogue marges avec une bordure rouge autour de la valeur de marge de gauche non valide.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF ne limite pas un utilisateur au contrôle non valide tant qu’il n’a pas entré de données valides. Il s’agit d’un bon comportement pour une boîte de dialogue. En effet, un utilisateur doit pouvoir naviguer librement entre les contrôles d’une boîte de dialogue, que les données soient valides ou non. Toutefois, cela signifie qu’un utilisateur peut entrer des données non valides et appuyer sur le bouton **OK** . Pour cette raison, votre code doit également valider tous les contrôles dans une boîte de dialogue lorsque le bouton **OK** est enfoncé en gérant l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Ce code énumère tous les objets de dépendance sur une fenêtre et, si ceux-ci sont non valides (tels qu’ils sont retournés par <xref:System.Windows.Controls.Validation.GetHasError%2A>, le contrôle non valide obtient le focus, la méthode `IsValid` retourne `false`et la fenêtre est considérée comme non valide.  
  
Une fois qu’une boîte de dialogue est valide, elle peut être fermée et retourner un résultat en toute sécurité. Dans le cadre du processus de retour, elle doit retourner un résultat à la fonction appelante.  
  
#### <a name="setting-the-modal-dialog-result"></a>Définition du résultat de la boîte de dialogue modale

L’ouverture d’une boîte de dialogue à l’aide de <xref:System.Windows.Window.ShowDialog%2A> revient fondamentalement à appeler une méthode : le code qui a ouvert la boîte de dialogue à l’aide de <xref:System.Windows.Window.ShowDialog%2A> attend jusqu’à ce que <xref:System.Windows.Window.ShowDialog%2A> retourne. Lorsque <xref:System.Windows.Window.ShowDialog%2A> retourne, le code qui l’a appelé doit décider s’il faut continuer le traitement ou arrêter le traitement, selon que l’utilisateur a appuyé sur le bouton **OK** ou sur le bouton **Annuler** . Pour faciliter cette décision, la boîte de dialogue doit retourner le choix de l’utilisateur sous la forme d’une <xref:System.Boolean> valeur retournée par la méthode <xref:System.Windows.Window.ShowDialog%2A>.  

Quand l’utilisateur clique sur le bouton **OK** , <xref:System.Windows.Window.ShowDialog%2A> doit retourner `true`. Pour ce faire, définissez la propriété <xref:System.Windows.Window.DialogResult%2A> de la boîte de dialogue lorsque l’utilisateur clique sur le bouton **OK** .  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Notez que la définition de la propriété <xref:System.Windows.Window.DialogResult%2A> entraîne également la fermeture automatique de la fenêtre, ce qui évite de devoir appeler explicitement <xref:System.Windows.Window.Close%2A>.  
  
Quand l’utilisateur clique sur le bouton **Annuler** , <xref:System.Windows.Window.ShowDialog%2A> doit retourner `false`, ce qui nécessite également la définition de la propriété <xref:System.Windows.Window.DialogResult%2A>.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Lorsque la propriété <xref:System.Windows.Controls.Button.IsCancel%2A> d’un bouton est définie sur `true` et que l’utilisateur appuie sur le bouton **Annuler** ou sur la touche échap, <xref:System.Windows.Window.DialogResult%2A> est automatiquement défini sur `false`. Le balisage suivant a le même effet que le code précédent, sans qu’il soit nécessaire de gérer l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Une boîte de dialogue retourne automatiquement `false` lorsqu’un utilisateur appuie sur le bouton **Fermer** dans la barre de titre ou choisit l’élément de menu **Fermer** dans le menu **système** .  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Traitement des données retournées par une boîte de dialogue modale  

Lorsque <xref:System.Windows.Window.DialogResult%2A> est défini par une boîte de dialogue, la fonction qui l’a ouvert peut obtenir le résultat de la boîte de dialogue en inspectant la propriété <xref:System.Windows.Window.DialogResult%2A> lorsque <xref:System.Windows.Window.ShowDialog%2A> retourne.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Si le résultat de la boîte de dialogue est `true`, la fonction l’utilise en tant que signal pour récupérer et traiter les données fournies par l’utilisateur.  
  
> [!NOTE]
> Une fois <xref:System.Windows.Window.ShowDialog%2A> retourné, une boîte de dialogue ne peut pas être rouverte. Au lieu de cela, vous devez créer une nouvelle instance.

Si le résultat de la boîte de dialogue est `false`, la fonction doit terminer le traitement de manière appropriée.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Création d’une boîte de dialogue personnalisée non modale

Une boîte de dialogue non modale, telle que la boîte de dialogue Rechercher affichée ci-dessous, a la même apparence fondamentale que la boîte de dialogue modale.  

![Capture d’écran montrant une boîte de dialogue Rechercher.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Toutefois, le comportement est légèrement différent, comme décrit dans les sections suivantes.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Ouverture d’une boîte de dialogue non modale

Pour ouvrir une boîte de dialogue non modale, appelez la méthode <xref:System.Windows.Window.Show%2A>.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Contrairement à <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> est retourné immédiatement. Ainsi, la fenêtre appelante ne peut pas savoir quand la boîte de dialogue non modale est fermée, et ne sait pas quand vérifier le résultat d’une boîte de dialogue ou obtenir des données à partir de la boîte de dialogue pour un traitement ultérieur. Au lieu de cela, la boîte de dialogue doit créer un autre moyen pour retourner des données à la fenêtre appelante en vue de leur traitement.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Traitement des données retournées par une boîte de dialogue non modale  

Dans cet exemple, la `FindDialogBox` peut retourner un ou plusieurs résultats de la recherche dans la fenêtre principale, en fonction du texte recherché sans fréquence spécifique. Comme avec une boîte de dialogue modale, une boîte de dialogue non modale peut retourner des résultats à l’aide de propriétés. Toutefois, la fenêtre propriétaire de la boîte de dialogue doit savoir quand vérifier ces propriétés. L’une des solutions consiste à ce que la boîte de dialogue implémente un événement déclenché chaque fois que le texte est trouvé. `FindDialogBox` implémente l' `TextFoundEvent` à cet effet, qui requiert tout d’abord un délégué.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

À l’aide du délégué `TextFoundEventHandler`, `FindDialogBox` implémente le `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

Par conséquent, `Find` pouvez déclencher l’événement lorsqu’un résultat de recherche est trouvé.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

La fenêtre propriétaire doit ensuite s’inscrire pour cet événement et le gérer.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Fermeture d’une boîte de dialogue non modale

Étant donné que <xref:System.Windows.Window.DialogResult%2A> n’a pas besoin d’être défini, une boîte de dialogue non modale peut être fermée à l’aide de mécanismes fournis par le système, notamment les suivants :  
  
- Cliquez sur le bouton **Fermer** dans la barre de titre.  
  
- Un appui sur Alt+F4  
  
- Choisissez **Fermer** dans le menu **système** .  
  
Votre code peut également appeler <xref:System.Windows.Window.Close%2A> lorsque l’utilisateur clique sur le bouton **Fermer** .  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de Popup](../controls/popup-overview.md)
- [Exemple de boîte de dialogue](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
