---
title: <NetFx40_LegacySecurityPolicy>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5bfa5449ece1b24d4f47fe3e77e36b26bbe430c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689846"
---
# <a name="netfx40legacysecuritypolicy-element"></a>\<NetFx40_LegacySecurityPolicy > élément

Indique si le runtime utilise la stratégie héritée de sécurité d’accès du code (CAS).

\<configuration>\
\<runtime>\
\<NetFx40_LegacySecurityPolicy>

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

|Value|Description|
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

## <a name="remarks"></a>Notes

Dans le .NET Framework version 3.5 et les versions antérieures, la stratégie CAS est toujours en vigueur. Dans le .NET Framework 4, la stratégie CAS doit être activée.

La stratégie CAS est spécifique à la version. Les stratégies CAS personnalisées qui existent dans les versions antérieures du .NET Framework doivent être de nouveau spécifiées dans le .NET Framework 4.

Appliquer le `<NetFx40_LegacySecurityPolicy>` élément à un assembly .NET Framework 4 n’affecte pas [code transparent de sécurité](../../../../../docs/framework/misc/security-transparent-code.md); les règles de transparence s’appliquent toujours.

> [!IMPORTANT]
> Appliquer le `<NetFx40_LegacySecurityPolicy>` élément peut entraîner des altérations des performances significatives pour les assemblys d’images natives créés par le [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) qui ne sont pas installés dans le [GAC ](../../../../../docs/framework/app-domains/gac.md). La dégradation des performances sont dû à l’incapacité du runtime à charger les assemblys en tant qu’images natives lorsque l’attribut est appliqué, ce qui provoque leur chargé les assemblys comme juste-à-temps.

> [!NOTE]
> Si vous spécifiez une version de .NET Framework cible est antérieure à .NET Framework 4 dans les paramètres du projet pour votre projet Visual Studio, stratégie des autorités de certification sera activée, y compris les stratégies autorités de certification personnalisées que vous avez spécifié pour cette version. Toutefois, vous ne serez pas en mesure d’utiliser des membres et les nouveaux types de .NET Framework 4. Vous pouvez également spécifier une version antérieure du .NET Framework à l’aide de la [ \<supportedRuntime > élément](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) dans le schéma de paramètres de démarrage dans votre [fichier de configuration d’application](../../../../../docs/framework/configure-apps/index.md).

> [!NOTE]
> Syntaxe du fichier de configuration respecte la casse. Vous devez utiliser la syntaxe comme indiqué dans les sections syntaxe et exemple.

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé uniquement dans le fichier de configuration d’application.

## <a name="example"></a>Exemple

L’exemple suivant montre comment activer la stratégie CAS héritée d’une application.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
