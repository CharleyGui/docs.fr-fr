---
title: Obtenir des détails d'attribut de texte mixte à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 13ebc6aefe925ecefe48a9b0fa8cf7a6ecd3c454
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042953"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="cdd90-102">Obtenir des détails d'attribut de texte mixte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdd90-102">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="cdd90-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="cdd90-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cdd90-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="cdd90-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="cdd90-105">Cette rubrique montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour obtenir des détails d’attribut de texte à partir d’une plage de texte qui couvre plusieurs valeurs d’attribut.</span><span class="sxs-lookup"><span data-stu-id="cdd90-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="cdd90-106">Une plage de texte peut correspondre à l’emplacement actuel du signe insertion (ou de la sélection dégénérée) dans un document, une sélection contiguë de texte, une collection de sélections disjointes de texte ou l’ensemble du contenu textuel d’un document.</span><span class="sxs-lookup"><span data-stu-id="cdd90-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdd90-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="cdd90-107">Example</span></span>  
 <span data-ttu-id="cdd90-108">L’exemple de code suivant montre comment obtenir le <xref:System.Windows.Automation.TextPattern.FontNameAttribute> d’une plage de texte où <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> retourne un objet <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> .</span><span class="sxs-lookup"><span data-stu-id="cdd90-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="cdd90-109">Le modèle de contrôle <xref:System.Windows.Automation.TextPattern> , associé à la classe <xref:System.Windows.Automation.Text.TextPatternRange> , prend en charge les attributs de texte, les propriétés et les méthodes de base.</span><span class="sxs-lookup"><span data-stu-id="cdd90-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="cdd90-110">Pour les fonctionnalités spécifiques au contrôle qui ne sont pas prises en charge par <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, la classe <xref:System.Windows.Automation.AutomationElement> fournit des méthodes permettant à un client UI Automation d’accéder au modèle objet natif correspondant.</span><span class="sxs-lookup"><span data-stu-id="cdd90-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd90-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdd90-111">See also</span></span>

- [<span data-ttu-id="cdd90-112">Vue d’ensemble de TextPattern d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdd90-112">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="cdd90-113">Ajouter du contenu à une zone de texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdd90-113">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="cdd90-114">Rechercher et mettre en surbrillance le texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdd90-114">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="cdd90-115">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdd90-115">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="cdd90-116">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="cdd90-116">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="cdd90-117">Obtenir des attributs de texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="cdd90-117">Obtain Text Attributes Using UI Automation</span></span>](obtain-text-attributes-using-ui-automation.md)
