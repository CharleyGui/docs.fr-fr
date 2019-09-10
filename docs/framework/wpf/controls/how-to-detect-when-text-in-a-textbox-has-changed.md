---
title: 'Procédure : Détecter la modification du texte figurant dans un TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855620"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Procédure : Détecter la modification du texte figurant dans un TextBox

Cet exemple illustre une façon d’utiliser l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement pour exécuter une méthode chaque fois que le texte <xref:System.Windows.Controls.TextBox> d’un contrôle a changé.

Dans la classe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code-behind du qui contient le <xref:System.Windows.Controls.TextBox> contrôle dont vous souhaitez analyser les modifications, insérez une méthode à appeler chaque fois que l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement se déclenche.  Cette méthode doit avoir une signature qui correspond à ce qui est attendu <xref:System.Windows.Controls.TextChangedEventHandler> par le délégué.

Le gestionnaire d’événements est appelé chaque fois que le <xref:System.Windows.Controls.TextBox> contenu du contrôle est modifié, soit par un utilisateur, soit par programme.

> [!NOTE]
> Cet événement se déclenche lorsque <xref:System.Windows.Controls.TextBox> le contrôle est créé et initialement rempli avec du texte.

## <a name="example"></a>Exemple

Dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit votre <xref:System.Windows.Controls.TextBox> contrôle, spécifiez <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> l’attribut avec une valeur qui correspond au nom de la méthode de gestionnaire d’événements.

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Exemple

Dans la classe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code-behind du qui contient le <xref:System.Windows.Controls.TextBox> contrôle dont vous souhaitez analyser les modifications, insérez une méthode à appeler chaque fois que l' <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement se déclenche.  Cette méthode doit avoir une signature qui correspond à ce qui est attendu <xref:System.Windows.Controls.TextChangedEventHandler> par le délégué.

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

Le gestionnaire d’événements est appelé chaque fois que le <xref:System.Windows.Controls.TextBox> contenu du contrôle est modifié, soit par un utilisateur, soit par programme.

> [!NOTE]
> Cet événement se déclenche lorsque <xref:System.Windows.Controls.TextBox> le contrôle est créé et initialement rempli avec du texte.

Commentaires

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [Vue d’ensemble de TextBox](textbox-overview.md)
- [Vue d’ensemble de RichTextBox](richtextbox-overview.md)
