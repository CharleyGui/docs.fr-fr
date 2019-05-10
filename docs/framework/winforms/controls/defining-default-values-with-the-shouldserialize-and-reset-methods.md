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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="4962c-102">Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset</span><span class="sxs-lookup"><span data-stu-id="4962c-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="4962c-103">`ShouldSerialize` et `Reset` sont des méthodes facultatives que vous pouvez fournir pour une propriété, si la propriété n’a pas un ont la valeur par défaut simple.</span><span class="sxs-lookup"><span data-stu-id="4962c-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="4962c-104">Si la propriété a une valeur par défaut simple, vous devez appliquer le <xref:System.ComponentModel.DefaultValueAttribute> et fournir la valeur par défaut pour le constructeur de classe d’attribut à la place.</span><span class="sxs-lookup"><span data-stu-id="4962c-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="4962c-105">Ces deux mécanismes Active les fonctionnalités suivantes dans le concepteur :</span><span class="sxs-lookup"><span data-stu-id="4962c-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="4962c-106">La propriété fournit une indication visuelle dans l’Explorateur de propriétés s’il a été modifié à partir de sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4962c-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="4962c-107">L’utilisateur avec le bouton droit sur la propriété et choisissez **réinitialiser** pour restaurer la propriété à sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4962c-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="4962c-108">Le concepteur génère du code plus efficace.</span><span class="sxs-lookup"><span data-stu-id="4962c-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4962c-109">Appliquez le <xref:System.ComponentModel.DefaultValueAttribute> ou fournir `Reset` *PropertyName* et `ShouldSerialize` *PropertyName* méthodes.</span><span class="sxs-lookup"><span data-stu-id="4962c-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="4962c-110">N’utilisez pas les deux.</span><span class="sxs-lookup"><span data-stu-id="4962c-110">Do not use both.</span></span>

 <span data-ttu-id="4962c-111">Le `Reset` *PropertyName* méthode définit une propriété à sa valeur par défaut, comme illustré dans le fragment de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4962c-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

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
>  <span data-ttu-id="4962c-112">Si une propriété n’a pas un `Reset` (méthode), n’est pas marqué avec un <xref:System.ComponentModel.DefaultValueAttribute>et n’a pas de valeur par défaut fournie dans sa déclaration, le `Reset` option de cette propriété est désactivée dans le menu contextuel de la **propriétés** fenêtre du Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4962c-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="4962c-113">Utilisent des concepteurs, tels que Visual Studio le `ShouldSerialize` *PropertyName* méthode pour vérifier si une propriété a changé sa valeur par défaut et d’écrire du code dans le formulaire uniquement si une propriété est modifiée, ce qui permet de code plus efficace génération.</span><span class="sxs-lookup"><span data-stu-id="4962c-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="4962c-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="4962c-114">For example:</span></span>

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

 <span data-ttu-id="4962c-115">Un exemple de code complet suit.</span><span class="sxs-lookup"><span data-stu-id="4962c-115">A complete code example follows.</span></span>

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

 <span data-ttu-id="4962c-116">Dans ce cas, même lorsque la valeur de la variable privée est accessible par le `MyFont` propriété est `null`, l’Explorateur de propriétés n’affiche pas `null`; au lieu de cela, il affiche le <xref:System.Windows.Forms.Control.Font%2A> propriété du parent, si elle n’est pas `null`, ou la valeur par défaut <xref:System.Windows.Forms.Control.Font%2A> valeur définie dans <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="4962c-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="4962c-117">Par conséquent, la valeur par défaut `MyFont` ne peut pas être simplement définie et un <xref:System.ComponentModel.DefaultValueAttribute> ne peut pas être appliqué à cette propriété.</span><span class="sxs-lookup"><span data-stu-id="4962c-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="4962c-118">Au lieu de cela, le `ShouldSerialize` et `Reset` méthodes doivent être implémentées pour la `MyFont` propriété.</span><span class="sxs-lookup"><span data-stu-id="4962c-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="4962c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4962c-119">See also</span></span>

- [<span data-ttu-id="4962c-120">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4962c-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="4962c-121">Définition d’une propriété</span><span class="sxs-lookup"><span data-stu-id="4962c-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="4962c-122">Événements de modification de propriété</span><span class="sxs-lookup"><span data-stu-id="4962c-122">Property-Changed Events</span></span>](property-changed-events.md)
