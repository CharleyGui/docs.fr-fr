---
title: Propriétés de dépendance en lecture seule
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: e74f7c2790a73211bcc8e6f13dcf2dfdc02e678b
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859980"
---
# <a name="read-only-dependency-properties"></a>Propriétés de dépendance en lecture seule
Cette rubrique décrit les propriétés de dépendance en lecture seule, y compris les propriétés de dépendance en lecture seule existantes, et les scénarios et techniques de création d’une propriété de dépendance en lecture seule personnalisée.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique part du principe que vous comprenez les scénarios de base de l’implémentation d’une propriété de dépendance et que vous savez comment les métadonnées sont appliquées à une propriété de dépendance personnalisée. Pour plus d’informations sur le contexte, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md) et [Métadonnées de propriété de dépendance](dependency-property-metadata.md).  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Propriétés de dépendance en lecture seule existantes  
 Certaines des propriétés de dépendance définies dans le framework [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sont en lecture seule. En règle générale, vous définissez des propriétés de dépendance en lecture seule parce qu’elles doivent être utilisées pour déterminer des états. Toutefois, quand l’état est influencé par plusieurs facteurs, le simple fait de définir la propriété sur cet état n’est pas souhaitable du point de vue de la conception de l’interface utilisateur. Par exemple, la propriété <xref:System.Windows.UIElement.IsMouseOver%2A> est simplement un état déterminé à partir de l’entrée de souris de surface. Si vous tentez de définir cette valeur par programmation en contournant la vraie entrée de souris, vous obtenez un comportement imprévisible qui entraîne une incohérence.  
  
 Parce qu’elles ne sont pas définissables, les propriétés de dépendance en lecture seule ne sont pas appropriées dans de nombreux scénarios pour lesquels les propriétés de dépendance offrent normalement une solution (à savoir : liaison de données, style applicable directement à une valeur, validation, animation, héritage). Bien qu’elles ne soient pas définissables, les propriétés de dépendance en lecture seule offrent néanmoins des fonctionnalités supplémentaires prises en charge par les propriétés de dépendance dans le système de propriétés. La fonctionnalité restante la plus importante est que la propriété de dépendance en lecture seule peut toujours être utilisée comme déclencheur de propriété dans un style. Vous ne pouvez pas activer de déclencheurs avec une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] normale, seule une propriété de dépendance le permet. Les susmentionnés <xref:System.Windows.UIElement.IsMouseOver%2A> propriété est un parfait exemple de scénario où il peut être très utile de définir un style pour un contrôle, où certains propriété visible comme un arrière-plan, premier plan ou des propriétés similaires d’éléments composés dans le contrôle change lorsque l’utilisateur place la souris sur une région définie de votre contrôle. Les changements d’une propriété de dépendance en lecture seule peuvent aussi être détectés et signalés par les processus d’invalidation inhérents au système de propriétés, la fonctionnalité de déclencheur de propriété étant prise en charge en interne.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Création de propriétés de dépendance en lecture seule personnalisées  
 Lisez attentivement la section ci-dessus qui explique pourquoi les propriétés de dépendance en lecture seule ne fonctionnent pas dans de nombreux scénarios de propriété de dépendance classiques. Toutefois, si vous avez un scénario approprié, vous pouvez créer votre propre propriété de dépendance en lecture seule.  
  
 Une grande partie du processus de création d’une propriété de dépendance en lecture seule est identique à celui décrit dans les rubriques [Propriétés de dépendance personnalisées](custom-dependency-properties.md) et [Implémenter une propriété de dépendance](how-to-implement-a-dependency-property.md). Il existe trois différences majeures :  
  
- Lorsque vous inscrivez votre propriété, appelez le <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> méthode au lieu de la normale <xref:System.Windows.DependencyProperty.Register%2A> méthode d’inscription de propriété.  
  
- Quand vous implémentez la propriété de « wrapper » [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], vérifiez que le wrapper n’a pas non plus d’implémentation définie, pour qu’il n’y ait pas d’incohérence dans l’état en lecture seule pour le wrapper public que vous exposez.  
  
- L’objet retourné par l’inscription en lecture seule est <xref:System.Windows.DependencyPropertyKey> plutôt que <xref:System.Windows.DependencyProperty>. Vous devez toujours stocker ce champ sous forme de membre, mais, en général, vous ne le convertissez pas en membre public du type.  
  
 Indépendamment de la valeur ou champ privé que vous utilisez, le stockage de votre propriété de dépendance en lecture seule peut être entièrement inscriptible en utilisant la logique de votre choix. Toutefois, la façon la plus simple pour définir la propriété initialement ou dans le cadre de la logique runtime consiste à utiliser les API du système de propriétés, plutôt que de contourner le système de propriétés et de définir le champ de stockage privé directement. En particulier, il existe une signature de <xref:System.Windows.DependencyObject.SetValue%2A> qui accepte un paramètre de type <xref:System.Windows.DependencyPropertyKey>. Comment et où vous définissez la valeur par programmation au sein de votre logique d’application affecteront la manière dont vous voulez définir l’accès sur le <xref:System.Windows.DependencyPropertyKey> créé quand vous avez inscrit la propriété de dépendance. Si vous gérez cette logique entièrement dans la classe, vous pouvez indiquer qu’elle est privée ou, si vous voulez qu’elle soit définie à partir d’autres parties de l’assembly, vous pouvez la définir en interne. Une approche consiste à appeler <xref:System.Windows.DependencyObject.SetValue%2A> au sein d’un gestionnaire d’événements de classe d’un événement pertinent qui indique à une instance de classe, la valeur de propriété stockée doit être modifiée. Une autre approche consiste à relier les propriétés de dépendance à l’aide associée <xref:System.Windows.PropertyChangedCallback> et <xref:System.Windows.CoerceValueCallback> rappels dans le cadre des métadonnées de ces propriétés lors de l’inscription.  
  
 Étant donné que le <xref:System.Windows.DependencyPropertyKey> est privé et n’est pas propagé par le système de propriétés en dehors de votre code, une propriété de dépendance en lecture seule a de mieux de la sécurité de paramétrage qu’une propriété de dépendance en lecture-écriture. Pour une propriété de dépendance en lecture-écriture, le champ d’identification est explicitement ou implicitement public et la propriété est donc largement définissable. Pour plus d’informations, consultez [Sécurité de propriété de dépendance](dependency-property-security.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Application d’un style et création de modèles](../controls/styling-and-templating.md)
