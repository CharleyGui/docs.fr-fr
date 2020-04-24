---
title: Ressources et code
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys [WPF], using objects as
- resources [WPF], accessing from procedural code
- procedural code [WPF], creating resources with
- procedural code [WPF], accessing resources from
- resources [WPF], creating with procedural code
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
ms.openlocfilehash: 8074562ddb865b482cf123743796ac68bb529f85
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646241"
---
# <a name="resources-and-code"></a>Ressources et code
Cette présentation décrit comment accéder aux ressources [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ou les créer à l’aide de code au lieu de la syntaxe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Pour plus d’informations sur l’utilisation générale des ressources et sur les ressources du point de vue de la syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  

<a name="accessing"></a>
## <a name="accessing-resources-from-code"></a>Accès aux ressources à partir du code  
 Les clés qui identifient les ressources, si elles sont définies en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], sont également utilisées pour récupérer des ressources spécifiques si vous demandez la ressource dans le code. La façon la plus simple de récupérer une <xref:System.Windows.FrameworkElement.FindResource%2A> ressource <xref:System.Windows.FrameworkElement.TryFindResource%2A> à partir du code est d’appeler soit la méthode ou la méthode à partir d’objets de niveau cadre dans votre application. La différence entre ces méthodes se situe au niveau de leur comportement quand la clé demandée est introuvable. <xref:System.Windows.FrameworkElement.FindResource%2A>soulève une exception; <xref:System.Windows.FrameworkElement.TryFindResource%2A> ne soulèvera pas `null`une exception mais revient . Chaque méthode prend la clé de ressource comme paramètre d’entrée et retourne un objet faiblement typé. Une clé de ressource est généralement une chaîne, mais il arrive que ce ne soit pas le cas. Pour plus d’informations, consultez la section [Utilisation d’objets comme clés](#objectaskey). En principe, vous castez l’objet retourné en type nécessaire pour la propriété que vous définissez quand vous demandez la ressource. La logique de recherche pour la résolution d’une ressource de code est la même que pour une référence de ressource dynamique [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. La recherche de ressources commence dans l’élément appelant, puis se poursuit dans les éléments parents successifs de l’arborescence logique. La recherche se poursuit dans les ressources d’application, les thèmes et les ressources système, si nécessaire. Une demande de code pour une ressource tient compte des changements d’exécution dans les dictionnaires de ressources qui ont pu avoir lieu à la suite du chargement du dictionnaire de ressources par [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ainsi que des changements des ressources système en temps réel.  
  
 Ce qui suit est un bref exemple de code qui trouve une ressource <xref:System.Windows.Controls.Primitives.ButtonBase.Click> par clé et utilise la valeur retournée pour définir une propriété, implémentée en tant que gestionnaire d’événements.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Une autre méthode pour attribuer <xref:System.Windows.FrameworkElement.SetResourceReference%2A>une référence de ressource est . Cette méthode accepte deux paramètres : la clé de la ressource et l’identificateur d’une propriété de dépendance particulière présente sur l’instance de l’élément auquel la valeur de ressource doit être assignée. En pratique, cette méthode est la même et a l’avantage de ne pas nécessiter de cast des valeurs de retour.  
  
 Une autre façon d’accéder aux ressources de <xref:System.Windows.FrameworkElement.Resources%2A> façon programmatique est d’accéder au contenu de la propriété en tant que dictionnaire. C’est aussi en accédant au dictionnaire contenu dans cette propriété que vous pouvez ajouter de nouvelles ressources aux collections existantes, vérifier si le nom d’une clé donnée est déjà utilisé dans la collection ainsi que d’autres opérations de dictionnaire/collection. Si vous écrivez une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application entièrement en code, vous pouvez également créer l’ensemble de la <xref:System.Windows.FrameworkElement.Resources%2A> collection dans le code, y attribuer des clés, puis affecter la collection finie à la propriété d’un élément établi. Ces opérations sont décrites dans la section suivante.  
  
 Vous pouvez indexer <xref:System.Windows.FrameworkElement.Resources%2A> au sein d’une collection donnée, en utilisant une clé spécifique comme index, mais vous devez être conscient que l’accès à la ressource de cette façon ne suit pas les règles normales de règlement des ressources. Vous accédez uniquement à cette collection particulière. La recherche de ressources ne s’étend pas à la racine ou à l’application si aucun objet valide n’est trouvé au niveau de la clé demandée. Toutefois, cette approche peut parfois améliorer les performances, précisément parce que l’étendue de la recherche de la clé est plus limitée. Consultez <xref:System.Windows.ResourceDictionary> la classe pour plus de détails sur la façon de travailler directement avec le dictionnaire des ressources.  
  
<a name="creating"></a>
## <a name="creating-resources-with-code"></a>Création de ressources avec du code  
 Si vous voulez créer une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] entière en code, vous voudrez vraisemblablement aussi créer des ressources de cette application en code. Pour ce faire, <xref:System.Windows.ResourceDictionary> créer une nouvelle instance, puis ajouter toutes <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>les ressources au dictionnaire en utilisant des appels successifs à . Ensuite, utilisez <xref:System.Windows.ResourceDictionary> le ainsi <xref:System.Windows.FrameworkElement.Resources%2A> créé pour définir la propriété sur un <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>élément qui est présent dans une portée de page, ou le . Vous pouvez également <xref:System.Windows.ResourceDictionary> maintenir l’objet autonome sans l’ajouter à un élément. Toutefois, dans ce cas, vous devez accéder aux ressources qu’il contient par clé d’élément, comme pour un dictionnaire générique. Un <xref:System.Windows.ResourceDictionary> qui n’est `Resources` pas attaché à une propriété élément n’existerait pas dans l’arbre <xref:System.Windows.FrameworkElement.FindResource%2A> élément et n’a aucune portée dans une séquence de recherche qui peut être utilisé par et les méthodes connexes.  
  
<a name="objectaskey"></a>
## <a name="using-objects-as-keys"></a>Utilisation d’objets comme clés  
 Dans la plupart des cas d’utilisation de ressources, la clé de la ressource est une chaîne. Toutefois, diverses fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’utilisent pas délibérément le type chaîne pour spécifier des clés, mais définissent ce paramètre sur un objet. Vous avez la possibilité d’indexer une ressource à l’aide d’un objet grâce à la prise en charge des thèmes et des styles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Les styles dans les thèmes qui deviennent le style par défaut pour <xref:System.Type> un contrôle autrement non-style sont chacun clé par le du contrôle qu’ils devraient appliquer à. L’indexation par le type est un mécanisme de recherche fiable qui fonctionne sur les instances par défaut de chaque type de contrôle, et le type peut être détecté par réflexion et utilisé pour appliquer un style aux classes dérivées, même si le type dérivé n’a aucun style par défaut. Vous pouvez <xref:System.Type> spécifier une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] clé pour une ressource définie en utilisant l’extension [de markup x:Type](../../../desktop-wpf/xaml-services/xtype-markup-extension.md). Des extensions similaires dans d’autres cas d’utilisation de clé non-chaîne prennent en charge des fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], comme l’[extension de balisage ComponentResourceKey](componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Voir aussi

- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
