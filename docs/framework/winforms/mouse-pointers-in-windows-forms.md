---
title: Pointeurs de souris
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: 4e8349effcd9b59045e39b763b4cb8b7d2fceb91
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740960"
---
# <a name="mouse-pointers-in-windows-forms"></a>Pointeurs de souris dans les Windows Forms
Le *pointeur*de la souris, qui est parfois appelé curseur, est une image bitmap qui spécifie un point de focus sur l’écran pour l’entrée d’utilisateur avec la souris. Cette rubrique fournit une vue d’ensemble du pointeur de la souris dans Windows Forms et décrit quelques-unes des façons de modifier et de contrôler le pointeur de la souris.  
  
## <a name="accessing-the-mouse-pointer"></a>Accès au pointeur de la souris  
 Le pointeur de la souris est représenté par la classe <xref:System.Windows.Forms.Cursor>, et chaque <xref:System.Windows.Forms.Control> a une propriété <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> qui spécifie le pointeur pour ce contrôle. La classe <xref:System.Windows.Forms.Cursor> contient des propriétés qui décrivent le pointeur, telles que les propriétés de <xref:System.Windows.Forms.Cursor.Position%2A> et de <xref:System.Windows.Forms.Cursor.HotSpot%2A>, ainsi que des méthodes qui peuvent modifier l’apparence du pointeur, comme les méthodes <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>et <xref:System.Windows.Forms.Cursor.DrawStretched%2A>.  
  
## <a name="controlling-the-mouse-pointer"></a>Contrôle du pointeur de la souris  
 Il peut arriver que vous souhaitiez limiter la zone dans laquelle le pointeur de la souris peut être utilisé ou modifier la position de la souris. Vous pouvez récupérer ou définir l’emplacement actuel de la souris à l’aide de la propriété <xref:System.Windows.Forms.Cursor.Position%2A> de la <xref:System.Windows.Forms.Cursor>. En outre, vous pouvez limiter la zone à laquelle le pointeur de la souris peut être utilisé pour définir la propriété <xref:System.Windows.Forms.Cursor.Clip%2A>. La zone de découpage est, par défaut, la totalité de l’écran.  
  
## <a name="changing-the-mouse-pointer"></a>Modification du pointeur de la souris  
 La modification du pointeur de la souris est un moyen important de fournir des commentaires à l’utilisateur. Par exemple, le pointeur de la souris peut être modifié dans les gestionnaires du <xref:System.Windows.Forms.Control.MouseEnter> et <xref:System.Windows.Forms.Control.MouseLeave> des événements pour indiquer à l’utilisateur que les calculs se produisent et pour limiter l’interaction de l’utilisateur dans le contrôle. Parfois, le pointeur de la souris change en raison des événements système, par exemple quand votre application est impliquée dans une opération de glisser-déplacer.  
  
 Le principal moyen de modifier le pointeur de la souris consiste à définir la propriété <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.Control.DefaultCursor%2A> d’un contrôle sur une nouvelle <xref:System.Windows.Forms.Cursor>. Pour obtenir des exemples de modification du pointeur de la souris, consultez l’exemple de code dans la classe <xref:System.Windows.Forms.Cursor>. En outre, la classe <xref:System.Windows.Forms.Cursors> expose un ensemble d’objets <xref:System.Windows.Forms.Cursor> pour de nombreux types différents de pointeurs, tels qu’un pointeur qui ressemble à une main. Pour afficher le pointeur d’attente, qui ressemble à un sablier, chaque fois que le pointeur de la souris se trouve sur le contrôle, utilisez la propriété <xref:System.Windows.Forms.Control.UseWaitCursor%2A> de la classe <xref:System.Windows.Forms.Control>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Cursor>
- [Entrée de la souris dans une application Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Fonctionnalité de glisser-déposer dans les Windows Forms](drag-and-drop-functionality-in-windows-forms.md)
