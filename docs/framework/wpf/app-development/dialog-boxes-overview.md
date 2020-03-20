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
ms.openlocfilehash: c98d6a45d151d4b683a21e48eaeb5f4a19eaadb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187453"
---
# <a name="dialog-boxes-overview"></a>Aperçu des boîtes de dialogue
Les applications autonomes ont généralement une fenêtre principale qui affiche les données principales sur lesquelles [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] l’application fonctionne et expose la fonctionnalité pour traiter ces données à travers des mécanismes comme les barres de menu, les barres d’outils et les barres d’état. Une application non triviale peut également afficher des fenêtres supplémentaires pour effectuer les opérations suivantes :  
  
- Présenter des informations spécifiques aux utilisateurs  
  
- Recueillir des informations auprès des utilisateurs  
  
- Afficher et recueillir des informations  
  
 Ces types de fenêtres sont connus sous le nom de *boîtes de dialogue,* et il existe deux types: modal et sans mode.  
  
 Une boîte de dialogue *modal* est affichée par une fonction lorsque la fonction a besoin de données supplémentaires d’un utilisateur pour continuer. Étant donné que la fonction dépend de la boîte de dialogue modale pour recueillir des données, celle-ci empêche également un utilisateur d’activer d’autres fenêtres de l’application pendant qu’elle reste ouverte. Dans la plupart des cas, une boîte de dialogue modal permet à un utilisateur de signaler quand ils ont terminé avec la boîte de dialogue modal en appuyant soit sur un **bouton OK** ou **Annuler.** Appuyer sur le bouton **OK** indique qu’un utilisateur a saisi des données et souhaite que la fonction continue de traiter avec ces données. Appuyer sur le bouton **Annuler** indique qu’un utilisateur veut empêcher la fonction de s’exécuter complètement. Les exemples les plus courants de boîtes de dialogue modales sont présentés pour ouvrir, enregistrer et imprimer des données.  
  
 Une boîte de dialogue *sans mode,* d’autre part, n’empêche pas un utilisateur d’activer d’autres fenêtres pendant qu’il est ouvert. Par exemple, si un utilisateur souhaite rechercher des occurrences d’un mot particulier dans un document, une fenêtre principale peut ouvrir une boîte de dialogue pour l’inviter à spécifier le mot qu’il recherche. Puisque rechercher un mot n’empêche pas l’utilisateur de modifier le document, la boîte de dialogue n’a pas besoin d’être modale. Une boîte de dialogue sans mode fournit au moins un bouton **Close** pour fermer la boîte de dialogue, et peut fournir des boutons supplémentaires pour exécuter des fonctions spécifiques, telles qu’un bouton **Trouver ensuite** pour trouver le mot suivant qui correspond aux critères de recherche d’un mot de recherche.  
  
 Windows Presentation Foundation (WPF) vous permet de créer plusieurs types de boîtes de dialogue, y compris les boîtes de messages, les boîtes de dialogue commune et les boîtes de dialogue personnalisées. Ce sujet traite de chacun, et [l’échantillon de boîte de dialogue](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) fournit des exemples correspondants.  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>Boîtes de messages  
 Une *boîte de message* est une boîte de dialogue qui peut être utilisée pour afficher des informations textuelles et permettre aux utilisateurs de prendre des décisions avec des boutons. L’illustration suivante montre une boîte de message qui affiche des informations textuelles, pose une question et fournit à l’utilisateur trois boutons pour répondre à la question.  
  
 ![Une boîte de dialogue de processeur de texte demandant si vous voulez enregistrer les modifications apportées au document avant la fermeture de l’application.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Pour créer une boîte de <xref:System.Windows.MessageBox> message, vous utilisez la classe. <xref:System.Windows.MessageBox>vous permet de configurer le texte, le titre, l’icône et les boutons de la boîte de messages, en utilisant du code comme ce qui suit.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Pour afficher une boîte de `static` <xref:System.Windows.MessageBox.Show%2A> message, vous appelez la méthode, comme le montre le code suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Quand le code qui affiche une boîte de message doit détecter et traiter la décision de l’utilisateur (quel bouton a été enfoncé), le code peut inspecter le résultat de la boîte de message, comme indiqué dans le code suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Pour plus d’informations sur <xref:System.Windows.MessageBox>l’utilisation des boîtes de messages, voir , [Exemple MessageBox](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox), et [Dialog Box Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).  
  
 Bien <xref:System.Windows.MessageBox> que peut offrir une expérience utilisateur boîte <xref:System.Windows.MessageBox> de dialogue simple, l’avantage de l’utilisation est que c’est le seul type de fenêtre qui peut être montré par des applications qui s’exécutent dans un bac à sable de sécurité de confiance partielle (voir [sécurité](../security-wpf.md)), tels que les applications de navigateur XAML (XBAPs).  
  
 La plupart des boîtes de dialogue affichent et recueillent des données plus complexes que le résultat d’une boîte de message, notamment du texte, une sélection (cases à cocher), une sélection mutuellement exclusive (boutons radio) et une sélection dans une liste (zones de liste, zones de liste modifiable, zones de liste déroulante). Pour ceux-ci, Windows Presentation Foundation (WPF) fournit plusieurs boîtes de dialogue communes et vous permet de créer vos propres boîtes de dialogue, bien que l’utilisation de l’un ou l’autre est limitée à des applications en cours d’exécution avec pleine confiance.  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>Boîtes de dialogue communes  
 Windows implémente une variété de boîtes de dialogue réutilisables qui sont communes à toutes les applications, y compris les boîtes de dialogue pour l’ouverture de fichiers, l’enregistrement de fichiers et l’impression. Ces boîtes de dialogue étant implémentées par le système d’exploitation, elles peuvent être partagées par toutes les applications qui s’exécutent sur le système d’exploitation, ce qui favorise la cohérence de l’expérience utilisateur. Quand les utilisateurs sont habitués à utiliser une boîte de dialogue fournie par le système d’exploitation dans une application, ils n’ont pas besoin d’apprendre à utiliser cette boîte de dialogue dans d’autres applications. Parce que ces boîtes de dialogue sont disponibles pour toutes les applications et parce qu’ils aident à fournir une expérience utilisateur cohérente, ils sont connus comme *des boîtes de dialogue commune*.  
  
 Windows Presentation Foundation (WPF) résume le fichier ouvert, enregistre le fichier et imprime des boîtes de dialogue communes et les expose comme des classes gérées pour vous d’utiliser dans des applications autonomes. Cette rubrique fournit une brève présentation de chacune de ces boîtes de dialogue.  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>Dialogue open File  
 La boîte de dialogue d’ouverture de fichier, illustrée ci-dessous, est utilisée par la fonctionnalité d’ouverture de fichier pour récupérer le nom d’un fichier à ouvrir.  
  
 ![Une boîte de dialogue ouverte indiquant l’emplacement pour récupérer le fichier.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 La boîte de dialogue de fichier <xref:Microsoft.Win32.OpenFileDialog> ouvert commune est <xref:Microsoft.Win32> implémentée comme la classe et est située dans l’espace de nom. Le code suivant montre comment en créer, configurer et afficher une, et comment traiter le résultat.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Pour plus d’informations sur la <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>boîte de dialogue de fichier ouvert, voir .  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>peut être utilisé pour récupérer en toute sécurité les noms de fichiers par des applications en cours d’exécution avec une confiance partielle (voir [Sécurité](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>Enregistrer le fichier (boîte de dialogue)  
 La boîte de dialogue d’enregistrement de fichier, illustrée ci-dessous, est utilisée par la fonctionnalité d’enregistrement de fichier pour récupérer le nom d’un fichier à enregistrer.  
  
 ![Une boîte de dialogue Save As montrant l’emplacement pour enregistrer le fichier.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 La boîte commune de dialogue de <xref:Microsoft.Win32.SaveFileDialog> fichier d’enregistrement <xref:Microsoft.Win32> est implémentée comme la classe, et est située dans l’espace de nom. Le code suivant montre comment en créer, configurer et afficher une, et comment traiter le résultat.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Pour plus d’informations sur la <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>boîte de dialogue de fichier d’enregistrement, voir .  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>Boîte de dialogue Imprimer

La boîte de dialogue d’impression, illustrée ci-dessous, est utilisée par la fonctionnalité d’impression pour choisir et configurer l’imprimante sur laquelle un utilisateur souhaite imprimer des données.  
  
![Capture d’écran qui montre une boîte de dialogue d’impression.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
La boîte de dialogue imprimée <xref:System.Windows.Controls.PrintDialog> commune est implémentée comme la classe, et est situé dans l’espace du <xref:System.Windows.Controls> nom. Le code suivant montre comment en créer, configurer et afficher une.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>boîte de dialogue d’impression, voir . Pour une discussion détaillée de l’impression dans WPF, voir [Aperçu de l’impression](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>Boîtes de dialogue personnalisées

Bien que les boîtes de dialogue communes soient utiles (et doivent être utilisées dans la mesure du possible), elles ne prennent pas en charge les exigences des boîtes de dialogue propres au domaine. Dans ces cas-là, vous devez créer vos propres boîtes de dialogue. Comme nous allons le voir, une boîte de dialogue est une fenêtre avec des comportements spéciaux. <xref:System.Windows.Window>implémente ces comportements et, <xref:System.Windows.Window> par conséquent, vous utilisez pour créer des boîtes de dialogue modales et sans mode personnalisées.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>Création d’une boîte de dialogue modal personnalisée

Ce sujet montre <xref:System.Windows.Window> comment utiliser pour créer une mise en `Margins` œuvre typique boîte de dialogue modal, en utilisant la boîte de dialogue comme exemple (voir [Dialog Box Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)). La `Margins` boîte de dialogue est indiquée dans la figure suivante.  
  
 ![Une boîte de dialogue Margins avec des champs pour définir la marge gauche, la marge supérieure, la marge droite et la marge inférieure.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Configurer une boîte de dialogue modal

L’interface utilisateur pour une boîte de dialogue classique comprend les éléments suivants :  
  
- Les différents contrôles nécessaires pour recueillir les données souhaitées  
  
- Un bouton **OK** que les utilisateurs cliquent pour fermer la boîte de dialogue, revenir à la fonction, et continuer le traitement.  
  
- Un bouton **Annuler** que les utilisateurs cliquent pour fermer la boîte de dialogue et empêcher la fonction de traiter davantage.  
  
- Un bouton **Close** dans la barre de titre.  
  
- icône ;  
  
- **Minimisez,** **maximisez**et **restaurez les** boutons.  
  
- Un menu **système** pour minimiser, maximiser, restaurer et fermer la boîte de dialogue.  
  
- Une position au-dessus et au centre de la fenêtre qui a ouvert la boîte de dialogue.  
  
- La possibilité d’être resized si possible pour empêcher la boîte de dialogue d’être trop petit, et de fournir à l’utilisateur une taille par défaut utile. Cela exige que vous définissiez à la fois les dimensions par défaut et les dimensions minimales.  
  
- La clé ESC comme raccourci clavier qui provoque le bouton **Annuler** d’être pressé. Vous le faites <xref:System.Windows.Controls.Button.IsCancel%2A> en définissant la `true`propriété du bouton **Annuler** à .  
  
- La touche ENTER (ou RETURN) comme raccourci clavier qui fait appuyer le bouton **OK.** Vous le faites <xref:System.Windows.Controls.Button.IsDefault%2A> en définissant `true`la propriété du bouton **OK** .  
  
Le code suivant illustre cette configuration.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
L’expérience utilisateur pour une boîte de dialogue s’étend également à la barre de menus de la fenêtre qui ouvre la boîte de dialogue. Quand un élément de menu exécute une fonction qui nécessite une interaction utilisateur par l’intermédiaire d’une boîte de dialogue pour que la fonction puisse se poursuivre, l’élément de menu de la fonction a des points de suspension dans son en-tête, comme illustré ici.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Quand un élément de menu exécute une fonction qui affiche une boîte de dialogue qui ne nécessite pas d’intervention de l’utilisateur, par exemple une boîte de dialogue À propos, les points de suspension ne sont pas nécessaires.  
  
#### <a name="opening-a-modal-dialog-box"></a>Ouverture d’une boîte de dialogue modal

Une boîte de dialogue apparaît généralement quand un utilisateur sélectionne un élément de menu pour exécuter une fonction propre à un domaine, par exemple pour définir les marges d’un document dans un traitement de texte. Afficher une fenêtre sous forme de boîte de dialogue s’apparente à afficher une fenêtre normale, bien que cela nécessite une configuration supplémentaire propre à la boîte de dialogue. L’ensemble du processus d’instanciation, de configuration et d’ouverture d’une boîte de dialogue est illustré dans le code suivant.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

Ici, le code transmet les informations par défaut (les marges actuelles) à la boîte de dialogue. Il définit <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> également la propriété avec une référence à la fenêtre qui montre la boîte de dialogue. En général, vous devez toujours définir le propriétaire pour une boîte de dialogue pour fournir des comportements liés à l’état de fenêtre qui sont communs à toutes les boîtes de dialogue (voir [WPF Windows Overview](wpf-windows-overview.md) pour plus d’informations).

> [!NOTE]
> Vous devez fournir un propriétaire pour prendre en charge l’automatisation de l’interface utilisateur (UI) pour les boîtes de dialogue (voir [UI Automation Overview](../../ui-automation/ui-automation-overview.md)).

Une fois que la boîte de dialogue est configurée, elle est montrée modalement en appelant la <xref:System.Windows.Window.ShowDialog%2A> méthode.  
  
#### <a name="validating-user-provided-data"></a>Validation des données fournies par l’utilisateur

Quand une boîte de dialogue est ouverte et que l’utilisateur fournit les données requises, une boîte de dialogue est chargée de vérifier que les données fournies sont valides pour les raisons suivantes :  
  
- Du point de vue de la sécurité, toutes les entrées doivent être validées.  
  
- D’un point de vue propre au domaine, la validation des données empêche que des données erronées soient traitées par le code, ce qui pourrait éventuellement lever des exceptions.  
  
- Du point de vue de l’expérience utilisateur, une boîte de dialogue peut aider les utilisateurs en leur montrant lesquelles des données entrées ne sont pas valides.  
  
- Du point de vue des performances, la validation des données dans une application multicouche peut réduire le nombre d’allers-retours entre le client et les couches Application, en particulier quand l’application est composée de services web ou de bases de données basées sur serveur.  

Pour valider un contrôle lié dans WPF, vous devez définir une règle de validation et l’associer à la liaison. Une règle de validation est une <xref:System.Windows.Controls.ValidationRule>classe personnalisée qui dérive de . L’exemple suivant montre `MarginValidationRule`une règle de validation, <xref:System.Double> qui vérifie qu’une valeur consolidée est a et se situe dans une plage spécifiée.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

Dans ce code, la logique de validation d’une <xref:System.Windows.Controls.ValidationRule.Validate%2A> règle de validation est mise <xref:System.Windows.Controls.ValidationResult>en œuvre en prépondant la méthode, qui valide les données et renvoie un approprié .  

Pour associer la règle de validation au contrôle dépendant, vous utilisez le balisage suivant.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Une fois la règle de validation associée, WPF l’appliquera automatiquement lorsque les données sont saisies dans le contrôle lié. Lorsqu’un contrôle contient des données non valides, le FMM affiche une bordure rouge autour du contrôle invalide, comme le montre le chiffre suivant.  
  
![Une boîte de dialogue Margins avec une bordure rouge autour de la valeur de marge gauche invalide.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF ne limite pas un utilisateur au contrôle invalide jusqu’à ce qu’il ait saisi les données valides. Il s’agit d’un bon comportement pour une boîte de dialogue. En effet, un utilisateur doit pouvoir naviguer librement entre les contrôles d’une boîte de dialogue, que les données soient valides ou non. Toutefois, cela signifie qu’un utilisateur peut entrer des données invalides et appuyer sur le bouton **OK.** Pour cette raison, votre code doit également valider toutes **OK** les commandes dans <xref:System.Windows.Controls.Primitives.ButtonBase.Click> une boîte de dialogue lorsque le bouton OK est appuyé sur la manipulation de l’événement.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Ce code énumère tous les objets de dépendance sur une fenêtre <xref:System.Windows.Controls.Validation.GetHasError%2A>et, le cas échéant, `IsValid` invalide (tel que retourné par , le contrôle invalide obtient la mise au point, la méthode renvoie, `false`et la fenêtre est considérée comme invalide.  
  
Une fois qu’une boîte de dialogue est valide, elle peut être fermée et retourner un résultat en toute sécurité. Dans le cadre du processus de retour, elle doit retourner un résultat à la fonction appelante.  
  
#### <a name="setting-the-modal-dialog-result"></a>Définir le résultat du dialogue modal

Ouvrir une boîte <xref:System.Windows.Window.ShowDialog%2A> de dialogue à l’aide est fondamentalement comme <xref:System.Windows.Window.ShowDialog%2A> appeler <xref:System.Windows.Window.ShowDialog%2A> une méthode: le code qui a ouvert la boîte de dialogue en utilisant attend jusqu’à ce que les retours. Lors <xref:System.Windows.Window.ShowDialog%2A> des déclarations, le code qui l’a appelé doit décider de continuer à traiter ou arrêter le traitement, en fonction du fait que l’utilisateur a appuyé sur le bouton **OK** ou le bouton **Annuler.** Pour faciliter cette décision, la boîte de dialogue doit <xref:System.Boolean> retourner le choix <xref:System.Windows.Window.ShowDialog%2A> de l’utilisateur comme une valeur qui est retournée de la méthode.  

Lorsque le bouton **OK** <xref:System.Windows.Window.ShowDialog%2A> est `true`cliqué, doit revenir . Ceci est réalisé <xref:System.Windows.Window.DialogResult%2A> en définissant la propriété de la boîte de dialogue lorsque le bouton **OK** est cliqué.  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Notez que <xref:System.Windows.Window.DialogResult%2A> la mise en place de la propriété provoque <xref:System.Windows.Window.Close%2A>également la fenêtre de fermer automatiquement, ce qui atténue la nécessité d’appeler explicitement .  
  
Lorsque le bouton **Annuler** <xref:System.Windows.Window.ShowDialog%2A> est `false`cliqué, devrait <xref:System.Windows.Window.DialogResult%2A> revenir, ce qui nécessite également la mise en place de la propriété.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Lorsque la propriété <xref:System.Windows.Controls.Button.IsCancel%2A> d’un `true` bouton est configuré et que l’utilisateur appuie `false`soit sur le bouton **Annuler,** soit la clé ESC, <xref:System.Windows.Window.DialogResult%2A> est automatiquement configuré . La balisage suivante a le même effet que le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> code précédent, sans avoir besoin de gérer l’événement.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Une boîte de `false` dialogue revient automatiquement lorsqu’un utilisateur appuie sur le bouton **Close** dans la barre de titre ou choisit l’élément de menu **Close** dans le menu **Système.**  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Traitement des données retournées d’une boîte de dialogue modal  

Quand <xref:System.Windows.Window.DialogResult%2A> est réglé par une boîte de dialogue, la fonction qui l’a ouverte peut obtenir le résultat de boîte de dialogue en inspectant la <xref:System.Windows.Window.DialogResult%2A> propriété lors <xref:System.Windows.Window.ShowDialog%2A> du retour.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

Si le résultat `true`du dialogue est, la fonction utilise cela comme un indice pour récupérer et traiter les données fournies par l’utilisateur.  
  
> [!NOTE]
> Après <xref:System.Windows.Window.ShowDialog%2A> son retour, une boîte de dialogue ne peut pas être rouverte. Au lieu de cela, vous devez créer une nouvelle instance.

Si le résultat `false`du dialogue est, la fonction doit mettre fin au traitement de manière appropriée.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>Création d’une boîte de dialogue personnalisée sans mode

Une boîte de dialogue non modale, telle que la boîte de dialogue Rechercher affichée ci-dessous, a la même apparence fondamentale que la boîte de dialogue modale.  

![Capture d’écran qui montre une boîte de dialogue Find.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Toutefois, le comportement est légèrement différent, comme décrit dans les sections suivantes.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Ouverture d’une boîte de dialogue sans mode

Une boîte de dialogue sans mode <xref:System.Windows.Window.Show%2A> est ouverte en appelant la méthode.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Contrairement <xref:System.Windows.Window.ShowDialog%2A> <xref:System.Windows.Window.Show%2A> à , revient immédiatement. Ainsi, la fenêtre appelante ne peut pas savoir quand la boîte de dialogue non modale est fermée, et ne sait pas quand vérifier le résultat d’une boîte de dialogue ou obtenir des données à partir de la boîte de dialogue pour un traitement ultérieur. Au lieu de cela, la boîte de dialogue doit créer un autre moyen pour retourner des données à la fenêtre appelante en vue de leur traitement.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Traitement des données retournées d’une boîte de dialogue sans mode  

Dans cet exemple, le `FindDialogBox` peut retourner un ou plusieurs résultats de trouver à la fenêtre principale, en fonction du texte recherché sans aucune fréquence spécifique. Comme avec une boîte de dialogue modale, une boîte de dialogue non modale peut retourner des résultats à l’aide de propriétés. Toutefois, la fenêtre propriétaire de la boîte de dialogue doit savoir quand vérifier ces propriétés. L’une des solutions consiste à ce que la boîte de dialogue implémente un événement déclenché chaque fois que le texte est trouvé. `FindDialogBox`met en `TextFoundEvent` œuvre le pour cette fin, qui exige d’abord un délégué.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

En `TextFoundEventHandler` utilisant `FindDialogBox` le délégué, met en œuvre le `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

Par conséquent, `Find` peut soulever l’événement quand un résultat de recherche est trouvé.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

La fenêtre propriétaire doit ensuite s’inscrire pour cet événement et le gérer.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Fermeture d’une boîte de dialogue sans mode

Parce <xref:System.Windows.Window.DialogResult%2A> qu’il n’est pas nécessaire d’être défini, un dialogue sans mode peut être fermé à l’aide de mécanismes de fournir le système, y compris les suivants :  
  
- Cliquez sur le bouton **Close** dans la barre de titre.  
  
- en appuyant sur Alt+F4 ;  
  
- Choisir **Close** dans le menu **Système.**  
  
Alternativement, votre code <xref:System.Windows.Window.Close%2A> peut appeler lorsque le bouton **Close** est cliqué.  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de Popup](../controls/popup-overview.md)
- [Exemple de boîte de dialogue](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
