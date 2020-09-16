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
ms.openlocfilehash: cd91abb288c1cfb281f17f2fce95d4956908468f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550844"
---
# <a name="startup-element"></a>\<startup>, élément

Spécifie common language runtime informations de démarrage.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

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
|`useLegacyV2RuntimeActivationPolicy`|Attribut facultatif.<br /><br /> Spécifie s’il faut activer la stratégie d’activation du Runtime .NET Framework 2,0 ou utiliser la stratégie d’activation .NET Framework 4.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy (attribut)

|Value|Description|
|-----------|-----------------|
|`true`|Activez .NET Framework stratégie d’activation du runtime 2,0 pour le runtime choisi, qui consiste à lier les techniques héritées d’activation du Runtime (telles que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) au runtime choisi à partir du fichier de configuration au lieu de les découper au niveau du CLR version 2,0. Par conséquent, si CLR version 4 ou ultérieure est choisi dans le fichier de configuration, les assemblys en mode mixte créés avec des versions antérieures du .NET Framework sont chargés avec la version CLR choisie. La définition de cette valeur empêche le chargement du CLR version 1,1 ou CLR version 2,0 dans le même processus, ce qui a pour effet de désactiver la fonctionnalité côte à côte in-process.|
|`false`|Utilisez la stratégie d’activation par défaut pour le .NET Framework 4 et versions ultérieures, ce qui permet d’autoriser les techniques d’activation du runtime héritées à charger CLR version 1,1 ou 2,0 dans le processus. La définition de cette valeur empêche le chargement des assemblys en mode mixte dans le .NET Framework 4 ou ultérieur, sauf s’ils ont été générés avec le .NET Framework 4 ou version ultérieure. Il s’agit de la valeur par défaut.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime. Les applications générées avec la version 1,1 ou ultérieure du Runtime doivent utiliser l' **\<supportedRuntime>** élément.|
|[\<supportedRuntime>](supportedruntime-element.md)|Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|

## <a name="remarks"></a>Notes

 L' **\<supportedRuntime>** élément doit être utilisé par toutes les applications générées à l’aide de la version 1,1 ou ultérieure du Runtime. Les applications générées pour prendre en charge uniquement la version 1,0 du Runtime doivent utiliser l' **\<requiredRuntime>** élément.

 Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore l' **\<startup>** élément et ses éléments enfants.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Attribut useLegacyV2RuntimeActivationPolicy

 Cet attribut est utile si votre application utilise des chemins d’activation hérités, tels que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), et si vous souhaitez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est générée avec l' .NET Framework 4, mais qu’elle a une dépendance sur un assembly en mode mixte créé avec une version antérieure du .NET Framework. Dans ces scénarios, affectez à l’attribut la valeur `true` .

> [!NOTE]
> L’affectation de la valeur à l’attribut `true` empêche le chargement du CLR version 1,1 ou CLR version 2,0 dans le même processus, ce qui a pour effet de désactiver la fonctionnalité côte à côte in-process (voir [exécution côte à côte pour COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

## <a name="example"></a> Exemple

 L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.

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

- [Schéma des paramètres de démarrage](index.md)
- [Schéma du fichier de configuration](../index.md)
- [Comment : configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Exécution côte à côte pour COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Exécution côte à côte in-process](../../../deployment/in-process-side-by-side-execution.md)
