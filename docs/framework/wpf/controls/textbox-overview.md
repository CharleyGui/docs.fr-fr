---
title: Vue d'ensemble de TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 9fbae5ac4de4c78a1086bcbd9bfc9e01eb597fb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186639"
---
# <a name="textbox-overview"></a>Vue d'ensemble de TextBox
La <xref:System.Windows.Controls.TextBox> classe vous permet d’afficher ou d’éditer du texte non formé. Une utilisation courante <xref:System.Windows.Controls.TextBox> d’un est l’édition de texte non formé sous une forme. Par exemple, un formulaire demandant le nom de l’utilisateur, le numéro de téléphone, etc. utiliserait <xref:System.Windows.Controls.TextBox> des contrôles pour l’entrée du texte. Ce sujet introduit <xref:System.Windows.Controls.TextBox> la classe et fournit des [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemples de la façon de l’utiliser à la fois dans les deux et C.  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox ?  
 Les <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> deux et permettent aux utilisateurs d’entrer du texte, mais les deux contrôles sont utilisés pour des scénarios différents. A <xref:System.Windows.Controls.TextBox> nécessite moins de <xref:System.Windows.Controls.RichTextBox> ressources système, puis un si il est idéal lorsque seul le texte simple doit être modifié (c.-à-d., l’utilisation sous une forme). A <xref:System.Windows.Controls.RichTextBox> est un meilleur choix lorsqu’il est nécessaire pour l’utilisateur de modifier du texte formaté, des images, des tables ou tout autre contenu pris en charge. Par exemple, l’édition d’un document, article, ou blog qui <xref:System.Windows.Controls.RichTextBox>nécessite le formatage, les images, etc est mieux accompli en utilisant un . Le tableau ci-dessous résume <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox>les principales caractéristiques de et .  
  
|Control|Vérification de l’orthographe en temps réel|Menu contextuel|Formatage de <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> commandes comme (Ctr-B)|<xref:System.Windows.Documents.FlowDocument>contenu comme des images, des paragraphes, des tables, etc.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Oui|Oui|Non |Non.|  
|<xref:System.Windows.Controls.RichTextBox>|Oui|Oui|Oui (voir [Vue d’ensemble de RichTextBox](richtextbox-overview.md))|Oui (voir [Vue d’ensemble de RichTextBox](richtextbox-overview.md))|  
  
> [!NOTE]
> Bien <xref:System.Windows.Controls.TextBox> que ne supporte pas <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> le formatage des commandes d’édition connexes comme <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>(Ctr-B), de nombreuses commandes de base sont prises en charge par les deux contrôles tels que . Consultez la rubrique <xref:System.Windows.Documents.EditingCommands> (éventuellement en anglais) pour plus d'informations.  
  
 Les fonctionnalités prises en charge sont <xref:System.Windows.Controls.TextBox> couvertes dans les sections ci-dessous. Pour plus <xref:System.Windows.Controls.RichTextBox>d’informations sur , voir [RichTextBox Aperçu](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Vérification de l’orthographe en temps réel  
 Vous pouvez activer le spellchecking en temps réel dans un <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox>. Lorsque la vérification de l’orthographe est activée, une ligne rouge apparaît sous les mots mal orthographiés (voir l’illustration ci-dessous).  
  
 ![Boîte à texte avec sort&#45;la vérification](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Pour savoir comment activer la vérification de l’orthographe, consultez [Activer la vérification de l’orthographe dans un contrôle d’édition de texte](how-to-enable-spell-checking-in-a-text-editing-control.md).  
  
### <a name="context-menu"></a>Menu contextuel  
 Par défaut, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> les deux et ont un menu contextuelle qui apparaît quand un utilisateur clics à droite à l’intérieur du contrôle. Ce menu contextuel permet à l’utilisateur de couper, de copier ou de coller du texte (voir l’image ci-dessous).  
  
 ![TextBox avec menu contextuel](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Vous pouvez créer votre propre menu contextuel personnalisé pour remplacer le comportement par défaut. Pour plus d’informations, consultez [Utiliser un menu contextuel personnalisé avec un TextBox](how-to-use-a-custom-context-menu-with-a-textbox.md).  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>Création de contrôles TextBox  
 A <xref:System.Windows.Controls.TextBox> peut être une seule ligne de hauteur ou de comprendre plusieurs lignes. Une seule <xref:System.Windows.Controls.TextBox> ligne est préférable pour entrer de petites quantités de texte simple (c.-à-d. "Nom", "Numéro de téléphone", etc. sous une forme). L’exemple suivant montre comment <xref:System.Windows.Controls.TextBox>créer une seule ligne .  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Vous pouvez également <xref:System.Windows.Controls.TextBox> créer un qui permet à l’utilisateur d’entrer plusieurs lignes de texte. Par exemple, si votre formulaire demandait une esquisse biographique de <xref:System.Windows.Controls.TextBox> l’utilisateur, vous souhaitez utiliser un qui prend en charge plusieurs lignes de texte. L’exemple suivant montre [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comment <xref:System.Windows.Controls.TextBox> utiliser pour définir un contrôle qui s’étend automatiquement pour s’adapter à plusieurs lignes de texte.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 La <xref:System.Windows.Controls.TextBox.TextWrapping%2A> définition `Wrap` de l’attribut provoque l’enveloppe du <xref:System.Windows.Controls.TextBox> texte sur une <xref:System.Windows.Controls.TextBox> nouvelle ligne lorsque le bord du contrôle est atteint, en élargissant automatiquement le contrôle pour inclure de la place pour une nouvelle ligne, si nécessaire.  
  
 La <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> définition `true` de l’attribut provoque l’insertion d’une nouvelle ligne <xref:System.Windows.Controls.TextBox> lorsque la clé RETURN est pressée, en élargissant de nouveau automatiquement la place pour une nouvelle ligne, si nécessaire.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> L’attribut ajoute une <xref:System.Windows.Controls.TextBox>barre de défilement <xref:System.Windows.Controls.TextBox> à la , <xref:System.Windows.Controls.TextBox> de sorte que le contenu de la peut être défilé à travers si l’expande au-delà de la taille du cadre ou de la fenêtre qui l’entoure.  
  
 Pour plus d’informations sur <xref:System.Windows.Controls.TextBox>les différentes tâches associées à l’utilisation d’un , voir [Comment faire.](textbox-how-to-topics.md)  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>Détecter la modification du contenu  
 Habituellement, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> l’événement doit être utilisé <xref:System.Windows.Controls.TextBox> pour <xref:System.Windows.Controls.RichTextBox> détecter chaque <xref:System.Windows.UIElement.KeyDown> fois que le texte dans un ou des modifications, plutôt que vous pourriez vous attendre. Pour obtenir un exemple, consultez [Détecter la modification du texte figurant dans un TextBox](how-to-detect-when-text-in-a-textbox-has-changed.md).  
  
## <a name="see-also"></a>Voir aussi

- [Sujets comment se passer](textbox-how-to-topics.md)
- [Vue d'ensemble de RichTextBox](richtextbox-overview.md)
