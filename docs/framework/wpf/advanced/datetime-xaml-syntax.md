---
title: DateTime, syntaxe XAML
ms.date: 03/30/2017
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
ms.openlocfilehash: 57b73d3b80f0392b99aacfbfac4d8709f72d52e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186330"
---
# <a name="datetime-xaml-syntax"></a>DateTime, syntaxe XAML
Certains contrôles, <xref:System.Windows.Controls.Calendar> tels <xref:System.Windows.Controls.DatePicker>que et , <xref:System.DateTime> ont des propriétés qui utilisent le type. Bien que vous spécifiiez généralement une date ou une heure initiale pour ces contrôles dans le code-behind au moment de l’exécution, vous pouvez en spécifier une en XAML. Le parsier WPF XAML gère <xref:System.DateTime> l’analyse des valeurs à l’aide d’une syntaxe texte XAML intégrée. Ce sujet décrit les spécificités de la <xref:System.DateTime> syntaxe texte XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>
## <a name="when-to-use-datetime-xaml-syntax"></a>Quand utiliser la syntaxe XAML de DateTime ?  
 La définition des dates en XAML n’est pas toujours nécessaire, et n’est même parfois pas souhaitable. Par exemple, vous <xref:System.DateTime.Now%2A?displayProperty=nameWithType> pouvez utiliser la propriété pour para initialiser une date à l’heure d’exécution, ou vous pouvez faire tous vos ajustements de date pour un calendrier dans le code-derrière basé sur l’entrée de l’utilisateur. Cependant, il existe des scénarios où vous pouvez <xref:System.Windows.Controls.Calendar> <xref:System.Windows.Controls.DatePicker> vouloir des dates de code dur dans un et dans un modèle de contrôle. La <xref:System.DateTime> syntaxe XAML doit être utilisée pour ces scénarios.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>La syntaxe XAML de DateTime est un comportement natif  
 <xref:System.DateTime>est une classe qui est définie dans les bibliothèques de classe de base du CLR. En raison de la façon dont les bibliothèques de classe de <xref:System.ComponentModel.TypeConverterAttribute> base se rapportent au reste du CLR, il n’est <xref:System.DateTime> pas possible de s’appliquer à la classe et d’utiliser un convertisseur de type pour traiter les chaînes de XAML et les convertir en modèle d’objet de temps d’exécution. Il existe aucune classe `DateTimeConverter` qui fournit le comportement de conversion ; le comportement de conversion décrit dans cette rubrique est natif à l’analyseur XAML WPF.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>
## <a name="format-strings-for-datetime-xaml-syntax"></a>Chaînes de format pour la syntaxe XAML de DateTime  
 Vous pouvez spécifier le format d’un <xref:System.DateTime> avec une chaîne de format. Les chaînes de format formalisent la syntaxe de texte qui peut être utilisée pour créer une valeur. <xref:System.DateTime>les valeurs pour les contrôles WPF existants <xref:System.DateTime> n’utilisent généralement que les composants de date des composants de temps et non.  
  
 Lorsque vous <xref:System.DateTime> spécifiez un XAML, vous pouvez utiliser l’une des chaînes de format de manière interchangeable.  
  
 Vous pouvez également utiliser des formats et des chaînes de format qui ne sont pas indiquées spécifiquement dans cette rubrique. Techniquement, le XAML <xref:System.DateTime> pour toute valeur qui est spécifiée, puis analysé par le parser WPF XAML utilise un appel interne à <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, donc vous pouvez utiliser n’importe quelle chaîne acceptée par <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> pour votre entrée XAML. Pour plus d’informations, consultez <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> La syntaxe DateTime XAML utilise `en-us` toujours comme <xref:System.Globalization.CultureInfo> pour sa conversion native. Cela n’est <xref:System.Windows.FrameworkElement.Language%2A> pas `xml:lang` influencé par la valeur ou la valeur dans le XAML, parce que XAML attribut-niveau de conversion de type agit sans ce contexte. N’essayez pas d’interpoler les chaînes de format présentées ici en raison des variations culturelles, telles que l’ordre d’affichage du jour et du mois. Les chaînes de format illustrées ici sont exactement celles utilisées lors de l’analyse du XAML, quels que soient les autres paramètres de culture.  
  
 Les sections suivantes décrivent <xref:System.DateTime> certaines des chaînes de format communes.  
  
### <a name="short-date-pattern-d"></a>Modèle de date courte (« d »)  
 Ce qui suit montre le <xref:System.DateTime> format de date courte pour un XAML :  
  
 `M/d/YYYY`  
  
 Il s’agit de la forme la plus simple qui spécifie toutes les informations nécessaires pour les utilisations typiques par les contrôles WPF. Elle ne peut pas être influencée par des décalages de fuseau horaire accidentels par rapport à un composant d’heure, et est donc recommandée par rapport aux autres formats.  
  
 Par exemple, pour spécifier le 1er juin 2010, utilisez la chaîne suivante :  
  
 `3/1/2010`  
  
 Pour plus d’informations, consultez <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Modèle de date/heure pouvant être trié (« s »)  
 Ce qui suit <xref:System.DateTime> montre le modèle triable dans XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Par exemple, pour spécifier le 1er juin 2010, utilisez la chaîne suivante (les composants heure sont tous entrés avec la valeur 0) :  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Modèle RFC1123 (« r »)  
 Le modèle RFC1123 est utile, car il peut constituer une entrée de chaîne pour d’autres générateurs de date qui utilisent également le modèle RFC1123 pour des raisons de culture dite indifférente. Ce qui suit montre le <xref:System.DateTime> modèle RFC1123 dans XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Par exemple, pour spécifier le 1er juin 2010, utilisez la chaîne suivante (les composants heure sont tous entrés avec la valeur 0) :  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Autres formats et modèles  
 Comme indiqué précédemment, un <xref:System.DateTime> dans XAML peut être spécifié <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>comme n’importe quelle chaîne qui est acceptable comme entrée pour . Cela comprend d’autres formats <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>formalisés (par exemple), et <xref:System.Globalization.DateTimeFormatInfo> des formats qui ne sont pas formalisés comme une forme particulière. Par exemple, `YYYY/mm/dd` le formulaire est <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>acceptable comme entrée pour . Cette rubrique n’a pas pour but de décrire tous les formats possibles qui fonctionnent, mais plutôt de recommander l’usage du modèle de date courte comme pratique standard.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
