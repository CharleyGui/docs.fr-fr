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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f16a2bbd2470b4aec9e95ab67ccb0e736c4c6d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920690"
---
# <a name="timespan_legacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode >, élément

Détermine si le runtime conserve le comportement hérité dans les opérations de mise en <xref:System.TimeSpan?displayProperty=nameWithType> forme avec des valeurs.

\<configuration>\
\<> du runtime \
\<TimeSpan_LegacyFormatMode>

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
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime utilise le comportement de mise <xref:System.TimeSpan?displayProperty=nameWithType> en forme hérité avec les valeurs.|

## <a name="enabled-attribute"></a>Attribut enabled

|`Value`|Description|
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

## <a name="remarks"></a>Notes

À partir du .NET Framework 4, la <xref:System.TimeSpan?displayProperty=nameWithType> structure implémente l' <xref:System.IFormattable> interface et prend en charge les opérations de mise en forme avec des chaînes de format standard et personnalisées. Si une méthode d’analyse rencontre un spécificateur de format ou une chaîne de format non pris en charge, elle lève une <xref:System.FormatException>.

Dans les versions précédentes du .NET Framework, la <xref:System.TimeSpan> structure n’a pas <xref:System.IFormattable> implémenté et ne prenait pas en charge les chaînes de format. Toutefois, de nombreux développeurs ont pris par <xref:System.TimeSpan> erreur pris en charge un ensemble de chaînes de format et les utilisaient dans des opérations de [mise en forme composite](../../../../standard/base-types/composite-formatting.md) avec des méthodes telles que. <xref:System.String.Format%2A?displayProperty=nameWithType> En règle générale, si un type implémente <xref:System.IFormattable> et prend en charge les chaînes de format, les appels aux méthodes de mise en forme avec des chaînes de format non prises en charge <xref:System.FormatException>lèvent généralement. Toutefois, étant <xref:System.TimeSpan> donné que n' <xref:System.IFormattable>a pas implémenté, le runtime a ignoré la chaîne de <xref:System.TimeSpan.ToString?displayProperty=nameWithType> format et a à la place appelé la méthode. Cela signifie que, bien que les chaînes de format n’aient aucun effet sur l’opération de mise en forme, leur présence <xref:System.FormatException>n’a pas entraîné de.

Dans les cas où le code hérité passe une méthode de mise en forme composite et une chaîne de format non valide, et que ce code ne peut `<TimeSpan_LegacyFormatMode>` pas être recompilé, <xref:System.TimeSpan> vous pouvez utiliser l’élément pour restaurer le comportement hérité. Lorsque vous affectez `enabled` à `true`l’attribut de cet élément la valeur, la méthode de mise en forme composite entraîne <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>un appel à <xref:System.FormatException> <xref:System.TimeSpan.ToString?displayProperty=nameWithType> plutôt que, et une n’est pas levée.

## <a name="example"></a>Exemple

L’exemple suivant instancie un <xref:System.TimeSpan> objet et tente de le mettre en forme <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> avec la méthode à l’aide d’une chaîne de format standard non prise en charge.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Lorsque vous exécutez l’exemple sur la .NET Framework 3,5 ou sur une version antérieure, la sortie suivante s’affiche:

```
12:30:45
```

Cela diffère de façon marquée de la sortie si vous exécutez l’exemple sur le .NET Framework 4 ou version ultérieure:

```
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
- [Schéma des fichiers de configuration](../index.md)
