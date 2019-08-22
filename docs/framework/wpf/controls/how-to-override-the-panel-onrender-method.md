---
title: 'Procédure : Substituer la méthode OnRender de Panel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666717"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Procédure : Substituer la méthode OnRender de Panel
Cet exemple montre comment substituer la <xref:System.Windows.Controls.Panel.OnRender%2A> méthode de afin d’ajouter des <xref:System.Windows.Controls.Panel> effets graphiques personnalisés à un élément Layout.  
  
## <a name="example"></a>Exemple  
 Utilisez la <xref:System.Windows.Controls.Panel.OnRender%2A> méthode pour ajouter des effets graphiques à un élément Panel rendu. Par exemple, vous pouvez utiliser cette méthode pour ajouter des effets de bordure ou d’arrière-plan personnalisés. Un <xref:System.Windows.Media.DrawingContext> objet est passé comme argument, qui fournit des méthodes pour dessiner des formes, du texte, des images ou des vidéos. Par conséquent, cette méthode est utile pour la personnalisation d’un objet Panel.  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Panel>
- [Vue d’ensemble de Panel](panels-overview.md)
- [Rubriques de guide pratique](panel-how-to-topics.md)
