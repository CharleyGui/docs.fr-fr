---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102890"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup> Élément

Indique si le garbage collection prend en charge plusieurs groupes de processeurs.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

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

|Valeur|Description|
|-----------|-----------------|
|`false`|La collecte des ordures ne prend pas en charge plusieurs groupes de processeurs. Il s’agit de la valeur par défaut.|
|`true`|La collecte des ordures prend en charge plusieurs groupes de processeurs, si la collecte des ordures du serveur est activée.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Notes

Lorsqu’un ordinateur dispose de plusieurs groupes de processeurs et que la collecte des ordures des serveurs est activée (voir [ \<l’élément gcServer>),](gcserver-element.md) ce qui permet à cet élément d’étendre la collecte des ordures dans tous les groupes de processeur et de prendre en compte tous les noyaux lors de la création et de l’équilibrage des tas.

> [!NOTE]
> Cet élément ne s’applique qu’aux fils de collecte des ordures. Pour activer le temps d’exécution pour distribuer des threads d’utilisateurs sur tous les groupes de processeurs, vous devez également activer [ \<l’élément Thread_UseAllCpuGroups>.](thread-useallcpugroups-element.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment permettre la collecte des ordures pour plusieurs groupes de processeurs.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Paramètres de durée d’exécution Schema](index.md)
- [Configuration Fichier Schema](../index.md)
- [Désactiver la collecte simultanée des ordures](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Garbage collection de station de travail et de serveur](../../../../standard/garbage-collection/workstation-server-gc.md)
