---
title: Obtenir des détails d'attribut de texte mixte à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 24aad50647fc5aef5b2c2a83cbab37120eccd88c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966409"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Obtenir des détails d'attribut de texte mixte à l'aide d'UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour obtenir des détails d’attribut de texte à partir d’une plage de texte qui couvre plusieurs valeurs d’attribut. Une plage de texte peut correspondre à l’emplacement actuel du signe insertion (ou de la sélection dégénérée) dans un document, une sélection contiguë de texte, une collection de sélections disjointes de texte ou l’ensemble du contenu textuel d’un document.  
  
## <a name="example"></a>Exemples  
 L’exemple de code suivant montre comment obtenir le <xref:System.Windows.Automation.TextPattern.FontNameAttribute> d’une plage de texte où <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> retourne un objet <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> .  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 Le modèle de contrôle <xref:System.Windows.Automation.TextPattern> , associé à la classe <xref:System.Windows.Automation.Text.TextPatternRange> , prend en charge les attributs de texte, les propriétés et les méthodes de base. Pour les fonctionnalités spécifiques au contrôle qui ne sont pas prises en charge par <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, la classe <xref:System.Windows.Automation.AutomationElement> fournit des méthodes permettant à un client UI Automation d’accéder au modèle objet natif correspondant.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de TextPattern d’UI Automation](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [Ajouter du contenu à une zone de texte à l’aide d’UI Automation](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [Rechercher et mettre en surbrillance le texte à l’aide d’UI Automation](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [Vue d’ensemble des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Modèles de contrôle UI Automation pour les clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Obtenir des attributs de texte à l’aide d’UI Automation](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
