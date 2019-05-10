---
title: Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: 5c95272c672d9b35d61e2fca8cccdbc532ef6776
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211303"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset
`ShouldSerialize` et `Reset` sont des méthodes facultatives que vous pouvez fournir pour une propriété, si la propriété n’a pas un ont la valeur par défaut simple. Si la propriété a une valeur par défaut simple, vous devez appliquer le <xref:System.ComponentModel.DefaultValueAttribute> et fournir la valeur par défaut pour le constructeur de classe d’attribut à la place. Ces deux mécanismes Active les fonctionnalités suivantes dans le concepteur :

- La propriété fournit une indication visuelle dans l’Explorateur de propriétés s’il a été modifié à partir de sa valeur par défaut.

- L’utilisateur avec le bouton droit sur la propriété et choisissez **réinitialiser** pour restaurer la propriété à sa valeur par défaut.

- Le concepteur génère du code plus efficace.

    > [!NOTE]
    >  Appliquez le <xref:System.ComponentModel.DefaultValueAttribute> ou fournir `Reset` *PropertyName* et `ShouldSerialize` *PropertyName* méthodes. N’utilisez pas les deux.

 Le `Reset` *PropertyName* méthode définit une propriété à sa valeur par défaut, comme illustré dans le fragment de code suivant.

```vb
Public Sub ResetMyFont()
   MyFont = Nothing
End Sub
```

```csharp
public void ResetMyFont() {
   MyFont = null;
}
```

> [!NOTE]
>  Si une propriété n’a pas un `Reset` (méthode), n’est pas marqué avec un <xref:System.ComponentModel.DefaultValueAttribute>et n’a pas de valeur par défaut fournie dans sa déclaration, le `Reset` option de cette propriété est désactivée dans le menu contextuel de la **propriétés** fenêtre du Concepteur Windows Forms dans Visual Studio.

 Utilisent des concepteurs, tels que Visual Studio le `ShouldSerialize` *PropertyName* méthode pour vérifier si une propriété a changé sa valeur par défaut et d’écrire du code dans le formulaire uniquement si une propriété est modifiée, ce qui permet de code plus efficace génération. Exemple :

```vb
'Returns true if the font has changed; otherwise, returns false.
' The designer writes code to the form only if true is returned.
Public Function ShouldSerializeMyFont() As Boolean
   Return Not (thefont Is Nothing)
End Function
```

```csharp
// Returns true if the font has changed; otherwise, returns false.
// The designer writes code to the form only if true is returned.
public bool ShouldSerializeMyFont() {
   return thefont != null;
}
```

 Un exemple de code complet suit.

```vb
Option Explicit
Option Strict

Imports System
Imports System.Windows.Forms
Imports System.Drawing

Public Class MyControl
   Inherits Control

   ' Declare an instance of the Font class
   ' and set its default value to Nothing.
   Private thefont As Font = Nothing

   ' The MyFont property.
   Public Property MyFont() As Font
      ' Note that the Font property never
      ' returns null.
      Get
         If Not (thefont Is Nothing) Then
            Return thefont
         End If
         If Not (Parent Is Nothing) Then
            Return Parent.Font
         End If
         Return Control.DefaultFont
      End Get
      Set
         thefont = value
      End Set
   End Property

   Public Function ShouldSerializeMyFont() As Boolean
      Return Not (thefont Is Nothing)
   End Function

   Public Sub ResetMyFont()
      MyFont = Nothing
   End Sub
End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Drawing;

public class MyControl : Control {
   // Declare an instance of the Font class
   // and set its default value to null.
   private Font thefont = null;

   // The MyFont property.
   public Font MyFont {
      // Note that the MyFont property never
      // returns null.
      get {
         if (thefont != null) return thefont;
         if (Parent != null) return Parent.Font;
         return Control.DefaultFont;
      }
      set {
         thefont = value;
      }
   }

   public bool ShouldSerializeMyFont() {
      return thefont != null;
   }

   public void ResetMyFont() {
      MyFont = null;
   }
}
```

 Dans ce cas, même lorsque la valeur de la variable privée est accessible par le `MyFont` propriété est `null`, l’Explorateur de propriétés n’affiche pas `null`; au lieu de cela, il affiche le <xref:System.Windows.Forms.Control.Font%2A> propriété du parent, si elle n’est pas `null`, ou la valeur par défaut <xref:System.Windows.Forms.Control.Font%2A> valeur définie dans <xref:System.Windows.Forms.Control>. Par conséquent, la valeur par défaut `MyFont` ne peut pas être simplement définie et un <xref:System.ComponentModel.DefaultValueAttribute> ne peut pas être appliqué à cette propriété. Au lieu de cela, le `ShouldSerialize` et `Reset` méthodes doivent être implémentées pour la `MyFont` propriété.

## <a name="see-also"></a>Voir aussi

- [Propriétés dans les contrôles Windows Forms](properties-in-windows-forms-controls.md)
- [Définition d’une propriété](defining-a-property-in-windows-forms-controls.md)
- [Événements de modification de propriété](property-changed-events.md)
