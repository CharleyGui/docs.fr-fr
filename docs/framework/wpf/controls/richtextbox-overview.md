---
title: Vue d'ensemble de RichTextBox
description: Découvrez comment le contrôle Windows Presentation Foundation RichTextBox permet aux utilisateurs d’afficher ou de modifier du contenu tel que du texte, des images et des tableaux. Consultez Exemples XAML et C#.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 525e27f9602136c68f160c738fd1c92ea761536c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166236"
---
# <a name="richtextbox-overview"></a>Vue d'ensemble de RichTextBox

Le <xref:System.Windows.Controls.RichTextBox> contrôle vous permet d’afficher ou de modifier du contenu de fluide, y compris des paragraphes, des images, des tableaux, etc. Cette rubrique présente la <xref:System.Windows.Controls.TextBox> classe et fournit des exemples d’utilisation de celle-ci dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et C#.

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>TextBox ou RichTextBox ?

<xref:System.Windows.Controls.RichTextBox>Et <xref:System.Windows.Controls.TextBox> permettent aux utilisateurs de modifier du texte, mais les deux contrôles sont utilisés dans différents scénarios. Un <xref:System.Windows.Controls.RichTextBox> est un meilleur choix lorsqu’il est nécessaire que l’utilisateur modifie du texte mis en forme, des images, des tableaux ou d’autres contenus enrichis. Par exemple, la modification d’un document, d’un article ou d’un blog nécessitant une mise en forme, des images, etc. est mieux accomplie à l’aide d’un <xref:System.Windows.Controls.RichTextBox> . Un <xref:System.Windows.Controls.TextBox> requiert moins de ressources système, <xref:System.Windows.Controls.RichTextBox> et est idéal lorsque seul du texte brut doit être modifié (par exemple, utilisation dans des formulaires). Pour plus d’informations sur, consultez [vue d’ensemble des zones de texte](textbox-overview.md) <xref:System.Windows.Controls.TextBox> . Le tableau ci-dessous résume les principales fonctionnalités de <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox> .

|Control|Vérification de l’orthographe en temps réel|Menu contextuel|Mise en forme des commandes telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTR + B)|<xref:System.Windows.Documents.FlowDocument>contenu tel que des images, des paragraphes, des tableaux, etc.|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|Oui|Oui|Non|Non.|
|<xref:System.Windows.Controls.RichTextBox>|Oui|Oui|Oui|Oui|

> [!NOTE]
> Bien que <xref:System.Windows.Controls.TextBox> ne prenne pas en charge les commandes associées à la mise en forme telles que <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTR + B), de nombreuses commandes de base sont prises en charge par les deux contrôles, tels que <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> .

Les fonctionnalités du tableau ci-dessus sont présentées plus en détail dans la suite de ce document.

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>Création d’un contrôle RichTextBox

Le code ci-dessous montre comment créer un <xref:System.Windows.Controls.RichTextBox> qu’un utilisateur peut modifier du contenu riche.

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

Plus précisément, le contenu modifié dans a <xref:System.Windows.Controls.RichTextBox> est le contenu dynamique. Le contenu dynamique peut contenir de nombreux types d’éléments, notamment du texte mis en forme, des images, des listes et des tableaux. Pour obtenir des informations complètes sur les documents dynamiques, consultez [Vue d’ensemble des documents dynamiques](../advanced/flow-document-overview.md). Pour pouvoir contenir du contenu dynamique, un <xref:System.Windows.Controls.RichTextBox> héberge un <xref:System.Windows.Documents.FlowDocument> objet qui, à son tour, contient le contenu modifiable. Pour illustrer le contenu dynamique d’un <xref:System.Windows.Controls.RichTextBox> , le code suivant montre comment créer un <xref:System.Windows.Controls.RichTextBox> avec un paragraphe et du texte en gras.

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

L’illustration suivante montre le rendu de cet exemple.

