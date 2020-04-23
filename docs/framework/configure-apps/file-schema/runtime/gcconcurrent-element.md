---
title: gc Élément courant
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
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102916"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent> élément

Spécifie si le common language runtime exécute l'opération garbage collection sur un thread distinct.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<>de temps d’exécution](runtime-element.md)\
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
|`false`|Il n’exécute pas la collecte des ordures en même temps.|
|`true`|Exécute l'opération garbage collection simultanément. Il s’agit de la valeur par défaut.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Notes

Avant .NET Framework 4, la collecte des ordures de poste de travail a soutenu la collecte simultanée des ordures, qui a effectué la collecte des ordures en arrière-plan sur un fil séparé. Dans .NET Framework 4, la collecte simultanée des ordures a été remplacée par GC de fond, qui effectue également la collecte des ordures en arrière-plan sur un fil séparé. À partir de .NET Framework 4.5, la collecte d’arrière-plan est devenue disponible dans la collecte des ordures serveur. **L’élément gcConcurrent** contrôle si le temps d’exécution effectue la collecte des ordures simultanées ou de fond, s’il est disponible, ou s’il effectue la collecte des ordures au premier plan.

### <a name="to-disable-background-garbage-collection"></a>Désactiver la collecte des ordures de fond

> [!WARNING]
> À partir du cadre .NET 4, la collecte simultanée des ordures est remplacée par la collecte des ordures de fond. Les termes *simultanés* et *les antécédents* sont utilisés de façon interchangeable dans la documentation du Cadre .NET. Pour désactiver la collecte des ordures de fond, utilisez **l’élément GCConcurrent,** tel que discuté dans cet article.

Par défaut, le runtime utilise le garbage collection simultané ou d’arrière-plan, dont la latence est optimisée. Si votre application implique une grande interaction avec l'utilisateur, laissez le garbage collection simultané activé pour minimiser le temps d'interruption de l'application pendant l'exécution de l'opération garbage collection. Si vous `enabled` définissez l’attribut de **l’élément gcConcurrent** à `false`, le temps d’exécution utilise la collecte des ordures non-concurrentes, qui est optimisée pour le débit.

Le fichier de configuration suivant désactive la collecte des ordures de fond :

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

S’il y a un paramètre **gcConcurrentSetting** dans le fichier de configuration de la machine, il définit la valeur par défaut pour toutes les applications cadre .NET. Ce paramètre se substitue au paramètre du fichier de configuration de l'application.

Pour plus d’informations sur la collecte des ordures simultanées et de fond, voir [Collection d’ordures de fond](../../../../standard/garbage-collection/background-gc.md).

## <a name="example"></a>Exemple

L’exemple suivant permet la collecte des ordures de fond :

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Paramètres de durée d’exécution Schema](index.md)
- [Configuration Fichier Schema](../index.md)
- [Principes de base du Garbage Collection](../../../../standard/garbage-collection/fundamentals.md)
