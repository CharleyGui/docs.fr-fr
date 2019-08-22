---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 197ab9dbc1ec85bf8961f60bb26496eab788e63f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663698"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup >, élément

Indique si le garbage collection prend en charge plusieurs groupes de processeurs.

\<configuration>\
\<> du runtime \
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

|Valeur|Description|
|-----------|-----------------|
|`false`|Le garbage collection ne prend pas en charge plusieurs groupes d’UC. Il s'agit de la valeur par défaut.|
|`true`|Le garbage collection prend en charge plusieurs groupes de PROCESSEURs, si le serveur garbage collection est activé.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Notes

Quand un ordinateur a plusieurs groupes d’UC et que la garbage collection du serveur est activée (Voir l' [ \<élément gcServer >](gcserver-element.md) ), l’activation de cet élément étend garbage collection sur tous les groupes de processeurs et prend en compte tous les cœurs lors de la création et équilibrage des tas.

> [!NOTE]
> Cet élément s’applique uniquement aux threads garbage collections. Pour permettre au runtime de distribuer des threads utilisateur sur tous les groupes de processeurs, vous devez également activer l' [ \<élément Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) .

## <a name="example"></a>Exemple

L’exemple suivant montre comment activer garbage collection pour plusieurs groupes d’UC.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Pour désactiver les garbage collection simultanées](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Garbage collection de station de travail et de serveur](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
