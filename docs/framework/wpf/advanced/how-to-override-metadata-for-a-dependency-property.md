---
title: 'Procédure : Substituer les métadonnées d’une propriété de dépendance'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
ms.openlocfilehash: ef0309ae0d03c8278134012e645960996c6f93c4
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610507"
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Procédure : Substituer les métadonnées d’une propriété de dépendance
Cet exemple montre comment substituer les métadonnées de propriété de dépendance par défaut héritées d’une classe, en appelant le <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> (méthode) et en fournissant des métadonnées spécifiques au type.  
  
## <a name="example"></a>Exemple  
 En définissant son <xref:System.Windows.PropertyMetadata>, une classe peut définir les comportements de la propriété de dépendance, telles que ses rappels de système de valeur et la propriété par défaut. De nombreuses classes de propriétés de dépendance ont déjà des métadonnées par défaut définies dans le cadre de leur processus d’inscription. Cela inclut les propriétés de dépendance qui font partie de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API. Une classe qui hérite de la propriété de dépendance par l’intermédiaire de son héritage de classe peut substituer les métadonnées d’origine pour que les caractéristiques de la propriété qui peuvent être modifiées via des métadonnées respectent les exigences propres à la sous-classe.  
  
 La substitution des métadonnées sur une propriété de dépendance doit être effectuée avant que celle-ci soit mise en cours d’utilisation par le système de propriétés (cela équivaut au moment où des instances spécifiques d’objets qui inscrivent la propriété sont instanciées). Les appels à <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> doivent être effectués dans les constructeurs statiques du type qui fournit lui-même comme le `forType` paramètre de <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Si vous tentez de changer des métadonnées une fois qu’il existe des instances du type propriétaire, cela ne déclenche pas d’exceptions mais provoque des comportements incohérents dans le système de propriétés. En outre, les métadonnées ne peuvent être substituée qu’une seule fois par type. Toute tentative ultérieure de substitution des métadonnées sur le même type lève une exception.  
  
 Dans l’exemple suivant, la classe personnalisée `MyAdvancedStateControl` remplace les métadonnées fournies pour `StateProperty` par `MyAdvancedStateControl` par de nouvelles métadonnées de propriété. Par exemple, la valeur par défaut de `StateProperty` est désormais `true` quand la propriété est interrogée sur une instance de `MyAdvancedStateControl` nouvellement construite.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty>
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Rubriques de guide pratique](properties-how-to-topics.md)
