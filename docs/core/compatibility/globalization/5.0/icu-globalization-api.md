---
title: 'Modification avec rupture : les API de globalisation utilisent des bibliothèques ICU sur Windows'
description: Découvrez les modifications avec rupture de la globalisation dans .NET 5,0 où les bibliothèques ICU sont utilisées pour la fonctionnalité de globalisation au lieu de NLS.
ms.date: 05/19/2020
ms.openlocfilehash: efc20e21969ea4a83c9122e40b262e1dc38e6770
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761291"
---
# <a name="globalization-apis-use-icu-libraries-on-windows"></a>Les API de globalisation utilisent des bibliothèques ICU sur Windows

.NET 5,0 et les versions ultérieures utilisent des bibliothèques [ICU (International Components for Unicode)](http://site.icu-project.org/home) pour la globalisation lorsqu’elles s’exécutent sur Windows 10 mai 2019 Update ou version ultérieure.

## <a name="change-description"></a>Description de la modification

Dans .NET Core 1,0-3,1 et .NET Framework 4 et versions ultérieures, les bibliothèques .NET utilisent les API [NLS (National Language Support)](/windows/win32/intl/national-language-support) pour la fonctionnalité de globalisation sur Windows. Par exemple, les fonctions NLS ont été utilisées pour comparer des chaînes, obtenir des informations sur la culture et effectuer la casse des chaînes dans la culture appropriée.

À compter de .NET 5,0, si une application s’exécute sur Windows 10 mai 2019 Update ou une version ultérieure, les bibliothèques .NET utilisent les API de globalisation [ICU](http://site.icu-project.org/home) , par défaut.

> [!NOTE]
> La mise à jour de Windows 10 mai 2019 et les versions ultérieures sont fournies avec la bibliothèque Native ICU. Si le Runtime .NET ne peut pas charger ICU, il utilise NLS à la place.

## <a name="behavioral-differences"></a>Différences de comportement

Vous pouvez voir les modifications apportées à votre application même si vous ne vous rendez pas compte que vous utilisez des fonctionnalités de globalisation. Cette section répertorie quelques-unes des modifications comportementales que vous pouvez constater, mais il en existe d’autres.

### <a name="stringindexof"></a>String.IndexOf

Prenons le code suivant qui appelle <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> pour Rechercher l’index du caractère de saut de ligne dans une chaîne.

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- Dans les versions précédentes de .NET sur Windows, l’extrait de code s’imprime `6` .
- Dans .NET 5,0 et versions ultérieures sur Windows 19H1 et versions ultérieures, l’extrait de code s’imprime `-1` .

Pour corriger ce code en effectuant une recherche ordinale au lieu d’une recherche dépendante de la culture, appelez la <xref:System.String.IndexOf(System.String,System.StringComparison)> surcharge et transmettez-la <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> en tant qu’argument.

Vous pouvez exécuter les règles [d’analyse du code CA1307 : spécifiez StringComparison pour plus de clarté](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) et [Ca1309 : utiliser StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) avec la valeur ordinale pour rechercher ces sites d’appel dans votre code.

Pour plus d’informations, consultez [changements de comportement lors de la comparaison de chaînes sur .net 5 +](../../../../standard/base-types/string-comparison-net-5-plus.md).

### <a name="currency-symbol"></a>Symbole monétaire

Considérez le code suivant qui met en forme une chaîne à l’aide du spécificateur de format monétaire `C` . La culture du thread actuel est définie sur une culture qui comprend uniquement la langue et non le pays.

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- Dans les versions précédentes de .NET sur Windows, la valeur de texte est `"100,00 €"` .
- Dans .NET 5,0 et versions ultérieures sur Windows 19H1 et versions ultérieures, la valeur de Text est `"100,00 ¤"` , qui utilise le symbole monétaire international au lieu de l’euro. Dans ICU, la conception est qu’une devise est une propriété d’un pays ou d’une région, et non d’une langue.

## <a name="reason-for-change"></a>Motif de modification

Cette modification a été introduite pour unifier. Comportement de la globalisation du réseau sur tous les systèmes d’exploitation pris en charge. Il offre également la possibilité pour les applications de regrouper leurs propres bibliothèques de globalisation plutôt que de dépendre des bibliothèques intégrées du système d’exploitation.

## <a name="version-introduced"></a>Version introduite

.NET 5,0

## <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de la part du développeur. Toutefois, si vous souhaitez continuer à utiliser les API de globalisation NLS, vous pouvez définir un [commutateur au moment](../../../run-time-config/globalization.md#nls) de l’exécution pour revenir à ce comportement. Pour plus d’informations sur les commutateurs disponibles, consultez l’article présentation de la [globalisation et de la bibliothèque .net](../../../../standard/globalization-localization/globalization-icu.md) .

## <a name="affected-apis"></a>API affectées

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- La plupart des types dans l' <xref:System.Globalization?displayProperty=fullName> espace de noms
- <xref:System.Array.Sort%2A?displayProperty=fullName> (lors du tri d’un tableau de chaînes)
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (lorsque les éléments de la liste sont des chaînes)
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (lorsque les clés sont des chaînes)
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (lorsque les clés sont des chaînes)
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (lorsque l’ensemble contient des chaînes)

<!--

### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

### Category

- Core .NET libraries
- Globalization

-->
