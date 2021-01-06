---
title: Modèle d’options dans .NET
author: IEvangelist
description: Découvrez comment utiliser le modèle d’options pour représenter des groupes de paramètres associés dans les applications .NET.
ms.author: dapine
ms.date: 12/04/2020
ms.openlocfilehash: 14a81608c41f63abfc562e1a845ca893ff7cdf25
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764919"
---
# <a name="options-pattern-in-net"></a>Modèle d’options dans .NET

Le modèle d’options utilise des classes pour fournir un accès fortement typé aux groupes de paramètres associés. Quand les [paramètres de configuration](configuration.md) sont isolés par scénario dans des classes distinctes, l’application est conforme à deux principes d’ingénierie logicielle importants :

- Le [principe de séparation d’interface (ISP) ou l’encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): les scénarios (classes) qui dépendent des paramètres de configuration dépendent uniquement des paramètres de configuration qu’ils utilisent.
- [Séparation des préoccupations](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns) : les paramètres des différentes parties de l’application ne sont pas dépendants ou associés les uns aux autres.

Ces options fournissent également un mécanisme de validation des données de configuration. Pour plus d'informations, reportez-vous à la section [Validation des options](#options-validation).

## <a name="bind-hierarchical-configuration"></a>Liaison de la configuration hiérarchique

La méthode recommandée pour lire les valeurs de configuration associées utilise le modèle d’options. Par exemple, pour lire les valeurs de configuration suivantes :

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

Créez la `TransientFaultHandlingOptions` classe suivante :

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-6":::

Une classe d’options :

* Doit être non abstract avec un constructeur sans paramètre public
* Contenir des propriétés publiques en lecture/écriture à lier (les champs **sont * liés**)

Le code suivant :

_ Appelle [ConfigurationBinder. bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) pour lier la `TransientFaultHandlingOptions` classe à la `"TransientFaultHandlingOptions"` section.
* Affiche les données de configuration.

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont lues.

[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) lie et retourne le type spécifié. `ConfigurationBinder.Get<T>` peut être plus pratique que l’utilisation de `ConfigurationBinder.Bind` . Le code suivant montre comment utiliser `ConfigurationBinder.Get<T>` avec la `TransientFaultHandlingOptions` classe :

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
        .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont lues.

Une autre approche de l’utilisation du modèle options consiste à lier la `"TransientFaultHandlingOptions"` section et à l’ajouter au [conteneur du service d’injection de dépendances](dependency-injection.md). Dans le code suivant, `TransientFaultHandlingOptions` est ajouté au conteneur de services avec <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> et lié à la configuration :

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> Le `key` paramètre est le nom de la section de configuration à rechercher. Il ne doit *pas* nécessairement correspondre au nom du type qui le représente. Par exemple, vous pouvez avoir une section nommée `"FaultHandling"` et elle peut être représentée par la `TransientFaultHandlingOptions` classe. Dans ce cas, vous devez passer `"FaultHandling"` à la <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> fonction à la place. L' `nameof` opérateur est utilisé à des fins pratiques lorsque la section nommée correspond au type auquel elle correspond.

À l’aide du code précédent, le code suivant lit les options de position :

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont ***non** _ Read. Pour lire les modifications une fois l’application démarrée, utilisez [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).

## <a name="options-interfaces"></a>Interfaces d’options

<xref:Microsoft.Extensions.Options.IOptions%601>:

