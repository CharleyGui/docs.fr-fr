---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1251f286a4e6168ef1d18b05288e0c5f353ad828
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689883"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup > élément

Indique si le garbage collection prend en charge plusieurs groupes de processeurs.

\<configuration>\
\<runtime>\
\<GCCpuGroup>

## <a name="syntax"></a>Syntaxe

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br /> Indique si le garbage collection prend en charge plusieurs groupes de processeurs.|

## <a name="enabled-attribute"></a>Attribut enabled

|Value|Description|
|-----------|-----------------|
|`false`|Le garbage collection ne prend pas en charge plusieurs groupes d’UC. Il s'agit de la valeur par défaut.|
|`true`|Le garbage collection prend en charge plusieurs groupes d’UC, si le garbage collection côté serveur est activé.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Notes

Quand un ordinateur a plusieurs groupes d’UC et de garbage collection côté serveur est activé (voir la [ \<< gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) élément), l’activation de cet élément s’étend le garbage collection dans tous les groupes d’UC et prend tous les cœurs dans compte lors de la création et l’équilibrage des segments de mémoire.

> [!NOTE]
> Cet élément s’applique uniquement aux threads de garbage collection. Pour activer le runtime distribuer les threads utilisateur sur tous les groupes d’UC, vous devez également activer le [ \<Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) élément.

## <a name="example"></a>Exemple

L’exemple suivant montre comment activer le garbage collection pour plusieurs groupes d’UC.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Pour désactiver le garbage collection simultané](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Garbage collection de station de travail et de serveur](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
