---
title: Accéder à des objets incorporés à l'aide d'UI Automation
description: Découvrez comment accéder aux objets incorporés à l’aide d’UI Automation au sein du contenu de contrôle de texte. Les objets incorporés sont considérés comme des enfants du fournisseur de texte UI Automation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 30b41e3a3d47802eb4a3e761c4282b3e937156f2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235777"
---
# <a name="access-embedded-objects-using-ui-automation"></a>Accéder à des objets incorporés à l'aide d'UI Automation

> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique montre comment [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] peut être utilisé pour exposer des objets incorporés dans le contenu d’un contrôle de texte.  
  
> [!NOTE]
> Les objets incorporés sont notamment des images, des liens hypertexte, des boutons, des tableaux ou des contrôles ActiveX.  
  
 Les objets incorporés sont considérés comme des enfants du fournisseur de texte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Cela leur permet d’être exposés par la même arborescence UI Automation que tous les autres éléments d’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] . La fonctionnalité, à son tour, est exposée par les modèles de contrôle généralement demandés par le type de contrôle des objets incorporés (par exemple, étant donné que les liens hypertexte sont textuels, ils prennent en charge <xref:System.Windows.Automation.TextPattern>).  
  
 ![Objets imbriqués dans un conteneur de texte.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Exemple de document avec du contenu textuel (« Saviez-vous ? » ...) et deux objets incorporés (une image de baleine et un lien hypertexte de texte), utilisés comme cible pour les exemples de code.  
  
## <a name="example"></a> Exemple  

 L’exemple de code suivant montre comment récupérer une collection d’objets incorporés à partir d’un fournisseur de texte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Pour l’exemple de document fourni dans l’introduction, deux objets sont retournés (un élément image et un élément de texte).  
  
> [!NOTE]
> L’élément image doit avoir du texte intrinsèque qui décrit l’image, généralement dans sa propriété <xref:System.Windows.Automation.AutomationElement.NameProperty> (par exemple, « une baleine bleue »). Toutefois, quand une plage de texte recouvrant l’image est obtenue, ni l’image ni le texte descriptif ne sont retournés dans le flux de texte.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a> Exemple  

 L’exemple de code suivant montre comment obtenir une plage de texte à partir d’un fournisseur de texte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . La plage de texte récupérée est une plage vide dans laquelle le point de terminaison de départ suit « ... ocean.(space) » et le point de terminaison de fin précède le « . » final qui représente le lien hypertexte incorporé (comme illustré par l’image fournie dans l’introduction). Même s’il s’agit d’une plage vide, elle n’est pas considérée comme une plage dégénérée, car son étendue n’est pas nulle.  
  
> [!NOTE]
> <xref:System.Windows.Automation.TextPattern> peut récupérer un objet incorporé textuel comme un lien hypertexte. Toutefois, un <xref:System.Windows.Automation.TextPattern> secondaire devra être obtenu à partir de l’objet incorporé afin d’exposer toute sa fonctionnalité.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de TextPattern d'UI Automation](ui-automation-textpattern-overview.md)
- [Vue d'ensemble des modèles de contrôle UI Automation](ui-automation-control-patterns-overview.md)
- [Modèles de contrôle UI Automation pour les clients](ui-automation-control-patterns-for-clients.md)
- [Ajouter du contenu à une zone de texte à l'aide d'UI Automation](add-content-to-a-text-box-using-ui-automation.md)
- [Rechercher et mettre un texte en surbrillance à l'aide d'UI Automation](find-and-highlight-text-using-ui-automation.md)