- Ne prend _*_pas_*_ en charge :
  - Lecture des données de configuration après le démarrage de l’application.
  - [Options nommées](#named-options-support-using-iconfigurenamedoptions)
- Est inscrit en tant que [Singleton](dependency-injection.md#singleton) et peut être injecté dans n’importe quelle [durée de vie de service](dependency-injection.md#service-lifetimes).

<xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:

- Est utile dans les scénarios où les options doivent être recalculées à chaque résolution d’injection, dans des [durées de vie délimitées ou transitoires](dependency-injection.md#service-lifetimes). Pour plus d’informations, consultez [utiliser IOptionsSnapshot pour lire des données mises à jour](#use-ioptionssnapshot-to-read-updated-data).
- Est inscrit en tant qu' [étendue](dependency-injection.md#scoped) et ne peut donc pas être injecté dans un service Singleton.
- Prend en charge les [options nommées](#named-options-support-using-iconfigurenamedoptions)

<xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:

- Est utilisé pour récupérer des options et gérer les notifications d’options pour les `TOptions` instances.
- Est inscrit en tant que [Singleton](dependency-injection.md#singleton) et peut être injecté dans n’importe quelle [durée de vie de service](dependency-injection.md#service-lifetimes).
- Prend en charge :
  - Notifications de modifications
  - [Options nommées](#named-options-support-using-iconfigurenamedoptions)
  - [Configuration rechargeable](#use-ioptionssnapshot-to-read-updated-data)
  - Invalidation sélective des options (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)
  
<xref:Microsoft.Extensions.Options.IOptionsFactory%601> est chargée de créer les instances d’options. Elle dispose d’une seule méthode <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A>. L’implémentation par défaut prend toutes les <xref:Microsoft.Extensions.Options.IConfigureOptions%601> et <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> inscrites et exécute toutes les configurations, puis les post-configurations. Elle fait la distinction entre <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> et <xref:Microsoft.Extensions.Options.IConfigureOptions%601> et n’appelle que l’interface appropriée.

<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> est utilisée par <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> pour mettre en cache les instances `TOptions`. <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalide les instances des options dans le moniteur afin que la valeur soit recalculée (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>). Les valeurs peuvent aussi être introduites manuellement avec <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>. La méthode <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> est utilisée quand toutes les instances nommées doivent être recréées à la demande.

## <a name="use-ioptionssnapshot-to-read-updated-data"></a>Utiliser IOptionsSnapshot pour lire les données mises à jour

Lorsque vous utilisez <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> , les options sont calculées une fois par demande lorsque vous y accédez et sont mises en cache pour la durée de vie de la demande. Les modifications apportées à la configuration sont lues après le démarrage de l’application lors de l’utilisation de fournisseurs de configuration qui prennent en charge la lecture des valeurs de configuration mises

La différence entre `IOptionsMonitor` et `IOptionsSnapshot` est que :

- `IOptionsMonitor` est un [service Singleton](dependency-injection.md#singleton) qui récupère les valeurs d’option actuelles à tout moment, ce qui est particulièrement utile dans les dépendances Singleton.
- `IOptionsSnapshot` est un [service étendu](dependency-injection.md#scoped) et fournit un instantané des options au moment de la construction de l' `IOptionsSnapshot<T>` objet. Les instantanés d’options sont conçus pour être utilisés avec des dépendances transitoires et délimitées.

Le code suivant utilise <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> .

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

Le code suivant inscrit une instance de configuration qui se `TransientFaultHandlingOptions` lie à :

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont lues.

## <a name="ioptionsmonitor"></a>IOptionsMonitor

Le code suivant inscrit une instance de configuration qui est `TransientFaultHandlingOptions` liée à.

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

L'exemple suivant utilise <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> :

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont lues.

## <a name="named-options-support-using-iconfigurenamedoptions"></a>Prise en charge des options nommées à l’aide de IConfigureNamedOptions

Options nommées :

- Sont utiles lorsque plusieurs sections de configuration sont liées aux mêmes propriétés.
- Respectent la casse.

Prenez en compte les _appsettings.jssuivantes sur le fichier * :

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

Au lieu de créer deux classes pour lier `Features:Personalize` et `Features:WeatherStation` , la classe suivante est utilisée pour chaque section :

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

Le code suivant configure les options nommées :

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

Le code suivant affiche les options nommées :

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

Toutes les options sont des instances nommées. <xref:Microsoft.Extensions.Options.IConfigureOptions%601> les instances sont traitées comme ciblant l' `Options.DefaultName` instance, qui est `string.Empty` . En outre, <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> implémente <xref:Microsoft.Extensions.Options.IConfigureOptions%601>. L’implémentation par défaut de <xref:Microsoft.Extensions.Options.IOptionsFactory%601> possède une logique qui utilise chaque élément de manière appropriée. L' `null` option nommée est utilisée pour cibler toutes les instances nommées au lieu d’une instance nommée spécifique. <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> et <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> utilisent cette Convention.

## <a name="optionsbuilder-api"></a>API OptionsBuilder

<xref:Microsoft.Extensions.Options.OptionsBuilder%601> permet de configurer des instances `TOptions`. `OptionsBuilder` simplifie la création d’options nommées. En effet, il est le seul paramètre de l’appel `AddOptions<TOptions>(string optionsName)` initial et n’apparaît pas dans les appels ultérieurs. La validation des options et les surcharges `ConfigureOptions` qui acceptent des dépendances de service sont uniquement disponibles avec `OptionsBuilder`.

`OptionsBuilder` est utilisé dans la section des [options de validation](#options-validation) .

## <a name="use-di-services-to-configure-options"></a>Utiliser les services d’injection de dépendances (DI) pour configurer des options

Les services sont accessibles à partir de l’injection de dépendances lors de la configuration des options de deux manières :

- Transmettez un délégué de configuration à [configurer](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) sur [OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601). `OptionsBuilder<TOptions>` fournit des surcharges de la [configuration](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) qui autorisent l’utilisation de cinq services au maximum pour configurer des options :

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- Créez un type qui implémente <xref:Microsoft.Extensions.Options.IConfigureOptions%601> ou <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> et inscrit le type en tant que service.

Nous vous recommandons de transmettre un délégué de configuration à [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), car il est plus complexe de créer un service. La création d’un type équivaut à ce que fait l’infrastructure lors de l’appel de [configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A). L’appel de [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) a pour effet d’inscrire une instance générique temporaire de <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, dont l’un des constructeurs accepte les types de service génériques spécifiés.

## <a name="options-validation"></a>Validation des options

La validation des options permet de valider les valeurs d’option.

Prenez en compte les *appsettings.jssuivantes sur* le fichier :

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

La classe suivante crée une liaison avec la `"Settings"` section de configuration et applique deux `DataAnnotations` règles :

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

Le code suivant :

- Appelle <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> pour recevoir un [OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601) qui crée une liaison avec la `SettingsOptions` classe.
- Appelle <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> pour activer la validation à l’aide de `DataAnnotations` .

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

La `ValidateDataAnnotations` méthode d’extension est définie dans le package NuGet [Microsoft. extensions. options. DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) .

Le code suivant affiche les valeurs de configuration ou les erreurs de validation :

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

Le code suivant applique une règle de validation plus complexe à l’aide d’un délégué :

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a>IValidateOptions pour la validation complexe

La classe suivante implémente <xref:Microsoft.Extensions.Options.IValidateOptions%601> :

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

`IValidateOptions` permet de déplacer le code de validation dans une classe.

À l’aide du code précédent, la validation est activée dans `ConfigureServices` avec le code suivant :

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a>Options de post-configuration

Définissez la post-configuration avec <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>. Après l’exécution de la configuration, une fois la configuration <xref:Microsoft.Extensions.Options.IConfigureOptions%601> effectuée, elle peut être utile dans les scénarios où vous devez remplacer la configuration :

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> permet de post-configurer les options nommées :

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

Utilisez <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> pour post-configurer toutes les instances de configuration :

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a>Voir aussi

- [Configuration dans .NET](configuration.md)
