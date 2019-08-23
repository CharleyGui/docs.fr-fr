---
title: Sécurité de propriété de dépendance
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: d9dd9306980b80f7845c10e8c0ccb59f29821245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940836"
---
# <a name="dependency-property-security"></a>Sécurité de propriété de dépendance
Les propriétés de dépendance doivent généralement être considérées comme des propriétés publiques. La nature du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] empêche de pouvoir garantir la sécurité d’une valeur de propriété de dépendance.  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Accès et sécurité des wrappers et des propriétés de dépendance  
 En règle générale, les propriétés de dépendance sont implémentées avec les propriétés de «wrapper» common language runtime (CLR) qui simplifient l’obtention ou la définition de la propriété à partir d’une instance. Toutefois, les wrappers sont simplement des méthodes pratiques qui implémentent <xref:System.Windows.DependencyObject.GetValue%2A> les <xref:System.Windows.DependencyObject.SetValue%2A> appels sous-jacents et statiques utilisés lors de l’interaction avec les propriétés de dépendance. D’une autre manière, les propriétés sont exposées en tant que propriétés common language runtime (CLR) qui sont sauvegardées par une propriété de dépendance plutôt que par un champ privé. Les mécanismes de sécurité appliqués aux wrappers ne sont pas identiques au comportement du système de propriétés et au niveau d’accès de la propriété de dépendance sous-jacente. Le placement d’une demande de sécurité sur le wrapper empêche uniquement l’utilisation de la méthode pratique, mais n’empêche <xref:System.Windows.DependencyObject.GetValue%2A> pas <xref:System.Windows.DependencyObject.SetValue%2A>les appels à ou. De même, placer un niveau d’accès privé ou protégé sur les wrappers ne procure pas une sécurité efficace.  
  
 Si vous écrivez vos propres propriétés de dépendance, vous devez déclarer les wrappers et le <xref:System.Windows.DependencyProperty> champ d’identificateur comme membres publics, afin que les appelants n’obtiennent pas d’informations trompeuses sur le niveau d’accès réel de cette propriété (en raison de l’absence de son magasin). implémenté en tant que propriété de dépendance).  
  
 Pour une propriété de dépendance personnalisée, vous pouvez inscrire votre propriété en tant que propriété de dépendance en lecture seule, ce qui fournit un moyen efficace d’empêcher une propriété qui est définie par quiconque ne contient pas de référence <xref:System.Windows.DependencyPropertyKey> à pour cette propriété. Pour plus d’informations, consultez [Propriétés de dépendance en lecture seule](read-only-dependency-properties.md).  
  
> [!NOTE]
> La déclaration d' <xref:System.Windows.DependencyProperty> un champ d’identificateur privé n’est pas interdite et elle peut être utilisée pour réduire l’espace de noms immédiatement exposé d’une classe personnalisée, mais une telle propriété ne doit pas être considérée comme «privée» dans le même sens que le Common Language les définitions de langage du Runtime (CLR) définissent ce niveau d’accès, pour les raisons décrites dans la section suivante.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Exposition des propriétés de dépendance par le système de propriétés  
 Il n’est généralement pas utile, et il est potentiellement trompeur, pour déclarer un <xref:System.Windows.DependencyProperty> comme niveau d’accès autre que public. Ce paramètre de niveau d’accès empêche seulement une personne d’obtenir une référence à l’instance à partir de la classe de déclaration. Toutefois, il existe plusieurs aspects du système de propriétés qui retournent un <xref:System.Windows.DependencyProperty> comme moyen d’identifier une propriété particulière telle qu’elle existe sur une instance d’une classe ou une instance de classe dérivée, et cet identificateur est toujours utilisable dans un <xref:System.Windows.DependencyObject.SetValue%2A> appel même Si l’identificateur statique d’origine est déclaré comme étant non public. En outre <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> , les méthodes virtuelles reçoivent des informations sur toute propriété de dépendance existante qui a modifié la valeur. En outre, la <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> méthode retourne des identificateurs pour toute propriété sur des instances avec une valeur définie localement.  
  
### <a name="validation-and-security"></a>Validation et sécurité  
 L’application d’une demande <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> à un et l’échec de la validation sur un échec de demande pour empêcher la définition d’une propriété n’est pas un mécanisme de sécurité approprié. L’invalidation de la valeur Set appliquée par le <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> biais de peut également être supprimée par des appelants malveillants, si ces appelants fonctionnent dans le domaine d’application.  
  
## <a name="see-also"></a>Voir aussi

- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
