---
title: Élément GCLOHThreshold
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451219"
---
# <a name="gclohthreshold-element"></a>Élément GCLOHThreshold

Spécifie la taille du seuil, en octets, qui amène le garbage collector à placer des objets sur le tas d’objets volumineux (LOH).

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a>Syntaxe

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br />Spécifie la taille du seuil qui amène les objets sur le tas des objets volumineux.|

### <a name="enabled-attribute"></a>attribut activé

|Valeur|Description|
|-----------|-----------------|
|`nnnn`|Taille du seuil, en octets, qui provoque l’accès des objets sur le tas d’objets volumineux.|

## <a name="child-elements"></a>Éléments enfants

Aucun.

## <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Remarques

Ce paramètre a été introduit dans .NET Framework 4,8.

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
- [Notions de base de garbage collection](../../../../standard/garbage-collection/fundamentals.md)
- [Options de configuration du runtime NET Core pour GC](../../../../core/run-time-config/garbage-collector.md)
