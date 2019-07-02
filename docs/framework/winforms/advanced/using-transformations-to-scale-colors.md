---
title: Utilisation de transformations pour mettre à l'échelle des couleurs
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 81c0ddf5b937d604559a9eb1a8b598885546c97f
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504960"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="7ba15-102">Utilisation de transformations pour mettre à l'échelle des couleurs</span><span class="sxs-lookup"><span data-stu-id="7ba15-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="7ba15-103">Une transformation de mise à l’échelle multiplie une ou plusieurs des quatre composantes de couleur par un nombre.</span><span class="sxs-lookup"><span data-stu-id="7ba15-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="7ba15-104">Les entrées de matrice de couleurs qui représentent la mise à l’échelle sont présentées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="7ba15-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="7ba15-105">Composant à l’échelle</span><span class="sxs-lookup"><span data-stu-id="7ba15-105">Component to be scaled</span></span>|<span data-ttu-id="7ba15-106">Entrée de la matrice</span><span class="sxs-lookup"><span data-stu-id="7ba15-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="7ba15-107">Rouge</span><span class="sxs-lookup"><span data-stu-id="7ba15-107">Red</span></span>|<span data-ttu-id="7ba15-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="7ba15-108">[0][0]</span></span>|  
|<span data-ttu-id="7ba15-109">Vert</span><span class="sxs-lookup"><span data-stu-id="7ba15-109">Green</span></span>|<span data-ttu-id="7ba15-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="7ba15-110">[1][1]</span></span>|  
|<span data-ttu-id="7ba15-111">Bleu</span><span class="sxs-lookup"><span data-stu-id="7ba15-111">Blue</span></span>|<span data-ttu-id="7ba15-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="7ba15-112">[2][2]</span></span>|  
|<span data-ttu-id="7ba15-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="7ba15-113">Alpha</span></span>|<span data-ttu-id="7ba15-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="7ba15-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="7ba15-115">Mise à l’échelle d’une couleur</span><span class="sxs-lookup"><span data-stu-id="7ba15-115">Scaling One Color</span></span>  
 <span data-ttu-id="7ba15-116">L’exemple suivant construit un <xref:System.Drawing.Image> objet à partir du fichier ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="7ba15-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="7ba15-117">Puis le code met à l’échelle le composant bleu de chaque pixel dans l’image d’un facteur de 2.</span><span class="sxs-lookup"><span data-stu-id="7ba15-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="7ba15-118">L’image d’origine est dessinée en même temps que l’image transformée.</span><span class="sxs-lookup"><span data-stu-id="7ba15-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="7ba15-119">L’illustration suivante montre l’image d’origine sur la gauche et l’image à l’échelle sur la droite :</span><span class="sxs-lookup"><span data-stu-id="7ba15-119">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Capture d’écran qui compare les couleurs d’origine et à l’échelle.](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 <span data-ttu-id="7ba15-121">Le tableau suivant répertorie les vecteurs de couleur pour les quatre barres avant et après la mise à l’échelle bleu.</span><span class="sxs-lookup"><span data-stu-id="7ba15-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="7ba15-122">Notez que le composant bleu dans la quatrième barre de couleurs est passé de 0,8 à 0,6.</span><span class="sxs-lookup"><span data-stu-id="7ba15-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="7ba15-123">C’est parce que GDI + conserve uniquement la partie fractionnaire du résultat.</span><span class="sxs-lookup"><span data-stu-id="7ba15-123">That is because GDI+ retains only the fractional part of the result.</span></span> <span data-ttu-id="7ba15-124">Par exemple, (2)(0.8) = 1.6, et la partie fractionnaire de 1,6 est 0,6.</span><span class="sxs-lookup"><span data-stu-id="7ba15-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="7ba15-125">En conservant uniquement la partie fractionnaire garantit que le résultat est toujours dans l’intervalle [0, 1].</span><span class="sxs-lookup"><span data-stu-id="7ba15-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="7ba15-126">D'origine</span><span class="sxs-lookup"><span data-stu-id="7ba15-126">Original</span></span>|<span data-ttu-id="7ba15-127">Mise à l’échelle</span><span class="sxs-lookup"><span data-stu-id="7ba15-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="7ba15-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="7ba15-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="7ba15-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="7ba15-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="7ba15-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="7ba15-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="7ba15-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="7ba15-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="7ba15-136">Mise à l’échelle de plusieurs couleurs</span><span class="sxs-lookup"><span data-stu-id="7ba15-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="7ba15-137">L’exemple suivant construit un <xref:System.Drawing.Image> objet à partir du fichier ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="7ba15-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="7ba15-138">Ensuite, le code ajuste les composants rouges, vert et bleus de chaque pixel de l’image.</span><span class="sxs-lookup"><span data-stu-id="7ba15-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="7ba15-139">Les composants rouge sont diminués de 25 pour cent, les composants de couleur vertes sont diminués 35 pour cent, et les composants bleus sont diminués de 50 pour cent.</span><span class="sxs-lookup"><span data-stu-id="7ba15-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="7ba15-140">L’illustration suivante montre l’image d’origine sur la gauche et l’image à l’échelle sur la droite :</span><span class="sxs-lookup"><span data-stu-id="7ba15-140">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Capture d’écran qui compare les couleurs d’origine et à l’échelle.](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 <span data-ttu-id="7ba15-142">Le tableau suivant répertorie les vecteurs de couleur pour les quatre barres avant et après le rouge, vert et bleu mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="7ba15-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="7ba15-143">D'origine</span><span class="sxs-lookup"><span data-stu-id="7ba15-143">Original</span></span>|<span data-ttu-id="7ba15-144">Mise à l’échelle</span><span class="sxs-lookup"><span data-stu-id="7ba15-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="7ba15-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="7ba15-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="7ba15-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="7ba15-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="7ba15-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="7ba15-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="7ba15-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="7ba15-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="7ba15-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ba15-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ba15-153">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="7ba15-154">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ba15-154">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="7ba15-155">Recoloriage des images</span><span class="sxs-lookup"><span data-stu-id="7ba15-155">Recoloring Images</span></span>](recoloring-images.md)
