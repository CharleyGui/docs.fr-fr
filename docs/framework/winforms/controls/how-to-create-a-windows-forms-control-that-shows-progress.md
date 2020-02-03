---
title: Créer un contrôle qui affiche la progression
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 9d2cf353ba2309380221bb51733baaca1b81a5d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731179"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Comment : créer un contrôle Windows Forms qui affiche la progression
L’exemple de code suivant illustre un contrôle personnalisé appelé `FlashTrackBar` qui peut être utilisé pour afficher le niveau ou la progression d’une application. Il utilise un dégradé pour représenter visuellement la progression.  
  
 Le contrôle `FlashTrackBar` illustre les concepts suivants :  
  
- Définition de propriétés personnalisées.  
  
- Définition d’événements personnalisés. (`FlashTrackBar` définit l’événement `ValueChanged`.)  
  
- Substitution de la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> pour fournir une logique pour dessiner le contrôle.  
  
- Calcul de la zone disponible pour dessiner le contrôle à l’aide de sa propriété <xref:System.Windows.Forms.Control.ClientRectangle%2A>. `FlashTrackBar` procède de cette manière dans sa méthode `OptimizedInvalidate`.  
  
- Implémentation de la sérialisation ou de la persistance d’une propriété lorsqu’elle est modifiée dans le Concepteur Windows Forms. `FlashTrackBar` définit les méthodes `ShouldSerializeStartColor` et `ShouldSerializeEndColor` pour sérialiser ses propriétés `StartColor` et `EndColor`.  
  
 Le tableau suivant présente les propriétés personnalisées définies par `FlashTrackBar`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`AllowUserEdit`|Indique si l’utilisateur peut modifier la valeur de la barre de suivi Flash en cliquant dessus et en la faisant glisser.|  
|`EndColor`|Spécifie la couleur de fin de la barre de suivi.|  
|`DarkenBy`|Spécifie l’obscurcissement de l’arrière-plan par rapport au dégradé de premier plan.|  
|`Max`|Spécifie la valeur maximale de la barre de suivi.|  
|`Min`|Spécifie la valeur minimale de la barre de suivi.|  
|`StartColor`|Spécifie la couleur de début du dégradé.|  
|`ShowPercentage`|Indique s’il faut afficher un pourcentage sur le dégradé.|  
|`ShowValue`|Indique s’il faut afficher la valeur actuelle sur le dégradé.|  
|`ShowGradient`|Indique si la barre de suivi doit afficher un dégradé de couleur illustrant la valeur actuelle.|  
|-   `Value`|Spécifie la valeur actuelle de la barre de suivi.|  
  
 Le tableau suivant montre d’autres membres définis par `FlashTrackBar:` l’événement modifié par une propriété et la méthode qui déclenche l’événement.  
  
|Membre|Description|  
|------------|-----------------|  
|`ValueChanged`|Événement déclenché lorsque la propriété `Value` de la barre de suivi change.|  
|`OnValueChanged`|Méthode qui déclenche l’événement `ValueChanged`.|  
  
> [!NOTE]
> `FlashTrackBar` utilise la classe <xref:System.EventArgs> pour les données d’événement et les <xref:System.EventHandler> pour le délégué d’événement.  
  
 Pour gérer les événements *EventName* correspondants, `FlashTrackBar` substitue les méthodes suivantes qu’il hérite de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Pour gérer les événements de modification de propriété correspondants, `FlashTrackBar` substitue les méthodes suivantes qu’il hérite de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Exemple  
 Le contrôle `FlashTrackBar` définit deux éditeurs de type d’interface utilisateur, `FlashTrackBarValueEditor` et `FlashTrackBarDarkenByEditor`, qui sont affichés dans les listes de code ci-dessous. La classe `HostApp` utilise le contrôle `FlashTrackBar` sur un formulaire Windows.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Voir aussi

- [Extension de la prise en charge au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Concepts de base du développement de contrôles Windows Forms](windows-forms-control-development-basics.md)
