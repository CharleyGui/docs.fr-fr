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
ms.openlocfilehash: 609fe4896a2b01b8a69ff8a3d0854c85ddbd6a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969098"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset
`ShouldSerialize`et `Reset` sont des méthodes facultatives que vous pouvez fournir pour une propriété, si la propriété n’a pas de valeur par défaut simple. Si la propriété a une valeur par défaut simple, vous devez appliquer <xref:System.ComponentModel.DefaultValueAttribute> et fournir la valeur par défaut au constructeur de classe d’attributs à la place. L’un ou l’autre de ces mécanismes active les fonctionnalités suivantes dans le concepteur:

- La propriété fournit une indication visuelle dans l’Explorateur de propriétés si elle a été modifiée à partir de sa valeur par défaut.

- L’utilisateur peut cliquer avec le bouton droit sur la propriété et choisir **Réinitialiser** pour rétablir la valeur par défaut de la propriété.

- Le concepteur génère du code plus efficace.

    > [!NOTE]
    > Appliquez ou fournissez <xref:System.ComponentModel.DefaultValueAttribute> `Reset`les méthodes *PropertyName* et `ShouldSerialize` *PropertyName* . N’utilisez pas les deux.

 La `Reset`méthode *PropertyName* affecte à une propriété sa valeur par défaut, comme indiqué dans le fragment de code suivant.

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
> Si une propriété n’a pas de `Reset` méthode, qu’elle n’est pas <xref:System.ComponentModel.DefaultValueAttribute>marquée avec un et qu’elle n’a pas de valeur par défaut fournie `Reset` dans sa déclaration, l’option de cette propriété est désactivée dans le menu contextuel de la fenêtre **Propriétés** de Concepteur Windows Forms dans Visual Studio.

 Les concepteurs tels que Visual Studio `ShouldSerialize`utilisent la méthode *PropertyName* pour vérifier si une propriété a été modifiée par rapport à sa valeur par défaut et écrire du code dans le formulaire uniquement si une propriété a été modifiée, ce qui permet une génération de code plus efficace. Par exemple :

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

 Vous trouverez ci-dessous un exemple de code complet.

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

 Dans ce cas, même lorsque la valeur de la variable privée accessible par la `MyFont` propriété est `null`, l’Explorateur de propriétés ne s' `null`affiche pas; à la place <xref:System.Windows.Forms.Control.Font%2A> , il affiche la propriété du parent, si `null`ce n’est pas le cas, ou la valeur <xref:System.Windows.Forms.Control.Font%2A> par défaut définie <xref:System.Windows.Forms.Control>dans. Par conséquent, la valeur `MyFont` par défaut pour ne peut pas être <xref:System.ComponentModel.DefaultValueAttribute> simplement définie et un ne peut pas être appliqué à cette propriété. Au lieu de `ShouldSerialize` cela `Reset` , les méthodes et doivent être `MyFont` implémentées pour la propriété.

## <a name="see-also"></a>Voir aussi

- [Propriétés dans les contrôles Windows Forms](properties-in-windows-forms-controls.md)
- [Définition d’une propriété](defining-a-property-in-windows-forms-controls.md)
- [Événements de modification de propriété](property-changed-events.md)
