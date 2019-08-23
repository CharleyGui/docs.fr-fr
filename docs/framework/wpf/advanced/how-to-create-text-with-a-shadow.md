---
title: 'Procédure : Créer du texte avec une ombre'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960438"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="2e51e-102">Procédure : Créer du texte avec une ombre</span><span class="sxs-lookup"><span data-stu-id="2e51e-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="2e51e-103">Les exemples de cette section indiquent comment créer un effet d’ombre pour du texte affiché.</span><span class="sxs-lookup"><span data-stu-id="2e51e-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e51e-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="2e51e-104">Example</span></span>  
 <span data-ttu-id="2e51e-105">L' <xref:System.Windows.Media.Effects.DropShadowEffect> objet vous permet de créer divers effets d’ombre portée pour les [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objets.</span><span class="sxs-lookup"><span data-stu-id="2e51e-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="2e51e-106">L’exemple suivant présente un effet d’ombre portée appliqué au texte.</span><span class="sxs-lookup"><span data-stu-id="2e51e-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="2e51e-107">Dans ce cas, l’ombre est une ombre légère, ce qui signifie que sa couleur devient floue.</span><span class="sxs-lookup"><span data-stu-id="2e51e-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Ombre du texte avec adoucissement &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <span data-ttu-id="2e51e-109">Vous pouvez contrôler la largeur d’une ombre en définissant <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> la propriété.</span><span class="sxs-lookup"><span data-stu-id="2e51e-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="2e51e-110">La valeur `4.0` indique une largeur de l’ombre de 4 pixels.</span><span class="sxs-lookup"><span data-stu-id="2e51e-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="2e51e-111">Vous pouvez contrôler l’adoucissement ou le flou d’une ombre en modifiant la <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="2e51e-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="2e51e-112">La valeur indique `0.0` l’absence de flou.</span><span class="sxs-lookup"><span data-stu-id="2e51e-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="2e51e-113">L’exemple de code suivant montre comment créer une ombre légère.</span><span class="sxs-lookup"><span data-stu-id="2e51e-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="2e51e-114">Ces effets d’ombre ne passent pas par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] le pipeline de rendu de texte.</span><span class="sxs-lookup"><span data-stu-id="2e51e-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="2e51e-115">En conséquence, ClearType est désactivé lors de l’utilisation de ces effets.</span><span class="sxs-lookup"><span data-stu-id="2e51e-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="2e51e-116">L’exemple suivant présente un effet d’ombre portée marquée appliqué au texte.</span><span class="sxs-lookup"><span data-stu-id="2e51e-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="2e51e-117">Dans ce cas, l’ombre n’est pas floue.</span><span class="sxs-lookup"><span data-stu-id="2e51e-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Ombre du texte avec adoucissement &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <span data-ttu-id="2e51e-119">Vous pouvez créer une ombre dure en affectant <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> à `0.0`la propriété la valeur, ce qui indique qu’aucun flou n’est utilisé.</span><span class="sxs-lookup"><span data-stu-id="2e51e-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="2e51e-120">Vous pouvez contrôler la direction de l’ombre en modifiant la <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="2e51e-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="2e51e-121">Définissez la valeur directionnelle de cette propriété sur un degré entre `0` et `360`.</span><span class="sxs-lookup"><span data-stu-id="2e51e-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="2e51e-122">L’illustration suivante montre les valeurs directionnelles du <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> paramètre de propriété.</span><span class="sxs-lookup"><span data-stu-id="2e51e-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Paramètre de degré DropShadow de l’ombre](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="2e51e-124">L’exemple de code suivant montre comment créer une ombre marquée.</span><span class="sxs-lookup"><span data-stu-id="2e51e-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="2e51e-125">Utilisation d’un effet de flou</span><span class="sxs-lookup"><span data-stu-id="2e51e-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="2e51e-126">Un <xref:System.Windows.Media.Effects.BlurBitmapEffect> peut être utilisé pour créer un effet similaire à une ombre pouvant être placé derrière un objet de texte.</span><span class="sxs-lookup"><span data-stu-id="2e51e-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="2e51e-127">Un effet bitmap flou appliqué au texte rend le texte flou uniformément dans toutes les directions.</span><span class="sxs-lookup"><span data-stu-id="2e51e-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="2e51e-128">L’exemple suivant présente un effet de flou appliqué au texte.</span><span class="sxs-lookup"><span data-stu-id="2e51e-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Ombre du texte utilisant BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="2e51e-130">L’exemple de code suivant montre comment créer un effet de flou.</span><span class="sxs-lookup"><span data-stu-id="2e51e-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="2e51e-131">Utilisation d’une transformation de traduction</span><span class="sxs-lookup"><span data-stu-id="2e51e-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="2e51e-132">Un <xref:System.Windows.Media.TranslateTransform> peut être utilisé pour créer un effet similaire à une ombre pouvant être placé derrière un objet de texte.</span><span class="sxs-lookup"><span data-stu-id="2e51e-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="2e51e-133">L’exemple de code suivant utilise <xref:System.Windows.Media.TranslateTransform> un pour décaler le texte.</span><span class="sxs-lookup"><span data-stu-id="2e51e-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="2e51e-134">Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d’ombre.</span><span class="sxs-lookup"><span data-stu-id="2e51e-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Ombre du texte utilisant TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 <span data-ttu-id="2e51e-136">L’exemple de code suivant indique comment créer une transformation pour un effet d’ombre.</span><span class="sxs-lookup"><span data-stu-id="2e51e-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
