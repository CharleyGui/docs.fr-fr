---
title: <NetFx40_PInvokeStackResilience>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f4dffe5428ccb7541055fa4f3f335f57deaf2ec
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252428"
---
# <a name="netfx40_pinvokestackresilience-element"></a>\<NetFx40_PInvokeStackResilience >, élément

Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx40_PInvokeStackResilience >**  

## <a name="syntax"></a>Syntaxe

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime détecte des déclarations d’appel de code non managé incorrectes et résout automatiquement la pile au moment de l’exécution sur les plateformes 32 bits.|

## <a name="enabled-attribute"></a>Attribut enabled

|`Value`|Description|
|-----------|-----------------|
|`0`|Le runtime utilise l’architecture de marshaling d’interopérabilité plus rapide introduite dans le .NET Framework 4, qui ne détecte pas et ne corrige pas les déclarations d’appel de code non managé incorrectes. Il s'agit de la valeur par défaut.|
|`1`|Le runtime utilise des transitions plus lentes qui détectent et corrigent les déclarations d’appel de code non managé incorrectes.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|

## <a name="remarks"></a>Notes

Cet élément vous permet d’échanger un marshaling d’interopérabilité plus rapide pour la résilience au moment de l’exécution contre les déclarations d’appel de code non managé incorrectes.

À partir du .NET Framework 4, une architecture de marshaling d’interopérabilité rationalisée offre une amélioration significative des performances des transitions du code managé vers du code non managé. Dans les versions antérieures du .NET Framework, la couche de marshaling a détecté des déclarations d’appel de code non managé incorrectes sur les plateformes 32 bits et a résolu automatiquement la pile. La nouvelle architecture de marshaling élimine cette étape. Par conséquent, les transitions sont très rapides, mais une déclaration d’appel de code non managé incorrecte peut provoquer un échec de programme.

Pour faciliter la détection des déclarations incorrectes pendant le développement, l’expérience de débogage de Visual Studio a été améliorée. L’Assistant Débogage managé (MDA) [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) vous avertit des déclarations d’appel de code non managé incorrectes lorsque votre application s’exécute avec le débogueur attaché.

Pour traiter les scénarios où votre application utilise des composants que vous ne pouvez pas recompiler et qui ont des déclarations d’appel de code `NetFx40_PInvokeStackResilience` non managé incorrectes, vous pouvez utiliser l’élément. L’ajout de cet élément à votre fichier de `enabled="1"` configuration de l’application avec opte dans un mode de compatibilité avec le comportement des versions antérieures du .NET Framework, au détriment des transitions plus lentes. Les assemblys qui ont été compilés sur des versions antérieures du .NET Framework sont automatiquement activés dans ce mode de compatibilité et n’ont pas besoin de cet élément.

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.

## <a name="example"></a>Exemple

L’exemple suivant montre comment opter pour une meilleure résilience par rapport aux déclarations d’appel de code non managé incorrectes pour une application, au détriment de transitions plus lentes entre le code managé et le code non managé.

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