![RichTextBox avec contenu](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

Les éléments tels que <xref:System.Windows.Documents.Paragraph> et <xref:System.Windows.Documents.Bold> déterminent la façon dont le contenu à l’intérieur d’un <xref:System.Windows.Controls.RichTextBox> s’affiche. Lorsqu’un utilisateur modifie <xref:System.Windows.Controls.RichTextBox> le contenu, il modifie ce contenu de fluide. Pour en savoir plus sur les fonctionnalités et l’utilisation du contenu dynamique, consultez [Vue d’ensemble des documents dynamiques](../advanced/flow-document-overview.md).

> [!NOTE]
> Le contenu dynamique à l’intérieur d’un <xref:System.Windows.Controls.RichTextBox> ne se comporte pas exactement comme le contenu de Flow contenu dans d’autres contrôles. Par exemple, il n’y a pas de colonnes dans un <xref:System.Windows.Controls.RichTextBox> et, par conséquent, aucun comportement de redimensionnement automatique. En outre, les fonctionnalités intégrées telles que la recherche, le mode d’affichage, la navigation entre les pages et le zoom ne sont pas disponibles dans un <xref:System.Windows.Controls.RichTextBox> .

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>Vérification de l’orthographe en temps réel

Vous pouvez activer la vérification de l’orthographe en temps réel dans un <xref:System.Windows.Controls.TextBox> ou un <xref:System.Windows.Controls.RichTextBox> . Lorsque la vérification de l’orthographe est activée, une ligne rouge apparaît sous les mots mal orthographiés (voir l’illustration ci-dessous).

![TextBox avec vérification de la&#45;de l’orthographe](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

Pour savoir comment activer la vérification de l’orthographe, consultez [Activer la vérification de l’orthographe dans un contrôle d’édition de texte](how-to-enable-spell-checking-in-a-text-editing-control.md).

<a name="context_menu"></a>

## <a name="context-menu"></a>Menu contextuel

Par défaut, <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.RichTextBox> ont un menu contextuel qui s’affiche quand un utilisateur clique avec le bouton droit dans le contrôle. Ce menu contextuel permet à l’utilisateur de couper, de copier ou de coller du texte (voir l’illustration ci-dessous).

![TextBox avec menu contextuel](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")

Vous pouvez créer votre propre menu contextuel personnalisé pour remplacer celui par défaut. Pour plus d’informations, consultez [Positionner un menu contextuel personnalisé dans un RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md).

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>Commandes d'édition

Les commandes d’édition permettent aux utilisateurs de mettre en forme le contenu modifiable à l’intérieur d’un <xref:System.Windows.Controls.RichTextBox> . Outre les commandes d’édition de base, <xref:System.Windows.Controls.RichTextBox> comprend des commandes de mise en forme qui <xref:System.Windows.Controls.TextBox> ne prennent pas en charge. Par exemple, lors de la modification d’un <xref:System.Windows.Controls.RichTextBox> , un utilisateur peut appuyer sur Ctr + B pour activer ou désactiver la mise en forme du texte en gras. <xref:System.Windows.Documents.EditingCommands>Pour obtenir la liste complète des commandes disponibles, consultez. Outre l’utilisation des raccourcis clavier, vous pouvez associer des commandes à d’autres contrôles, notamment des boutons. L’exemple suivant montre comment créer une barre d’outils simple contenant des boutons que l’utilisateur peut utiliser pour modifier la mise en forme du texte.

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

L’illustration suivante montre comment cet exemple s’affiche.

![RichTextBox avec barre d'outils](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>Détecter la modification du contenu

En règle générale, l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement doit être utilisé pour détecter chaque fois que le texte d’un <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.RichTextBox> change, <xref:System.Windows.UIElement.KeyDown> comme vous pouvez vous y attendre. Pour obtenir un exemple, consultez [Détecter la modification du texte figurant dans un TextBox](how-to-detect-when-text-in-a-textbox-has-changed.md).

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>Enregistrer, charger et imprimer le contenu d'un RichTextBox

L’exemple suivant montre comment enregistrer le contenu d’un <xref:System.Windows.Controls.RichTextBox> dans un fichier, charger à nouveau ce contenu dans le <xref:System.Windows.Controls.RichTextBox> et imprimer le contenu. Voici le balisage de l’exemple.

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

Voici le code-behind de l’exemple.

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>Voir aussi

- [Rubriques Comment](richtextbox-how-to-topics.md)
- [Vue d'ensemble de TextBox](textbox-overview.md)
