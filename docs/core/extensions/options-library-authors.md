---
title: Aide sur les modèles d’options pour les auteurs de bibliothèques .NET
author: IEvangelist
description: Découvrez comment exposer le modèle d’options en tant qu’auteur de bibliothèque dans .NET.
ms.author: dapine
ms.date: 01/28/2021
ms.openlocfilehash: d0da94a8f25c9e5aba6093fab07ccca6a0a7c345
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217214"
---
# <a name="options-pattern-guidance-for-net-library-authors"></a>Aide sur les modèles d’options pour les auteurs de bibliothèques .NET

Avec l’aide de l’injection de dépendances, l’inscription de vos services et de leurs configurations correspondantes peut utiliser le *modèle d’options*. Le modèle d’options permet aux consommateurs de votre bibliothèque (et à vos services) de demander des instances d' [interfaces d’options](options.md#options-interfaces) où `TOptions` est votre classe d’options. L’utilisation d’options de configuration par le biais d’objets fortement typés permet d’assurer une représentation cohérente des valeurs, et supprime la charge liée à l’analyse manuelle des valeurs de chaîne. De nombreux [fournisseurs de configuration](configuration-providers.md) peuvent être utilisés par les consommateurs de votre bibliothèque. Avec ces fournisseurs, les consommateurs peuvent configurer votre bibliothèque de nombreuses façons.

En tant qu’auteur de bibliothèque .NET, vous apprendrez des conseils généraux sur la façon d’exposer correctement le modèle d’options aux consommateurs de votre bibliothèque. Il existe plusieurs façons d’accomplir la même chose, et plusieurs considérations à prendre en compte.

## <a name="naming-conventions"></a>Conventions d’affectation de noms

Par Convention, les méthodes d’extension responsables de l’inscription des services sont nommées `Add{Service}` , où `{Service}` est un nom explicite et descriptif. Selon le package, l’inscription des services peut être accompagnée de `Use{Service}` méthodes d’extension. Les `Use{Service}` méthodes d’extension sont banales dans [ASP.net Core](/aspnet).

✔️ PRENDRE en compte les noms qui lèvent une ambiguïté entre votre service et d’autres offres.

❌ N’utilisez pas les noms qui font déjà partie de l’écosystème .NET des packages Microsoft officiels.

✔️ ENVISAGER de nommer des classes statiques qui exposent des méthodes d’extension en tant que `{Type}Extensions` , où `{Type}` est le type que vous étendez.

### <a name="namespace-guidance"></a>Aide sur les espaces de noms

Les packages Microsoft utilisent l' `Microsoft.Extensions.DependencyInjection` espace de noms pour unifier l’inscription de diverses offres de service.

✔️ ENVISAGER un espace de noms qui identifie clairement votre offre de package.

❌ N’utilisez pas l' `Microsoft.Extensions.DependencyInjection` espace de noms pour les packages Microsoft non officiels.

## <a name="parameterless"></a>Sans paramètre

Si votre service peut fonctionner avec une configuration minimale ou sans configuration explicite, pensez à une méthode d’extension sans paramètre.

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

Dans le code précédent, `AddMyLibraryService` :

- Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- Appelle <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> avec le paramètre de type de `LibraryOptions`
- Chaîne un appel à <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A> , qui spécifie les valeurs d’option par défaut

## <a name="iconfiguration-parameter"></a>Paramètre `IConfiguration`

Lorsque vous créez une bibliothèque qui expose de nombreuses options aux consommateurs, vous pouvez envisager d’exiger une `IConfiguration` méthode d’extension de paramètre. L’instance attendue `IConfiguration` doit être limitée à une section nommée de la configuration à l’aide de la <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> fonction.

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-16":::

Dans le code précédent, `AddMyLibraryService` :

- Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- Définit un <xref:Microsoft.Extensions.Configuration.IConfiguration> paramètre `namedConfigurationSection`
- Appels <xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind(Microsoft.Extensions.Configuration.IConfiguration,System.Object)> passant une instance d’options à laquelle la configuration est liée

Les consommateurs dans ce modèle fournissent l' `IConfiguration` instance étendue de la section nommée :

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

L’appel à `.AddMyLibraryService` est effectué dans la <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> méthode. Il en va de même pour l’utilisation d’une `Startup` classe, l’ajout de services en cours d’inscription dans `ConfigureServices` .

En tant qu’auteur de bibliothèque, il vous revient de spécifier les valeurs par défaut.

> [!NOTE]
> Il est possible de lier la configuration à une instance d’options. Toutefois, il existe un risque de collisions de noms, ce qui entraîne des erreurs. En outre, lors de la liaison manuelle de cette manière, vous limitez la consommation de votre modèle d’options à la lecture une fois. Les modifications apportées aux paramètres ne seront pas reliées, car ces consommateurs ne pourront pas utiliser l’interface [IOptionsMonitor](options.md#ioptionsmonitor) .
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a>Paramètre `Action<TOptions>`

Les consommateurs de votre bibliothèque peuvent souhaiter fournir une expression lambda qui produit une instance de votre classe d’options. Dans ce scénario, vous définissez un `Action<LibraryOptions>` paramètre dans votre méthode d’extension.

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

Dans le code précédent, `AddMyLibraryService` :

- Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- Définit un <xref:System.Action%601> `T` paramètre Where `LibraryOptions``configureOptions`
- Appelle en <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> fonction de l' `configureOptions` action

Dans ce modèle, les consommateurs fournissent une expression lambda (ou un délégué qui satisfait au `Action<LibraryOptions>` paramètre) :

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a>Paramètre d’instance options

Les consommateurs de votre bibliothèque préfèrent peut-être fournir une instance d’options inline. Dans ce scénario, vous exposez une méthode d’extension qui prend une instance de votre objet d’options, `LibraryOptions` .

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

Dans le code précédent, `AddMyLibraryService` :

- Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- Appelle <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> avec le paramètre de type de `LibraryOptions`
- Chaîne un appel à <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> , qui spécifie les valeurs d’option par défaut qui peuvent être substituées à partir de l' `userOptions` instance donnée

Dans ce modèle, les consommateurs fournissent une instance de la `LibraryOptions` classe, en définissant les valeurs de propriété souhaitées inline :

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a>Après la configuration

Une fois que toutes les valeurs d’option de configuration sont liées ou spécifiées, la fonctionnalité de configuration de la publication est disponible. En exposant le même [ `Action<TOptions>` paramètre](#actiontoptions-parameter) détaillé précédemment, vous pouvez choisir d’appeler <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> . La commande après la configuration s’exécute après tous les `.Configure` appels.

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

Dans le code précédent, `AddMyLibraryService` :

- Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- Définit un <xref:System.Action%601> `T` paramètre Where `LibraryOptions``configureOptions`
- Appelle en <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> fonction de l' `configureOptions` action

Dans ce modèle, les consommateurs fournissent une expression lambda (ou un délégué qui répond au `Action<LibraryOptions>` paramètre), comme ils le feraient avec [ `Action<TOptions>` paramètre] dans un scénario de non-publication de configuration :

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a>Voir aussi

- [Modèle d’options dans .NET](options.md)
- [Injection de dépendances dans .NET](dependency-injection.md)
- [Recommandations relatives à l’injection de dépendances](dependency-injection-guidelines.md)
