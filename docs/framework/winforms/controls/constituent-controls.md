---
title: Contrôles constitutifs
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 2865a3d85bd56151038ee90c18d199d3a584b5d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182413"
---
# <a name="constituent-controls"></a><span data-ttu-id="64f9b-102">Contrôles constitutifs</span><span class="sxs-lookup"><span data-stu-id="64f9b-102">Constituent Controls</span></span>
<span data-ttu-id="64f9b-103">Les contrôles qui composent un contrôle utilisateur, appelés *contrôles constitutifs*, sont relativement peu flexibles en matière de rendu graphique personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64f9b-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="64f9b-104">Tous les contrôles Windows Forms gèrent <xref:System.Windows.Forms.Control.OnPaint%2A> leur propre rendu à travers leur propre méthode.</span><span class="sxs-lookup"><span data-stu-id="64f9b-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="64f9b-105">Comme cette méthode est protégée, elle n’est pas accessible au développeur et il n’est pas possible d’empêcher son exécution quand le contrôle est dessiné.</span><span class="sxs-lookup"><span data-stu-id="64f9b-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="64f9b-106">Cela ne signifie pas pour autant que vous ne pouvez pas ajouter du code pour modifier l’apparence des contrôles constitutifs.</span><span class="sxs-lookup"><span data-stu-id="64f9b-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="64f9b-107">Un rendu supplémentaire est possible en ajoutant un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="64f9b-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="64f9b-108">Par exemple, supposons que <xref:System.Windows.Forms.UserControl> vous étiez `MyButton`l’auteur d’un bouton nommé .</span><span class="sxs-lookup"><span data-stu-id="64f9b-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="64f9b-109">Si vous souhaitez avoir un rendu supplémentaire <xref:System.Web.UI.WebControls.Button>au-delà de ce qui a été fourni par le , vous ajouteriez du code à votre contrôle utilisateur similaire à ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="64f9b-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="64f9b-110">Certains contrôles de formulaires Windows, tels que <xref:System.Windows.Forms.TextBox>, sont peints directement par Windows.</span><span class="sxs-lookup"><span data-stu-id="64f9b-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="64f9b-111">Dans ces cas, la méthode n’est <xref:System.Windows.Forms.Control.OnPaint%2A> jamais appelée, et donc l’exemple ci-dessus ne sera jamais appelé.</span><span class="sxs-lookup"><span data-stu-id="64f9b-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="64f9b-112">Ceci crée une méthode qui s’exécute chaque fois que l’événement `MyButton.Paint` s’exécute, ce qui ajoute une représentation graphique supplémentaire à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="64f9b-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="64f9b-113">Notez que ceci n’empêche pas l’exécution de `MyButton.OnPaint`, et tout le dessin généralement effectué par un bouton est donc exécuté en plus de votre dessin personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64f9b-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="64f9b-114">Pour plus d’informations sur la technologie GDI+ et le rendu personnalisé, consultez [Création d’images graphiques avec GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="64f9b-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="64f9b-115">Si vous voulez avoir une représentation unique de votre contrôle, le mieux est de créer un contrôle hérité et d’écrire pour celui-ci du code de rendu personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64f9b-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="64f9b-116">Pour plus d’informations, consultez [Contrôles dessinés par l’utilisateur](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="64f9b-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f9b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64f9b-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="64f9b-118">Contrôles dessinés par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="64f9b-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="64f9b-119">Comment : créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="64f9b-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="64f9b-120">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="64f9b-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
