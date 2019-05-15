---
title: 'Procédure : utiliser un stylet pour dessiner des lignes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 263c0fbda377e64753cd2d607f633117b4b44253
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593147"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="84187-102">Procédure : utiliser un stylet pour dessiner des lignes</span><span class="sxs-lookup"><span data-stu-id="84187-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="84187-103">Pour dessiner des lignes, vous devez un <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet.</span><span class="sxs-lookup"><span data-stu-id="84187-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="84187-104">Le <xref:System.Drawing.Graphics> objet fournit les <xref:System.Drawing.Graphics.DrawLine%2A> (méthode) et le <xref:System.Drawing.Pen> objet stocke les fonctionnalités de la ligne, telles que la couleur et la largeur.</span><span class="sxs-lookup"><span data-stu-id="84187-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84187-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="84187-105">Example</span></span>  
 <span data-ttu-id="84187-106">L’exemple suivant dessine une ligne à partir de (20, 10) à (300, 100).</span><span class="sxs-lookup"><span data-stu-id="84187-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="84187-107">La première instruction utilise le <xref:System.Drawing.Pen.%23ctor%2A> constructeur de classe pour créer un stylet noir.</span><span class="sxs-lookup"><span data-stu-id="84187-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="84187-108">L’argument passé à la <xref:System.Drawing.Pen.%23ctor%2A> constructeur est un <xref:System.Drawing.Color> objet créé avec le <xref:System.Drawing.Color.FromArgb%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="84187-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="84187-109">Les valeurs utilisées pour créer le <xref:System.Drawing.Color> objet — (255, 0, 0, 0), correspondent aux composants alphabétiques, rouges, vert et bleus de la couleur.</span><span class="sxs-lookup"><span data-stu-id="84187-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="84187-110">Ces valeurs définissent un stylet noir opaque.</span><span class="sxs-lookup"><span data-stu-id="84187-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84187-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="84187-111">Compiling the Code</span></span>  
 <span data-ttu-id="84187-112">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="84187-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84187-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84187-113">See also</span></span>

- <xref:System.Drawing.Pen>
- [<span data-ttu-id="84187-114">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="84187-114">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="84187-115">Stylets, lignes et rectangles dans GDI+</span><span class="sxs-lookup"><span data-stu-id="84187-115">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
