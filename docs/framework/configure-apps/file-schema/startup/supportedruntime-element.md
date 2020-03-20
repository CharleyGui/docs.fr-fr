---
title: <supportedRuntime>élément de configuration - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: e16eb098db4bce115a5f1e043829eb272c952860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153696"
---
# <a name="supportedruntime-element"></a>\<supportRuntime> élément

Précise quelle version courante de l’heure d’exécution de langue et, optionnellement, version cadre .NET l’application prend en charge.  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<>de démarrage](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportRuntime>**  

## <a name="syntax"></a>Syntaxe

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|**version**|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la version du Common Language Runtime (CLR) prise en charge par cette application. Pour les valeurs `version` valides de l’attribut, consultez la section [des valeurs « version runtime](#version) ». **Note:**  Grâce au cadre .NET 3.5, la valeur "*version runtime*" prend la forme *majeure.* *mineur*. *construire*. À partir du cadre .NET 4, seuls les numéros de version majeur et mineur sont requis (c’est-à-dire " v4.0 " au lieu de " v4.0.30319 "). La chaîne courte est recommandée.|
|**Sku**|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la référence (SKU), qui à son tour spécifie quelle mise en production du .NET Framework cette application prend en charge.<br /><br /> À compter du .NET Framework 4.0, l’utilisation de l’attribut `sku` est recommandée.  Quand il est présent, il indique la version du .NET Framework ciblée par l’application.<br /><br /> Pour les valeurs valides de l’attribut sku, voir la section [des valeurs "sku id".](#sku)|

## <a name="remarks"></a>Notes 

Si ** \<** l’élément de>de prise en charge n’est pas présent dans le fichier de configuration d’application, la version du temps d’exécution utilisé pour construire l’application est utilisée.

** \<L’élément de>Deruntime pris en charge** doit être utilisé par toutes les applications construites à l’aide de la version 1.1 ou plus tard de l’exécution. Les applications conçues pour prendre en charge uniquement la version 1.0 du temps d’exécution doivent utiliser [ \<l’élément>runtime requis.](../startup/requiredruntime-element.md)

> [!NOTE]
> Si vous utilisez la fonction [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) pour spécifier le fichier de configuration, vous devez utiliser l’élément `<requiredRuntime>` pour toutes les versions du temps d’exécution. L’élément `<supportedRuntime>` est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Pour les applications prenant en charge les versions du runtime du .NET Framework 1.1 à 3.5, quand plusieurs versions du runtime sont prises en charge, le premier élément doit spécifier la version du runtime préférée en premier tandis que le dernier élément doit spécifier la version préférée en dernier. Pour les applications qui prennent en charge le cadre .NET 4.0 ou les versions ultérieures, l’attribut `version` indique `sku` la version CLR, qui est commune au cadre .NET 4 et versions ultérieures, et l’attribut indique la version cadre unique .NET que l’application cible.

Si ** \<l’élément de>supporté** avec l’attribut `sku` est présent dans le fichier de configuration et que la version cadre .NET installée est inférieure, puis la version prise en charge spécifiée, l’application ne s’exécute pas et affiche plutôt un message demandant d’installer la version prise en charge. Dans le cas contraire, l’application tente de s’exécuter sur n’importe quelle version installée, mais elle peut se comporter de façon inattendue si elle n’est pas entièrement compatible avec cette version. (Pour les différences de compatibilité entre les versions de .NET Framework, voir [Compatibilité d’application dans le cadre .NET](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Par conséquent, nous vous recommandons d’inclure cet élément dans le fichier de configuration d’application pour des diagnostics d’erreur plus faciles. (Le fichier de configuration généré automatiquement par Visual Studio lors de la création d’un nouveau projet le contient déjà.)
  
> [!NOTE]
> Si votre application utilise des voies d’activation héritées, telles que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), et que vous voulez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est construite avec le cadre .NET 4 mais a une dépendance sur un assemblage en mode mixte construit avec une version antérieure du cadre .NET, il ne suffit pas de spécifier le cadre .NET 4 dans la liste des runtimes pris en charge. En outre, [ \<](../startup/startup-element.md) dans le démarrage> élément dans votre `useLegacyV2RuntimeActivationPolicy` fichier `true`de configuration, vous devez définir l’attribut à . Cependant, la fixation `true` de cet attribut signifie que tous les composants construits avec des versions antérieures du cadre .NET sont exécutés en utilisant le cadre .NET 4 au lieu des temps d’exécution avec lequel ils ont été construits.

Nous vous recommandons de tester les applications avec toutes les versions du .NET Framework sur lesquelles elles peuvent s'exécuter.

<a name="version"></a>
## <a name="runtime-version-values"></a>valeurs de "runtime version"
L’attribut `runtime` spécifie la version Common Language Runtime (CLR) qui est requise pour une application donnée. Notez que toutes les versions .NET `v4.0` Framework v4.x spécifier le CLR. Le tableau suivant énumère les valeurs valides `version` pour la valeur de la version en temps *d’exécution* de l’attribut.

|Version du .NET Framework|Attribut `version`|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3,5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku-id-values"></a><a name="sku"></a>valeurs "sku id"

L’attribut `sku` utilise un nom-cadre cible (TFM) pour indiquer la version du cadre .NET que l’application cible et nécessite pour exécuter. Le tableau suivant énumère les valeurs `sku` valides qui sont étayées par l’attribut, à commencer par le cadre .NET 4.

|Version du .NET Framework|Attribut `sku`|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4.0, Client Profile|".NETFramework,Version=v4.0,Profile=Client"|
|4.0, Platform Update 1|". NETFramework,Version-v4.0.1"|
|4.0, Client Profile, Update 1|". NETFramework,Version-v4.0.1,Profile-Client"|
|4.0, Platform Update 2|". NETFramework,Version v4.0.2"|
|4.0, Client Profile, Update 2|". NETFramework,Version-v4.0.2,Profile-Client"|
|4.0, Platform Update 3|". NETFramework,Version v4.0.3"|
|4.0, Client Profile, Update 3|". NETFramework,Version-v4.0.3,Profile-Client"|
|4.5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|". NETFramework,Version v4.6.2"|
|4,7|". NETFramework,Version v4.7"|
|4.7.1|". NETFramework,Version v4.7.1"|
|4.7.2|". NETFramework,Version v4.7.2"|
|4.8|". NETFramework,Version v4.8"|

## <a name="example"></a> Exemple

L’exemple suivant montre comment spécifier la version du runtime prise en charge dans un fichier de configuration. Le fichier de configuration indique que l’application cible le cadre .NET 4.7.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l'application.

## <a name="see-also"></a>Voir aussi

- [Paramètres de démarrage Schema](../startup/index.md)
- [Configuration Fichier Schema](../index.md)
- [Exécution côte à côte in-process](../../../deployment/in-process-side-by-side-execution.md)
