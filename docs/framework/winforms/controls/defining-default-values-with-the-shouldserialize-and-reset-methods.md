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
ms.openlocfilehash: 11181bacdb919693ffc82c48c061357463a6343b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336761"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset
`ShouldSerialize` et `Reset` sont des méthodes facultatives que vous pouvez fournir pour une propriété, si la propriété n’a pas de valeur par défaut simple. Si la propriété a une valeur par défaut simple, vous devez appliquer la <xref:System.ComponentModel.DefaultValueAttribute> et fournir la valeur par défaut au constructeur de classe d’attributs à la place. L’un ou l’autre de ces mécanismes active les fonctionnalités suivantes dans le concepteur :

- La propriété fournit une indication visuelle dans l’Explorateur de propriétés si elle a été modifiée à partir de sa valeur par défaut.

- L’utilisateur peut cliquer avec le bouton droit sur la propriété et choisir **Réinitialiser** pour rétablir la valeur par défaut de la propriété.

- Le concepteur génère du code plus efficace.

    > [!NOTE]
    > Appliquez la <xref:System.ComponentModel.DefaultValueAttribute> ou fournissez `Reset`méthodes *NomPropriété* et `ShouldSerialize`*NomPropriété* . N’utilisez pas les deux.

 La méthode `Reset`*PropertyName* affecte à une propriété sa valeur par défaut, comme indiqué dans le fragment de code suivant.

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
> Si une propriété n’a pas de méthode `Reset`, qu’elle n’est pas marquée avec un <xref:System.ComponentModel.DefaultValueAttribute>et qu’elle n’a pas de valeur par défaut fournie dans sa déclaration, l’option `Reset` pour cette propriété est désactivée dans le menu contextuel de la fenêtre **Propriétés** de la Concepteur Windows Forms dans Visual Studio.

 Les concepteurs tels que Visual Studio utilisent la méthode `ShouldSerialize`*PropertyName* pour vérifier si une propriété a changé de sa valeur par défaut et écrire du code dans le formulaire uniquement si une propriété a été modifiée, ce qui permet une génération de code plus efficace. Exemple :

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

Imports System.Drawing
Imports System.Windows.Forms

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
using System.Drawing;
using System.Windows.Forms;

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

 Dans ce cas, même lorsque la valeur de la variable privée accessible par la propriété `MyFont` est `null`, l’Explorateur de propriétés n’affiche pas `null`; au lieu de cela, il affiche la propriété <xref:System.Windows.Forms.Control.Font%2A> du parent, s’il n’est pas `null`, ou la valeur <xref:System.Windows.Forms.Control.Font%2A> par défaut définie dans <xref:System.Windows.Forms.Control>. Par conséquent, la valeur par défaut de `MyFont` ne peut pas être simplement définie et un <xref:System.ComponentModel.DefaultValueAttribute> ne peut pas être appliqué à cette propriété. Au lieu de cela, les méthodes `ShouldSerialize` et `Reset` doivent être implémentées pour la propriété `MyFont`.

## <a name="see-also"></a>Voir aussi

- [Propriétés dans les contrôles Windows Forms](properties-in-windows-forms-controls.md)
- [Définition d’une propriété](defining-a-property-in-windows-forms-controls.md)
- [Événements de modification de propriété](property-changed-events.md)
