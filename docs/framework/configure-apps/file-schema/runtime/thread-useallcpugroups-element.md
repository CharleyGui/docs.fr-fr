---
title: <Thread_UseAllCpuGroups>, élément
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115411"
---
# <a name="thread_useallcpugroups-element"></a>\<élément Thread_UseAllCpuGroups >

Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups** >  

## <a name="syntax"></a>Syntaxe

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br /> Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.|

## <a name="enabled-attribute"></a>Attribut enabled

|valeur|Description|
|-----------|-----------------|
|`false`|Le runtime ne distribue pas les threads managés sur plusieurs groupes d’UC. Il s'agit de la valeur par défaut.|
|`true`|Le runtime distribue des threads managés sur plusieurs groupes de PROCESSEURs, si l’ordinateur a plusieurs groupes de PROCESSEURs et que l’élément [\<GCCpuGroup >](gccpugroup-element.md) est activé.|

### <a name="child-elements"></a>Éléments enfants

Aucun(e).

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Notes

Lorsqu’un ordinateur possède plusieurs groupes d’UC, l’activation de cet élément amène le runtime à distribuer des threads managés sur tous les groupes de PROCESSEURs. Pour utiliser cette fonctionnalité, vous devez également activer l’élément [\<GCCpuGroup >](gccpugroup-element.md) , qui étend garbage collection à tous les groupes de processeurs et prend en compte tous les cœurs lors de la création et de l’équilibrage des tas. L’activation de l’élément [\<GCCpuGroup >](gccpugroup-element.md) requiert l’activation de l’élément [\<gcServer](gcserver-element.md) . Si ces éléments ne sont pas activés, l’activation de l’élément `<Thread_UseAllCpuGroups>` n’a aucun effet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment activer la prise en charge de plusieurs groupes d’UC.

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [\<élément GCCpuGroup >](gccpugroup-element.md)
