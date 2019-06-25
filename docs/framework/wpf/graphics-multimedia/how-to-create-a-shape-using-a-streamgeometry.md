---
title: 'Procédure : Créer une forme à l’aide d’un StreamGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: ce2097568349ad376540163f5fe05d6a3e5b0643
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348028"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="889b1-102">Procédure : Créer une forme à l’aide d’un StreamGeometry</span><span class="sxs-lookup"><span data-stu-id="889b1-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="889b1-103"><xref:System.Windows.Media.StreamGeometry> est une alternative légère à <xref:System.Windows.Media.PathGeometry> pour créer des formes géométriques.</span><span class="sxs-lookup"><span data-stu-id="889b1-103"><xref:System.Windows.Media.StreamGeometry> is lightweight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="889b1-104">Utilisez un <xref:System.Windows.Media.StreamGeometry> lorsque vous devez décrire une géométrie complexe mais ne souhaitez pas que la surcharge de prendre en charge la liaison de données, l’animation ou la modification.</span><span class="sxs-lookup"><span data-stu-id="889b1-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="889b1-105">Par exemple, en raison de son efficacité, la <xref:System.Windows.Media.StreamGeometry> classe est un bon choix pour décrire des ornements.</span><span class="sxs-lookup"><span data-stu-id="889b1-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="889b1-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="889b1-106">Example</span></span>  
 <span data-ttu-id="889b1-107">L’exemple suivant utilise la syntaxe d’attribut pour créer un triangulaire <xref:System.Windows.Media.StreamGeometry> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="889b1-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="889b1-108">Pour plus d’informations sur <xref:System.Windows.Media.StreamGeometry> syntaxe d’attribut, consultez le [syntaxe de balisage de chemin d’accès](path-markup-syntax.md) page.</span><span class="sxs-lookup"><span data-stu-id="889b1-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="889b1-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="889b1-109">Example</span></span>  
 <span data-ttu-id="889b1-110">L’exemple suivant utilise un <xref:System.Windows.Media.StreamGeometry> pour définir un triangle dans le code.</span><span class="sxs-lookup"><span data-stu-id="889b1-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="889b1-111">Tout d’abord, l’exemple crée un <xref:System.Windows.Media.StreamGeometry>, puis obtient un <xref:System.Windows.Media.StreamGeometryContext> et l’utilise pour décrire le triangle.</span><span class="sxs-lookup"><span data-stu-id="889b1-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="889b1-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="889b1-112">Example</span></span>  
 <span data-ttu-id="889b1-113">L’exemple suivant crée une méthode qui utilise un <xref:System.Windows.Media.StreamGeometry> et <xref:System.Windows.Media.StreamGeometryContext> pour définir une forme géométrique en fonction des paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="889b1-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="889b1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="889b1-114">See also</span></span>

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [<span data-ttu-id="889b1-115">Créer une forme à l’aide d’un PathGeometry</span><span class="sxs-lookup"><span data-stu-id="889b1-115">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [<span data-ttu-id="889b1-116">Vue d’ensemble de Geometry</span><span class="sxs-lookup"><span data-stu-id="889b1-116">Geometry Overview</span></span>](geometry-overview.md)
