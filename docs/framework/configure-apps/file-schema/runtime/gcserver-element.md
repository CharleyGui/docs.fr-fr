---
title: Élément gcServer
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968945"
---
# <a name="gcserver-element"></a>\<gcServer>, élément

Spécifie si le common language runtime exécute le garbage collection côté serveur.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a>Syntaxe

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br />Spécifie si le runtime exécute le garbage collection côté serveur.|

#### <a name="enabled-attribute"></a>attribut activé

|Valeur|Description|
|-----------|-----------------|
|`false`|N'exécute pas le garbage collection côté serveur. Il s'agit de la valeur par défaut.|
|`true`|Exécute le garbage collection côté serveur.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Remarques

Le common language runtime (ou CLR) prend en charge deux types de garbage collection : le garbage collection côté station de travail, qui est disponible sur tous les systèmes, et le garbage collection côté serveur, qui est disponible sur les systèmes multiprocesseurs. Utilisez l’élément **gcServer** pour contrôler le type de garbage collection que le CLR effectue. Utilisez la propriété <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> pour déterminer si le garbage collection côté serveur est activé.

Pour les ordinateurs monoprocesseurs, le garbage collection côté station de travail configuré par défaut représente normalement l'option la plus rapide. L'option station de travail ou serveur peut être utilisée pour les ordinateurs biprocesseurs. Le garbage collection côté serveur est normalement l'option la plus rapide pour les ordinateurs comptant plus de deux processeurs. En règle générale, les systèmes de serveurs multiprocesseurs désactivent le garbage collector du serveur et utilisent le GC de station de travail à la place lorsque de nombreuses instances d’une application serveur s’exécutent sur le même ordinateur.

Cet élément peut être défini uniquement dans le fichier de configuration de l'application (il est ignoré s'il est défini dans le fichier de configuration de l'ordinateur).

> [!NOTE]
> Dans .NET Framework 4 et les versions antérieures, le garbage collection simultané n'est pas disponible si le garbage collection côté serveur est activé. À partir de la .NET Framework 4,5, le garbage collection du serveur est simultané. Pour utiliser des garbage collection de serveur non simultanées, affectez à l’élément **gcServer** la valeur `true` et à l' [élément gcConcurrent](gcconcurrent-element.md) la valeur `false` .

À compter de .NET Framework 4.6.2, vous pouvez également utiliser les éléments suivants pour configurer le garbage collector du serveur :

- [GCNoAffinitize](gcnoaffinitize-element.md), qui spécifie s’il existe une affinité entre les tas et les PROCESSEURs GC du serveur. Par défaut, il existe un tas GC de serveur pour chaque processeur.

- [GCHeapCount](gcheapcount-element.md), qui limite le nombre de segments de mémoire utilisés par un processus.

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), qui définit l’affinité entre les tas de garbage collection de serveur disponibles et les processeurs individuels.

## <a name="example"></a>Exemple

L’exemple suivant active le garbage collection serveur :

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Pour désactiver les garbage collection simultanées](gcconcurrent-element.md#to-disable-background-garbage-collection)
