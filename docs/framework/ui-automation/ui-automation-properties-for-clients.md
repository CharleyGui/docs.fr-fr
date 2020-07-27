---
title: Propriétés UI Automation pour les clients
description: Lisez une vue d’ensemble des propriétés UI Automation telles qu’elles sont exposées aux applications clientes UI Automation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
ms.openlocfilehash: fe78d7da154d79a5f66ee6c190b199065675841f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163129"
---
# <a name="ui-automation-properties-for-clients"></a>Propriétés UI Automation pour les clients
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette vue d’ensemble présente les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] telles qu’elles sont exposées aux applications clientes UI Automation.  
  
 Les propriétés des objets <xref:System.Windows.Automation.AutomationElement> contiennent des informations sur les éléments d’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , généralement les contrôles. Les propriétés de <xref:System.Windows.Automation.AutomationElement> sont génériques. En d’autres termes, elles ne sont pas spécifiques à un type de contrôle. Un grand nombre de ces propriétés est exposé dans la structure <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> .  
  
 Les modèles de contrôle ont également des propriétés. Les propriétés des modèles de contrôle sont spécifiques au modèle. Par exemple, <xref:System.Windows.Automation.ScrollPattern> possède des propriétés qui permettent à une application cliente de déterminer si une fenêtre peut faire l’objet d’un défilement vertical ou horizontal, et de connaître les tailles d’affichage ainsi que les positions de défilement actuelles. Les modèles de contrôle exposent toutes leurs propriétés via une structure, par exemple <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 Les propriétés[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sont en lecture seule. Pour définir les propriétés d’un contrôle, vous devez utiliser les méthodes du modèle de contrôle approprié. Par exemple, utilisez <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> pour changer les valeurs de position d’une fenêtre de défilement.  
  
 Pour améliorer les performances, vous pouvez mettre en cache les valeurs des propriétés des contrôles et des modèles de contrôle quand des objets <xref:System.Windows.Automation.AutomationElement> sont récupérés. Pour plus d’informations, consultez [mise en cache dans les clients UI Automation](caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>ID de propriété  
 Les identificateurs de propriété (ID) sont des valeurs constantes uniques qui sont encapsulées dans des <xref:System.Windows.Automation.AutomationProperty> objets. Les applications clientes UI Automation obtiennent ces ID à partir de la <xref:System.Windows.Automation.AutomationElement> classe ou de la classe de modèle de contrôle appropriée, telle que <xref:System.Windows.Automation.ScrollPattern> . Les fournisseurs UI Automation les obtiennent à partir de <xref:System.Windows.Automation.AutomationElementIdentifiers> , ou de l’une des classes d’identificateurs de modèle de contrôle, par exemple <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 Les fournisseurs utilisent l’ <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> numérique de <xref:System.Windows.Automation.AutomationProperty> pour identifier les propriétés interrogées dans la méthode <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> . En général, les applications clientes n’ont pas besoin d’examiner l’ <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> n’est utilisé que pour le débogage et le diagnostic.  
  
## <a name="property-conditions"></a>Conditions de propriété  
 Les ID de propriété sont utilisés dans la construction des <xref:System.Windows.Automation.PropertyCondition> objets utilisés pour rechercher des <xref:System.Windows.Automation.AutomationElement> objets. Par exemple, vous pouvez être amené à rechercher un <xref:System.Windows.Automation.AutomationElement> ayant un nom spécifique, ou tous les contrôles qui sont activés. Chaque <xref:System.Windows.Automation.PropertyCondition> spécifie un identificateur <xref:System.Windows.Automation.AutomationProperty> et la valeur à laquelle la propriété doit correspondre.  
  
 Pour plus d’informations, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Récupération de propriétés  
 Certaines propriétés de <xref:System.Windows.Automation.AutomationElement> et toutes les propriétés d’une classe de modèle de contrôle sont exposées en tant que propriétés imbriquées de la propriété `Current` ou `Cached` de <xref:System.Windows.Automation.AutomationElement> ou de l’objet de modèle de contrôle.  
  
 En outre, <xref:System.Windows.Automation.AutomationElement> ou les propriétés de modèles de contrôle, ainsi que les propriétés non disponibles dans la structure <xref:System.Windows.Automation.AutomationElement.Cached%2A> ou <xref:System.Windows.Automation.AutomationElement.Current%2A> , peuvent être récupérés via l’une des méthodes suivantes :  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Ces méthodes offrent des performances un peu meilleures, ainsi qu’un accès à la gamme complète des propriétés.  
  
 L’exemple de code suivant montre deux façons de récupérer une propriété sur <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Pour récupérer les propriétés de modèles de contrôle pris en charge par <xref:System.Windows.Automation.AutomationElement>, vous n’avez pas besoin de récupérer l’objet de modèle de contrôle. Transmettez simplement l’un des identificateurs de propriété de modèle à la méthode.  
  
 L’exemple de code suivant montre deux façons de récupérer une propriété sur un modèle de contrôle.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 Les méthodes `Get` retournent <xref:System.Object>. L’application doit effectuer un cast de l’objet retourné vers le type approprié avant d’utiliser la valeur.  
  
## <a name="default-property-values"></a>Valeurs de propriété par défaut  
 Si un fournisseur UI Automation n’implémente pas une propriété, le système [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] peut fournir une valeur par défaut. Par exemple, si le fournisseur d’un contrôle ne prend pas en charge la propriété identifiée par <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] retourne une chaîne vide. De même, si le fournisseur ne prend pas en charge la propriété identifiée par <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] retourne `false`.  
  
 Vous pouvez changer ce comportement à l’aide des surcharges de méthode <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> . Quand vous spécifiez `true` comme second paramètre, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ne retourne pas de valeur par défaut mais la valeur spéciale <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 L’exemple de code suivant tente de récupérer une propriété d’un élément. Si la propriété n’est pas prise en charge, une valeur définie par l’application est utilisée à la place.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Pour découvrir les propriétés prises en charge par un élément, utilisez <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Un tableau d’identificateurs <xref:System.Windows.Automation.AutomationProperty> est retourné.  
  
