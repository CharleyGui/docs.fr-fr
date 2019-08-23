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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="afb6b-102">Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset</span><span class="sxs-lookup"><span data-stu-id="afb6b-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="afb6b-103">`ShouldSerialize`et `Reset` sont des méthodes facultatives que vous pouvez fournir pour une propriété, si la propriété n’a pas de valeur par défaut simple.</span><span class="sxs-lookup"><span data-stu-id="afb6b-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="afb6b-104">Si la propriété a une valeur par défaut simple, vous devez appliquer <xref:System.ComponentModel.DefaultValueAttribute> et fournir la valeur par défaut au constructeur de classe d’attributs à la place.</span><span class="sxs-lookup"><span data-stu-id="afb6b-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="afb6b-105">L’un ou l’autre de ces mécanismes active les fonctionnalités suivantes dans le concepteur:</span><span class="sxs-lookup"><span data-stu-id="afb6b-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="afb6b-106">La propriété fournit une indication visuelle dans l’Explorateur de propriétés si elle a été modifiée à partir de sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="afb6b-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="afb6b-107">L’utilisateur peut cliquer avec le bouton droit sur la propriété et choisir **Réinitialiser** pour rétablir la valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="afb6b-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="afb6b-108">Le concepteur génère du code plus efficace.</span><span class="sxs-lookup"><span data-stu-id="afb6b-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="afb6b-109">Appliquez ou fournissez <xref:System.ComponentModel.DefaultValueAttribute> `Reset`les méthodes *PropertyName* et `ShouldSerialize` *PropertyName* .</span><span class="sxs-lookup"><span data-stu-id="afb6b-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="afb6b-110">N’utilisez pas les deux.</span><span class="sxs-lookup"><span data-stu-id="afb6b-110">Do not use both.</span></span>

 <span data-ttu-id="afb6b-111">La `Reset`méthode *PropertyName* affecte à une propriété sa valeur par défaut, comme indiqué dans le fragment de code suivant.</span><span class="sxs-lookup"><span data-stu-id="afb6b-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

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
> <span data-ttu-id="afb6b-112">Si une propriété n’a pas de `Reset` méthode, qu’elle n’est pas <xref:System.ComponentModel.DefaultValueAttribute>marquée avec un et qu’elle n’a pas de valeur par défaut fournie `Reset` dans sa déclaration, l’option de cette propriété est désactivée dans le menu contextuel de la fenêtre **Propriétés** de Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="afb6b-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="afb6b-113">Les concepteurs tels que Visual Studio `ShouldSerialize`utilisent la méthode *PropertyName* pour vérifier si une propriété a été modifiée par rapport à sa valeur par défaut et écrire du code dans le formulaire uniquement si une propriété a été modifiée, ce qui permet une génération de code plus efficace.</span><span class="sxs-lookup"><span data-stu-id="afb6b-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="afb6b-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="afb6b-114">For example:</span></span>

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

 <span data-ttu-id="afb6b-115">Vous trouverez ci-dessous un exemple de code complet.</span><span class="sxs-lookup"><span data-stu-id="afb6b-115">A complete code example follows.</span></span>

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

 <span data-ttu-id="afb6b-116">Dans ce cas, même lorsque la valeur de la variable privée accessible par la `MyFont` propriété est `null`, l’Explorateur de propriétés ne s' `null`affiche pas; à la place <xref:System.Windows.Forms.Control.Font%2A> , il affiche la propriété du parent, si `null`ce n’est pas le cas, ou la valeur <xref:System.Windows.Forms.Control.Font%2A> par défaut définie <xref:System.Windows.Forms.Control>dans.</span><span class="sxs-lookup"><span data-stu-id="afb6b-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="afb6b-117">Par conséquent, la valeur `MyFont` par défaut pour ne peut pas être <xref:System.ComponentModel.DefaultValueAttribute> simplement définie et un ne peut pas être appliqué à cette propriété.</span><span class="sxs-lookup"><span data-stu-id="afb6b-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="afb6b-118">Au lieu de `ShouldSerialize` cela `Reset` , les méthodes et doivent être `MyFont` implémentées pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="afb6b-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="afb6b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb6b-119">See also</span></span>

- [<span data-ttu-id="afb6b-120">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="afb6b-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="afb6b-121">Définition d’une propriété</span><span class="sxs-lookup"><span data-stu-id="afb6b-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="afb6b-122">Événements de modification de propriété</span><span class="sxs-lookup"><span data-stu-id="afb6b-122">Property-Changed Events</span></span>](property-changed-events.md)
