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
ms.openlocfilehash: 36066d6b2405051a3d35befffe53af8895e26220
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964835"
---
# <a name="datetime-xaml-syntax"></a>DateTime, syntaxe XAML
Certains contrôles, tels que <xref:System.Windows.Controls.Calendar> et <xref:System.Windows.Controls.DatePicker>, ont des propriétés qui utilisent <xref:System.DateTime> le type. Bien que vous spécifiiez généralement une date ou une heure initiale pour ces contrôles dans le code-behind au moment de l’exécution, vous pouvez en spécifier une en XAML. L’analyseur XAML WPF gère l’analyse des <xref:System.DateTime> valeurs à l’aide d’une syntaxe de texte XAML intégrée. Cette rubrique décrit les caractéristiques de la <xref:System.DateTime> syntaxe de texte XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>Quand utiliser la syntaxe XAML de DateTime ?  
 La définition des dates en XAML n’est pas toujours nécessaire, et n’est même parfois pas souhaitable. Par exemple, vous pouvez utiliser la <xref:System.DateTime.Now%2A?displayProperty=nameWithType> propriété pour initialiser une date au moment de l’exécution, ou vous pouvez effectuer tous vos ajustements de date pour un calendrier dans le code-behind en fonction de l’entrée de l’utilisateur. Toutefois, il existe des scénarios dans lesquels vous pouvez souhaiter coder en dur des dates <xref:System.Windows.Controls.Calendar> dans <xref:System.Windows.Controls.DatePicker> un et dans un modèle de contrôle. La <xref:System.DateTime> syntaxe XAML doit être utilisée pour ces scénarios.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>La syntaxe XAML de DateTime est un comportement natif  
 <xref:System.DateTime>est une classe qui est définie dans les bibliothèques de classes de base du CLR. En raison de la façon dont les bibliothèques de classes de base sont liées au reste du CLR, il n' <xref:System.ComponentModel.TypeConverterAttribute> est pas possible d’appliquer à la classe et d’utiliser un convertisseur de type pour traiter <xref:System.DateTime> des chaînes à partir de XAML et les convertir en dans le modèle objet au moment de l’exécution. Il existe aucune classe `DateTimeConverter` qui fournit le comportement de conversion ; le comportement de conversion décrit dans cette rubrique est natif à l’analyseur XAML WPF.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>Chaînes de format pour la syntaxe XAML de DateTime  
 Vous pouvez spécifier le format d’un <xref:System.DateTime> avec une chaîne de format. Les chaînes de format formalisent la syntaxe de texte qui peut être utilisée pour créer une valeur. <xref:System.DateTime>les valeurs des contrôles WPF existants utilisent généralement uniquement les composants date de <xref:System.DateTime> et non les composants Time.  
  
 Lorsque vous spécifiez un <xref:System.DateTime> en XAML, vous pouvez utiliser n’importe quelle chaîne de format de façon interchangeable.  
  
 Vous pouvez également utiliser des formats et des chaînes de format qui ne sont pas indiquées spécifiquement dans cette rubrique. Techniquement, le code XAML pour <xref:System.DateTime> toute valeur spécifiée puis analysée par l’analyseur XAML WPF utilise un appel interne à <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, par conséquent, vous pouvez utiliser n’importe quelle chaîne <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> acceptée par pour votre entrée XAML. Pour plus d'informations, consultez <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> La syntaxe XAML DateTime utilise `en-us` toujours <xref:System.Globalization.CultureInfo> comme pour sa conversion native. Cela n’est pas influencé <xref:System.Windows.FrameworkElement.Language%2A> par la `xml:lang` valeur ou la valeur dans le XAML, car la conversion de type au niveau de l’attribut XAML agit sans ce contexte. N’essayez pas d’interpoler les chaînes de format présentées ici en raison des variations culturelles, telles que l’ordre d’affichage du jour et du mois. Les chaînes de format illustrées ici sont exactement celles utilisées lors de l’analyse du XAML, quels que soient les autres paramètres de culture.  
  
 Les sections suivantes décrivent certaines chaînes de <xref:System.DateTime> format courantes.  
  
### <a name="short-date-pattern-d"></a>Modèle de date courte (« d »)  
 L’exemple suivant montre le format de date abrégée d’un <xref:System.DateTime> en XAML:  
  
 `M/d/YYYY`  
  
 Il s’agit de la forme la plus simple qui spécifie toutes les informations nécessaires pour les utilisations typiques par les contrôles WPF. Elle ne peut pas être influencée par des décalages de fuseau horaire accidentels par rapport à un composant d’heure, et est donc recommandée par rapport aux autres formats.  
  
 Par exemple, pour spécifier le 1er juin 2010, utilisez la chaîne suivante :  
  
 `3/1/2010`  
  
 Pour plus d'informations, consultez <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Modèle de date/heure pouvant être trié (« s »)  
 L’exemple suivant montre le <xref:System.DateTime> modèle triable en XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Par exemple, pour spécifier le 1er juin 2010, utilisez la chaîne suivante (les composants heure sont tous entrés avec la valeur 0) :  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Modèle RFC1123 (« r »)  
 Le modèle RFC1123 est utile, car il peut constituer une entrée de chaîne pour d’autres générateurs de date qui utilisent également le modèle RFC1123 pour des raisons de culture dite indifférente. L’exemple suivant montre le <xref:System.DateTime> modèle RFC1123 en XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Par exemple, pour spécifier le 1er juin 2010, utilisez la chaîne suivante (les composants heure sont tous entrés avec la valeur 0) :  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Autres formats et modèles  
 Comme indiqué précédemment, un <xref:System.DateTime> en XAML peut être spécifié comme n’importe quelle chaîne acceptable comme entrée pour <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Cela comprend d’autres formats formalisés (par <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>exemple) et des formats qui ne sont pas formalisés comme <xref:System.Globalization.DateTimeFormatInfo> un formulaire particulier. Par exemple, le formulaire `YYYY/mm/dd` est acceptable comme entrée pour <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Cette rubrique n’a pas pour but de décrire tous les formats possibles qui fonctionnent, mais plutôt de recommander l’usage du modèle de date courte comme pratique standard.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
