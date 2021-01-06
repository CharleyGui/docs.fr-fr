---
title: Mise en forme des journaux de la console
description: Découvrez comment utiliser la mise en forme de journal de la console disponible ou implémenter une mise en forme de journal personnalisée pour vos applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 12/17/2020
ms.openlocfilehash: 0ec8fc2018febe4273aa646d1682be197933f925
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700818"
---
# <a name="console-log-formatting"></a><span data-ttu-id="e486c-103">Mise en forme des journaux de la console</span><span class="sxs-lookup"><span data-stu-id="e486c-103">Console log formatting</span></span>

<span data-ttu-id="e486c-104">Dans .NET 5, la prise en charge de la mise en forme personnalisée a été ajoutée aux journaux de la console dans l' `Microsoft.Extensions.Logging.Console` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e486c-104">In .NET 5, support for custom formatting was added to console logs in the `Microsoft.Extensions.Logging.Console` namespace.</span></span> <span data-ttu-id="e486c-105">Trois options de mise en forme prédéfinies sont disponibles : [`Simple`](#simple) , [`Systemd`](#systemd) et [`Json`](#json) .</span><span class="sxs-lookup"><span data-stu-id="e486c-105">There are three predefined formatting options available: [`Simple`](#simple), [`Systemd`](#systemd), and [`Json`](#json).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e486c-106">Auparavant, l' <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> énumération permettait de sélectionner le format de journal souhaité, lisible par l’utilisateur, qui était le `Default` ou une seule ligne, également appelée `Systemd` .</span><span class="sxs-lookup"><span data-stu-id="e486c-106">Previously, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> enum allowed for selecting the desired log format, either human readable which was the `Default`, or single line which is also known as `Systemd`.</span></span> <span data-ttu-id="e486c-107">Toutefois, ceux-ci n’étaient **pas** personnalisables et sont désormais dépréciés.</span><span class="sxs-lookup"><span data-stu-id="e486c-107">However, these were **not** customizable, and are now deprecated.</span></span>

<span data-ttu-id="e486c-108">Dans cet article, vous allez découvrir les formateurs de journaux de console.</span><span class="sxs-lookup"><span data-stu-id="e486c-108">In this article, you will learn about console log formatters.</span></span> <span data-ttu-id="e486c-109">L’exemple de code source montre comment :</span><span class="sxs-lookup"><span data-stu-id="e486c-109">The sample source code demonstrates how to:</span></span>

- <span data-ttu-id="e486c-110">Inscrire un nouveau formateur</span><span class="sxs-lookup"><span data-stu-id="e486c-110">Register a new formatter</span></span>
- <span data-ttu-id="e486c-111">Sélectionner un formateur inscrit à utiliser</span><span class="sxs-lookup"><span data-stu-id="e486c-111">Select a registered formatter to use</span></span>
  - <span data-ttu-id="e486c-112">Par le biais du code ou de la [configuration](configuration.md)</span><span class="sxs-lookup"><span data-stu-id="e486c-112">Either through code, or [configuration](configuration.md)</span></span>
- <span data-ttu-id="e486c-113">Implémenter un formateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="e486c-113">Implement a custom formatter</span></span>
  - <span data-ttu-id="e486c-114">Mettre à jour la configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601></span><span class="sxs-lookup"><span data-stu-id="e486c-114">Update configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601></span></span>
  - <span data-ttu-id="e486c-115">Activer la mise en forme personnalisée des couleurs</span><span class="sxs-lookup"><span data-stu-id="e486c-115">Enable custom color formatting</span></span>

## <a name="register-formatter"></a><span data-ttu-id="e486c-116">Inscrire le formateur</span><span class="sxs-lookup"><span data-stu-id="e486c-116">Register formatter</span></span>

