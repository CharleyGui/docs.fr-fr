---
title: Élément gcConcurrent
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102916"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent>, élément

Spécifie si le common language runtime exécute l'opération garbage collection sur un thread distinct.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a>Syntaxe

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br />Spécifie si le runtime exécute l’opération garbage collection simultanément.|

#### <a name="enabled-attribute"></a>attribut activé

|Valeur|Description|
|-----------|-----------------|
|`false`|Ne s’exécute pas garbage collection simultanément.|
|`true`|Exécute l'opération garbage collection simultanément. Il s'agit de la valeur par défaut.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Remarques

Avant le .NET Framework 4, la station de travail garbage collection prenait en charge garbage collection simultanés, qui effectuaient garbage collection en arrière-plan sur un thread distinct. Dans .NET Framework 4, la garbage collection simultanée a été remplacée par le GC d’arrière-plan, qui exécute également garbage collection en arrière-plan sur un thread distinct. À compter de .NET Framework 4,5, la collecte d’arrière-plan est disponible dans le garbage collection serveur. L’élément **gcConcurrent** contrôle si le runtime effectue une exécution simultanée ou d’arrière-plan garbage collection, s’il est disponible, ou s’il effectue des garbage collection au premier plan.

### <a name="to-disable-background-garbage-collection"></a>Pour désactiver les garbage collection d’arrière-plan

> [!WARNING]
> À partir de .NET Framework 4, la garbage collection simultanée est remplacée par l’garbage collection d’arrière-plan. Les termes *simultanés* et en *arrière-plan* sont utilisés de manière interchangeable dans la documentation de .NET Framework. Pour désactiver les garbage collection d’arrière-plan, utilisez l’élément **gcConcurrent** , comme indiqué dans cet article.

Par défaut, le runtime utilise le garbage collection simultané ou d’arrière-plan, dont la latence est optimisée. Si votre application implique une grande interaction avec l'utilisateur, laissez le garbage collection simultané activé pour minimiser le temps d'interruption de l'application pendant l'exécution de l'opération garbage collection. Si vous affectez `enabled` à l’attribut de l’élément **gcConcurrent** la valeur `false` , le runtime utilise des garbage collection non simultanées, ce qui est optimisé pour le débit.

Le fichier de configuration suivant désactive les garbage collection d’arrière-plan :

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

S’il existe un paramètre **gcConcurrentSetting** dans le fichier de configuration de l’ordinateur, il définit la valeur par défaut pour toutes les applications .NET Framework. Ce paramètre se substitue au paramètre du fichier de configuration de l'application.

Pour plus d’informations sur les garbage collection simultanés et d’arrière-plan, consultez [garbage collection d’arrière-plan](../../../../standard/garbage-collection/background-gc.md).

## <a name="example"></a>Exemple

L’exemple suivant active les garbage collection d’arrière-plan :

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Principes de base du Garbage Collection](../../../../standard/garbage-collection/fundamentals.md)
