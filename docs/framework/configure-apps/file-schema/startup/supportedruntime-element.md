---
title: <supportedRuntime>, élément de configuration-.NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: 5e7fc5f81468ff7c4eba8145ee42a4c7cf8bc0b8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697518"
---
# <a name="supportedruntime-element"></a>élément \<supportedRuntime >

Spécifie la version de common language runtime et, éventuellement, la version .NET Framework prise en charge par l’application.  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<supportedRuntime>**  

## <a name="syntax"></a>Syntaxe

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Attributes

|Attribut|Description|
|---------------|-----------------|
|**version**|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la version du Common Language Runtime (CLR) prise en charge par cette application. Pour connaître les valeurs valides de l’attribut `version`, consultez la section valeurs de la [version du runtime](#version) . **Remarque :**  Par le biais du .NET Framework 3,5, la valeur «*version du runtime*» prend la forme *principale*. *mineure*. *générer*. À partir du .NET Framework 4, seuls les numéros de version majeure et mineure sont requis (autrement dit, « v 4.0 » au lieu de « v 4.0.30319 »). La chaîne courte est recommandée.|
|**sku**|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la référence (SKU), qui à son tour spécifie quelle mise en production du .NET Framework cette application prend en charge.<br /><br /> À compter du .NET Framework 4.0, l’utilisation de l’attribut `sku` est recommandée.  Quand il est présent, il indique la version du .NET Framework ciblée par l’application.<br /><br /> Pour connaître les valeurs valides de l’attribut SKU, consultez la section [« Réf SKU »](#sku) .|

## <a name="remarks"></a>Remarques

Si l’élément **\<supportedRuntime >** n’est pas présent dans le fichier de configuration de l’application, la version du runtime utilisée pour générer l’application est utilisée.

L’élément **\<supportedRuntime >** doit être utilisé par toutes les applications générées à l’aide de la version 1,1 ou ultérieure du Runtime. Les applications générées pour prendre en charge uniquement la version 1,0 du Runtime doivent utiliser l’élément [\<requiredRuntime >](../startup/requiredruntime-element.md) .

> [!NOTE]
> Si vous utilisez la fonction [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) pour spécifier le fichier de configuration, vous devez utiliser l’élément `<requiredRuntime>` pour toutes les versions du Runtime. L’élément `<supportedRuntime>` est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Pour les applications prenant en charge les versions du runtime du .NET Framework 1.1 à 3.5, quand plusieurs versions du runtime sont prises en charge, le premier élément doit spécifier la version du runtime préférée en premier tandis que le dernier élément doit spécifier la version préférée en dernier. Pour les applications qui prennent en charge le .NET Framework 4,0 ou versions ultérieures, l’attribut `version` indique la version CLR, qui est commune à la .NET Framework 4 et versions ultérieures, et l’attribut `sku` indique la version .NET Framework unique ciblée par l’application. 

Si l’élément **\<supportedRuntime >** avec l’attribut `sku` est présent dans le fichier de configuration et que la version .NET Framework installée est inférieure à la version spécifiée, l’application ne s’exécute pas et affiche à la place un message vous demandant d’installer la version prise en charge. Dans le cas contraire, l’application tente de s’exécuter sur n’importe quelle version installée, mais elle peut se comporter de façon inattendue si elle n’est pas entièrement compatible avec cette version. (Pour connaître les différences de compatibilité entre les versions de .NET Framework, consultez [compatibilité des applications dans le .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Par conséquent, nous vous recommandons d’inclure cet élément dans le fichier de configuration de l’application pour faciliter les diagnostics d’erreur. (Le fichier de configuration généré automatiquement par Visual Studio lors de la création d’un projet le contient déjà.)
  
> [!NOTE]
> Si votre application utilise des chemins d’activation hérités, tels que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), et que vous souhaitez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est générée avec l' .NET Framework 4, mais qu’elle dépende d’un assembly en mode mixte créé avec une version antérieure du .NET Framework, il n’est pas suffisant de spécifier le .NET Framework 4 dans De plus, dans le [\<> élément de démarrage](../startup/startup-element.md) de votre fichier de configuration, vous devez définir l’attribut `useLegacyV2RuntimeActivationPolicy` sur `true`. Toutefois, l’affectation de la valeur `true` à cet attribut signifie que tous les composants générés avec des versions antérieures du .NET Framework sont exécutés à l’aide du .NET Framework 4 au lieu des runtimes avec lesquels ils ont été générés.

Nous vous recommandons de tester les applications avec toutes les versions du .NET Framework sur lesquelles elles peuvent s'exécuter.

<a name="version"></a> 
## <a name="runtime-version-values"></a>valeurs de "runtime version"
L’attribut `runtime` spécifie la version du Common Language Runtime (CLR) qui est requise pour une application donnée. Notez que toutes les versions .NET Framework v4. x spécifient le CLR `v4.0`. Le tableau suivant répertorie les valeurs valides pour la valeur de *version du runtime* de l’attribut `version`.

|Version du .NET Framework|attribut `version`|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2,0|"v2.0.50727"|
|3,0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku"></a>valeurs « SKU ID »

L’attribut `sku` utilise un moniker de Framework cible (TFM) pour indiquer la version de l' .NET Framework que l’application cible et requiert l’exécution. Le tableau suivant répertorie les valeurs valides prises en charge par l’attribut `sku`, à partir de la .NET Framework 4.

|Version du .NET Framework|attribut `sku`|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4.0, Client Profile|".NETFramework,Version=v4.0,Profile=Client"|
|4.0, Platform Update 1|". NETFramework, version = v 4.0.1 "|
|4.0, Client Profile, Update 1|". NETFramework, version = v 4.0.1, Profile = client "|
|4.0, Platform Update 2|". NETFramework, version = v 4.0.2»|
|4.0, Client Profile, Update 2|". NETFramework, version = v 4.0.2, Profile = client "|
|4.0, Platform Update 3|". NETFramework, version = v 4.0.3»|
|4.0, Client Profile, Update 3|". NETFramework, version = v 4.0.3, Profile = client»|
|4,5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|". NETFramework, version = v 4.6.2|
|4.7|". NETFramework, version = v 4.7 "|
|4.7.1|". NETFramework, version = v 4.7.1 "|
|4.7.2|". NETFramework, version = v 4.7.2 "|
|4.8|". NETFramework, version = v 4.8|

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier la version du runtime prise en charge dans un fichier de configuration. Le fichier de configuration indique que l’application cible le .NET Framework 4,7.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l'application.

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres de démarrage](../startup/index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Exécution côte à côte in-process](../../../deployment/in-process-side-by-side-execution.md)
