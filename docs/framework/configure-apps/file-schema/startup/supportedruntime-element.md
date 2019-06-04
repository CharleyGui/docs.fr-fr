---
title: <supportedRuntime> élément de configuration - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: 90bdd5b8c5fdebe2c5d7ec580975dc63144b2401
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489299"
---
# <a name="supportedruntime-element"></a>\<supportedRuntime > élément

Spécifie quelle version du common language runtime et, éventuellement, la version de .NET Framework l’application prend en charge.  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](../startup/startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<supportedRuntime>**  

## <a name="syntax"></a>Syntaxe

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|**version**|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la version du Common Language Runtime (CLR) prise en charge par cette application. Pour les valeurs valides de la `version` d’attribut, consultez le [les valeurs de « version du runtime »](#version) section. **Remarque :**  Via le .NET Framework 3.5, le «*version du runtime*» valeur prend la forme *majeure*. *mineure*. *build*. Commençant par le .NET Framework 4, seuls les numéros de version majeure et mineure sont nécessaires (c'est-à-dire « v4.0 » au lieu de « v4.0.30319 »). La chaîne courte est recommandée.|
|**sku**|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la référence (SKU), qui à son tour spécifie quelle mise en production du .NET Framework cette application prend en charge.<br /><br /> À compter du .NET Framework 4.0, l’utilisation de l’attribut `sku` est recommandée.  Quand il est présent, il indique la version du .NET Framework ciblée par l’application.<br /><br /> Pour obtenir des valeurs valides de l’attribut de référence (SKU), consultez le [les valeurs « id de référence (SKU) »](#sku) section.|

## <a name="remarks"></a>Notes

Si le  **\<supportedRuntime >** élément n’est pas présent dans le fichier de configuration d’application, la version du runtime utilisée pour générer l’application est utilisée.

Le  **\<supportedRuntime >** élément doit être utilisé par toutes les applications générées à l’aide de la version 1.1 ou ultérieure du runtime. Les applications générées pour prendre en charge uniquement la version 1.0 du runtime doivent utiliser le [ \<requiredRuntime >](../startup/requiredruntime-element.md) élément.

> [!NOTE]
> Si vous utilisez le [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) de fonction pour spécifier le fichier de configuration, vous devez utiliser le `<requiredRuntime>` élément pour toutes les versions du runtime. Le `<supportedRuntime>` élément est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Pour les applications prenant en charge les versions du runtime du .NET Framework 1.1 à 3.5, quand plusieurs versions du runtime sont prises en charge, le premier élément doit spécifier la version du runtime préférée en premier tandis que le dernier élément doit spécifier la version préférée en dernier. Pour les applications qui prennent en charge le .NET Framework 4.0 ou versions ultérieures, le `version` attribut indique la version du CLR, ce qui est courant pour le .NET Framework 4 et versions ultérieures, et le `sku` attribut indique la version du .NET Framework qui le application cible. 

Si le  **\<supportedRuntime >** élément avec la `sku` attribut est présent dans le fichier de configuration et la version de .NET Framework installée est inférieure, puis la version prise en charge spécifiée, l’application ne parvient pas à exécuter et à la place affiche un message vous demandant d’installer la version prise en charge. Sinon, l’application tente de s’exécuter sur n’importe quelle version installée, mais il peut se comportent de façon inattendue si elle n’est pas entièrement compatible avec cette version. (Pour les différences de compatibilité entre les versions du .NET Framework, consultez [compatibilité des applications dans le .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Par conséquent, nous vous conseillons d’inclure cet élément dans le fichier de configuration d’application pour les diagnostics d’erreur plus facile. (Le fichier de configuration généré automatiquement par Visual Studio lorsque vous créez un nouveau projet déjà contient.)
  
> [!NOTE]
> Si votre application utilise des chemins d’accès d’activation héritée, tel que le [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), et vous souhaitez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est générée avec le .NET Framework 4 mais a une dépendance sur un assembly en mode mixte généré avec une version antérieure du .NET Framework, il n’est pas suffisant spécifier le .NET Framework 4 dans la liste des runtimes pris en charge. En outre, dans le [ \<démarrage > élément](../startup/startup-element.md) dans votre fichier de configuration, vous devez définir le `useLegacyV2RuntimeActivationPolicy` attribut `true`. Toutefois, si cet attribut `true` signifie que tous les composants générés avec les versions antérieures du .NET Framework sont exécutés à l’aide de .NET Framework 4 au lieu des runtimes, ils ont été générés.

Nous vous recommandons de tester les applications avec toutes les versions du .NET Framework sur lesquelles elles peuvent s'exécuter.

<a name="version"></a> 
## <a name="runtime-version-values"></a>valeurs de "runtime version"
Le `runtime` attribut spécifie la version du Common Language Runtime (CLR) qui est requise pour une application donnée. Notez que toutes les versions de .NET Framework 4.x spécifient le `v4.0` CLR. Le tableau suivant répertorie les valeurs valides pour le *version du runtime* valeur de la `version` attribut.

|Version du .NET Framework|`version` Attribut|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku"></a> valeurs « id de référence (SKU) »

Le `sku` attribut utilise un moniker du framework cible (TFM) pour indiquer la version du .NET Framework que l’application cible et nécessaires à l’exécution. Le tableau suivant répertorie les valeurs valides sont pris en charge par le `sku` attribut, en commençant par le .NET Framework 4.

|Version du .NET Framework|`sku` Attribut|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4.0, Client Profile|".NETFramework,Version=v4.0,Profile=Client"|
|4.0, Platform Update 1|".NETFramework,Version=v4.0.1"|
|4.0, Client Profile, Update 1|". NETFramework, Version = v4.0.1, profil = Client »|
|4.0, Platform Update 2|".NETFramework,Version=v4.0.2"|
|4.0, Client Profile, Update 2|". NETFramework, Version = version 4.0.2, profil = Client »|
|4.0, Platform Update 3|".NETFramework,Version=v4.0.3"|
|4.0, Client Profile, Update 3|". NETFramework, Version = verze 4.0.3, profil = Client »|
|4.5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|". NETFramework, Version = v4.6.2 »|
|4.7|". NETFramework, Version = v4.7 »|
|4.7.1|". NETFramework, Version = v4.7.1 »|
|4.7.2|". NETFramework, Version = v4.7.2 »|
|4.8|".NETFramework,Version=v4.8"|

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier la version du runtime prise en charge dans un fichier de configuration. Le fichier de configuration indique que l’application cible le .NET Framework 4.7.

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
