---
title: Propriétés de dépendance en lecture seule
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 8adc90182f0f42f52e6ace4e13c68acb3539516b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187182"
---
# <a name="read-only-dependency-properties"></a>Propriétés de dépendance en lecture seule
Cette rubrique décrit les propriétés de dépendance en lecture seule, y compris les propriétés de dépendance en lecture seule existantes, et les scénarios et techniques de création d’une propriété de dépendance en lecture seule personnalisée.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique part du principe que vous comprenez les scénarios de base de l’implémentation d’une propriété de dépendance et que vous savez comment les métadonnées sont appliquées à une propriété de dépendance personnalisée. Pour plus d’informations sur le contexte, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md) et [Métadonnées de propriété de dépendance](dependency-property-metadata.md).  
  
<a name="existing"></a>
## <a name="existing-read-only-dependency-properties"></a>Propriétés de dépendance en lecture seule existantes  
 Certaines des propriétés de dépendance définies dans le framework [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sont en lecture seule. En règle générale, vous définissez des propriétés de dépendance en lecture seule parce qu’elles doivent être utilisées pour déterminer des états. Toutefois, quand l’état est influencé par plusieurs facteurs, le simple fait de définir la propriété sur cet état n’est pas souhaitable du point de vue de la conception de l’interface utilisateur. Par exemple, <xref:System.Windows.UIElement.IsMouseOver%2A> la propriété est vraiment juste état de revêtement tel que déterminé à partir de l’entrée de la souris. Si vous tentez de définir cette valeur par programmation en contournant la vraie entrée de souris, vous obtenez un comportement imprévisible qui entraîne une incohérence.  
  
 Parce qu’elles ne sont pas définissables, les propriétés de dépendance en lecture seule ne sont pas appropriées dans de nombreux scénarios pour lesquels les propriétés de dépendance offrent normalement une solution (à savoir : liaison de données, style applicable directement à une valeur, validation, animation, héritage). Bien qu’elles ne soient pas définissables, les propriétés de dépendance en lecture seule offrent néanmoins des fonctionnalités supplémentaires prises en charge par les propriétés de dépendance dans le système de propriétés. La fonctionnalité restante la plus importante est que la propriété de dépendance en lecture seule peut toujours être utilisée comme déclencheur de propriété dans un style. Vous ne pouvez pas activer les déclencheurs avec une propriété normale de temps courant d’exécution de langue (CLR); il doit être une propriété de dépendance. La propriété susmentionnée <xref:System.Windows.UIElement.IsMouseOver%2A> est un parfait exemple d’un scénario où il pourrait être très utile de définir un style pour un contrôle, où certains biens visibles tels qu’un arrière-plan, au premier plan, ou des propriétés similaires d’éléments composites dans le contrôle va changer lorsque l’utilisateur place une souris sur une région définie de votre contrôle. Les changements d’une propriété de dépendance en lecture seule peuvent aussi être détectés et signalés par les processus d’invalidation inhérents au système de propriétés, la fonctionnalité de déclencheur de propriété étant prise en charge en interne.  
  
<a name="new"></a>
## <a name="creating-custom-read-only-dependency-properties"></a>Création de propriétés de dépendance en lecture seule personnalisées  
 Lisez attentivement la section ci-dessus qui explique pourquoi les propriétés de dépendance en lecture seule ne fonctionnent pas dans de nombreux scénarios de propriété de dépendance classiques. Toutefois, si vous avez un scénario approprié, vous pouvez créer votre propre propriété de dépendance en lecture seule.  
  
 Une grande partie du processus de création d’une propriété de dépendance en lecture seule est identique à celui décrit dans les rubriques [Propriétés de dépendance personnalisées](custom-dependency-properties.md) et [Implémenter une propriété de dépendance](how-to-implement-a-dependency-property.md). Il existe trois différences majeures :  
  
- Lors de l’enregistrement <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> de votre propriété, appelez la méthode au lieu de la méthode normale <xref:System.Windows.DependencyProperty.Register%2A> pour l’enregistrement des biens.  
  
- Lors de la mise en œuvre de la propriété CLR "wrapper", assurez-vous que l’emballage n’a pas non plus une mise en œuvre ensemble, de sorte qu’il n’y a aucune incohérence dans l’état de lecture seulement pour l’emballage public que vous exposez.  
  
- L’objet retourné par l’enregistrement lu-seulement est <xref:System.Windows.DependencyPropertyKey> plutôt que <xref:System.Windows.DependencyProperty>. Vous devez toujours stocker ce champ sous forme de membre, mais, en général, vous ne le convertissez pas en membre public du type.  
  
 Indépendamment de la valeur ou champ privé que vous utilisez, le stockage de votre propriété de dépendance en lecture seule peut être entièrement inscriptible en utilisant la logique de votre choix. Cependant, la façon la plus simple de définir la propriété soit initialement ou dans le cadre de la logique de temps d’exécution est d’utiliser les API du système de propriété, plutôt que de contourner le système de propriété et de définir le champ de soutien privé directement. En particulier, il ya <xref:System.Windows.DependencyObject.SetValue%2A> une signature de <xref:System.Windows.DependencyPropertyKey>qui accepte un paramètre de type . Comment et où vous définissez cette valeur de façon programmatique dans <xref:System.Windows.DependencyPropertyKey> votre logique d’application affectera la façon dont vous pouvez définir l’accès sur le créé lorsque vous avez enregistré la propriété de dépendance pour la première fois. Si vous gérez cette logique entièrement dans la classe, vous pouvez indiquer qu’elle est privée ou, si vous voulez qu’elle soit définie à partir d’autres parties de l’assembly, vous pouvez la définir en interne. Une approche consiste <xref:System.Windows.DependencyObject.SetValue%2A> à appeler dans un gestionnaire d’événements de classe d’un événement pertinent qui informe une instance de classe que la valeur de la propriété stockée doit être changée. Une autre approche consiste à lier <xref:System.Windows.PropertyChangedCallback> <xref:System.Windows.CoerceValueCallback> les propriétés de dépendance en utilisant des rappels et des rappels appariés dans le cadre des métadonnées de ces propriétés lors de l’enregistrement.  
  
 Parce <xref:System.Windows.DependencyPropertyKey> que le est privé, et n’est pas propagé par le système de propriété en dehors de votre code, une propriété de dépendance lecture-seulement a une meilleure sécurité de réglage qu’une propriété de dépendance lire-écrire. Pour une propriété de dépendance en lecture-écriture, le champ d’identification est explicitement ou implicitement public et la propriété est donc largement définissable. Pour plus d’informations, consultez [Sécurité de propriété de dépendance](dependency-property-security.md).  
  
## <a name="see-also"></a>Voir aussi

- [Aperçu des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
