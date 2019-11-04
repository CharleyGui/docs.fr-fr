---
title: 'Comment : effectuer une liaison à une énumération'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454443"
---
# <a name="how-to-bind-to-an-enumeration"></a>Comment : effectuer une liaison à une énumération
Cet exemple montre comment effectuer une liaison à une énumération par liaison à la méthode GetValues de l’énumération.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la <xref:System.Windows.Controls.ListBox> affiche la liste des valeurs d’énumération <xref:System.Windows.HorizontalAlignment> par le biais de la liaison de données. Les <xref:System.Windows.Controls.ListBox> et les <xref:System.Windows.Controls.Button> sont liés de telle sorte que vous pouvez modifier la valeur de la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> du <xref:System.Windows.Controls.Button> en sélectionnant une valeur dans le <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Voir aussi

- [Effectuer une liaison à une méthode](how-to-bind-to-a-method.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
