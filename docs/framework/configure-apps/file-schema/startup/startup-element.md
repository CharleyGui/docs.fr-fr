---
title: <startup> (élément)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153727"
---
# <a name="startup-element"></a>\<> élément de démarrage

Spécifie les informations de démarrage en temps courant.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<>de démarrage**  

## <a name="syntax"></a>Syntaxe

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|Attribut facultatif.<br /><br /> Précise s’il faut activer la politique d’activation du temps d’exécution .NET Framework 2.0 ou utiliser la politique d’activation .NET Framework 4.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>utiliser l’attributLegacyV2RuntimeActivationPolicy

|Valeur|Description|
|-----------|-----------------|
|`true`|Activez la politique d’activation de temps d’exécution .NET Framework 2.0 pour le temps d’exécution choisi, qui consiste à lier les techniques d’activation du temps d’exécution de l’héritage (comme la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) au temps d’exécution choisi à partir du fichier de configuration au lieu de les plafonner à la version CLR 2.0. Ainsi, si la version CLR 4 ou plus tard est choisie à partir du fichier de configuration, les assemblages en mode mixte créés avec des versions antérieures du cadre .NET sont chargés de la version CLR choisie. La définition de cette valeur empêche la version CLR 1.1 ou la version CLR 2.0 de se charger dans le même processus, désactivant efficacement la fonction en cours côte à côte.|
|`false`|Utilisez la stratégie d’activation par défaut pour le cadre .NET 4 et plus tard, qui est de permettre aux techniques d’activation de temps d’exécution hérités pour charger la version CLR 1.1 ou 2.0 dans le processus. La définition de cette valeur empêche les assemblages en mode mixte de se charger dans le cadre .NET 4 ou plus tard, à moins qu’ils ne soient construits avec le cadre .NET 4 ou plus tard. Cette valeur est la valeur par défaut.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[\<requisRuntime>](requiredruntime-element.md)|Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime. Les applications construites avec la version 1.1 ou plus tard doivent utiliser l’élément ** \<>SupportRuntime.**|
|[\<supportRuntime>](supportedruntime-element.md)|Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|

## <a name="remarks"></a>Notes 

 ** \<L’élément de>Deruntime pris en charge** doit être utilisé par toutes les applications construites à l’aide de la version 1.1 ou plus tard de l’exécution. Les applications conçues pour prendre en charge uniquement la version 1.0 du temps d’exécution doivent utiliser ** \<l’élément>runtime requis.**

 Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore la ** \<startup>** élément et ses éléments pour enfants.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>L’attribut useLegacyV2RuntimeActivationPolicy

 Cet attribut est utile si votre application utilise des trajectoires d’activation héritées, telles que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), et que vous voulez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est construite avec le cadre .NET 4, mais a une dépendance sur un assemblage en mode mixte construit avec une version antérieure du cadre .NET. Dans ces scénarios, définissez `true`l’attribut à .

> [!NOTE]
> Définir l’attribut pour `true` empêcher la version CLR 1.1 ou CLR version 2.0 de charger dans le même processus, désactiver efficacement la fonction en cours côte à côte (voir Exécution côte à côte pour COM [Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

## <a name="example"></a> Exemple

 L’exemple suivant montre comment spécifier la version de l’exécution dans un fichier de configuration.

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Paramètres de démarrage Schema](index.md)
- [Configuration Fichier Schema](../index.md)
- [Comment configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Exécution côte à côte pour COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Exécution côte à côte in-process](../../../deployment/in-process-side-by-side-execution.md)
