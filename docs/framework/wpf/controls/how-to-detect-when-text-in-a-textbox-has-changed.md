---
title: 'Comment : détecter la modification du texte figurant dans un TextBox'
description: Découvrez comment utiliser l’événement TextChanged pour exécuter une méthode chaque fois que le texte d’un contrôle TextBox change dans une application Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166230"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Comment : détecter la modification du texte figurant dans un TextBox

Cet exemple illustre une façon d’utiliser l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement pour exécuter une méthode chaque fois que le texte d’un <xref:System.Windows.Controls.TextBox> contrôle a changé.

Dans la classe code-behind du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le <xref:System.Windows.Controls.TextBox> contrôle dont vous souhaitez analyser les modifications, insérez une méthode à appeler chaque fois que l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement se déclenche.  Cette méthode doit avoir une signature qui correspond à ce qui est attendu par le <xref:System.Windows.Controls.TextChangedEventHandler> délégué.

Le gestionnaire d’événements est appelé chaque fois que le contenu du <xref:System.Windows.Controls.TextBox> contrôle est modifié, soit par un utilisateur, soit par programme.

> [!NOTE]
> Cet événement se déclenche lorsque le <xref:System.Windows.Controls.TextBox> contrôle est créé et initialement rempli avec du texte.

## <a name="example"></a>Exemple

Dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit votre <xref:System.Windows.Controls.TextBox> contrôle, spécifiez l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribut avec une valeur qui correspond au nom de la méthode de gestionnaire d’événements.

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Exemple

Dans la classe code-behind du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le <xref:System.Windows.Controls.TextBox> contrôle dont vous souhaitez analyser les modifications, insérez une méthode à appeler chaque fois que l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement se déclenche.  Cette méthode doit avoir une signature qui correspond à ce qui est attendu par le <xref:System.Windows.Controls.TextChangedEventHandler> délégué.

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

Le gestionnaire d’événements est appelé chaque fois que le contenu du <xref:System.Windows.Controls.TextBox> contrôle est modifié, soit par un utilisateur, soit par programme.

> [!NOTE]
> Cet événement se déclenche lorsque le <xref:System.Windows.Controls.TextBox> contrôle est créé et initialement rempli avec du texte.

Commentaires

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [Vue d'ensemble de TextBox](textbox-overview.md)
- [Vue d'ensemble de RichTextBox](richtextbox-overview.md)
