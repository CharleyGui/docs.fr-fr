---
title: Propriétés de dépendance et chargement XAML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
ms.openlocfilehash: de8050e582f5b1a5a288c350c179cfa24fb5471c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186254"
---
# <a name="xaml-loading-and-dependency-properties"></a>Propriétés de dépendance et chargement XAML
L’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] actuelle de son processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] connaît de manière inhérente la propriété de dépendance. Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur utilise des méthodes de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] système de propriété pour les propriétés de dépendance lors du chargement binaire et des attributs de traitement qui sont des propriétés de dépendance. Cette fonctionnalité ignore efficacement les wrappers de propriété. Lorsque vous implémentez des propriétés de dépendance personnalisées, vous devez tenir compte de <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>ce comportement et devez éviter de placer n’importe quel autre code dans votre emballage de propriété autre que les méthodes de système de propriété et.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique part du principe que vous savez ce que sont les propriétés de dépendance, comme consommateur et comme auteur, et que vous avez lu [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md) et [Propriétés de dépendance personnalisées](custom-dependency-properties.md). Vous devez également avoir lu [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) et [Syntaxe XAML en détail](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Performance et implémentation du chargeur XAML WPF  
 Pour des raisons de mise en œuvre, il est computationnellement <xref:System.Windows.DependencyObject.SetValue%2A> moins coûteux d’identifier une propriété comme une propriété de dépendance et d’accéder à la méthode du système de propriété pour la définir, plutôt que d’utiliser l’emballage de propriété et son setter. Cela est dû au fait qu’un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit déduire l’intégralité du modèle objet du code de stockage uniquement sur la base de la connaissance du type et des relations entre les membres indiqués par la structure du balisage et différentes chaînes.  
  
 Le type est recherché par une combinaison de xmlns et d’attributs d’assemblage, mais l’identification des membres, la détermination <xref:System.Reflection.PropertyInfo>qui pourrait soutenir être fixé comme un attribut, et la résolution des types de la valeur de la propriété soutien aurait autrement besoin d’une réflexion approfondie en utilisant . Étant donné que les propriétés de dépendance à un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] type donné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont accessibles en tant que table de stockage par le biais du <xref:System.Windows.DependencyObject> système de propriété, la mise en œuvre de son processeur utilise cette table et déduit que n’importe quelle propriété donnée *ABC* peut être plus efficacement définie en faisant appel <xref:System.Windows.DependencyObject.SetValue%2A> au type dérivé contenant, en utilisant l’identifiant de propriété de dépendance *ABCProperty*.  
  
<a name="implications"></a>
## <a name="implications-for-custom-dependency-properties"></a>Implications pour les propriétés de dépendance personnalisées  
 Du fait que l’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] actuelle du comportement du processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour le paramètre de propriété ignore l’intégralité des wrappers, vous ne devez placer aucune logique supplémentaire dans les définitions du wrapper de votre propriété de dépendance personnalisée. Si vous intégrez cette logique dans la définition du jeu, la logique n’est pas exécutée quand la propriété est définie en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plutôt que dans le code.  
  
 De même, d’autres aspects du transformateur qui obtiennent la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] valeur de propriété du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] traitement utilisent <xref:System.Windows.DependencyObject.GetValue%2A> également plutôt que d’utiliser l’emballage. Par conséquent, vous devez également `get` éviter toute <xref:System.Windows.DependencyObject.GetValue%2A> mise en œuvre supplémentaire dans la définition au-delà de l’appel.  
  
 L’exemple suivant est une définition de propriété de dépendance recommandée `public` `static` `readonly` avec des `get` emballages, où l’identifiant de propriété est stocké comme un champ, et le et `set` les définitions ne contiennent aucun code au-delà des méthodes nécessaires de système de propriété qui définissent le soutien de propriété de dépendance.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Voir aussi

- [Aperçu des propriétés de dépendance](dependency-properties-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
- [Propriétés de dépendance de type collection](collection-type-dependency-properties.md)
- [Sécurité de propriété de dépendance](dependency-property-security.md)
- [Modèles de constructeur sécurisé pour DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
