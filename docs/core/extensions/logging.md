---
title: Journalisation dans .NET
author: IEvangelist
description: Découvrez comment utiliser le framework de journalisation fourni par le package NuGet Microsoft.Extensions.Logging.
ms.author: dapine
ms.date: 09/30/2020
ms.openlocfilehash: a742e192f8e080e2c76ebeb005168647e440d8ef
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614721"
---
# <a name="logging-in-net"></a><span data-ttu-id="58fc4-103">Journalisation dans .NET</span><span class="sxs-lookup"><span data-stu-id="58fc4-103">Logging in .NET</span></span>

<span data-ttu-id="58fc4-104">.NET prend en charge une API de journalisation qui fonctionne avec un large éventail de fournisseurs de journalisation intégrés et tiers.</span><span class="sxs-lookup"><span data-stu-id="58fc4-104">.NET supports a logging API that works with a variety of built-in and third-party logging providers.</span></span> <span data-ttu-id="58fc4-105">Cet article explique comment utiliser cette API de journalisation avec les fournisseurs de journalisation intégrés.</span><span class="sxs-lookup"><span data-stu-id="58fc4-105">This article shows how to use the logging API with built-in providers.</span></span> <span data-ttu-id="58fc4-106">La plupart des exemples de code présentés dans cet article s’appliquent à toutes les applications .NET qui utilisent l' [hôte générique](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="58fc4-106">Most of the code examples shown in this article apply to any .NET app that uses the [Generic Host](generic-host.md).</span></span> <span data-ttu-id="58fc4-107">Pour les applications qui n’utilisent pas l’hôte générique, consultez [application console non-hôte](#non-host-console-app).</span><span class="sxs-lookup"><span data-stu-id="58fc4-107">For apps that don't use the Generic Host, see [Non-host console app](#non-host-console-app).</span></span>

## <a name="create-logs"></a><span data-ttu-id="58fc4-108">Créer des journaux</span><span class="sxs-lookup"><span data-stu-id="58fc4-108">Create logs</span></span>

<span data-ttu-id="58fc4-109">Pour créer des journaux, utilisez un <xref:Microsoft.Extensions.Logging.ILogger%601> objet à partir de l' [injection de dépendances (di)](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="58fc4-109">To create logs, use an <xref:Microsoft.Extensions.Logging.ILogger%601> object from [dependency injection (DI)](dependency-injection.md).</span></span>

<span data-ttu-id="58fc4-110">L’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="58fc4-110">The following example:</span></span>

- <span data-ttu-id="58fc4-111">Crée un enregistreur d’événements, `ILogger<Worker>` , qui utilise une *catégorie* de journal du nom qualifié complet du type `Worker` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-111">Creates a logger, `ILogger<Worker>`, which uses a log *category* of the fully qualified name of the type `Worker`.</span></span> <span data-ttu-id="58fc4-112">La catégorie du journal est une chaîne associée à chaque journal.</span><span class="sxs-lookup"><span data-stu-id="58fc4-112">The log category is a string that is associated with each log.</span></span>
- <span data-ttu-id="58fc4-113">Appels <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> à consigner au `Information` niveau.</span><span class="sxs-lookup"><span data-stu-id="58fc4-113">Calls <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> to log at the `Information` level.</span></span> <span data-ttu-id="58fc4-114">Le *niveau* du journal indique la gravité de l’événement consigné.</span><span class="sxs-lookup"><span data-stu-id="58fc4-114">The Log *level* indicates the severity of the logged event.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service/Worker.cs" range="9-24" highlight="12":::

<span data-ttu-id="58fc4-115">Les [niveaux](#log-level) et les [catégories](#log-category) sont expliqués plus en détail plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="58fc4-115">[Levels](#log-level) and [categories](#log-category) are explained in more detail later in this article.</span></span>

## <a name="configure-logging"></a><span data-ttu-id="58fc4-116">Configuration de la journalisation</span><span class="sxs-lookup"><span data-stu-id="58fc4-116">Configure logging</span></span>

<span data-ttu-id="58fc4-117">La configuration de la journalisation est généralement fournie par la `Logging` section de *appSettings*. `{Environment}` fichiers *. JSON* .</span><span class="sxs-lookup"><span data-stu-id="58fc4-117">Logging configuration is commonly provided by the `Logging` section of *appsettings*.`{Environment}`*.json* files.</span></span> <span data-ttu-id="58fc4-118">Leappsettings.Development.jssuivant sur le fichier est généré par les modèles \* de service de\* travail .net :</span><span class="sxs-lookup"><span data-stu-id="58fc4-118">The following *appsettings.Development.json* file is generated by the .NET Worker service templates:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Development.json":::

<span data-ttu-id="58fc4-119">Dans le code JSON précédent :</span><span class="sxs-lookup"><span data-stu-id="58fc4-119">In the preceding JSON:</span></span>

- <span data-ttu-id="58fc4-120">Les `"Default"` `"Microsoft"` catégories, et `"Microsoft.Hosting.Lifetime"` sont spécifiées.</span><span class="sxs-lookup"><span data-stu-id="58fc4-120">The `"Default"`, `"Microsoft"`, and `"Microsoft.Hosting.Lifetime"` categories are specified.</span></span>
- <span data-ttu-id="58fc4-121">La `"Microsoft"` catégorie s’applique à toutes les catégories qui commencent par `"Microsoft"` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-121">The `"Microsoft"` category applies to all categories that start with `"Microsoft"`.</span></span>
- <span data-ttu-id="58fc4-122">La `"Microsoft"` catégorie enregistre les journaux au niveau du journal et au niveau `Warning` supérieur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-122">The `"Microsoft"` category logs at log level `Warning` and higher.</span></span>
- <span data-ttu-id="58fc4-123">La catégorie `"Microsoft.Hosting.Lifetime"` est plus spécifique que la catégorie `"Microsoft"` , de sorte que la `"Microsoft.Hosting.Lifetime"` catégorie enregistre les journaux au niveau du journal « information » et supérieur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-123">The `"Microsoft.Hosting.Lifetime"` category is more specific than the `"Microsoft"` category, so the `"Microsoft.Hosting.Lifetime"` category logs at log level "Information" and higher.</span></span>
- <span data-ttu-id="58fc4-124">Un module fournisseur d’informations spécifique n’étant pas spécifié, `LogLevel` s’applique à tous les fournisseurs de journalisation activés, à l’exception du journal des [événements Windows](logging-providers.md#windows-eventlog).</span><span class="sxs-lookup"><span data-stu-id="58fc4-124">A specific log provider is not specified, so `LogLevel` applies to all the enabled logging providers except for the [Windows EventLog](logging-providers.md#windows-eventlog).</span></span>

<span data-ttu-id="58fc4-125">La `Logging` propriété peut avoir <xref:Microsoft.Extensions.Logging.LogLevel> et enregistrer les propriétés du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-125">The `Logging` property can have <xref:Microsoft.Extensions.Logging.LogLevel> and log provider properties.</span></span> <span data-ttu-id="58fc4-126">`LogLevel`Spécifie le [niveau](#log-level) minimal à enregistrer pour les catégories sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="58fc4-126">The `LogLevel` specifies the minimum [level](#log-level) to log for selected categories.</span></span> <span data-ttu-id="58fc4-127">Dans le code JSON précédent, les `Information` `Warning` niveaux de journalisation sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="58fc4-127">In the preceding JSON, `Information` and `Warning` log levels are specified.</span></span> <span data-ttu-id="58fc4-128">`LogLevel` indique la gravité du journal et les plages de 0 à 6 :</span><span class="sxs-lookup"><span data-stu-id="58fc4-128">`LogLevel` indicates the severity of the log and ranges from 0 to 6:</span></span>

<span data-ttu-id="58fc4-129">`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5 et `None` = 6.</span><span class="sxs-lookup"><span data-stu-id="58fc4-129">`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5, and `None` = 6.</span></span>

<span data-ttu-id="58fc4-130">Lorsqu’un `LogLevel` est spécifié, la journalisation est activée pour les messages au niveau spécifié et supérieur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-130">When a `LogLevel` is specified, logging is enabled for messages at the specified level and higher.</span></span> <span data-ttu-id="58fc4-131">Dans le code JSON précédent, la `Default` catégorie est journalisée pour `Information` et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="58fc4-131">In the preceding JSON, the `Default` category is logged for `Information` and higher.</span></span> <span data-ttu-id="58fc4-132">Par exemple, les messages,, `Information` `Warning` `Error` et `Critical` sont journalisés.</span><span class="sxs-lookup"><span data-stu-id="58fc4-132">For example, `Information`, `Warning`, `Error`, and `Critical` messages are logged.</span></span> <span data-ttu-id="58fc4-133">Si aucun `LogLevel` n’est spécifié, la journalisation est définie par défaut sur le `Information` niveau.</span><span class="sxs-lookup"><span data-stu-id="58fc4-133">If no `LogLevel` is specified, logging defaults to the `Information` level.</span></span> <span data-ttu-id="58fc4-134">Pour plus d’informations, consultez [niveaux de journalisation](#log-level).</span><span class="sxs-lookup"><span data-stu-id="58fc4-134">For more information, see [Log levels](#log-level).</span></span>

<span data-ttu-id="58fc4-135">Une propriété de fournisseur peut spécifier une `LogLevel` propriété.</span><span class="sxs-lookup"><span data-stu-id="58fc4-135">A provider property can specify a `LogLevel` property.</span></span> <span data-ttu-id="58fc4-136">`LogLevel` sous un fournisseur spécifie les niveaux de journalisation pour ce fournisseur, et remplace les paramètres du journal non fournisseur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-136">`LogLevel` under a provider specifies levels to log for that provider, and overrides the non-provider log settings.</span></span> <span data-ttu-id="58fc4-137">Prenez en compte les *appsettings.jssuivantes sur* le fichier :</span><span class="sxs-lookup"><span data-stu-id="58fc4-137">Consider the following *appsettings.json* file:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Staging.json":::

<span data-ttu-id="58fc4-138">Paramètres dans les `Logging.{ProviderName}.LogLevel` paramètres de remplacement dans `Logging.LogLevel` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-138">Settings in `Logging.{ProviderName}.LogLevel` override settings in `Logging.LogLevel`.</span></span> <span data-ttu-id="58fc4-139">Dans le code JSON précédent, le `Debug` niveau de journalisation par défaut du fournisseur est défini sur `Information` :</span><span class="sxs-lookup"><span data-stu-id="58fc4-139">In the preceding JSON, the `Debug` provider's default log level is set to `Information`:</span></span>

`Logging:Debug:LogLevel:Default:Information`

<span data-ttu-id="58fc4-140">Le paramètre précédent spécifie le `Information` niveau de journalisation pour chaque `Logging:Debug:` catégorie, à l’exception de `Microsoft.Hosting` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-140">The preceding setting specifies the `Information` log level for every `Logging:Debug:` category except `Microsoft.Hosting`.</span></span> <span data-ttu-id="58fc4-141">Quand une catégorie spécifique est indiquée, la catégorie spécifique remplace la catégorie par défaut.</span><span class="sxs-lookup"><span data-stu-id="58fc4-141">When a specific category is listed, the specific category overrides the default category.</span></span> <span data-ttu-id="58fc4-142">Dans le JSON précédent, les `Logging:Debug:LogLevel` catégories `"Microsoft.Hosting"` et `"Default"` remplacent les paramètres dans `Logging:LogLevel`</span><span class="sxs-lookup"><span data-stu-id="58fc4-142">In the preceding JSON, the `Logging:Debug:LogLevel` categories `"Microsoft.Hosting"` and `"Default"` override the settings in `Logging:LogLevel`</span></span>

<span data-ttu-id="58fc4-143">Le niveau de journal minimal peut être spécifié pour l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="58fc4-143">The minimum log level can be specified for any of:</span></span>

- <span data-ttu-id="58fc4-144">Fournisseurs spécifiques : par exemple, `Logging:EventSource:LogLevel:Default:Information`</span><span class="sxs-lookup"><span data-stu-id="58fc4-144">Specific providers:  For example, `Logging:EventSource:LogLevel:Default:Information`</span></span>
- <span data-ttu-id="58fc4-145">Catégories spécifiques : par exemple, `Logging:LogLevel:Microsoft:Warning`</span><span class="sxs-lookup"><span data-stu-id="58fc4-145">Specific categories: For example, `Logging:LogLevel:Microsoft:Warning`</span></span>
- <span data-ttu-id="58fc4-146">Tous les fournisseurs et toutes les catégories : `Logging:LogLevel:Default:Warning`</span><span class="sxs-lookup"><span data-stu-id="58fc4-146">All providers and all categories: `Logging:LogLevel:Default:Warning`</span></span>

<span data-ttu-id="58fc4-147">Les journaux situés en dessous du niveau minimal ne sont ***pas***:</span><span class="sxs-lookup"><span data-stu-id="58fc4-147">Any logs below the minimum level are ***not***:</span></span>

- <span data-ttu-id="58fc4-148">Passé au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-148">Passed to the provider.</span></span>
- <span data-ttu-id="58fc4-149">Consigné ou affiché.</span><span class="sxs-lookup"><span data-stu-id="58fc4-149">Logged or displayed.</span></span>

<span data-ttu-id="58fc4-150">Pour supprimer tous les journaux, spécifiez [LogLevel. None](xref:Microsoft.Extensions.Logging.LogLevel).</span><span class="sxs-lookup"><span data-stu-id="58fc4-150">To suppress all logs, specify [LogLevel.None](xref:Microsoft.Extensions.Logging.LogLevel).</span></span> <span data-ttu-id="58fc4-151">`LogLevel.None` a une valeur de 6, qui est supérieure à `LogLevel.Critical` (5).</span><span class="sxs-lookup"><span data-stu-id="58fc4-151">`LogLevel.None` has a value of 6, which is higher than `LogLevel.Critical` (5).</span></span>

<span data-ttu-id="58fc4-152">Si un fournisseur prend en charge les [étendues de journal](#log-scopes), `IncludeScopes` indique s’ils sont activés.</span><span class="sxs-lookup"><span data-stu-id="58fc4-152">If a provider supports [log scopes](#log-scopes), `IncludeScopes` indicates whether they're enabled.</span></span> <span data-ttu-id="58fc4-153">Pour plus d’informations, consultez [étendues de journaux](#log-scopes)</span><span class="sxs-lookup"><span data-stu-id="58fc4-153">For more information, see [log scopes](#log-scopes)</span></span>

<span data-ttu-id="58fc4-154">Le *appsettings.jssuivant sur* le fichier contient les paramètres de tous les fournisseurs intégrés :</span><span class="sxs-lookup"><span data-stu-id="58fc4-154">The following *appsettings.json* file contains settings for all of the built-in providers:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Production.json":::

<span data-ttu-id="58fc4-155">Dans l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="58fc4-155">In the preceding sample:</span></span>

- <span data-ttu-id="58fc4-156">Les catégories et les niveaux ne sont pas des valeurs suggérées.</span><span class="sxs-lookup"><span data-stu-id="58fc4-156">The categories and levels are not suggested values.</span></span> <span data-ttu-id="58fc4-157">L’exemple est fourni pour afficher tous les fournisseurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="58fc4-157">The sample is provided to show all the default providers.</span></span>
- <span data-ttu-id="58fc4-158">Paramètres dans les `Logging.{ProviderName}.LogLevel` paramètres de remplacement dans `Logging.LogLevel` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-158">Settings in `Logging.{ProviderName}.LogLevel` override settings in `Logging.LogLevel`.</span></span> <span data-ttu-id="58fc4-159">Par exemple, le niveau dans `Debug.LogLevel.Default` remplace le niveau dans `LogLevel.Default` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-159">For example, the level in `Debug.LogLevel.Default` overrides the level in `LogLevel.Default`.</span></span>
- <span data-ttu-id="58fc4-160">L' *alias* de chaque fournisseur est utilisé.</span><span class="sxs-lookup"><span data-stu-id="58fc4-160">Each provider's *alias* is used.</span></span> <span data-ttu-id="58fc4-161">Chaque fournisseur définit un *alias* qui peut être utilisé dans la configuration à la place du nom de type complet.</span><span class="sxs-lookup"><span data-stu-id="58fc4-161">Each provider defines an *alias* that can be used in configuration in place of the fully qualified type name.</span></span> <span data-ttu-id="58fc4-162">Les alias des fournisseurs intégrés sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="58fc4-162">The built-in providers' aliases are:</span></span>
  - <span data-ttu-id="58fc4-163">Console</span><span class="sxs-lookup"><span data-stu-id="58fc4-163">Console</span></span>
  - <span data-ttu-id="58fc4-164">Débogage</span><span class="sxs-lookup"><span data-stu-id="58fc4-164">Debug</span></span>
  - <span data-ttu-id="58fc4-165">EventSource</span><span class="sxs-lookup"><span data-stu-id="58fc4-165">EventSource</span></span>
  - <span data-ttu-id="58fc4-166">EventLog</span><span class="sxs-lookup"><span data-stu-id="58fc4-166">EventLog</span></span>
  - <span data-ttu-id="58fc4-167">AzureAppServicesFile</span><span class="sxs-lookup"><span data-stu-id="58fc4-167">AzureAppServicesFile</span></span>
  - <span data-ttu-id="58fc4-168">AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="58fc4-168">AzureAppServicesBlob</span></span>
  - <span data-ttu-id="58fc4-169">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="58fc4-169">ApplicationInsights</span></span>

### <a name="set-log-level-by-command-line-environment-variables-and-other-configuration"></a><span data-ttu-id="58fc4-170">Définir le niveau de journalisation à l’aide d’une ligne de commande, de variables d’environnement et d’autres configurations</span><span class="sxs-lookup"><span data-stu-id="58fc4-170">Set log level by command line, environment variables, and other configuration</span></span>

<span data-ttu-id="58fc4-171">Le niveau de journal peut être défini par l’un des [fournisseurs de configuration](configuration-providers.md).</span><span class="sxs-lookup"><span data-stu-id="58fc4-171">Log level can be set by any of the [configuration providers](configuration-providers.md).</span></span>

<span data-ttu-id="58fc4-172">Les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="58fc4-172">The following commands:</span></span>

- <span data-ttu-id="58fc4-173">Affectez à la clé d’environnement la `Logging:LogLevel:Microsoft` valeur `Information` sur Windows.</span><span class="sxs-lookup"><span data-stu-id="58fc4-173">Set the environment key `Logging:LogLevel:Microsoft` to a value of `Information` on Windows.</span></span>
- <span data-ttu-id="58fc4-174">Testez les paramètres lors de l’utilisation d’une application créée avec les modèles de service de travail .NET.</span><span class="sxs-lookup"><span data-stu-id="58fc4-174">Test the settings when using an app created with the .NET Worker service templates.</span></span> <span data-ttu-id="58fc4-175">La `dotnet run` commande doit être exécutée dans le répertoire du projet après l’utilisation de `set` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-175">The `dotnet run` command must be run in the project directory after using `set`.</span></span>

```cmd
set Logging__LogLevel__Microsoft=Information
dotnet run
```

<span data-ttu-id="58fc4-176">Le paramètre d’environnement précédent :</span><span class="sxs-lookup"><span data-stu-id="58fc4-176">The preceding environment setting:</span></span>

- <span data-ttu-id="58fc4-177">Est défini uniquement dans les processus lancés à partir de la fenêtre de commande dans laquelle ils ont été définis.</span><span class="sxs-lookup"><span data-stu-id="58fc4-177">Is only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="58fc4-178">N’est pas lu par les applications lancées avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58fc4-178">Isn't read by apps launched with Visual Studio.</span></span>

<span data-ttu-id="58fc4-179">La commande [setx](/windows-server/administration/windows-commands/setx) suivante définit également la clé et la valeur de l’environnement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="58fc4-179">The following [setx](/windows-server/administration/windows-commands/setx) command also sets the environment key and value on Windows.</span></span> <span data-ttu-id="58fc4-180">Contrairement à `set` , `setx` les paramètres sont conservés.</span><span class="sxs-lookup"><span data-stu-id="58fc4-180">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="58fc4-181">Le `/M` commutateur définit la variable dans l’environnement système.</span><span class="sxs-lookup"><span data-stu-id="58fc4-181">The `/M` switch sets the variable in the system environment.</span></span> <span data-ttu-id="58fc4-182">Si `/M` n’est pas utilisé, une variable d’environnement utilisateur est définie.</span><span class="sxs-lookup"><span data-stu-id="58fc4-182">If `/M` isn't used, a user environment variable is set.</span></span>

```cmd
setx Logging__LogLevel__Microsoft=Information /M
```

<span data-ttu-id="58fc4-183">Dans [Azure App service](https://azure.microsoft.com/services/app-service/), sélectionnez **nouveau paramètre d’application** dans la page **paramètres > configuration** .</span><span class="sxs-lookup"><span data-stu-id="58fc4-183">On [Azure App Service](https://azure.microsoft.com/services/app-service/), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="58fc4-184">Azure App Service paramètres de l’application sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="58fc4-184">Azure App Service application settings are:</span></span>

- <span data-ttu-id="58fc4-185">Chiffré au repos et transmis sur un canal chiffré.</span><span class="sxs-lookup"><span data-stu-id="58fc4-185">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="58fc4-186">Exposés en tant que variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="58fc4-186">Exposed as environment variables.</span></span>

<span data-ttu-id="58fc4-187">Pour plus d’informations sur la définition des valeurs de configuration .NET à l’aide de variables d’environnement, consultez [variables d’environnement](configuration-providers.md#environment-variable-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="58fc4-187">For more information on setting .NET configuration values using environment variables, see [environment variables](configuration-providers.md#environment-variable-configuration-provider).</span></span>

## <a name="how-filtering-rules-are-applied"></a><span data-ttu-id="58fc4-188">Mode d’application des règles de filtre</span><span class="sxs-lookup"><span data-stu-id="58fc4-188">How filtering rules are applied</span></span>

<span data-ttu-id="58fc4-189">À la création d’un objet <xref:Microsoft.Extensions.Logging.ILogger%601>, l’objet <xref:Microsoft.Extensions.Logging.ILoggerFactory> sélectionne une seule règle à appliquer à cet enregistrement d’événements par fournisseur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-189">When an <xref:Microsoft.Extensions.Logging.ILogger%601> object is created, the <xref:Microsoft.Extensions.Logging.ILoggerFactory> object selects a single rule per provider to apply to that logger.</span></span> <span data-ttu-id="58fc4-190">Tous les messages écrits par une instance `ILogger` sont filtrés selon les règles sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="58fc4-190">All messages written by an `ILogger` instance are filtered based on the selected rules.</span></span> <span data-ttu-id="58fc4-191">La règle la plus spécifique pour chaque paire fournisseur et catégorie est sélectionnée parmi les règles disponibles.</span><span class="sxs-lookup"><span data-stu-id="58fc4-191">The most specific rule for each provider and category pair is selected from the available rules.</span></span>

<span data-ttu-id="58fc4-192">L’algorithme suivant est utilisé pour chaque fournisseur quand un objet `ILogger` est créé pour une catégorie donnée :</span><span class="sxs-lookup"><span data-stu-id="58fc4-192">The following algorithm is used for each provider when an `ILogger` is created for a given category:</span></span>

- <span data-ttu-id="58fc4-193">Sélectionnez toutes les règles qui correspondent au fournisseur ou à son alias.</span><span class="sxs-lookup"><span data-stu-id="58fc4-193">Select all rules that match the provider or its alias.</span></span> <span data-ttu-id="58fc4-194">Si aucune correspondance n’est trouvée, sélectionnez toutes les règles avec un fournisseur vide.</span><span class="sxs-lookup"><span data-stu-id="58fc4-194">If no match is found, select all rules with an empty provider.</span></span>
- <span data-ttu-id="58fc4-195">À partir du résultat de l’étape précédente, sélectionnez les règles ayant le plus long préfixe de catégorie correspondant.</span><span class="sxs-lookup"><span data-stu-id="58fc4-195">From the result of the preceding step, select rules with longest matching category prefix.</span></span> <span data-ttu-id="58fc4-196">Si aucune correspondance n’est trouvée, sélectionnez toutes les règles qui ne spécifient pas de catégorie.</span><span class="sxs-lookup"><span data-stu-id="58fc4-196">If no match is found, select all rules that don't specify a category.</span></span>
- <span data-ttu-id="58fc4-197">Si plusieurs règles sont sélectionnées, prenez la **dernière**.</span><span class="sxs-lookup"><span data-stu-id="58fc4-197">If multiple rules are selected, take the **last** one.</span></span>
- <span data-ttu-id="58fc4-198">Si aucune règle n’est sélectionnée, utilisez <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> pour spécifier le niveau de journalisation minimale.</span><span class="sxs-lookup"><span data-stu-id="58fc4-198">If no rules are selected, use <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> to specify the minimum logging level.</span></span>

## <a name="log-category"></a><span data-ttu-id="58fc4-199">Catégorie de journal</span><span class="sxs-lookup"><span data-stu-id="58fc4-199">Log category</span></span>

<span data-ttu-id="58fc4-200">Lorsqu’un `ILogger` objet est créé, une *catégorie* est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="58fc4-200">When an `ILogger` object is created, a *category* is specified.</span></span> <span data-ttu-id="58fc4-201">Cette catégorie est incluse dans tous les messages de journal créés par cette instance de `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="58fc4-201">That category is included with each log message created by that instance of `ILogger`.</span></span> <span data-ttu-id="58fc4-202">La chaîne de catégorie est arbitraire, mais la Convention consiste à utiliser le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="58fc4-202">The category string is arbitrary, but the convention is to use the class name.</span></span> <span data-ttu-id="58fc4-203">Par exemple, dans une application avec un service défini comme l’objet suivant, la catégorie peut être `"Example.DefaultService"` :</span><span class="sxs-lookup"><span data-stu-id="58fc4-203">For example, in an application with a service define like the following object, the category might be `"Example.DefaultService"`:</span></span>

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger<DefaultService> _logger;

        public DefaultService(ILogger<DefaultService> logger) =>
            _logger = logger;

        // ...
    }
}
```

<span data-ttu-id="58fc4-204">Pour spécifier explicitement la catégorie, appelez <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="58fc4-204">To explicitly specify the category, call <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType>:</span></span>

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger _logger;

        public DefaultService(ILoggerFactory loggerFactory) =>
            _logger = logger.CreateLogger("CustomCategory");

        // ...
    }
}
```

<span data-ttu-id="58fc4-205">L’appel de `CreateLogger` avec un nom fixe peut être utile lorsqu’il est utilisé dans plusieurs méthodes afin que les événements puissent être organisés par catégorie.</span><span class="sxs-lookup"><span data-stu-id="58fc4-205">Calling `CreateLogger` with a fixed name can be useful when used in multiple methods so the events can be organized by category.</span></span>

<span data-ttu-id="58fc4-206">`ILogger<T>` équivaut à appeler `CreateLogger` avec le nom de type complet `T`.</span><span class="sxs-lookup"><span data-stu-id="58fc4-206">`ILogger<T>` is equivalent to calling `CreateLogger` with the fully qualified type name of `T`.</span></span>

## <a name="log-level"></a><span data-ttu-id="58fc4-207">Log level</span><span class="sxs-lookup"><span data-stu-id="58fc4-207">Log level</span></span>

<span data-ttu-id="58fc4-208">Le tableau suivant répertorie les <xref:Microsoft.Extensions.Logging.LogLevel> valeurs, la `Log{LogLevel}` méthode d’extension de commodité et l’utilisation suggérée :</span><span class="sxs-lookup"><span data-stu-id="58fc4-208">The following table lists the <xref:Microsoft.Extensions.Logging.LogLevel> values, the convenience `Log{LogLevel}` extension method, and the suggested usage:</span></span>

| <span data-ttu-id="58fc4-209">LogLevel</span><span class="sxs-lookup"><span data-stu-id="58fc4-209">LogLevel</span></span> | <span data-ttu-id="58fc4-210">Valeur</span><span class="sxs-lookup"><span data-stu-id="58fc4-210">Value</span></span> | <span data-ttu-id="58fc4-211">Méthode</span><span class="sxs-lookup"><span data-stu-id="58fc4-211">Method</span></span> | <span data-ttu-id="58fc4-212">Description</span><span class="sxs-lookup"><span data-stu-id="58fc4-212">Description</span></span> |
|--|--|--|--|
| [<span data-ttu-id="58fc4-213">Trace</span><span class="sxs-lookup"><span data-stu-id="58fc4-213">Trace</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="58fc4-214">0</span><span class="sxs-lookup"><span data-stu-id="58fc4-214">0</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogTrace%2A> | <span data-ttu-id="58fc4-215">Contiennent les messages les plus détaillés.</span><span class="sxs-lookup"><span data-stu-id="58fc4-215">Contain the most detailed messages.</span></span> <span data-ttu-id="58fc4-216">Ces messages peuvent contenir des données d’application sensibles.</span><span class="sxs-lookup"><span data-stu-id="58fc4-216">These messages may contain sensitive app data.</span></span> <span data-ttu-id="58fc4-217">Ces messages sont désactivés par défaut et ***ne doivent pas*** être activés en production.</span><span class="sxs-lookup"><span data-stu-id="58fc4-217">These messages are disabled by default and should ***not*** be enabled in production.</span></span> |
| [<span data-ttu-id="58fc4-218">Déboguer</span><span class="sxs-lookup"><span data-stu-id="58fc4-218">Debug</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="58fc4-219">1</span><span class="sxs-lookup"><span data-stu-id="58fc4-219">1</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> | <span data-ttu-id="58fc4-220">Pour le débogage et le développement.</span><span class="sxs-lookup"><span data-stu-id="58fc4-220">For debugging and development.</span></span> <span data-ttu-id="58fc4-221">Utilisez avec précaution en production en raison du volume élevé.</span><span class="sxs-lookup"><span data-stu-id="58fc4-221">Use with caution in production due to the high volume.</span></span> |
| [<span data-ttu-id="58fc4-222">Informations</span><span class="sxs-lookup"><span data-stu-id="58fc4-222">Information</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="58fc4-223">2</span><span class="sxs-lookup"><span data-stu-id="58fc4-223">2</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> | <span data-ttu-id="58fc4-224">Effectue le suivi du déroulement général de l’application.</span><span class="sxs-lookup"><span data-stu-id="58fc4-224">Tracks the general flow of the app.</span></span> <span data-ttu-id="58fc4-225">Peut avoir une valeur à long terme.</span><span class="sxs-lookup"><span data-stu-id="58fc4-225">May have long-term value.</span></span> |
| [<span data-ttu-id="58fc4-226">Avertissement</span><span class="sxs-lookup"><span data-stu-id="58fc4-226">Warning</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="58fc4-227">3</span><span class="sxs-lookup"><span data-stu-id="58fc4-227">3</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogWarning%2A> | <span data-ttu-id="58fc4-228">Pour les événements anormaux ou inattendus.</span><span class="sxs-lookup"><span data-stu-id="58fc4-228">For abnormal or unexpected events.</span></span> <span data-ttu-id="58fc4-229">Comprend généralement des erreurs ou des conditions qui ne provoquent pas l’échec de l’application.</span><span class="sxs-lookup"><span data-stu-id="58fc4-229">Typically includes errors or conditions that don't cause the app to fail.</span></span> |
| [<span data-ttu-id="58fc4-230">Error</span><span class="sxs-lookup"><span data-stu-id="58fc4-230">Error</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="58fc4-231">4</span><span class="sxs-lookup"><span data-stu-id="58fc4-231">4</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogError%2A> | <span data-ttu-id="58fc4-232">Fournit des informations sur des erreurs et des exceptions qui ne peuvent pas être gérées.</span><span class="sxs-lookup"><span data-stu-id="58fc4-232">For errors and exceptions that cannot be handled.</span></span> <span data-ttu-id="58fc4-233">Ces messages indiquent un échec dans l’opération ou la demande en cours, et non dans l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="58fc4-233">These messages indicate a failure in the current operation or request, not an app-wide failure.</span></span> |
| [<span data-ttu-id="58fc4-234">Critical</span><span class="sxs-lookup"><span data-stu-id="58fc4-234">Critical</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="58fc4-235">5</span><span class="sxs-lookup"><span data-stu-id="58fc4-235">5</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogCritical%2A> | <span data-ttu-id="58fc4-236">Fournit des informations sur des échecs qui nécessitent un examen immédiat.</span><span class="sxs-lookup"><span data-stu-id="58fc4-236">For failures that require immediate attention.</span></span> <span data-ttu-id="58fc4-237">Exemples : perte de données, espace disque insuffisant.</span><span class="sxs-lookup"><span data-stu-id="58fc4-237">Examples: data loss scenarios, out of disk space.</span></span> |
| [<span data-ttu-id="58fc4-238">Aucun</span><span class="sxs-lookup"><span data-stu-id="58fc4-238">None</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="58fc4-239">6</span><span class="sxs-lookup"><span data-stu-id="58fc4-239">6</span></span> |  | <span data-ttu-id="58fc4-240">Spécifie qu’aucun message ne doit être écrit.</span><span class="sxs-lookup"><span data-stu-id="58fc4-240">Specifies that no messages should be written.</span></span> |

<span data-ttu-id="58fc4-241">Dans le tableau précédent, la `LogLevel` est indiquée du niveau de gravité le plus bas au plus élevé.</span><span class="sxs-lookup"><span data-stu-id="58fc4-241">In the previous table, the `LogLevel` is listed from lowest to highest severity.</span></span>

<span data-ttu-id="58fc4-242">Le premier paramètre de la méthode de [journalisation](xref:Microsoft.Extensions.Logging.LoggerExtensions) , <xref:Microsoft.Extensions.Logging.LogLevel> , indique la gravité du journal.</span><span class="sxs-lookup"><span data-stu-id="58fc4-242">The [Log](xref:Microsoft.Extensions.Logging.LoggerExtensions) method's first parameter, <xref:Microsoft.Extensions.Logging.LogLevel>, indicates the severity of the log.</span></span> <span data-ttu-id="58fc4-243">Au lieu d’appeler `Log(LogLevel, ...)` , la plupart des développeurs appellent les méthodes d’extension [log {LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions) .</span><span class="sxs-lookup"><span data-stu-id="58fc4-243">Rather than calling `Log(LogLevel, ...)`, most developers call the [Log{LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions) extension methods.</span></span> <span data-ttu-id="58fc4-244">Les `Log{LogLevel}` méthodes d’extension [appellent la méthode log et spécifient LogLevel](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs).</span><span class="sxs-lookup"><span data-stu-id="58fc4-244">The `Log{LogLevel}` extension methods [call the Log method and specify the LogLevel](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs).</span></span> <span data-ttu-id="58fc4-245">Par exemple, les deux appels de journalisation suivants sont fonctionnellement équivalents et produisent le même journal :</span><span class="sxs-lookup"><span data-stu-id="58fc4-245">For example, the following two logging calls are functionally equivalent and produce the same log:</span></span>

```csharp
public void LogDetails()
{
    var logMessage = "Details for log.";

    _logger.Log(LogLevel.Information, AppLogEvents.Details, logMessage);
    _logger.LogInformation(AppLogEvents.Details, logMessage);
}
```

<span data-ttu-id="58fc4-246">`AppLogEvents.Details` est l’ID d’événement et est implicitement représenté par une valeur de constante <xref:System.Int32> .</span><span class="sxs-lookup"><span data-stu-id="58fc4-246">`AppLogEvents.Details` is the event ID, and is implicitly represented by a constant <xref:System.Int32> value.</span></span> <span data-ttu-id="58fc4-247">`AppLogEvents` est une classe qui expose différentes constantes d’identificateur nommées et qui est affichée dans la section de l' [ID d’événement de journal](#log-event-id) .</span><span class="sxs-lookup"><span data-stu-id="58fc4-247">`AppLogEvents` is a class that exposes various named identifier constants and is displayed in the [Log event ID](#log-event-id) section.</span></span>

<span data-ttu-id="58fc4-248">Le code suivant crée des journaux `Information` et `Warning` :</span><span class="sxs-lookup"><span data-stu-id="58fc4-248">The following code creates `Information` and `Warning` logs:</span></span>

```csharp
public async Task<T> GetAsync<T>(string id)
{
    _logger.LogInformation(AppLogEvents.Read, "Reading value for {Id}", id);

    var result = await _repository.GetAsync(id);
    if (result is null)
    {
        _logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
    }

    return result;
}
```

<span data-ttu-id="58fc4-249">Dans le code précédent, le premier `Log{LogLevel}` paramètre, `AppLogEvents.Read` , est l' [ID d’événement du journal](#log-event-id).</span><span class="sxs-lookup"><span data-stu-id="58fc4-249">In the preceding code, the first `Log{LogLevel}` parameter,`AppLogEvents.Read`, is the [Log event ID](#log-event-id).</span></span> <span data-ttu-id="58fc4-250">Le deuxième paramètre est un modèle de message contenant des espaces réservés pour les valeurs d’argument fournies par les autres paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="58fc4-250">The second parameter is a message template with placeholders for argument values provided by the remaining method parameters.</span></span> <span data-ttu-id="58fc4-251">Les paramètres de méthode sont expliqués dans la section [modèle de message](#log-message-template) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="58fc4-251">The method parameters are explained in the [message template](#log-message-template) section later in this article.</span></span>

<span data-ttu-id="58fc4-252">Configurez le niveau de journalisation approprié et appelez les `Log{LogLevel}` méthodes appropriées pour contrôler la quantité de sortie de journal écrite sur un support de stockage particulier.</span><span class="sxs-lookup"><span data-stu-id="58fc4-252">Configure the the appropriate log level and call the correct `Log{LogLevel}` methods to control how much log output is written to a particular storage medium.</span></span> <span data-ttu-id="58fc4-253">Exemple :</span><span class="sxs-lookup"><span data-stu-id="58fc4-253">For example:</span></span>

- <span data-ttu-id="58fc4-254">En production :</span><span class="sxs-lookup"><span data-stu-id="58fc4-254">In production:</span></span>
  - <span data-ttu-id="58fc4-255">La journalisation au `Trace` niveau des ou de `Information` génère un volume important de messages journaux détaillés.</span><span class="sxs-lookup"><span data-stu-id="58fc4-255">Logging at the `Trace` or `Information` levels produces a high-volume of detailed log messages.</span></span> <span data-ttu-id="58fc4-256">Pour contrôler les coûts et ne pas dépasser les limites de stockage des données, `Trace` `Information` les messages de journal et de niveau dans un magasin de données volumineux et à faible coût.</span><span class="sxs-lookup"><span data-stu-id="58fc4-256">To control costs and not exceed data storage limits, log `Trace` and `Information` level messages to a high-volume, low-cost data store.</span></span> <span data-ttu-id="58fc4-257">Envisagez `Trace` de limiter et `Information` à des catégories spécifiques.</span><span class="sxs-lookup"><span data-stu-id="58fc4-257">Consider limiting `Trace` and `Information` to specific categories.</span></span>
  - <span data-ttu-id="58fc4-258">La journalisation au `Warning` `Critical` niveau des niveaux doit produire peu de messages de journal.</span><span class="sxs-lookup"><span data-stu-id="58fc4-258">Logging at `Warning` through `Critical` levels should produce few log messages.</span></span>
    - <span data-ttu-id="58fc4-259">Les coûts et les limites de stockage ne sont généralement pas un problème.</span><span class="sxs-lookup"><span data-stu-id="58fc4-259">Costs and storage limits usually aren't a concern.</span></span>
    - <span data-ttu-id="58fc4-260">Certains journaux offrent davantage de flexibilité dans les choix de magasins de données.</span><span class="sxs-lookup"><span data-stu-id="58fc4-260">Few logs allow more flexibility in data store choices.</span></span>
- <span data-ttu-id="58fc4-261">En cours de développement :</span><span class="sxs-lookup"><span data-stu-id="58fc4-261">In development:</span></span>
  - <span data-ttu-id="58fc4-262">Défini sur `Warning`.</span><span class="sxs-lookup"><span data-stu-id="58fc4-262">Set to `Warning`.</span></span>
  - <span data-ttu-id="58fc4-263">Ajoutez `Trace` `Information` des messages ou lors de la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="58fc4-263">Add `Trace` or `Information` messages when troubleshooting.</span></span> <span data-ttu-id="58fc4-264">Pour limiter la sortie, `Trace` la définition ou `Information` uniquement pour les catégories en cours d’investigation.</span><span class="sxs-lookup"><span data-stu-id="58fc4-264">To limit output, set `Trace` or `Information` only for the categories under investigation.</span></span>

<span data-ttu-id="58fc4-265">Le code JSON suivant définit `Logging:Console:LogLevel:Microsoft:Information` :</span><span class="sxs-lookup"><span data-stu-id="58fc4-265">The following JSON sets `Logging:Console:LogLevel:Microsoft:Information`:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.MSFT.json":::

## <a name="log-event-id"></a><span data-ttu-id="58fc4-266">ID d’événement de log</span><span class="sxs-lookup"><span data-stu-id="58fc4-266">Log event ID</span></span>

<span data-ttu-id="58fc4-267">Chaque journal peut spécifier un *identificateur d’événement*, le <xref:Microsoft.Extensions.Logging.EventId> est une structure avec un `Id` et des `Name` propriétés ReadOnly facultatives.</span><span class="sxs-lookup"><span data-stu-id="58fc4-267">Each log can specify an *event identifer*, the <xref:Microsoft.Extensions.Logging.EventId> is a structure with an `Id` and optional `Name` readonly properties.</span></span> <span data-ttu-id="58fc4-268">L’exemple de code source utilise la `AppLogEvents` classe pour définir les ID d’événement :</span><span class="sxs-lookup"><span data-stu-id="58fc4-268">The sample source code uses the `AppLogEvents` class to define event IDs:</span></span>

```csharp
internal static class AppLogEvents
{
    internal const int Create = 1000;
    internal const int Read = 1001;
    internal const int Update = 1002;
    internal const int Delete = 1003;

    internal const int Details = 3000;
    internal const int Error = 3001;

    internal const int ReadNotFound = 4000;
    internal const int UpdateNotFound = 4001;

    // ...
}
```

<span data-ttu-id="58fc4-269">Un ID d’événement associe un jeu d’événements.</span><span class="sxs-lookup"><span data-stu-id="58fc4-269">An event ID associates a set of events.</span></span> <span data-ttu-id="58fc4-270">Par exemple, tous les journaux liés à la lecture des valeurs d’un référentiel peuvent être `1001` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-270">For example, all logs related to reading values from a repository might be `1001`.</span></span>

<span data-ttu-id="58fc4-271">Le fournisseur de journalisation peut enregistrer l’ID d’événement dans un champ ID, dans le message de journalisation, ou pas du tout.</span><span class="sxs-lookup"><span data-stu-id="58fc4-271">The logging provider may log the event ID in an ID field, in the logging message, or not at all.</span></span> <span data-ttu-id="58fc4-272">Le fournisseur Debug n’affiche pas les ID d’événements.</span><span class="sxs-lookup"><span data-stu-id="58fc4-272">The Debug provider doesn't show event IDs.</span></span> <span data-ttu-id="58fc4-273">Le fournisseur Console affiche les ID d’événements entre crochets après la catégorie :</span><span class="sxs-lookup"><span data-stu-id="58fc4-273">The console provider shows event IDs in brackets after the category:</span></span>

```console
info: Example.DefaultService.GetAsync[1001]
      Reading value for a1b2c3
warn: Example.DefaultService.GetAsync[4000]
      GetAsync(a1b2c3) not found
```

<span data-ttu-id="58fc4-274">Certains fournisseurs de journalisation stockent l’ID d’événement dans un champ, ce qui permet de filtrer l’ID.</span><span class="sxs-lookup"><span data-stu-id="58fc4-274">Some logging providers store the event ID in a field, which allows for filtering on the ID.</span></span>

## <a name="log-message-template"></a><span data-ttu-id="58fc4-275">Modèle de message de journal</span><span class="sxs-lookup"><span data-stu-id="58fc4-275">Log message template</span></span>

<span data-ttu-id="58fc4-276">Chaque API de journal utilise un modèle de message.</span><span class="sxs-lookup"><span data-stu-id="58fc4-276">Each log API uses a message template.</span></span> <span data-ttu-id="58fc4-277">Ce dernier peut contenir des espaces réservés pour lesquels les arguments sont fournis.</span><span class="sxs-lookup"><span data-stu-id="58fc4-277">The message template can contain placeholders for which arguments are provided.</span></span> <span data-ttu-id="58fc4-278">Utilisez des noms et non des nombres pour les espaces réservés.</span><span class="sxs-lookup"><span data-stu-id="58fc4-278">Use names for the placeholders, not numbers.</span></span> <span data-ttu-id="58fc4-279">L’ordre des espaces réservés, pas leurs noms, détermine quels paramètres sont utilisés pour fournir leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="58fc4-279">The order of placeholders, not their names, determines which parameters are used to provide their values.</span></span> <span data-ttu-id="58fc4-280">Dans le code suivant, les noms de paramètres sont hors séquence dans le modèle de message :</span><span class="sxs-lookup"><span data-stu-id="58fc4-280">In the following code, the parameter names are out of sequence in the message template:</span></span>

```csharp
string p1 = "param1";
string p2 = "param2";
_logger.LogInformation("Parameter values: {p2}, {p1}", p1, p2);
```

<span data-ttu-id="58fc4-281">Le code précédent crée un message de journal avec les valeurs de paramètre dans l’ordre :</span><span class="sxs-lookup"><span data-stu-id="58fc4-281">The preceding code creates a log message with the parameter values in sequence:</span></span>

```text
Parameter values: param1, param2
```

<span data-ttu-id="58fc4-282">Cette approche permet aux fournisseurs de journalisation d’implémenter la [journalisation sémantique ou structurée](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging).</span><span class="sxs-lookup"><span data-stu-id="58fc4-282">This approach allows logging providers to implement [semantic or structured logging](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging).</span></span> <span data-ttu-id="58fc4-283">Les arguments proprement dits, et pas seulement le modèle de message mis en forme, sont transmis au système de journalisation.</span><span class="sxs-lookup"><span data-stu-id="58fc4-283">The arguments themselves are passed to the logging system, not just the formatted message template.</span></span> <span data-ttu-id="58fc4-284">Cela permet aux fournisseurs de journalisation de stocker les valeurs de paramètres en tant que champs.</span><span class="sxs-lookup"><span data-stu-id="58fc4-284">This enables logging providers to store the parameter values as fields.</span></span> <span data-ttu-id="58fc4-285">Examinez la méthode d’enregistreur d’événements suivante :</span><span class="sxs-lookup"><span data-stu-id="58fc4-285">Consider the following logger method:</span></span>

```csharp
_logger.LogInformation("Getting item {Id} at {RunTime}", id, DateTime.Now);
```

<span data-ttu-id="58fc4-286">Par exemple, lors de la journalisation dans le stockage table Azure :</span><span class="sxs-lookup"><span data-stu-id="58fc4-286">For example, when logging to Azure Table Storage:</span></span>

- <span data-ttu-id="58fc4-287">Chaque entité de table Azure peut avoir des `ID` `RunTime` Propriétés et.</span><span class="sxs-lookup"><span data-stu-id="58fc4-287">Each Azure Table entity can have `ID` and `RunTime` properties.</span></span>
- <span data-ttu-id="58fc4-288">Les tables avec des propriétés simplifient les requêtes sur les données journalisées.</span><span class="sxs-lookup"><span data-stu-id="58fc4-288">Tables with properties simplify queries on logged data.</span></span> <span data-ttu-id="58fc4-289">Par exemple, une requête peut trouver tous les journaux d’une `RunTime` plage donnée sans avoir à analyser le délai d’attente du message texte.</span><span class="sxs-lookup"><span data-stu-id="58fc4-289">For example, a query can find all logs within a particular `RunTime` range without having to parse the time out of the text message.</span></span>

## <a name="log-exceptions"></a><span data-ttu-id="58fc4-290">Journaliser les exceptions</span><span class="sxs-lookup"><span data-stu-id="58fc4-290">Log exceptions</span></span>

<span data-ttu-id="58fc4-291">Les méthodes d’enregistreur d’événements ont des surcharges qui prennent un paramètre d’exception :</span><span class="sxs-lookup"><span data-stu-id="58fc4-291">The logger methods have overloads that take an exception parameter:</span></span>

```csharp
public void Test(string id)
{
    try
    {
        if (id == "none")
        {
            throw new Exception("Default Id detected.");
        }
    }
    catch (Exception ex)
    {
        _logger.LogWarning(
            AppLogEvents.Error, ex,
            "Failed to process iteration: {Id}", id)
    }
}
```

<span data-ttu-id="58fc4-292">La journalisation des exceptions est spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-292">Exception logging is provider-specific.</span></span>

### <a name="default-log-level"></a><span data-ttu-id="58fc4-293">Niveau de journalisation par défaut</span><span class="sxs-lookup"><span data-stu-id="58fc4-293">Default log level</span></span>

<span data-ttu-id="58fc4-294">Si le niveau de journalisation par défaut n’est pas défini, la valeur par défaut du niveau de journal est `Information` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-294">If the default log level is not set, the default log level value is `Information`.</span></span>

<span data-ttu-id="58fc4-295">Par exemple, considérez l’application de service de travail suivante :</span><span class="sxs-lookup"><span data-stu-id="58fc4-295">For example, consider the following worker service app:</span></span>

- <span data-ttu-id="58fc4-296">Créé avec les modèles de travail .NET.</span><span class="sxs-lookup"><span data-stu-id="58fc4-296">Created with the .NET Worker templates.</span></span>
- <span data-ttu-id="58fc4-297">*appsettings.jssur* et *appsettings.Development.jssur* supprimé ou renommé.</span><span class="sxs-lookup"><span data-stu-id="58fc4-297">*appsettings.json* and *appsettings.Development.json* deleted or renamed.</span></span>

<span data-ttu-id="58fc4-298">Avec la configuration précédente, la navigation vers la page confidentialité ou d’origine génère de nombreux `Trace` `Debug` messages, et `Information`  avec `Microsoft` dans le nom de catégorie.</span><span class="sxs-lookup"><span data-stu-id="58fc4-298">With the preceding setup, navigating to the privacy or home page produces many `Trace`, `Debug`, and `Information`  messages with `Microsoft` in the category name.</span></span>

<span data-ttu-id="58fc4-299">Le code suivant définit le niveau de journalisation par défaut lorsque le niveau de journalisation par défaut n’est pas défini dans la configuration :</span><span class="sxs-lookup"><span data-stu-id="58fc4-299">The following code sets the default log level when the default log level is not set in configuration:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging => logging.SetMinimumLevel(LogLevel.Warning));
}
```

### <a name="filter-function"></a><span data-ttu-id="58fc4-300">fonction Filter</span><span class="sxs-lookup"><span data-stu-id="58fc4-300">Filter function</span></span>

<span data-ttu-id="58fc4-301">Une fonction de filtre est appelée pour tous les fournisseurs et toutes les catégories pour lesquels aucune règle n’est assignée par la configuration ou le code :</span><span class="sxs-lookup"><span data-stu-id="58fc4-301">A filter function is invoked for all providers and categories that don't have rules assigned to them by configuration or code:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddFilter((provider, category, logLevel) =>
                {
                    return provider.Contains("ConsoleLoggerProvider")
                        && (category.Contains("Example") || category.Contains("Microsoft"))
                        && logLevel >= LogLevel.Information;
                }));
}
```

<span data-ttu-id="58fc4-302">Le code précédent affiche les journaux de console lorsque la catégorie contient `Example` ou `Microsoft` et que le niveau de journal est `Information` ou supérieur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-302">The preceding code displays console logs when the category contains `Example` or `Microsoft` and the log level is `Information` or higher.</span></span>

## <a name="log-scopes"></a><span data-ttu-id="58fc4-303">Étendues de journal</span><span class="sxs-lookup"><span data-stu-id="58fc4-303">Log scopes</span></span>

 <span data-ttu-id="58fc4-304">Une *étendue* peut regrouper un ensemble d’opérations logiques.</span><span class="sxs-lookup"><span data-stu-id="58fc4-304">A *scope* can group a set of logical operations.</span></span> <span data-ttu-id="58fc4-305">Ce regroupement permet de joindre les mêmes données à tous les journaux créés au sein d’un ensemble.</span><span class="sxs-lookup"><span data-stu-id="58fc4-305">This grouping can be used to attach the same data to each log that's created as part of a set.</span></span> <span data-ttu-id="58fc4-306">Par exemple, chaque journal créé dans le cadre du traitement d’une transaction peut contenir l’ID de la transaction.</span><span class="sxs-lookup"><span data-stu-id="58fc4-306">For example, every log created as part of processing a transaction can include the transaction ID.</span></span>

<span data-ttu-id="58fc4-307">Une étendue :</span><span class="sxs-lookup"><span data-stu-id="58fc4-307">A scope:</span></span>

- <span data-ttu-id="58fc4-308">Est un <xref:System.IDisposable> type qui est retourné par la <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="58fc4-308">Is an <xref:System.IDisposable> type that's returned by the <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> method.</span></span>
- <span data-ttu-id="58fc4-309">Dure jusqu’à ce qu’il soit supprimé.</span><span class="sxs-lookup"><span data-stu-id="58fc4-309">Lasts until it's disposed.</span></span>

<span data-ttu-id="58fc4-310">Les fournisseurs suivants prennent en charge les étendues :</span><span class="sxs-lookup"><span data-stu-id="58fc4-310">The following providers support scopes:</span></span>

- `Console`
- [<span data-ttu-id="58fc4-311">AzureAppServicesFile et AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="58fc4-311">AzureAppServicesFile and AzureAppServicesBlob</span></span>](xref:Microsoft.Extensions.Logging.AzureAppServices.BatchingLoggerOptions.IncludeScopes)

<span data-ttu-id="58fc4-312">Utilisez une étendue en incluant les appels de l’enregistrement d’événements dans un bloc `using` :</span><span class="sxs-lookup"><span data-stu-id="58fc4-312">Use a scope by wrapping logger calls in a `using` block:</span></span>

```csharp
public async Task<T> GetAsync<T>(string id)
{
    T result;

    using (_logger.BeginScope("using block message"))
    {
        _logger.LogInformation(
            AppLogEvents.Read, "Reading value for {Id}", id);

        var result = await _repository.GetAsync(id);
        if (result is null)
        {
            _logger.LogWarning(
                AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
        }
    }

    return result;
}
```

<span data-ttu-id="58fc4-313">Le code JSON suivant active des étendues pour le fournisseur de console :</span><span class="sxs-lookup"><span data-stu-id="58fc4-313">The following JSON enables scopes for the console provider:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.IncludeScopes.json" highlight="9":::

<span data-ttu-id="58fc4-314">Le code suivant active les étendues pour le fournisseur Console :</span><span class="sxs-lookup"><span data-stu-id="58fc4-314">The following code enables scopes for the console provider:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging((_, logging) =>
                logging.ClearProviders()
                    .AddConsole(options => options.IncludeScopes = true));
}
```

## <a name="non-host-console-app"></a><span data-ttu-id="58fc4-315">Application console non-hôte</span><span class="sxs-lookup"><span data-stu-id="58fc4-315">Non-host console app</span></span>

<span data-ttu-id="58fc4-316">La journalisation du code pour les applications sans [hôte générique](generic-host.md) diffère dans la façon dont les [fournisseurs sont ajoutés](#add-providers) et les [journaux sont créés](#create-logs).</span><span class="sxs-lookup"><span data-stu-id="58fc4-316">Logging code for apps without a [Generic Host](generic-host.md) differs in the way [providers are added](#add-providers) and [loggers are created](#create-logs).</span></span> <span data-ttu-id="58fc4-317">Dans une application de console non hôte, appelez la méthode d’extension `Add{provider name}` du fournisseur lors de la création d’un `LoggerFactory` :</span><span class="sxs-lookup"><span data-stu-id="58fc4-317">In a non-host console app, call the provider's `Add{provider name}` extension method while creating a `LoggerFactory`:</span></span>

```csharp
class Program
{
    static void Main(string[] args)
    {
        using var loggerFactory = LoggerFactory.Create(builder =>
        {
            builder
                .AddFilter("Microsoft", LogLevel.Warning)
                .AddFilter("System", LogLevel.Warning)
                .AddFilter("LoggingConsoleApp.Program", LogLevel.Debug)
                .AddConsole();
        });

        ILogger logger = loggerFactory.CreateLogger<Program>();
        logger.LogInformation("Example log message");
    }
}
```

<span data-ttu-id="58fc4-318">L' `loggerFactory` objet est utilisé pour créer une <xref:Microsoft.Extensions.Logging.ILogger> instance.</span><span class="sxs-lookup"><span data-stu-id="58fc4-318">The `loggerFactory` object is used to create an <xref:Microsoft.Extensions.Logging.ILogger> instance.</span></span>

## <a name="create-logs-in-main"></a><span data-ttu-id="58fc4-319">Créer des journaux dans main</span><span class="sxs-lookup"><span data-stu-id="58fc4-319">Create logs in Main</span></span>

<span data-ttu-id="58fc4-320">Le code suivant se connecte `Main` en obtenant une `ILogger` instance à partir de di après avoir généré l’hôte :</span><span class="sxs-lookup"><span data-stu-id="58fc4-320">The following code logs in `Main` by getting an `ILogger` instance from DI after building the host:</span></span>

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

class Program
{
    static Task Main(string[] args)
    {
        IHost host = Host.CreateDefaultBuilder(args).Build();

        var logger = host.Services.GetRequiredService<ILogger<Program>>();
        logger.LogInformation("Host created.");

        return host.RunAsync();
    }
}
```

### <a name="no-asynchronous-logger-methods"></a><span data-ttu-id="58fc4-321">Aucune méthode d’enregistreur d’événements asynchrone</span><span class="sxs-lookup"><span data-stu-id="58fc4-321">No asynchronous logger methods</span></span>

<span data-ttu-id="58fc4-322">La journalisation doit être suffisamment rapide par rapport au coût du code asynchrone en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="58fc4-322">Logging should be so fast that it isn't worth the performance cost of asynchronous code.</span></span> <span data-ttu-id="58fc4-323">Si un magasin de données de journalisation est lent, n’écrivez pas directement dessus.</span><span class="sxs-lookup"><span data-stu-id="58fc4-323">If a logging data store is slow, don't write to it directly.</span></span> <span data-ttu-id="58fc4-324">Envisagez d’écrire les messages du journal dans un magasin rapide, puis de les déplacer ultérieurement vers la Banque lente.</span><span class="sxs-lookup"><span data-stu-id="58fc4-324">Consider writing the log messages to a fast store initially, then moving them to the slow store later.</span></span> <span data-ttu-id="58fc4-325">Par exemple, lorsque vous vous connectez à SQL Server, ne le faites pas directement dans une `Log` méthode, puisque les `Log` méthodes sont synchrones.</span><span class="sxs-lookup"><span data-stu-id="58fc4-325">For example, when logging to SQL Server, don't do so directly in a `Log` method, since the `Log` methods are synchronous.</span></span> <span data-ttu-id="58fc4-326">Ajoutez plutôt de façon synchronisée des messages de journal à une file d’attente en mémoire, puis configurez un traitement en arrière-plan afin d’extraire les messages de la file d’attente et d’effectuer le travail asynchrone d’envoi des données vers SQL Server.</span><span class="sxs-lookup"><span data-stu-id="58fc4-326">Instead, synchronously add log messages to an in-memory queue and have a background worker pull the messages out of the queue to do the asynchronous work of pushing data to SQL Server.</span></span>

## <a name="change-log-levels-in-a-running-app"></a><span data-ttu-id="58fc4-327">Modifier les niveaux de journal dans une application en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="58fc4-327">Change log levels in a running app</span></span>

<span data-ttu-id="58fc4-328">L’API de journalisation n’inclut pas de scénario pour modifier les niveaux de journal lorsqu’une application est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="58fc4-328">The Logging API doesn't include a scenario to change log levels while an app is running.</span></span> <span data-ttu-id="58fc4-329">Toutefois, certains fournisseurs de configuration sont en charge du rechargement de la configuration, ce qui prend immédiatement effet sur la configuration de la journalisation.</span><span class="sxs-lookup"><span data-stu-id="58fc4-329">However, some configuration providers are capable of reloading configuration, which takes immediate effect on logging configuration.</span></span> <span data-ttu-id="58fc4-330">Par exemple, le [fournisseur de configuration de fichier](configuration-providers.md#file-configuration-provider) recharge la configuration de journalisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="58fc4-330">For example, the [File Configuration Provider](configuration-providers.md#file-configuration-provider) reloads logging configuration by default.</span></span> <span data-ttu-id="58fc4-331">Si la configuration est modifiée dans le code pendant qu’une application est en cours d’exécution, l’application peut appeler [IConfigurationRoot. Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) pour mettre à jour la configuration de journalisation de l’application.</span><span class="sxs-lookup"><span data-stu-id="58fc4-331">If configuration is changed in code while an app is running, the app can call [IConfigurationRoot.Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) to update the app's logging configuration.</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="58fc4-332">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="58fc4-332">NuGet packages</span></span>

<span data-ttu-id="58fc4-333">Les <xref:Microsoft.Extensions.Logging.ILogger%601> <xref:Microsoft.Extensions.Logging.ILoggerFactory> interfaces et et les implémentations sont incluses dans la kit SDK .net core.</span><span class="sxs-lookup"><span data-stu-id="58fc4-333">The <xref:Microsoft.Extensions.Logging.ILogger%601> and <xref:Microsoft.Extensions.Logging.ILoggerFactory> interfaces and implementations are included in the .NET Core SDK.</span></span> <span data-ttu-id="58fc4-334">Ils sont également disponibles dans les packages NuGet suivants :</span><span class="sxs-lookup"><span data-stu-id="58fc4-334">They are also available in the following NuGet packages:</span></span>

- <span data-ttu-id="58fc4-335">Les interfaces se trouvent dans [Microsoft. extensions. Logging. Abstracts](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions).</span><span class="sxs-lookup"><span data-stu-id="58fc4-335">The interfaces are in [Microsoft.Extensions.Logging.Abstractions](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions).</span></span>
- <span data-ttu-id="58fc4-336">Les implémentations par défaut se trouvent dans [Microsoft. extensions. Logging](https://www.nuget.org/packages/microsoft.extensions.logging).</span><span class="sxs-lookup"><span data-stu-id="58fc4-336">The default implementations are in [Microsoft.Extensions.Logging](https://www.nuget.org/packages/microsoft.extensions.logging).</span></span>

## <a name="apply-log-filter-rules-in-code"></a><span data-ttu-id="58fc4-337">Appliquer les règles de filtre de journal dans le code</span><span class="sxs-lookup"><span data-stu-id="58fc4-337">Apply log filter rules in code</span></span>

<span data-ttu-id="58fc4-338">L’approche recommandée pour définir des règles de filtre de journal consiste à utiliser la [configuration](configuration.md).</span><span class="sxs-lookup"><span data-stu-id="58fc4-338">The preferred approach for setting log filter rules is by using [Configuration](configuration.md).</span></span>

<span data-ttu-id="58fc4-339">L'exemple suivant montre comment enregistrer des règles de filtre dans le code :</span><span class="sxs-lookup"><span data-stu-id="58fc4-339">The following example shows how to register filter rules in code:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
               logging.AddFilter("System", LogLevel.Debug)
                  .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)
                  .AddFilter<ConsoleLoggerProvider>("Microsoft", LogLevel.Trace));
}
```

<span data-ttu-id="58fc4-340">`logging.AddFilter("System", LogLevel.Debug)` spécifie la `System` catégorie et le niveau de journalisation `Debug` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-340">`logging.AddFilter("System", LogLevel.Debug)` specifies the `System` category and log level `Debug`.</span></span> <span data-ttu-id="58fc4-341">Le filtre est appliqué à tous les fournisseurs, car un fournisseur spécifique n’a pas été configuré.</span><span class="sxs-lookup"><span data-stu-id="58fc4-341">The filter is applied to all providers because a specific provider was not configured.</span></span>

<span data-ttu-id="58fc4-342">`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` indiquant</span><span class="sxs-lookup"><span data-stu-id="58fc4-342">`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` specifies:</span></span>

- <span data-ttu-id="58fc4-343">`Debug`Fournisseur de journalisation.</span><span class="sxs-lookup"><span data-stu-id="58fc4-343">The `Debug` logging provider.</span></span>
- <span data-ttu-id="58fc4-344">Niveau de journalisation `Information` et supérieur.</span><span class="sxs-lookup"><span data-stu-id="58fc4-344">Log level `Information` and higher.</span></span>
- <span data-ttu-id="58fc4-345">Toutes les catégories commençant par `"Microsoft"` .</span><span class="sxs-lookup"><span data-stu-id="58fc4-345">All categories starting with `"Microsoft"`.</span></span>

## <a name="see-also"></a><span data-ttu-id="58fc4-346">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58fc4-346">See also</span></span>

- [<span data-ttu-id="58fc4-347">Fournisseurs de journalisation dans .NET</span><span class="sxs-lookup"><span data-stu-id="58fc4-347">Logging providers in .NET</span></span>](logging-providers.md)
- [<span data-ttu-id="58fc4-348">Implémenter un fournisseur de journalisation personnalisé dans .NET</span><span class="sxs-lookup"><span data-stu-id="58fc4-348">Implement a custom logging provider in .NET</span></span>](custom-logging-provider.md)
- [<span data-ttu-id="58fc4-349">Journalisation hautes performances dans .NET</span><span class="sxs-lookup"><span data-stu-id="58fc4-349">High-performance logging in .NET</span></span>](high-performance-logging.md)
- <span data-ttu-id="58fc4-350">Les bogues de journalisation doivent être créés dans [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) référentiel</span><span class="sxs-lookup"><span data-stu-id="58fc4-350">Logging bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
