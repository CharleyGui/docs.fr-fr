---
title: Contrôles dessinés par l'utilisateur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: 50036f5bef323368b4970a080ca7a70cf94252d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966486"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="5ec2b-102">Contrôles dessinés par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5ec2b-102">User-Drawn Controls</span></span>
<span data-ttu-id="5ec2b-103">Le .NET Framework vous permet de développer facilement vos propres contrôles.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="5ec2b-104">Vous pouvez créer un contrôle utilisateur, qui est un ensemble de contrôles standard liés ensemble par du code, ou vous pouvez concevoir votre propre contrôle à partir de zéro.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="5ec2b-105">Vous pouvez même utiliser l’héritage pour créer un contrôle qui hérite d’un contrôle existant et l’ajouter à ses fonctionnalités inhérentes.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="5ec2b-106">Quelle que soit l’approche que vous utilisez, le .NET Framework fournit les fonctionnalités permettant de dessiner une interface graphique personnalisée pour n’importe quel contrôle que vous créez.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="5ec2b-107">La peinture d’un contrôle est effectuée par l’exécution de code dans la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="5ec2b-108">L’argument unique de la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode est un <xref:System.Windows.Forms.PaintEventArgs> objet qui fournit toutes les informations et les fonctionnalités requises pour restituer votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="5ec2b-109"><xref:System.Windows.Forms.PaintEventArgs> Fournit comme propriétés deux objets principal qui seront utilisés dans le rendu de votre contrôle:</span><span class="sxs-lookup"><span data-stu-id="5ec2b-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="5ec2b-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>Object: rectangle qui représente la partie du contrôle qui sera dessinée.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="5ec2b-111">Il peut s’agir du contrôle entier ou d’une partie du contrôle en fonction de la façon dont le contrôle est dessiné.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="5ec2b-112"><xref:System.Drawing.Graphics>objet: encapsule plusieurs objets et méthodes graphiques qui fournissent les fonctionnalités nécessaires pour dessiner votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="5ec2b-113">Pour plus d’informations sur <xref:System.Drawing.Graphics> l’objet et sur son utilisation, consultez [procédure: Créez des objets graphiques pour](../advanced/how-to-create-graphics-objects-for-drawing.md)le dessin.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="5ec2b-114">L' <xref:System.Windows.Forms.Control.OnPaint%2A> événement est déclenché chaque fois que le contrôle est dessiné ou actualisé à l’écran, et l' <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objet représente le rectangle dans lequel la peinture aura lieu.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="5ec2b-115">Si l’intégralité du contrôle doit être actualisée, le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> représentera la taille de l’ensemble du contrôle.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="5ec2b-116">Toutefois, si seule une partie du contrôle doit être actualisée, l' <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objet ne représente que la région qui doit être redessinée.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="5ec2b-117">C’est le cas, par exemple, lorsqu’un contrôle était partiellement masqué par un autre contrôle ou formulaire dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="5ec2b-118">Lorsque vous héritez de <xref:System.Windows.Forms.Control> la classe, vous devez substituer <xref:System.Windows.Forms.Control.OnPaint%2A> la méthode et fournir le code de rendu graphique dans.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="5ec2b-119">Si vous souhaitez fournir une interface graphique personnalisée à un contrôle utilisateur ou à un contrôle hérité, vous pouvez également le faire en substituant la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="5ec2b-120">Un exemple est illustré ci-dessous:</span><span class="sxs-lookup"><span data-stu-id="5ec2b-120">An example is shown below:</span></span>  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
         this.Size));  
   }
}  
```  
  
 <span data-ttu-id="5ec2b-121">L’exemple précédent montre comment restituer un contrôle avec une représentation graphique très simple.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="5ec2b-122">Elle appelle la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de la classe de base, elle crée <xref:System.Drawing.Pen> un objet avec lequel dessiner, puis dessine une ellipse dans <xref:System.Windows.Forms.Control.Location%2A> le rectangle déterminé par et <xref:System.Windows.Forms.Control.Size%2A> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="5ec2b-123">Bien que la plupart des codes de rendu soient beaucoup plus compliqués, cet exemple illustre l’utilisation <xref:System.Drawing.Graphics> de l’objet contenu <xref:System.Windows.Forms.PaintEventArgs> dans l’objet.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="5ec2b-124">Notez que si vous héritez d’une classe qui possède déjà une représentation graphique, telle que <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Button>, et que vous ne souhaitez pas incorporer cette représentation dans votre rendu, vous ne devez pas appeler la classe de <xref:System.Windows.Forms.Control.OnPaint%2A> base méthode.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="5ec2b-125">Le code de la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de votre contrôle s’exécute lorsque le contrôle est dessiné pour la première fois, et chaque fois qu’il est actualisé.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="5ec2b-126">Pour vous assurer que votre contrôle est redessiné chaque fois qu’il est redimensionné, ajoutez la ligne suivante au constructeur de votre contrôle:</span><span class="sxs-lookup"><span data-stu-id="5ec2b-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="5ec2b-127">Utilisez la <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> propriété pour implémenter un contrôle non rectangulaire.</span><span class="sxs-lookup"><span data-stu-id="5ec2b-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec2b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ec2b-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="5ec2b-129">Guide pratique pour Créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="5ec2b-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="5ec2b-130">Contrôles constitutifs</span><span class="sxs-lookup"><span data-stu-id="5ec2b-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="5ec2b-131">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="5ec2b-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
