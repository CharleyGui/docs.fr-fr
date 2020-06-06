---
title: Élément GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84004736"
---
# <a name="gcnoaffinitize-element"></a>\<GCNoAffinitize>, élément

Spécifie s’il faut ou non affinité les threads GC du serveur avec des processeurs.

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a>Syntaxe

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br />Spécifie si les threads/segments de mémoire GC du serveur sont affinités avec les processeurs disponibles sur l’ordinateur.|

#### <a name="enabled-attribute"></a>attribut activé

|Valeur|Description|
|-----------|-----------------|
|`false`|Threads GC affinité entre Server avec UC. Il s'agit de la valeur par défaut.|
|`true`|Ne affinité pas les threads GC du serveur avec des processeurs.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Remarques

Par défaut, les threads GC de serveur sont affinités avec leurs UC respectives. Chacun des processeurs disponibles du système a son propre tas GC et son propre thread. Il s’agit généralement du paramètre préféré, car il optimise l’utilisation du cache. À compter de .NET Framework 4.6.2, en affectant à l’attribut de l’élément **GCNoAffinitize** la valeur `enabled` `true` , vous pouvez spécifier que les threads de garbage collection du serveur et les processeurs ne doivent pas être étroitement couplés.

Vous pouvez spécifier l’élément de configuration **GCNoAffinitize** seul pour ne pas affinité les threads GC du serveur avec des processeurs. Vous pouvez également l’utiliser avec l’élément [GCHeapCount](gcheapcount-element.md) pour contrôler le nombre de tas GC et de threads utilisés par une application.

Si l' `enabled` attribut de l’élément **GCNoAffinitize** est `false` (sa valeur par défaut), vous pouvez également utiliser l’élément [GCHeapCount](gcheapcount-element.md) pour spécifier le nombre de threads GC et de tas, ainsi que l’élément [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) pour spécifier les processeurs sur lesquels les threads GC et les segments de mémoire sont affinité.

## <a name="example"></a>Exemple

L’exemple suivant ne prend pas en affinité les threads GC du serveur :

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

L’exemple suivant n’affinité pas les threads GC du serveur et limite le nombre de tas/threads GC à 10 :

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Élément GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)
- [Élément GCHeapCount](gcheapcount-element.md)
- [Notions de base de garbage collection](../../../../standard/garbage-collection/fundamentals.md)
- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
