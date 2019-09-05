---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef814d1b5f32359033e8a19999d6271677315fff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252422"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >, élément

Spécifie si le runtime utilise une quantité de mémoire fixe pour calculer les codes de hachage pour la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >**  

## <a name="syntax"></a>Syntaxe

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br /> Spécifie si le CLR (Common Langage Runtime) alloue une quantité de mémoire fixe lors du calcul des codes de hachage.|

## <a name="enabled-attribute"></a>Attribut enabled

|Valeur|Description|
|-----------|-----------------|
|0|Le Common Langage Runtime alloue une quantité de mémoire variable à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> pour calculer les codes de hachage. Il s'agit de la valeur par défaut.|
|1|Le Common Langage Runtime alloue une quantité de mémoire fixe à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> pour calculer les codes de hachage.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|

## <a name="remarks"></a>Notes

Par défaut, le CLR alloue une quantité de mémoire variable à la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> , et une exception <xref:System.ArgumentException> peut être levée lorsque la méthode tente de calculer le code de hachage de chaînes très longues (de plusieurs millions de caractères). Ajouter cet élément dans un fichier de configuration de l'application et affecter la valeur « 1 » à son attribut `enabled` vous permet de spécifier que la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> utilise un autre algorithme qui alloue une quantité de mémoire fixe au calcul du code de hachage.

> [!IMPORTANT]
> L'élément `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` n'est pas utilisé dans [!INCLUDE[win8](../../../../../includes/win8-md.md)] et ses versions ultérieures.

## <a name="see-also"></a>Voir aussi

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
