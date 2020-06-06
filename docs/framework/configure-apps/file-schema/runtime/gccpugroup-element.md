---
title: Élément <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102890"
---
# <a name="gccpugroup-element"></a>Élément \<GCCpuGroup>

Indique si le garbage collection prend en charge plusieurs groupes de processeurs.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
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
|`false`|Le garbage collection ne prend pas en charge plusieurs groupes d’UC. Il s'agit de la valeur par défaut.|
|`true`|Le garbage collection prend en charge plusieurs groupes de PROCESSEURs, si le serveur garbage collection est activé.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Remarques

Quand un ordinateur a plusieurs groupes d’UC et que la garbage collection du serveur est activée (Voir l' [\<gcServer>](gcserver-element.md) élément), l’activation de cet élément étend garbage collection sur tous les groupes de processeurs et prend en compte tous les cœurs lors de la création et de l’équilibrage des tas.

> [!NOTE]
> Cet élément s’applique uniquement aux threads garbage collections. Pour permettre au runtime de distribuer des threads utilisateur sur tous les groupes de PROCESSEURs, vous devez également activer l' [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) élément.

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
- [Désactiver les garbage collection simultanées](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Garbage collection de station de travail et de serveur](../../../../standard/garbage-collection/workstation-server-gc.md)
