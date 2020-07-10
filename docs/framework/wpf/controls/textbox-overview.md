---
title: Vue d'ensemble de TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 86b2cf8cb0c72186fd92bdad0af6bf5bd3fa9f3f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174430"
---
# <a name="textbox-overview"></a>Vue d'ensemble de TextBox
La <xref:System.Windows.Controls.TextBox> classe vous permet d’afficher ou de modifier du texte non mis en forme. Une utilisation courante d’un <xref:System.Windows.Controls.TextBox> consiste à modifier du texte non mis en forme dans un formulaire. Par exemple, un formulaire qui demande le nom de l’utilisateur, son numéro de téléphone, etc <xref:System.Windows.Controls.TextBox> . utilise des contrôles pour l’entrée de texte. Cette rubrique présente la <xref:System.Windows.Controls.TextBox> classe et fournit des exemples d’utilisation de celle-ci dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et C#.  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox ?  
 <xref:System.Windows.Controls.TextBox>Et <xref:System.Windows.Controls.RichTextBox> permettent aux utilisateurs d’entrer du texte, mais les deux contrôles sont utilisés pour différents scénarios. Un <xref:System.Windows.Controls.TextBox> requiert moins de ressources système, <xref:System.Windows.Controls.RichTextBox> et est donc idéal lorsque seul du texte brut doit être modifié (par exemple, utilisation dans un formulaire). Un <xref:System.Windows.Controls.RichTextBox> est un meilleur choix lorsqu’il est nécessaire que l’utilisateur modifie le texte mis en forme, les images, les tables ou tout autre contenu pris en charge. Par exemple, la modification d’un document, d’un article ou d’un blog nécessitant une mise en forme, des images, etc. est mieux accomplie à l’aide d’un <xref:System.Windows.Controls.RichTextBox> . Le tableau ci-dessous résume les principales fonctionnalités de <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox> .  
  
|Control|Vérification de l’orthographe en temps réel|Menu contextuel|Mise en forme des commandes telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTR + B)|<xref:System.Windows.Documents.FlowDocument>contenu tel que des images, des paragraphes, des tableaux, etc.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Oui|Oui|Non|Non.|  
|<xref:System.Windows.Controls.RichTextBox>|Oui|Oui|Oui (voir [Vue d’ensemble de RichTextBox](richtextbox-overview.md))|Oui (voir [Vue d’ensemble de RichTextBox](richtextbox-overview.md))|  
  
> [!NOTE]
> Bien que <xref:System.Windows.Controls.TextBox> ne prenne pas en charge les commandes de modification associées à la mise en forme telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTR + B), de nombreuses commandes de base sont prises en charge par les deux contrôles tels que <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> . Consultez la rubrique <xref:System.Windows.Documents.EditingCommands> (éventuellement en anglais) pour plus d'informations.  
  
 Les fonctionnalités prises en charge par <xref:System.Windows.Controls.TextBox> sont décrites dans les sections ci-dessous. Pour plus d’informations sur <xref:System.Windows.Controls.RichTextBox> , consultez [vue d’ensemble de RichTextBox](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Vérification de l’orthographe en temps réel  
 Vous pouvez activer la vérification de l’orthographe en temps réel dans un <xref:System.Windows.Controls.TextBox> ou un <xref:System.Windows.Controls.RichTextBox> . Lorsque la vérification de l’orthographe est activée, une ligne rouge apparaît sous les mots mal orthographiés (voir l’illustration ci-dessous).  
  
 ![TextBox avec vérification de la&#45;de l’orthographe](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Pour savoir comment activer la vérification de l’orthographe, consultez [Activer la vérification de l’orthographe dans un contrôle d’édition de texte](how-to-enable-spell-checking-in-a-text-editing-control.md).  
  
### <a name="context-menu"></a>Menu contextuel  
 Par défaut, <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox> ont un menu contextuel qui s’affiche quand un utilisateur clique avec le bouton droit dans le contrôle. Ce menu contextuel permet à l’utilisateur de couper, de copier ou de coller du texte (voir l’image ci-dessous).  
  
 ![TextBox avec menu contextuel](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Vous pouvez créer votre propre menu contextuel personnalisé pour remplacer le comportement par défaut. Pour plus d’informations, consultez [Utiliser un menu contextuel personnalisé avec un TextBox](how-to-use-a-custom-context-menu-with-a-textbox.md).  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>Création de contrôles TextBox  
 Un <xref:System.Windows.Controls.TextBox> peut être une seule ligne de hauteur ou comporter plusieurs lignes. Une seule ligne <xref:System.Windows.Controls.TextBox> est idéale pour entrer de petites quantités de texte brut (par exemple, « nom », « numéro de téléphone », etc. dans un formulaire). L’exemple suivant montre comment créer une ligne unique <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Vous pouvez également créer un <xref:System.Windows.Controls.TextBox> qui permet à l’utilisateur d’entrer plusieurs lignes de texte. Par exemple, si votre formulaire vous demande une ébauche biographique de l’utilisateur, vous pouvez utiliser un <xref:System.Windows.Controls.TextBox> qui prend en charge plusieurs lignes de texte. L’exemple suivant montre comment utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour définir un <xref:System.Windows.Controls.TextBox> contrôle qui se développe automatiquement pour s’adapter à plusieurs lignes de texte.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 L’affectation de la valeur à l' <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribut `Wrap` provoque l’encapsulation du texte sur une nouvelle ligne lorsque le bord du <xref:System.Windows.Controls.TextBox> contrôle est atteint, en développant automatiquement le <xref:System.Windows.Controls.TextBox> contrôle pour inclure de l’espace pour une nouvelle ligne, si nécessaire.  
  
 Le <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> fait d’affecter à l’attribut la valeur entraîne l’insertion d' `true` une nouvelle ligne lorsque la touche retour est enfoncée, en développant de nouveau automatiquement <xref:System.Windows.Controls.TextBox> pour inclure de l’espace pour une nouvelle ligne, si nécessaire.  
  
 L' <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribut ajoute une barre de défilement au <xref:System.Windows.Controls.TextBox> , afin que le contenu du <xref:System.Windows.Controls.TextBox> puisse être défilé si le se <xref:System.Windows.Controls.TextBox> développe au-delà de la taille du frame ou de la fenêtre qui l’englobe.  
  
 Pour plus d’informations sur les différentes tâches associées à l’utilisation d’un <xref:System.Windows.Controls.TextBox> , consultez les [rubriques de procédures](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>Détecter la modification du contenu  
 En règle générale <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> , l’événement doit être utilisé pour détecter chaque fois que le texte d’un <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox> change, au lieu de <xref:System.Windows.UIElement.KeyDown> vous attendre. Pour obtenir un exemple, consultez [Détecter la modification du texte figurant dans un TextBox](how-to-detect-when-text-in-a-textbox-has-changed.md).  
  
## <a name="see-also"></a>Voir aussi

- [Rubriques de procédures](textbox-how-to-topics.md)
- [Vue d'ensemble de RichTextBox](richtextbox-overview.md)
