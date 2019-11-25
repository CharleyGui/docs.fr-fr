---
title: 'Comment : lier les propriétés de deux contrôles'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: d38c473b8c4d3f71f1e3decd4f66be248665c57b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974814"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Comment : lier les propriétés de deux contrôles

Cet exemple montre comment lier la propriété d’un contrôle instancié à celle d’un autre à l’aide de la propriété <xref:System.Windows.Data.Binding.ElementName%2A>.

## <a name="example"></a>Exemple

L’exemple suivant montre comment lier la propriété <xref:System.Windows.Controls.Panel.Background%2A> d’un <xref:System.Windows.Controls.Canvas> à la propriété [SelectedItem. Content](xref:System.Windows.Controls.ContentControl.Content%2A) d’un <xref:System.Windows.Controls.ComboBox>:

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

Lors de l’affichage, on obtient un résultat similaire à ce qui suit :

![Capture d’écran montrant une zone de liste modifiable avec la valeur vert sélectionnée et un carré vert.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> La propriété de la cible de liaison (dans cet exemple, la propriété <xref:System.Windows.Controls.Panel.Background%2A>) doit être une propriété de dépendance. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).

## <a name="see-also"></a>Voir aussi

- [Spécifier la source de liaison](how-to-specify-the-binding-source.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