<span data-ttu-id="e486c-117">Le module [ `Console` fournisseur de journalisation](logging-providers.md#console) comporte plusieurs formateurs prédéfinis et expose la possibilité de créer votre propre formateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e486c-117">The [`Console` logging provider](logging-providers.md#console) has several predefined formatters, and exposes the ability to author your own custom formatter.</span></span> <span data-ttu-id="e486c-118">Pour inscrire l’un des formateurs disponibles, utilisez la `Add{Type}Console` méthode d’extension correspondante :</span><span class="sxs-lookup"><span data-stu-id="e486c-118">To register any of the available formatters, use the corresponding `Add{Type}Console` extension method:</span></span>

| <span data-ttu-id="e486c-119">Types disponibles</span><span class="sxs-lookup"><span data-stu-id="e486c-119">Available types</span></span> | <span data-ttu-id="e486c-120">Méthode d’inscription de type</span><span class="sxs-lookup"><span data-stu-id="e486c-120">Method to register type</span></span> |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a><span data-ttu-id="e486c-121">Simple</span><span class="sxs-lookup"><span data-stu-id="e486c-121">Simple</span></span>

<span data-ttu-id="e486c-122">Pour utiliser le `Simple` formateur de console, inscrivez-le auprès des `AddSimpleConsole` éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e486c-122">To use the `Simple` console formatter, register it with `AddSimpleConsole`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

<span data-ttu-id="e486c-123">Dans l’exemple de code source précédent, le <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> formateur a été inscrit.</span><span class="sxs-lookup"><span data-stu-id="e486c-123">In the preceding sample source code, the <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> formatter was registered.</span></span> <span data-ttu-id="e486c-124">Il offre aux journaux la possibilité d’encapsuler des informations telles que le temps et le niveau de journalisation dans chaque message de journal, mais permet également l’incorporation et la mise en retrait de couleurs ANSI des messages.</span><span class="sxs-lookup"><span data-stu-id="e486c-124">It provides logs with the ability to not only wrap information such as time and log level in each log message, but also allows for ANSI color embedding and indentation of messages.</span></span>

### <a name="systemd"></a><span data-ttu-id="e486c-125">SystemD</span><span class="sxs-lookup"><span data-stu-id="e486c-125">Systemd</span></span>

<span data-ttu-id="e486c-126">Le <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> Journal de console :</span><span class="sxs-lookup"><span data-stu-id="e486c-126">The <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> console logger:</span></span>

- <span data-ttu-id="e486c-127">Utilise le format et les niveaux de gravité du journal « syslog »</span><span class="sxs-lookup"><span data-stu-id="e486c-127">Uses the "Syslog" log level format and severities</span></span>
- <span data-ttu-id="e486c-128">Ne met **pas** en forme les messages avec des couleurs</span><span class="sxs-lookup"><span data-stu-id="e486c-128">Does **not** format messages with colors</span></span>
- <span data-ttu-id="e486c-129">Enregistre toujours les messages sur une seule ligne</span><span class="sxs-lookup"><span data-stu-id="e486c-129">Always logs messages in a single line</span></span>

<span data-ttu-id="e486c-130">Cela est souvent utile pour les conteneurs, qui utilisent souvent la `Systemd` journalisation de la console.</span><span class="sxs-lookup"><span data-stu-id="e486c-130">This is commonly useful for containers, which often make use of `Systemd` console logging.</span></span> <span data-ttu-id="e486c-131">Avec .NET 5, le `Simple` Journal de console permet également une version compacte qui se connecte sur une seule ligne et permet également de désactiver les couleurs comme indiqué dans un exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="e486c-131">With .NET 5, the `Simple` console logger also enables a compact version that logs in a single line, and also allows for disabling colors as shown in an earlier sample.</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a><span data-ttu-id="e486c-132">Json</span><span class="sxs-lookup"><span data-stu-id="e486c-132">Json</span></span>

<span data-ttu-id="e486c-133">Pour écrire des journaux au format JSON, le module de formatage de la `Json` console est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e486c-133">To write logs in a JSON format, the `Json` console formatter is used.</span></span> <span data-ttu-id="e486c-134">L’exemple de code source montre comment un ASP.NET Core application peut l’inscrire.</span><span class="sxs-lookup"><span data-stu-id="e486c-134">The sample source code shows how an ASP.NET Core app might register it.</span></span> <span data-ttu-id="e486c-135">À l’aide du `webapp` modèle, créez une nouvelle ASP.net Core application avec la commande [dotnet New](../tools/dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="e486c-135">Using the `webapp` template, create a new ASP.NET Core app with the [dotnet new](../tools/dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

<span data-ttu-id="e486c-136">Quand vous exécutez l’application, à l’aide du code du modèle, vous recevez le format de journal par défaut ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="e486c-136">When running the app, using the template code, you get the default log format below:</span></span>

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

<span data-ttu-id="e486c-137">Par défaut, le module `Simple` de formatage du journal de la console est sélectionné avec la configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="e486c-137">By default, the `Simple` console log formatter is selected with default configuration.</span></span> <span data-ttu-id="e486c-138">Pour modifier cela, appelez `AddJsonConsole` dans *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="e486c-138">You change this by calling `AddJsonConsole` in the *Program.cs*:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

<span data-ttu-id="e486c-139">Exécutez à nouveau l’application, avec la modification ci-dessus, le message de journal est désormais au format JSON :</span><span class="sxs-lookup"><span data-stu-id="e486c-139">Run the app again, with the above change, the log message is now formatted as JSON:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> <span data-ttu-id="e486c-140">Le module de `Json` formatage de la console, par défaut, journalise chaque message sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="e486c-140">The `Json` console formatter, by default, logs each message in a single line.</span></span> <span data-ttu-id="e486c-141">Pour le rendre plus lisible lors de la configuration du formateur, affectez <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> à la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="e486c-141">In order to make it more readable while configuring the formatter, set <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> to `true`.</span></span>

## <a name="set-formatter-with-configuration"></a><span data-ttu-id="e486c-142">Définir le formateur avec la configuration</span><span class="sxs-lookup"><span data-stu-id="e486c-142">Set formatter with configuration</span></span>

<span data-ttu-id="e486c-143">Les exemples précédents ont montré comment inscrire un formateur par programme.</span><span class="sxs-lookup"><span data-stu-id="e486c-143">The previous samples have shown how to register a formatter programmatically.</span></span> <span data-ttu-id="e486c-144">Vous pouvez également effectuer cette opération avec la [configuration](configuration.md).</span><span class="sxs-lookup"><span data-stu-id="e486c-144">Alternatively, this can be done with [configuration](configuration.md).</span></span> <span data-ttu-id="e486c-145">Prenons l’exemple de code source précédent de l’application Web, si vous mettez à jour le *appsettings.jssur* le fichier au lieu `ConfigureLogging` d’appeler dans le fichier *Program.cs* , vous pouvez avoir le même résultat.</span><span class="sxs-lookup"><span data-stu-id="e486c-145">Consider the previous web application sample source code, if you update the *appsettings.json* file rather than calling `ConfigureLogging` in the *Program.cs* file, you could get the same outcome.</span></span> <span data-ttu-id="e486c-146">Le fichier mis à jour `appsettings.json` configure le formateur comme suit :</span><span class="sxs-lookup"><span data-stu-id="e486c-146">The updated `appsettings.json` file would configure the formatter as follows:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

<span data-ttu-id="e486c-147">Les deux valeurs de clés qui doivent être définies sont `"FormatterName"` et `"FormatterOptions"` .</span><span class="sxs-lookup"><span data-stu-id="e486c-147">The two key values that need to be set are `"FormatterName"` and `"FormatterOptions"`.</span></span> <span data-ttu-id="e486c-148">Si un formateur avec la valeur définie pour `"FormatterName"` est déjà inscrit, ce formateur est sélectionné, et ses propriétés peuvent être configurées tant qu’elles sont fournies en tant que clé à l’intérieur du `"FormatterOptions"` nœud.</span><span class="sxs-lookup"><span data-stu-id="e486c-148">If a formatter with the value set for `"FormatterName"` is already registered, that formatter is selected, and its properties can be configured as long as they are provided as a key inside the `"FormatterOptions"` node.</span></span> <span data-ttu-id="e486c-149">Les noms de formateur prédéfinis sont réservés sous <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames> :</span><span class="sxs-lookup"><span data-stu-id="e486c-149">The predefined formatter names are reserved under <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames>:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a><span data-ttu-id="e486c-150">Implémenter un formateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="e486c-150">Implement a custom formatter</span></span>

<span data-ttu-id="e486c-151">Pour implémenter un formateur personnalisé, vous devez :</span><span class="sxs-lookup"><span data-stu-id="e486c-151">To implement a custom formatter, you need to:</span></span>

- <span data-ttu-id="e486c-152">Créer une sous-classe de <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter> , qui représente votre formateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="e486c-152">Create a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter>, this represents your custom formatter</span></span>
- <span data-ttu-id="e486c-153">Inscrire votre formateur personnalisé avec</span><span class="sxs-lookup"><span data-stu-id="e486c-153">Register your custom formatter with</span></span>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

<span data-ttu-id="e486c-154">Créez une méthode d’extension pour la gérer pour vous :</span><span class="sxs-lookup"><span data-stu-id="e486c-154">Create an extension method to handle this for you:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

<span data-ttu-id="e486c-155">Les `CustomOptions` sont définis comme suit :</span><span class="sxs-lookup"><span data-stu-id="e486c-155">The `CustomOptions` are defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

<span data-ttu-id="e486c-156">Dans le code précédent, les options sont une sous-classe de <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> .</span><span class="sxs-lookup"><span data-stu-id="e486c-156">In the preceding code, the options are a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>.</span></span>

<span data-ttu-id="e486c-157">L' `AddConsoleFormatter` API :</span><span class="sxs-lookup"><span data-stu-id="e486c-157">The `AddConsoleFormatter` API:</span></span>

- <span data-ttu-id="e486c-158">Inscrit une sous-classe de `ConsoleFormatter`</span><span class="sxs-lookup"><span data-stu-id="e486c-158">Registers a subclass of `ConsoleFormatter`</span></span>
- <span data-ttu-id="e486c-159">Gère la configuration :</span><span class="sxs-lookup"><span data-stu-id="e486c-159">Handles configuration:</span></span>
  - <span data-ttu-id="e486c-160">Utilise un jeton de modification pour synchroniser les mises à jour, en fonction du [modèle d’options](options.md)et de l’interface [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601)</span><span class="sxs-lookup"><span data-stu-id="e486c-160">Uses a change token to synchronize updates, based on the [options pattern](options.md), and the [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) interface</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

<span data-ttu-id="e486c-161">Définissez une `CustomerFormatter` sous-classe de `ConsoleFormatter` :</span><span class="sxs-lookup"><span data-stu-id="e486c-161">Define a `CustomerFormatter` subclass of `ConsoleFormatter`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

<span data-ttu-id="e486c-162">L' `CustomFormatter.Write<TState>` API précédente dicte le texte qui est encapsulé autour de chaque message de journal.</span><span class="sxs-lookup"><span data-stu-id="e486c-162">The preceding `CustomFormatter.Write<TState>` API dictates what text gets wrapped around each log message.</span></span> <span data-ttu-id="e486c-163">Une norme `ConsoleFormatter` doit pouvoir habiller au minimum les étendues, les horodatages et le niveau de gravité des journaux.</span><span class="sxs-lookup"><span data-stu-id="e486c-163">A standard `ConsoleFormatter` should be able to wrap around scopes, time stamps, and severity level of logs at a minimum.</span></span> <span data-ttu-id="e486c-164">En outre, vous pouvez encoder les couleurs ANSI dans les messages du journal et fournir également les mises en retrait souhaitées.</span><span class="sxs-lookup"><span data-stu-id="e486c-164">Additionally, you can encode ANSI colors in the log messages, and provide desired indentations as well.</span></span> <span data-ttu-id="e486c-165">L’implémentation du n’a `CustomFormatter.Write<TState>` pas ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="e486c-165">The implementation of the `CustomFormatter.Write<TState>` lacks these capabilities.</span></span>

<span data-ttu-id="e486c-166">Pour plus d’informations sur la personnalisation de la mise en forme, consultez les implémentations existantes dans l' `Microsoft.Extensions.Logging.Console` espace de noms :</span><span class="sxs-lookup"><span data-stu-id="e486c-166">For inspiration on further customizing formatting, see the existing implementations in the `Microsoft.Extensions.Logging.Console` namespace:</span></span>

- <span data-ttu-id="e486c-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).</span><span class="sxs-lookup"><span data-stu-id="e486c-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).</span></span>
- [<span data-ttu-id="e486c-168">SystemdConsoleFormatter</span><span class="sxs-lookup"><span data-stu-id="e486c-168">SystemdConsoleFormatter</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)
- [<span data-ttu-id="e486c-169">JsonConsoleFormatter</span><span class="sxs-lookup"><span data-stu-id="e486c-169">JsonConsoleFormatter</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)

