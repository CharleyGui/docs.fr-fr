---
title: Élément GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978374"
---
# <a name="gcnoaffinitize-element"></a>\<élément GCNoAffinitize >

Spécifie s’il faut ou non affinité les threads GC du serveur avec des processeurs.

\<> de configuration \
&nbsp;&nbsp;\<Runtime > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize >

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

|valeur|Description|
|-----------|-----------------|
|`false`|Threads GC affinité entre Server avec UC. Il s'agit de la valeur par défaut.|
|`true`|Ne affinité pas les threads GC du serveur avec des processeurs.|

### <a name="child-elements"></a>Éléments enfants

Aucun(e).

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Notes

Par défaut, les threads GC de serveur sont affinités avec leurs UC respectives. Chacun des processeurs disponibles du système a son propre tas GC et son propre thread. Il s’agit généralement du paramètre préféré, car il optimise l’utilisation du cache. À partir de .NET Framework 4.6.2, en affectant à l’attribut `enabled` de l’élément **GCNoAffinitize** la valeur `false`, vous pouvez spécifier que les threads et les processeurs de garbage collection du serveur ne doivent pas être étroitement couplés.

Vous pouvez spécifier l’élément de configuration **GCNoAffinitize** seul pour ne pas affinité les threads GC du serveur avec des processeurs. Vous pouvez également l’utiliser avec l’élément [GCHeapCount](gcheapcount-element.md) pour contrôler le nombre de tas GC et de threads utilisés par une application.

Si l’attribut `enabled` de l’élément **GCNoAffinitize** est `false` (sa valeur par défaut), vous pouvez également utiliser l’élément [GCHeapCount](gcheapcount-element.md) pour spécifier le nombre de threads GC et de tas, ainsi que l’élément [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) pour spécifier les processeurs sur lesquels les threads GC et les tas sont affinité.

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
- [Notions de base du garbage collection](../../../../standard/garbage-collection/fundamentals.md)
- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
