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
ms.openlocfilehash: 863726a6264f01de9f00296b4a64b9fd1bb96765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182032"
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="95220-102">Substitution de la méthode OnPaint</span><span class="sxs-lookup"><span data-stu-id="95220-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="95220-103">Les étapes de base pour prépondérer tout événement défini dans le cadre .NET sont identiques et sont résumées dans la liste suivante.</span><span class="sxs-lookup"><span data-stu-id="95220-103">The basic steps for overriding any event defined in the .NET Framework are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="95220-104">Remplacer un événement héréditaire</span><span class="sxs-lookup"><span data-stu-id="95220-104">To override an inherited event</span></span>  
  
1. <span data-ttu-id="95220-105">Remplacer la `On`méthode *protégée EventName.*</span><span class="sxs-lookup"><span data-stu-id="95220-105">Override the protected `On`*EventName* method.</span></span>  
  
2. <span data-ttu-id="95220-106">Appelez `On`la méthode *EventName* de la classe `On`de base à partir de la méthode *EventName,* de sorte que les délégués inscrits reçoivent l’événement.</span><span class="sxs-lookup"><span data-stu-id="95220-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="95220-107">L’événement <xref:System.Windows.Forms.Control.Paint> est discuté en détail ici parce <xref:System.Windows.Forms.Control.Paint> que chaque contrôle <xref:System.Windows.Forms.Control>des formulaires Windows doit remplacer l’événement dont il hérite .</span><span class="sxs-lookup"><span data-stu-id="95220-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="95220-108">La <xref:System.Windows.Forms.Control> classe de base ne sait pas comment un contrôle dérivé doit <xref:System.Windows.Forms.Control.OnPaint%2A> être dessiné et ne fournit aucune logique de peinture dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="95220-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="95220-109">La <xref:System.Windows.Forms.Control.OnPaint%2A> méthode <xref:System.Windows.Forms.Control> de simplement <xref:System.Windows.Forms.Control.Paint> envoyer l’événement aux récepteurs d’événements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="95220-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="95220-110">Si vous avez travaillé à travers l’échantillon dans [Comment: Développer un contrôle simple des formulaires Windows](how-to-develop-a-simple-windows-forms-control.md), vous avez vu un exemple de dépassement de la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="95220-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="95220-111">Le fragment de code suivant provient de cet échantillon.</span><span class="sxs-lookup"><span data-stu-id="95220-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="95220-112">La <xref:System.Windows.Forms.PaintEventArgs> classe contient <xref:System.Windows.Forms.Control.Paint> des données pour l’événement.</span><span class="sxs-lookup"><span data-stu-id="95220-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="95220-113">Il a deux propriétés, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="95220-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="95220-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>est le rectangle à peindre, et <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> la <xref:System.Drawing.Graphics> propriété se réfère à un objet.</span><span class="sxs-lookup"><span data-stu-id="95220-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="95220-115">Les classes <xref:System.Drawing?displayProperty=nameWithType> dans l’espace de nom sont des classes gérées qui donnent accès à la fonctionnalité de GDI, la nouvelle bibliothèque graphique Windows.</span><span class="sxs-lookup"><span data-stu-id="95220-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of GDI+, the new Windows graphics library.</span></span> <span data-ttu-id="95220-116">L’objet <xref:System.Drawing.Graphics> a des méthodes pour dessiner des points, des cordes, des lignes, des arcs, des ellipses, et beaucoup d’autres formes.</span><span class="sxs-lookup"><span data-stu-id="95220-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="95220-117">Un contrôle invoque sa <xref:System.Windows.Forms.Control.OnPaint%2A> méthode chaque fois qu’il a besoin de changer son affichage visuel.</span><span class="sxs-lookup"><span data-stu-id="95220-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="95220-118">Cette méthode soulève <xref:System.Windows.Forms.Control.Paint> à son tour l’événement.</span><span class="sxs-lookup"><span data-stu-id="95220-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95220-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95220-119">See also</span></span>

- [<span data-ttu-id="95220-120">Événements</span><span class="sxs-lookup"><span data-stu-id="95220-120">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="95220-121">Rendu d'un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95220-121">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)
- [<span data-ttu-id="95220-122">Définition d’un événement</span><span class="sxs-lookup"><span data-stu-id="95220-122">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