## <a name="implement-custom-color-formatting"></a><span data-ttu-id="e486c-170">Implémenter une mise en forme personnalisée des couleurs</span><span class="sxs-lookup"><span data-stu-id="e486c-170">Implement custom color formatting</span></span>

<span data-ttu-id="e486c-171">Pour activer correctement les fonctionnalités de couleur dans votre formateur de journalisation personnalisé, vous pouvez étendre le <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> comme il dispose d’une <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> propriété qui peut être utile pour activer les couleurs dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="e486c-171">In order to properly enable color capabilities in your custom logging formatter, you can extend the <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> as it has a <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> property that can be useful for enabling colors in logs.</span></span>

<span data-ttu-id="e486c-172">Créez un `CustomColorOptions` qui dérive de `SimpleConsoleFormatterOptions` :</span><span class="sxs-lookup"><span data-stu-id="e486c-172">Create a `CustomColorOptions` that derives from `SimpleConsoleFormatterOptions`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

<span data-ttu-id="e486c-173">Ensuite, écrivez des méthodes d’extension dans une `TextWriterExtensions` classe qui permettent d’incorporer facilement des couleurs codées ANSI dans les messages de journal mis en forme :</span><span class="sxs-lookup"><span data-stu-id="e486c-173">Next, write some extension methods in a `TextWriterExtensions` class that allow for conveniently embedding ANSI coded colors within formatted log messages:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

