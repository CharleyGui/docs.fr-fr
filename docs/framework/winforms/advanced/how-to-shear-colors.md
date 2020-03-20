---
title: 'Comment : altérer des couleurs'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142392"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="78899-102">Comment : altérer des couleurs</span><span class="sxs-lookup"><span data-stu-id="78899-102">How to: Shear Colors</span></span>
<span data-ttu-id="78899-103">La tonte augmente ou diminue un composant de couleur d’une quantité proportionnelle à un autre composant de couleur.</span><span class="sxs-lookup"><span data-stu-id="78899-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="78899-104">Par exemple, considérez la transformation où la composante rouge est augmentée de la moitié de la valeur du composant bleu.</span><span class="sxs-lookup"><span data-stu-id="78899-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="78899-105">Dans le cadre d’une telle transformation, la couleur (0,2, 0,5, 1) deviendrait (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="78899-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="78899-106">Le nouveau composant rouge est de 0,2 euro (1/2)(1) à 0,7.</span><span class="sxs-lookup"><span data-stu-id="78899-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78899-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="78899-107">Example</span></span>  
 <span data-ttu-id="78899-108">L’exemple suivant <xref:System.Drawing.Image> construit un objet à partir du fichier ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="78899-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="78899-109">Ensuite, le code applique la transformation de cisaillement décrite dans le paragraphe précédent à chaque pixel de l’image.</span><span class="sxs-lookup"><span data-stu-id="78899-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="78899-110">L’illustration suivante montre l’image originale à gauche et l’image cisaillement à droite :</span><span class="sxs-lookup"><span data-stu-id="78899-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span>
  
 ![Deux carrés avec des rayures colorées côte à côte illustrant l’image originale et l’image cisaillement.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="78899-112">Le tableau suivant répertorie les vecteurs de couleur des quatre barres avant et après la transformation de tonte.</span><span class="sxs-lookup"><span data-stu-id="78899-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="78899-113">Original</span><span class="sxs-lookup"><span data-stu-id="78899-113">Original</span></span>|<span data-ttu-id="78899-114">Cisaillée</span><span class="sxs-lookup"><span data-stu-id="78899-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="78899-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="78899-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="78899-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="78899-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="78899-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="78899-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="78899-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="78899-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="78899-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="78899-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="78899-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="78899-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="78899-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="78899-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="78899-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="78899-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78899-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="78899-123">Compiling the Code</span></span>  
 <span data-ttu-id="78899-124">L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e`utilisation avec Windows Forms, et il nécessite , qui est un paramètre du gestionnaire d’événements. <xref:System.Windows.Forms.Control.Paint></span><span class="sxs-lookup"><span data-stu-id="78899-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="78899-125">Remplacez-le par `ColorBars.bmp` un nom d’image et un chemin valables sur votre système.</span><span class="sxs-lookup"><span data-stu-id="78899-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78899-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78899-126">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="78899-127">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78899-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="78899-128">Recoloriage des images</span><span class="sxs-lookup"><span data-stu-id="78899-128">Recoloring Images</span></span>](recoloring-images.md)
