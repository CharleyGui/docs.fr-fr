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
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182007"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="01e44-102">Contrôles dessinés par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="01e44-102">User-Drawn Controls</span></span>
<span data-ttu-id="01e44-103">Le cadre .NET vous offre la possibilité de développer facilement vos propres contrôles.</span><span class="sxs-lookup"><span data-stu-id="01e44-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="01e44-104">Vous pouvez créer un contrôle utilisateur, qui est un ensemble de contrôles standard liés entre eux par code, ou vous pouvez concevoir votre propre contrôle à partir de zéro.</span><span class="sxs-lookup"><span data-stu-id="01e44-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="01e44-105">Vous pouvez même utiliser l’héritage pour créer un contrôle qui hérite d’un contrôle existant et ajouter à sa fonctionnalité inhérente.</span><span class="sxs-lookup"><span data-stu-id="01e44-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="01e44-106">Quelle que soit l’approche que vous utilisez, le cadre .NET fournit la fonctionnalité pour dessiner une interface graphique personnalisée pour tout contrôle que vous créez.</span><span class="sxs-lookup"><span data-stu-id="01e44-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="01e44-107">La peinture d’un contrôle est accomplie par <xref:System.Windows.Forms.Control.OnPaint%2A> l’exécution du code dans la méthode du contrôle.</span><span class="sxs-lookup"><span data-stu-id="01e44-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="01e44-108">L’argument unique <xref:System.Windows.Forms.Control.OnPaint%2A> de <xref:System.Windows.Forms.PaintEventArgs> la méthode est un objet qui fournit toutes les informations et fonctionnalités nécessaires pour rendre votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="01e44-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="01e44-109">Les <xref:System.Windows.Forms.PaintEventArgs> fournit comme propriétés deux objets principaux qui seront utilisés dans le rendu de votre contrôle:</span><span class="sxs-lookup"><span data-stu-id="01e44-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="01e44-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objet - le rectangle qui représente la partie du contrôle qui sera dessiné.</span><span class="sxs-lookup"><span data-stu-id="01e44-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="01e44-111">Cela peut être l’ensemble du contrôle, ou une partie du contrôle en fonction de la façon dont le contrôle est établi.</span><span class="sxs-lookup"><span data-stu-id="01e44-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="01e44-112"><xref:System.Drawing.Graphics>objet - encapsule plusieurs objets et méthodes graphiques qui fournissent la fonctionnalité nécessaire pour dessiner votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="01e44-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="01e44-113">Pour plus d’informations sur l’objet et comment l’utiliser, <xref:System.Drawing.Graphics> voir Comment : Créer des objets [graphiques pour le dessin](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="01e44-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="01e44-114">L’événement <xref:System.Windows.Forms.Control.OnPaint%2A> est déclenché chaque fois que le contrôle <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est dessiné ou rafraîchi sur l’écran, et l’objet représente le rectangle dans lequel la peinture aura lieu.</span><span class="sxs-lookup"><span data-stu-id="01e44-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="01e44-115">Si l’ensemble du contrôle doit <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> être rafraîchi, le représentera la taille de l’ensemble du contrôle.</span><span class="sxs-lookup"><span data-stu-id="01e44-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="01e44-116">Si seulement une partie du contrôle doit être <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> rafraîchie, cependant, l’objet ne représentera que la région qui doit être redessinée.</span><span class="sxs-lookup"><span data-stu-id="01e44-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="01e44-117">Un exemple d’un tel cas serait quand un contrôle a été partiellement obscurci par un autre contrôle ou forme dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01e44-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="01e44-118">Lorsque vous héritez de la <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Control.OnPaint%2A> classe, vous devez passer outre à la méthode et fournir un code de rendu graphique à l’intérieur.</span><span class="sxs-lookup"><span data-stu-id="01e44-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="01e44-119">Si vous souhaitez fournir une interface graphique personnalisée à un contrôle utilisateur ou à un <xref:System.Windows.Forms.Control.OnPaint%2A> contrôle hérité, vous pouvez également le faire en l’emportent sur la méthode.</span><span class="sxs-lookup"><span data-stu-id="01e44-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="01e44-120">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="01e44-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="01e44-121">L’exemple précédent montre comment rendre un contrôle avec une représentation graphique très simple.</span><span class="sxs-lookup"><span data-stu-id="01e44-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="01e44-122">Il appelle <xref:System.Windows.Forms.Control.OnPaint%2A> la méthode de la <xref:System.Drawing.Pen> classe de base, il crée un objet avec lequel dessiner, et tire enfin une ellipse dans le rectangle déterminé par le <xref:System.Windows.Forms.Control.Location%2A> et <xref:System.Windows.Forms.Control.Size%2A> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="01e44-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="01e44-123">Bien que la plupart des codes de rendu seront beaucoup plus <xref:System.Drawing.Graphics> compliqués <xref:System.Windows.Forms.PaintEventArgs> que celui-ci, cet exemple démontre l’utilisation de l’objet contenu dans l’objet.</span><span class="sxs-lookup"><span data-stu-id="01e44-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="01e44-124">Notez que si vous héritez d’une classe qui <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>a déjà une représentation graphique, telle que ou, et que vous <xref:System.Windows.Forms.Control.OnPaint%2A> ne souhaitez pas intégrer cette représentation dans votre rendu, vous ne devriez pas appeler la méthode de votre classe de base.</span><span class="sxs-lookup"><span data-stu-id="01e44-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="01e44-125">Le code <xref:System.Windows.Forms.Control.OnPaint%2A> dans la méthode de votre contrôle s’exécute lorsque le contrôle est tiré pour la première fois, et chaque fois qu’il est actualisé.</span><span class="sxs-lookup"><span data-stu-id="01e44-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="01e44-126">Pour vous assurer que votre contrôle est redessiné chaque fois qu’il est resized, ajoutez la ligne suivante au constructeur de votre contrôle :</span><span class="sxs-lookup"><span data-stu-id="01e44-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="01e44-127">Utilisez <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> la propriété pour mettre en œuvre un contrôle non rectangulaire.</span><span class="sxs-lookup"><span data-stu-id="01e44-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e44-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01e44-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="01e44-129">Comment : créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="01e44-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="01e44-130">Contrôles constitutifs</span><span class="sxs-lookup"><span data-stu-id="01e44-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="01e44-131">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="01e44-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