<span data-ttu-id="e486c-174">Un formateur de couleurs personnalisé qui gère l’application de couleurs personnalisées peut être défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="e486c-174">A custom color formatter that handles applying custom colors could be defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

<span data-ttu-id="e486c-175">Lorsque vous exécutez l’application, les journaux affichent le `CustomPrefix` message dans la couleur verte lorsque `FormatterOptions.ColorBehavior` est `Enabled` .</span><span class="sxs-lookup"><span data-stu-id="e486c-175">When you run the application, the logs will show the `CustomPrefix` message in the color green when `FormatterOptions.ColorBehavior` is `Enabled`.</span></span>

> [!NOTE]
> <span data-ttu-id="e486c-176">Lorsque <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> est `Disabled` , les messages de journalisation n’interprètent _pas_ les codes de couleur ANSI incorporés dans les messages de journal.</span><span class="sxs-lookup"><span data-stu-id="e486c-176">When <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> is `Disabled`, log messages do _not_ interpret embedded ANSI color codes within log messages.</span></span> <span data-ttu-id="e486c-177">Au lieu de cela, ils génèrent le message brut.</span><span class="sxs-lookup"><span data-stu-id="e486c-177">Instead, they output the raw message.</span></span> <span data-ttu-id="e486c-178">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e486c-178">For example, consider the following:</span></span>
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> <span data-ttu-id="e486c-179">Cela génère la chaîne textuelle et n’est _pas_ colorée.</span><span class="sxs-lookup"><span data-stu-id="e486c-179">This would output the verbatim string, and it is _not_ colorized.</span></span>
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a><span data-ttu-id="e486c-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e486c-180">See also</span></span>

- [<span data-ttu-id="e486c-181">Journalisation dans .NET</span><span class="sxs-lookup"><span data-stu-id="e486c-181">Logging in .NET</span></span>](logging.md)
- [<span data-ttu-id="e486c-182">Implémenter un fournisseur de journalisation personnalisé dans .NET</span><span class="sxs-lookup"><span data-stu-id="e486c-182">Implement a custom logging provider in .NET</span></span>](custom-logging-provider.md)
- [<span data-ttu-id="e486c-183">Journalisation hautes performances dans .NET</span><span class="sxs-lookup"><span data-stu-id="e486c-183">High-performance logging in .NET</span></span>](high-performance-logging.md)
