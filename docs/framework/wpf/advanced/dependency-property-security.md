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
ms.openlocfilehash: f5640b348ccd68819052f58756489489371862d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186396"
---
# <a name="dependency-property-security"></a>Sécurité de propriété de dépendance
Les propriétés de dépendance doivent généralement être considérées comme des propriétés publiques. La nature du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] empêche de pouvoir garantir la sécurité d’une valeur de propriété de dépendance.  

<a name="AccessSecurity"></a>
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Accès et sécurité des wrappers et des propriétés de dépendance  
 Typiquement, les propriétés de dépendance sont mises en œuvre avec "wrapper" propriétés de l’heure courante de langue commune (CLR) qui simplifient d’obtenir ou de définir la propriété à partir d’une instance. Mais les emballages sont vraiment juste <xref:System.Windows.DependencyObject.GetValue%2A> des <xref:System.Windows.DependencyObject.SetValue%2A> méthodes de commodité qui mettent en œuvre les appels sous-jacents et statiques qui sont utilisés lors de l’interaction avec les propriétés de dépendance. En y pensant d’une autre manière, les propriétés sont exposées comme des propriétés courantes de temps d’exécution de langue (CLR) qui se trouvent être soutenues par une propriété de dépendance plutôt que par un champ privé. Les mécanismes de sécurité appliqués aux wrappers ne sont pas identiques au comportement du système de propriétés et au niveau d’accès de la propriété de dépendance sous-jacente. Placer une demande de sécurité sur l’emballage n’empêchera que <xref:System.Windows.DependencyObject.GetValue%2A> l’utilisation de la méthode de commodité, mais n’empêchera pas les appels vers ou <xref:System.Windows.DependencyObject.SetValue%2A>. De même, placer un niveau d’accès privé ou protégé sur les wrappers ne procure pas une sécurité efficace.  
  
 Si vous écrivez vos propres propriétés de dépendance, vous devez déclarer les emballages et le <xref:System.Windows.DependencyProperty> champ d’identification en tant que membres du public, de sorte que les appelants n’obtiennent pas des informations trompeuses sur le niveau d’accès réel de cette propriété (en raison de son magasin étant mis en œuvre comme une propriété de dépendance).  
  
 Pour une propriété de dépendance personnalisée, vous pouvez enregistrer votre propriété comme une propriété de dépendance de lecture-seulement, et ceci <xref:System.Windows.DependencyPropertyKey> fournit un moyen efficace d’empêcher une propriété étant réglée par n’importe qui qui ne tient pas une référence à la pour cette propriété. Pour plus d’informations, consultez [Propriétés de dépendance en lecture seule](read-only-dependency-properties.md).  
  
> [!NOTE]
> Déclarer un <xref:System.Windows.DependencyProperty> champ d’identification privé n’est pas interdit, et il peut être utilisé pour aider à réduire l’espace de nom immédiatement exposé d’une classe personnalisée, mais une telle propriété ne devrait pas être considérée comme «privée» dans le même sens que les définitions de langage courant runtime (CLR) définir ce niveau d’accès, pour des raisons décrites dans la section suivante.  
  
<a name="PropertySystemExposure"></a>
## <a name="property-system-exposure-of-dependency-properties"></a>Exposition des propriétés de dépendance par le système de propriétés  
 Il n’est généralement pas utile, et <xref:System.Windows.DependencyProperty> il est potentiellement trompeur, de déclarer un niveau d’accès autre que le public. Ce paramètre de niveau d’accès empêche seulement une personne d’obtenir une référence à l’instance à partir de la classe de déclaration. Mais il y a plusieurs aspects du <xref:System.Windows.DependencyProperty> système de propriété qui retourneront un comme moyen d’identifier une propriété particulière car elle existe <xref:System.Windows.DependencyObject.SetValue%2A> sur une instance d’une classe ou d’une instance de classe dérivée, et cet identifiant est toujours utilisable dans un appel même si l’identifiant statique original est déclaré non public. En <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> outre, les méthodes virtuelles reçoivent des informations de toute propriété de dépendance existante qui a changé de valeur. En outre, <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> la méthode renvoie les identificateurs pour toute propriété sur les instances ayant une valeur définie localement.  
  
### <a name="validation-and-security"></a>Validation et sécurité  
 L’application d’une demande à a <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> et s’attendre à l’échec de validation sur un défaut de demande d’empêcher une propriété d’être fixé n’est pas un mécanisme de sécurité adéquat. L’invalidation de la <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> valeur définie appliquée par le biais pourrait également être supprimée par les appelants malveillants, si ces appelants opèrent dans le domaine de l’application.  
  
## <a name="see-also"></a>Voir aussi

- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
