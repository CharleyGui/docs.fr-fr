---
title: 'Procédure : Ouvrir un fichier qui est déplacé dans un contrôle RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: 408d48856362fa8a77a44e2cc97cb2d5ff608dcf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046351"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Procédure : Ouvrir un fichier qui est déplacé dans un contrôle RichTextBox

Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les <xref:System.Windows.Controls.TextBox>contrôles <xref:System.Windows.Controls.RichTextBox>, et<xref:System.Windows.Documents.FlowDocument> ont tous des fonctionnalités de glisser-déplacer intégrées. La fonctionnalité intégrée permet le glisser-déplacer de texte dans et entre les contrôles. Toutefois, il n’active pas l’ouverture d’un fichier en déplaçant le fichier sur le contrôle. Ces contrôles marquent également les événements de glisser-déplacer comme étant gérés. Par conséquent, par défaut, vous ne pouvez pas ajouter vos propres gestionnaires d’événements pour fournir des fonctionnalités permettant d’ouvrir des fichiers supprimés.

Pour ajouter une gestion supplémentaire pour les événements de glisser-déplacer dans ces contrôles, utilisez <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> la méthode pour ajouter vos gestionnaires d’événements pour les événements de glisser-déplacer. Affectez au `true` paramètrelavaleurpourquelegestionnairespécifiésoitappelépourunévénementroutéquiadéjàétémarquécommegéréparunautreélémentlelongdel’itinéraired’événement.`handledEventsToo`

> [!TIP]
> Vous pouvez remplacer la fonctionnalité de glisser-déplacer intégrée de <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>et <xref:System.Windows.Documents.FlowDocument> en gérant les versions préliminaires des événements de glisser-déplacer et en marquant les événements d’aperçu comme gérés. Toutefois, cette opération désactive la fonctionnalité de glisser-déplacer intégrée, et n’est pas recommandée.

## <a name="example"></a>Exemples

L’exemple suivant montre comment ajouter des gestionnaires pour les <xref:System.Windows.DragDrop.DragOver> événements et <xref:System.Windows.DragDrop.Drop> sur un. <xref:System.Windows.Controls.RichTextBox> Cet exemple utilise la <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> méthode et définit le `handledEventsToo` paramètre sur `true` afin que les gestionnaires d’événements soient appelés, même si le <xref:System.Windows.Controls.RichTextBox> marque ces événements comme gérés. Le code dans les gestionnaires d’événements ajoute des fonctionnalités pour ouvrir un fichier texte qui est déposé sur <xref:System.Windows.Controls.RichTextBox>le.

Pour tester cet exemple, faites glisser un fichier texte ou un fichier au format RTF (Rich Text Format) à partir <xref:System.Windows.Controls.RichTextBox>de l’Explorateur Windows vers le. Le fichier sera ouvert dans le <xref:System.Windows.Controls.RichTextBox>. Si vous appuyez sur la touche Maj avant de supprimer le fichier, le fichier s’ouvre en texte brut.

[!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]

[!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
[!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
