---
title: <NetFx40_LegacySecurityPolicy>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: d5192eb56bb8b640544bdc52a0bb9d8a5277efef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116250"
---
# <a name="netfx40_legacysecuritypolicy-element"></a>Élément \<NetFx40_LegacySecurityPolicy>

Indique si le runtime utilise la stratégie héritée de sécurité d’accès du code (CAS).

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

## <a name="syntax"></a>Syntaxe

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime utilise la stratégie CAS héritée.|

## <a name="enabled-attribute"></a>Attribut enabled

|Valeur|Description|
|-----------|-----------------|
|`false`|Le runtime n’utilise pas la stratégie CAS héritée. Il s'agit de la valeur par défaut.|
|`true`|Le runtime utilise la stratégie CAS héritée.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|

## <a name="remarks"></a>Remarques

Dans le .NET Framework version 3,5 et les versions antérieures, la stratégie CAS est toujours activée. Dans la .NET Framework 4, la stratégie CAS doit être activée.

La stratégie CAS est spécifique à la version. Les stratégies CAS personnalisées qui existent dans les versions antérieures du .NET Framework doivent être spécifiées à l' .NET Framework 4.

L’application `<NetFx40_LegacySecurityPolicy>` de l’élément à un assembly .NET Framework 4 n’affecte pas le [code transparent de sécurité](../../../misc/security-transparent-code.md); les règles de transparence s’appliquent toujours.

> [!IMPORTANT]
> L’application de l' `<NetFx40_LegacySecurityPolicy>` élément peut entraîner des pénalités de performances significatives pour les assemblys d’images natives créés par le [Générateur d’images natives (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) qui ne sont pas installés dans le [global assembly cache](../../../app-domains/gac.md). La dégradation des performances est provoquée par l’incapacité du runtime à charger les assemblys en tant qu’images natives lorsque l’attribut est appliqué, ce qui entraîne leur chargement en tant qu’assemblys juste-à-temps.

> [!NOTE]
> Si vous spécifiez une version de .NET Framework cible antérieure à la .NET Framework 4 dans les paramètres de projet de votre projet Visual Studio, la stratégie CAS est activée, y compris les stratégies CAS personnalisées que vous avez spécifiées pour cette version. Toutefois, vous ne pourrez pas utiliser les nouveaux types et membres de .NET Framework 4. Vous pouvez également spécifier une version antérieure du .NET Framework à l’aide de l' [ \<supportedRuntime> élément](../startup/supportedruntime-element.md) dans le schéma des paramètres de démarrage de votre [fichier de configuration](../../index.md)de l’application.

> [!NOTE]
> La syntaxe du fichier de configuration respecte la casse. Vous devez utiliser la syntaxe fournie dans les sections syntaxe et example.

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.

## <a name="example"></a>Exemple

L’exemple suivant montre comment activer la stratégie CAS héritée pour une application.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
