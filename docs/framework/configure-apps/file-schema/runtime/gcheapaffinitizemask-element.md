---
title: Élément GCHeapAffinitizeMask
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978381"
---
# <a name="gcheapaffinitizemask-element"></a>\<GCHeapAffinitizeMask>, élément

Définit l’affinité entre les tas GC et les processeurs individuels.

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a>Syntaxe

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br />Spécifie l’affinité entre les tas GC et les processeurs individuels. |

#### <a name="enabled-attribute"></a>attribut activé

|Valeur|Description|
|-----------|-----------------|
|`nnnn`|Valeur décimale qui forme un masque de masque définissant l’affinité entre les segments de mémoire GC du serveur et les processeurs individuels. |

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Remarques

Par défaut, les threads de garbage collection de serveur sont affinités avec leur processeur respectif, de sorte qu’il existe un tas GC, un thread GC de serveur et un thread de garbage collection de serveur d’arrière-plan pour chaque processeur. À compter de .NET Framework 4.6.2, vous pouvez utiliser l’élément **GCHeapAffinitizeMask** pour contrôler l’affinité entre les tas et les processeurs de garbage collection de serveur lorsque le nombre de segments est limité par l’élément **GCHeapCount** .

**GCHeapAffinitizeMask** est généralement utilisé avec deux autres indicateurs :

- [GCNoAffinitize](gcnoaffinitize-element.md), qui contrôle si les threads/segments de mémoire GC du serveur sont affinité avec des processeurs. L' `enabled` attribut de l’élément [GCNoAffinitize](gcnoaffinitize-element.md) doit être `false` (sa valeur par défaut) pour que le paramètre **GCHeapAffinitizeMask** soit utilisé.

- [GCHeapCount](gcheapcount-element.md), qui limite le nombre de segments de mémoire utilisés par le processus pour le garbage collection de serveur. Par défaut, il existe un tas pour chaque processeur.

**nnnn** est un masque de bits exprimé sous la forme d’une valeur décimale. Le bit 0 de l’octet 0 représente le processeur 0, le bit 1 de l’octet 0 représente le processeur 1, et ainsi de suite. Par exemple :

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

La valeur 1023 est 0x3FF ou 0011 1111 1111b. Le processus utilise 10 processeurs, du processeur 0 jusqu’au processeur 9.

## <a name="example"></a>Exemple

L’exemple suivant indique qu’une application utilise le garbage collection de serveur avec 10 tas/threads. Étant donné que vous ne voulez pas que ces tas chevauchent les tas d’autres applications s’exécutant sur le système, utilisez **GCHeapAffinitizeMask** pour spécifier que le processus doit utiliser les UC de 0 à 9.

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Élément GCNoAffinitize](gcnoaffinitize-element.md)
- [Élément GCHeapCount](gcheapcount-element.md)
- [Notions de base de garbage collection](../../../../standard/garbage-collection/fundamentals.md)
- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
