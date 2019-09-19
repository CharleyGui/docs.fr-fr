---
title: Accéder à des objets incorporés à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 110407079b37bce13bb6037d5755d2ef16a40214
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043962"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="48827-102">Accéder à des objets incorporés à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="48827-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="48827-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="48827-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="48827-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="48827-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="48827-105">Cette rubrique montre comment [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] peut être utilisé pour exposer des objets incorporés dans le contenu d’un contrôle de texte.</span><span class="sxs-lookup"><span data-stu-id="48827-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48827-106">Les objets incorporés sont notamment des images, des liens hypertexte, des boutons, des tableaux ou des contrôles ActiveX.</span><span class="sxs-lookup"><span data-stu-id="48827-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="48827-107">Les objets incorporés sont considérés comme des enfants du fournisseur de texte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48827-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="48827-108">Cela leur permet d’être exposés par la même arborescence UI Automation que tous les autres éléments d’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48827-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="48827-109">La fonctionnalité, à son tour, est exposée par les modèles de contrôle généralement demandés par le type de contrôle des objets incorporés (par exemple, étant donné que les liens hypertexte sont textuels, ils prennent en charge <xref:System.Windows.Automation.TextPattern>).</span><span class="sxs-lookup"><span data-stu-id="48827-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="48827-110">![Objets incorporés dans un conteneur de texte.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="48827-110">![Embedded objects in a text container.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="48827-111">Exemple de document avec du contenu textuel (« Saviez-vous ? » ...) et deux objets incorporés (une image de baleine et un lien hypertexte de texte), utilisés comme cible pour les exemples de code.</span><span class="sxs-lookup"><span data-stu-id="48827-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48827-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="48827-112">Example</span></span>  
 <span data-ttu-id="48827-113">L’exemple de code suivant montre comment récupérer une collection d’objets incorporés à partir d’un fournisseur de texte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48827-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="48827-114">Pour l’exemple de document fourni dans l’introduction, deux objets sont retournés (un élément image et un élément de texte).</span><span class="sxs-lookup"><span data-stu-id="48827-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48827-115">L’élément image doit avoir du texte intrinsèque qui décrit l’image, généralement dans sa propriété <xref:System.Windows.Automation.AutomationElement.NameProperty> (par exemple, « une baleine bleue »).</span><span class="sxs-lookup"><span data-stu-id="48827-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="48827-116">Toutefois, quand une plage de texte recouvrant l’image est obtenue, ni l’image ni le texte descriptif ne sont retournés dans le flux de texte.</span><span class="sxs-lookup"><span data-stu-id="48827-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="48827-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="48827-117">Example</span></span>  
 <span data-ttu-id="48827-118">L’exemple de code suivant montre comment obtenir une plage de texte à partir d’un fournisseur de texte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48827-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="48827-119">La plage de texte récupérée est une plage vide dans laquelle le point de terminaison de départ suit « ...</span><span class="sxs-lookup"><span data-stu-id="48827-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="48827-120">ocean.(space) » et le point de terminaison de fin précède le « . » final qui représente le lien hypertexte incorporé (comme illustré par l’image fournie dans l’introduction).</span><span class="sxs-lookup"><span data-stu-id="48827-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="48827-121">Même s’il s’agit d’une plage vide, elle n’est pas considérée comme une plage dégénérée, car son étendue n’est pas nulle.</span><span class="sxs-lookup"><span data-stu-id="48827-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48827-122"><xref:System.Windows.Automation.TextPattern> peut récupérer un objet incorporé textuel comme un lien hypertexte. Toutefois, un <xref:System.Windows.Automation.TextPattern> secondaire devra être obtenu à partir de l’objet incorporé afin d’exposer toute sa fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="48827-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="48827-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48827-123">See also</span></span>

- [<span data-ttu-id="48827-124">Vue d’ensemble de TextPattern d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="48827-124">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="48827-125">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="48827-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="48827-126">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="48827-126">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="48827-127">Ajouter du contenu à une zone de texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="48827-127">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="48827-128">Rechercher et mettre en surbrillance le texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="48827-128">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
