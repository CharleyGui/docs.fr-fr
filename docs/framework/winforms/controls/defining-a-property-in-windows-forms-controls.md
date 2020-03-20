---
title: Définir les propriétés de contrôle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: 7223f8c88bee4ee9c1db621cc39bbcf70d0c4589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182374"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Définition d'une propriété dans les contrôles Windows Forms
Vous trouverez une vue d’ensemble de propriétés sur la page [Vue d’ensemble des propriétés](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Il est important de prendre en compte plusieurs points avant de définir une propriété :  
  
- Vous devez appliquer des attributs aux propriétés que vous définissez. Les attributs spécifient la manière dont le concepteur doit afficher une propriété. Pour plus d’informations, consultez la page [Attributs au moment du design des composants](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).  
  
- Si le changement de propriété affecte l’affichage visuel du contrôle, appelez la <xref:System.Windows.Forms.Control.Invalidate%2A> méthode (dont votre contrôle <xref:System.Windows.Forms.Control>hérite) de l’accesseur. `set` <xref:System.Windows.Forms.Control.Invalidate%2A>à son <xref:System.Windows.Forms.Control.OnPaint%2A> tour appelle la méthode, qui redessiner le contrôle. Plusieurs appels <xref:System.Windows.Forms.Control.Invalidate%2A> pour donner lieu <xref:System.Windows.Forms.Control.OnPaint%2A> à un seul appel à l’efficacité.  
  
- La bibliothèque de classes .NET Framework fournit des convertisseurs de type pour les types de données courants : entiers, nombres décimaux, valeurs booléennes, etc. L’objectif d’un convertisseur de type consiste généralement à fournir une conversion de chaînes en valeurs (des données de chaîne vers d’autres types de données). Les types de données courants sont associés à des convertisseurs de type par défaut qui convertissent les valeurs en chaînes et les chaînes vers les types de données adéquats. Si vous définissez une propriété d’un type de donnée personnalisé (autrement dit, non standard), il vous faudra appliquer un attribut qui spécifie le convertisseur de type à associer à cette propriété. Vous pouvez également utiliser un attribut pour associer un éditeur de type avec interface utilisateur personnalisé à une propriété. Un éditeur de type avec interface utilisateur fournit une interface utilisateur permettant de modifier un type de données ou une propriété. Par exemple, un sélecteur de couleurs est un éditeur de type avec interface utilisateur. Des exemples d’attributs sont donnés à la fin de cette rubrique.  
  
    > [!NOTE]
    > S’il n’y a pas de convertisseur de type ou d’éditeur de type avec interface utilisateur disponible pour votre propriété personnalisée, vous pouvez en implémenter un en suivant les instructions de la page [Étendre la prise en charge au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).  
  
 Le fragment de code suivant montre définit une propriété personnalisée nommée `EndColor` pour le contrôle personnalisé `FlashTrackBar`.  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.
   ' The Description attribute provides a description of  
   ' the property.
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.
   // The Description attribute provides a description of  
   // the property.
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 Le fragment de code suivant associe un convertisseur de type et un éditeur de type avec interface utilisateur à la propriété `Value`. Dans ce `Value` cas est un integer et a <xref:System.ComponentModel.TypeConverterAttribute> un convertisseur de type`FlashTrackBarValueConverter`par défaut, mais l’attribut applique un convertisseur de type personnalisé ( ) qui permet au concepteur de l’afficher en pourcentage. L’éditeur de type avec interface utilisateur, `FlashTrackBarValueEditor`, permet d’afficher visuellement le pourcentage. Cet exemple montre également que le convertisseur <xref:System.ComponentModel.TypeConverterAttribute> <xref:System.ComponentModel.EditorAttribute> ou l’éditeur de type spécifié par le convertisseur ou l’attribut l’emporte sur le convertisseur par défaut.  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Propriétés dans les contrôles Windows Forms](properties-in-windows-forms-controls.md)
- [Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [Événements de modification de propriété](property-changed-events.md)
- [Attributs dans les contrôles Windows Forms](attributes-in-windows-forms-controls.md)
