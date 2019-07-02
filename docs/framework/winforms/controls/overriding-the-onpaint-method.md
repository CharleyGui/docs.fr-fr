---
title: Substitution de la méthode OnPaint
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: e3c48aec830cdc3ccceb8683f93e3a99ee6364e2
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506196"
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="87a86-102">Substitution de la méthode OnPaint</span><span class="sxs-lookup"><span data-stu-id="87a86-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="87a86-103">Les étapes de base pour la substitution d’un événement défini dans le .NET Framework sont identiques et sont résumés dans la liste suivante.</span><span class="sxs-lookup"><span data-stu-id="87a86-103">The basic steps for overriding any event defined in the .NET Framework are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="87a86-104">Pour remplacer un événement hérité</span><span class="sxs-lookup"><span data-stu-id="87a86-104">To override an inherited event</span></span>  
  
1. <span data-ttu-id="87a86-105">Remplacer l’élément protégé `On` *EventName* (méthode).</span><span class="sxs-lookup"><span data-stu-id="87a86-105">Override the protected `On`*EventName* method.</span></span>  
  
2. <span data-ttu-id="87a86-106">Appeler le `On` *EventName* méthode de la classe de base à partir de l’élément substitué `On` *EventName* (méthode), afin que les délégués inscrits reçoivent l’événement.</span><span class="sxs-lookup"><span data-stu-id="87a86-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="87a86-107">Le <xref:System.Windows.Forms.Control.Paint> événement est décrit en détail ici, car tous les contrôles Windows Forms doivent substituer la <xref:System.Windows.Forms.Control.Paint> événement qu’il hérite <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="87a86-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="87a86-108">La base de <xref:System.Windows.Forms.Control> classe ne sait pas comment un contrôle dérivé doit être dessiné et ne fournit pas de logique de peinture dans le <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="87a86-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="87a86-109">Le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de <xref:System.Windows.Forms.Control> distribue simplement le <xref:System.Windows.Forms.Control.Paint> événement aux récepteurs d’événements inscrits.</span><span class="sxs-lookup"><span data-stu-id="87a86-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="87a86-110">Si vous avez utilisé l’exemple dans [Comment : Développer un contrôle de formulaires Windows Simple](how-to-develop-a-simple-windows-forms-control.md), vous avez vu un exemple de substitution le <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="87a86-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="87a86-111">Le fragment de code suivant provient de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="87a86-111">The following code fragment is taken from that sample.</span></span>  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <span data-ttu-id="87a86-112">Le <xref:System.Windows.Forms.PaintEventArgs> classe contient des données pour le <xref:System.Windows.Forms.Control.Paint> événement.</span><span class="sxs-lookup"><span data-stu-id="87a86-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="87a86-113">Il a deux propriétés, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="87a86-113">It has two properties, as shown in the following code.</span></span>  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <span data-ttu-id="87a86-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est le rectangle à peindre et la <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> propriété fait référence à un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="87a86-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="87a86-115">Les classes dans le <xref:System.Drawing?displayProperty=nameWithType> espace de noms sont gérés les classes qui fournissent l’accès aux fonctionnalités de GDI +, la nouvelle bibliothèque de graphiques Windows.</span><span class="sxs-lookup"><span data-stu-id="87a86-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of GDI+, the new Windows graphics library.</span></span> <span data-ttu-id="87a86-116">Le <xref:System.Drawing.Graphics> objet possède des méthodes pour dessiner des points, chaînes, lignes, arcs, points de suspension et de nombreuses autres formes.</span><span class="sxs-lookup"><span data-stu-id="87a86-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="87a86-117">Un contrôle appelle son <xref:System.Windows.Forms.Control.OnPaint%2A> méthode chaque fois qu’il doit modifier son affichage visuel.</span><span class="sxs-lookup"><span data-stu-id="87a86-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="87a86-118">Cette méthode déclenche à son tour le <xref:System.Windows.Forms.Control.Paint> événement.</span><span class="sxs-lookup"><span data-stu-id="87a86-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a86-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87a86-119">See also</span></span>

- [<span data-ttu-id="87a86-120">Événements</span><span class="sxs-lookup"><span data-stu-id="87a86-120">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="87a86-121">Rendu d'un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87a86-121">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)
- [<span data-ttu-id="87a86-122">Définition d’un événement</span><span class="sxs-lookup"><span data-stu-id="87a86-122">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
