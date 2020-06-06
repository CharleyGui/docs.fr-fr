---
title: <TimeSpan_LegacyFormatMode>, élément
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968905"
---
# <a name="timespan_legacyformatmode-element"></a>Élément \<TimeSpan_LegacyFormatMode>

Détermine si le runtime conserve le comportement hérité dans les opérations de mise en forme avec des <xref:System.TimeSpan?displayProperty=nameWithType> valeurs.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

## <a name="syntax"></a>Syntaxe

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime utilise le comportement de mise en forme hérité avec les <xref:System.TimeSpan?displayProperty=nameWithType> valeurs.|

## <a name="enabled-attribute"></a>Attribut enabled

|Valeur|Description|
|-----------|-----------------|
|`false`|Le runtime ne restaure pas le comportement de mise en forme hérité.|
|`true`|Le runtime restaure le comportement de mise en forme hérité.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|

## <a name="remarks"></a>Remarques

À partir du .NET Framework 4, la <xref:System.TimeSpan?displayProperty=nameWithType> structure implémente l' <xref:System.IFormattable> interface et prend en charge les opérations de mise en forme avec des chaînes de format standard et personnalisées. Si une méthode d’analyse rencontre un spécificateur de format ou une chaîne de format non pris en charge, elle lève une <xref:System.FormatException> .

Dans les versions précédentes du .NET Framework, la <xref:System.TimeSpan> structure n’a pas implémenté <xref:System.IFormattable> et ne prenait pas en charge les chaînes de format. Toutefois, de nombreux développeurs ont pris par erreur pris <xref:System.TimeSpan> en charge un ensemble de chaînes de format et les utilisaient dans des [opérations de mise en forme composite](../../../../standard/base-types/composite-formatting.md) avec des méthodes telles que <xref:System.String.Format%2A?displayProperty=nameWithType> . En règle générale, si un type implémente <xref:System.IFormattable> et prend en charge les chaînes de format, les appels aux méthodes de mise en forme avec des chaînes de format non prises en charge lèvent généralement <xref:System.FormatException> . Toutefois, étant donné que <xref:System.TimeSpan> n’a pas implémenté <xref:System.IFormattable> , le runtime a ignoré la chaîne de format et a à la place appelé la <xref:System.TimeSpan.ToString?displayProperty=nameWithType> méthode. Cela signifie que, bien que les chaînes de format n’aient aucun effet sur l’opération de mise en forme, leur présence n’a pas entraîné de <xref:System.FormatException> .

Dans les cas où le code hérité passe une méthode de mise en forme composite et une chaîne de format non valide, et que ce code ne peut pas être recompilé, vous pouvez utiliser l' `<TimeSpan_LegacyFormatMode>` élément pour restaurer le <xref:System.TimeSpan> comportement hérité. Lorsque vous affectez `enabled` à l’attribut de cet élément `true` la valeur, la méthode de mise en forme composite entraîne un appel à <xref:System.TimeSpan.ToString?displayProperty=nameWithType> plutôt que <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> , et une <xref:System.FormatException> n’est pas levée.

## <a name="example"></a>Exemple

L’exemple suivant instancie un <xref:System.TimeSpan> objet et tente de le mettre en forme avec la <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> méthode à l’aide d’une chaîne de format standard non prise en charge.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Lorsque vous exécutez l’exemple sur la .NET Framework 3,5 ou sur une version antérieure, la sortie suivante s’affiche :

```console
12:30:45
```

Cela diffère de façon marquée de la sortie si vous exécutez l’exemple sur le .NET Framework 4 ou version ultérieure :

```console
Invalid Format
```

Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l’exemple, puis exécutez l’exemple sur le .NET Framework 4 ou une version ultérieure, la sortie est identique à celle produite par l’exemple lorsqu’elle est exécutée sur .NET Framework 3,5.

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