## <a name="property-changed-events"></a>Événements de modification de propriété  
 Quand une valeur de propriété change pour <xref:System.Windows.Automation.AutomationElement> ou un modèle de contrôle, un événement est déclenché. Une application peut s’abonner à ces événements en appelant <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, et en fournissant un tableau d’identificateurs <xref:System.Windows.Automation.AutomationProperty> comme dernier paramètre pour spécifier les propriétés pertinentes.  
  
 Dans <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>, vous pouvez identifier la propriété qui a changé en vérifiant le membre <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> des arguments d’événement. Les arguments contiennent également les valeurs anciennes et nouvelles de la propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ayant changé. Ces valeurs sont de type <xref:System.Object> , et doivent être castées vers le type approprié avant d’être utilisées.  
  
## <a name="additional-automationelement-properties"></a>Propriétés AutomationElement supplémentaires  
 Outre les structures de propriété <xref:System.Windows.Automation.AutomationElement.Current%2A> et <xref:System.Windows.Automation.AutomationElement.Cached%2A> , <xref:System.Windows.Automation.AutomationElement> possède les propriétés suivantes, qui sont récupérées via des accesseurs de propriétés simples.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Collection d’objets <xref:System.Windows.Automation.AutomationElement> enfants qui se trouvent dans le cache.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|Objet parent <xref:System.Windows.Automation.AutomationElement> qui se trouve dans le cache.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Propriété statique) <xref:System.Windows.Automation.AutomationElement> ayant le focus d’entrée.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Propriété statique) <xref:System.Windows.Automation.AutomationElement>racine.|  
  
## <a name="see-also"></a>Voir aussi

- [Mise en cache dans les clients UI Automation](caching-in-ui-automation-clients.md)
- [Implémentation de fournisseur UI Automation côté serveur](server-side-ui-automation-provider-implementation.md)
- [S'abonner à des événements UI Automation](subscribe-to-ui-automation-events.md)
