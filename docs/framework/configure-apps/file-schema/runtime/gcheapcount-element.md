---
title: Élément GCHeapCount
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74283069"
---
# <a name="gcheapcount-element"></a>\<GCHeapCount>, élément

Spécifie le nombre de segments/threads à utiliser pour le garbage collection serveur.

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a>Syntaxe

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br />Spécifie le nombre de segments de mémoire à utiliser pour le garbage collection serveur. Le nombre réel de tas est le nombre minimal de segments de mémoire que vous spécifiez et le nombre de processeurs que votre processus est autorisé à utiliser. |

#### <a name="enabled-attribute"></a>attribut activé

|Valeur|Description|
|-----------|-----------------|
|`nn`|Nombre de segments de mémoire à utiliser pour le garbage collector du serveur.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Remarques

Par défaut, les threads de garbage collection de serveur sont affinités avec leur processeur respectif, de sorte qu’il existe un tas GC, un thread GC de serveur et un thread de garbage collection de serveur d’arrière-plan pour chaque processeur. À compter de .NET Framework 4.6.2, vous pouvez utiliser l’élément **GCHeapCount** pour limiter le nombre de segments de mémoire utilisés par votre application pour le garbage collector du serveur. Limiter le nombre de segments de mémoire utilisés pour le garbage collection de serveur est particulièrement utile pour les systèmes qui exécutent plusieurs instances d’une application serveur.

**GCHeapCount** est généralement utilisé avec deux autres indicateurs :

- [GCNoAffinitize](gcnoaffinitize-element.md), qui contrôle si les threads/segments de mémoire GC du serveur sont affinité avec des processeurs.

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), qui contrôle l’affinité des threads/tas GC avec des processeurs.

Si **GCHeapCount** est défini et **GCNoAffinitize** est désactivé (paramètre par défaut), il existe une affinité entre les segments de mémoire/tas GC *nn* et les premiers processeurs *nn* . Vous pouvez utiliser l’élément **GCHeapAffinitizeMask** pour spécifier quels processeurs sont utilisés par les tas GC du serveur du processus. Dans le cas contraire, si plusieurs processus serveur s’exécutent sur un système, leur utilisation se chevauchera.

Si **GCHeapCount** est défini et que **GCNoAffinitize** est activé, le garbage collector limite le nombre de processeurs utilisés pour le garbage collector du serveur, mais ne affinité pas les tas et les processeurs gc.

## <a name="example"></a>Exemple

L’exemple suivant indique qu’une application utilise le garbage collection de serveur avec 10 tas/threads. Étant donné que vous ne voulez pas que ces tas chevauchent les tas d’autres applications s’exécutant sur le système, vous utilisez **GCHeapAffinitizeMask** pour spécifier que le processus doit utiliser les UC de 0 à 9.

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

L’exemple suivant n’affinité pas les threads GC du serveur et limite le nombre de tas/threads GC à 10.

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
- [Élément GCNoAffinitize](gcnoaffinitize-element.md)
- [Élément GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)
- [Notions de base de garbage collection](../../../../standard/garbage-collection/fundamentals.md)
- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
