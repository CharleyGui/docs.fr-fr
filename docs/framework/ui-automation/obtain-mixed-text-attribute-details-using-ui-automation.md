---
title: Obtenir des détails d'attribut de texte mixte à l'aide d'UI Automation
description: Obtenez des détails d’attribut de texte mixte à l’aide des classes UI Automation managées dans l’espace de noms System. Windows. Automation de l’API .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 111d110be9365c4a58f2bd2b033c1ff4e3a6a95d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903855"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="d8710-103">Obtenir des détails d'attribut de texte mixte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="d8710-103">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="d8710-104">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d8710-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d8710-105">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="d8710-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d8710-106">Cette rubrique montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour obtenir des détails d’attribut de texte à partir d’une plage de texte qui couvre plusieurs valeurs d’attribut.</span><span class="sxs-lookup"><span data-stu-id="d8710-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="d8710-107">Une plage de texte peut correspondre à l’emplacement actuel du signe insertion (ou de la sélection dégénérée) dans un document, une sélection contiguë de texte, une collection de sélections disjointes de texte ou l’ensemble du contenu textuel d’un document.</span><span class="sxs-lookup"><span data-stu-id="d8710-107">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8710-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8710-108">Example</span></span>  
 <span data-ttu-id="d8710-109">L’exemple de code suivant montre comment obtenir le <xref:System.Windows.Automation.TextPattern.FontNameAttribute> d’une plage de texte où <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> retourne un objet <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> .</span><span class="sxs-lookup"><span data-stu-id="d8710-109">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="d8710-110">Le modèle de contrôle <xref:System.Windows.Automation.TextPattern> , associé à la classe <xref:System.Windows.Automation.Text.TextPatternRange> , prend en charge les attributs de texte, les propriétés et les méthodes de base.</span><span class="sxs-lookup"><span data-stu-id="d8710-110">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="d8710-111">Pour les fonctionnalités spécifiques au contrôle qui ne sont pas prises en charge par <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, la classe <xref:System.Windows.Automation.AutomationElement> fournit des méthodes permettant à un client UI Automation d’accéder au modèle objet natif correspondant.</span><span class="sxs-lookup"><span data-stu-id="d8710-111">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8710-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8710-112">See also</span></span>

- [<span data-ttu-id="d8710-113">Vue d'ensemble de TextPattern d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="d8710-113">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="d8710-114">Ajouter du contenu à une zone de texte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="d8710-114">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="d8710-115">Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="d8710-115">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="d8710-116">Vue d'ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="d8710-116">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="d8710-117">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="d8710-117">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="d8710-118">Obtenir des attributs de texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="d8710-118">Obtain Text Attributes Using UI Automation</span></span>](obtain-text-attributes-using-ui-automation.md)
