---
title: "Comment : personnaliser le dessin d'un contrôle ToolStrip"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: a9f603efdb4b4a5f68154da9c6a8bd05b55b8f46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182226"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="b748b-102">Comment : personnaliser le dessin d'un contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b748b-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="b748b-103">Les contrôles <xref:System.Windows.Forms.ToolStrip> disposent des classes de rendu (peinture) associées suivantes :</span><span class="sxs-lookup"><span data-stu-id="b748b-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
- <span data-ttu-id="b748b-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> fournit l'apparence et le style de votre système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="b748b-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
- <span data-ttu-id="b748b-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> fournit l'apparence et le style de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="b748b-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
- <span data-ttu-id="b748b-106"><xref:System.Windows.Forms.ToolStripRenderer> est la classe de base abstraite pour les deux autres classes de rendu.</span><span class="sxs-lookup"><span data-stu-id="b748b-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="b748b-107">Pour le dessin personnalisé (également appelé Owner Draw) d'un <xref:System.Windows.Forms.ToolStrip>, vous pouvez substituer l'une des classes du convertisseur et modifier un aspect de la logique de rendu.</span><span class="sxs-lookup"><span data-stu-id="b748b-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="b748b-108">Les procédures suivantes décrivent divers aspects du dessin personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b748b-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="b748b-109">Pour basculer entre les convertisseurs fournis</span><span class="sxs-lookup"><span data-stu-id="b748b-109">To switch between the provided renderers</span></span>  
  
- <span data-ttu-id="b748b-110">Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> la valeur <xref:System.Windows.Forms.ToolStripRenderMode> souhaitée.</span><span class="sxs-lookup"><span data-stu-id="b748b-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="b748b-111">Avec <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, la propriété statique <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> détermine le convertisseur pour votre application.</span><span class="sxs-lookup"><span data-stu-id="b748b-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="b748b-112">Les autres valeurs de <xref:System.Windows.Forms.ToolStripRenderMode> sont <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional> et <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span><span class="sxs-lookup"><span data-stu-id="b748b-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="b748b-113">Pour appliquer des bordures de style Microsoft Office droites</span><span class="sxs-lookup"><span data-stu-id="b748b-113">To change the Microsoft Office–style borders to straight</span></span>  
  
- <span data-ttu-id="b748b-114">Substituez <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, mais n'appelez pas la classe de base.</span><span class="sxs-lookup"><span data-stu-id="b748b-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b748b-115">Il existe une version de cette méthode pour <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span><span class="sxs-lookup"><span data-stu-id="b748b-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="b748b-116">Pour modifier ProfessionalColorTable</span><span class="sxs-lookup"><span data-stu-id="b748b-116">To change the ProfessionalColorTable</span></span>  
  
- <span data-ttu-id="b748b-117">Substituez <xref:System.Windows.Forms.ProfessionalColorTable> et modifiez les couleurs de votre choix.</span><span class="sxs-lookup"><span data-stu-id="b748b-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="b748b-118">Pour modifier le rendu de tous les contrôles ToolStrip dans votre application</span><span class="sxs-lookup"><span data-stu-id="b748b-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1. <span data-ttu-id="b748b-119">Utilisez la propriété <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> pour choisir l'un des convertisseurs fournis.</span><span class="sxs-lookup"><span data-stu-id="b748b-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2. <span data-ttu-id="b748b-120">Utilisez <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> pour assigner un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b748b-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3. <span data-ttu-id="b748b-121">Vérifiez que <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> a la valeur par défaut de <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="b748b-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="b748b-122">Pour désactiver les couleurs Microsoft Office pour l'application entière</span><span class="sxs-lookup"><span data-stu-id="b748b-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
- <span data-ttu-id="b748b-123">Définissez <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> sur `false`.</span><span class="sxs-lookup"><span data-stu-id="b748b-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="b748b-124">Pour désactiver les couleurs Microsoft Office pour un contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b748b-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
- <span data-ttu-id="b748b-125">Utilisez du code semblable à l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b748b-125">Use code similar to the following code example.</span></span>  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b748b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b748b-126">See also</span></span>

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [<span data-ttu-id="b748b-127">Contrôles avec prise en charge intégrée du dessin owner-drawn</span><span class="sxs-lookup"><span data-stu-id="b748b-127">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="b748b-128">Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b748b-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [<span data-ttu-id="b748b-129">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b748b-129">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
