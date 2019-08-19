---
title: Collecte des données de télémétrie par la CLI ML.NET
description: Découvrez les fonctionnalités de télémétrie de la CLI ML.NET, qui collectent des informations d’utilisation à des fins d’analyse, les types de données collectées et comment désactiver la télémétrie. En outre, vous trouverez des liens vers le contrat de licence de .NET et des informations sur la conformité de Microsoft au RGPD.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: b9f6ccf7ff76f0cf4ce806f39909b7607a20b9f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567493"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="23713-104">Collecte des données de télémétrie par la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="23713-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="23713-105">La [CLI ML.NET](https://aka.ms/mlnet-cli) inclut une fonctionnalité de télémétrie qui collecte les données d’utilisation anonymes, qui sont agrégées en vue d’une utilisation par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="23713-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="23713-106">Comment Microsoft utilise les données</span><span class="sxs-lookup"><span data-stu-id="23713-106">How Microsoft uses the data</span></span>

<span data-ttu-id="23713-107">L’équipe de produit utilise les données de télémétrie collectées par la CLI ML.NET pour essayer de comprendre comment améliorer les outils.</span><span class="sxs-lookup"><span data-stu-id="23713-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="23713-108">Par exemple, si les clients utilisent rarement une tâche de machine learning spécifique, l’équipe de produit en analyse la raison, puis hiérarchise le développement des fonctionnalités à partir des conclusions qu’elle a tirées.</span><span class="sxs-lookup"><span data-stu-id="23713-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="23713-109">En outre, les données de télémétrie collectées par la CLI ML.NET facilitent le débogage des problèmes tels que les plantages et les anomalies de code.</span><span class="sxs-lookup"><span data-stu-id="23713-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="23713-110">Bien que l’équipe de produit apprécie cet insight, nous savons également que tout le monde n’est pas disposé à envoyer ces données.</span><span class="sxs-lookup"><span data-stu-id="23713-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="23713-111">Découvrez comment désactiver la télémétrie.</span><span class="sxs-lookup"><span data-stu-id="23713-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="23713-112">Portée</span><span class="sxs-lookup"><span data-stu-id="23713-112">Scope</span></span>

<span data-ttu-id="23713-113">La commande `mlnet` lance l’interface CLI ML.NET, mais ne collecte pas elle-même les données de télémétrie.</span><span class="sxs-lookup"><span data-stu-id="23713-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="23713-114">La télémétrie *n’est pas activée* quand vous exécutez la commande `mlnet` sans aucune autre commande attachée.</span><span class="sxs-lookup"><span data-stu-id="23713-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="23713-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="23713-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="23713-116">La télémétrie *est activée* quand vous exécutez une [commande CLI ML.NET](../reference/ml-net-cli-reference.md), telle que `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="23713-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="23713-117">Refuser la collecte de données</span><span class="sxs-lookup"><span data-stu-id="23713-117">Opt out of data collection</span></span>

<span data-ttu-id="23713-118">La fonctionnalité de télémétrie de la CLI ML.NET est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="23713-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="23713-119">Pour la désactiver, affectez la valeur `1` ou `true` à la variable d’environnement `MLDOTNET_CLI_TELEMETRY_OPTOUT`.</span><span class="sxs-lookup"><span data-stu-id="23713-119">Opt out of the telemetry feature by setting the `MLDOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="23713-120">Cette variable d’environnement s’applique globalement à l’outil CLI .NET.</span><span class="sxs-lookup"><span data-stu-id="23713-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="23713-121">Points de données collectés</span><span class="sxs-lookup"><span data-stu-id="23713-121">Data points collected</span></span>

<span data-ttu-id="23713-122">La fonctionnalité recueille les données suivantes :</span><span class="sxs-lookup"><span data-stu-id="23713-122">The feature collects the following data:</span></span>

- <span data-ttu-id="23713-123">Des commandes ont été appelées, comme `auto-train`</span><span class="sxs-lookup"><span data-stu-id="23713-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="23713-124">Noms de paramètres de ligne de commande utilisés (par exemple, « dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity »)</span><span class="sxs-lookup"><span data-stu-id="23713-124">Command-line parameter names used (i.e. "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="23713-125">Adresse MAC hachée : ID unique et anonyme chiffré (SHA256) pour une machine</span><span class="sxs-lookup"><span data-stu-id="23713-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="23713-126">Horodatage d’un appel</span><span class="sxs-lookup"><span data-stu-id="23713-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="23713-127">Adresse IP de trois octets (non complète) utilisée uniquement pour déterminer l’emplacement géographique</span><span class="sxs-lookup"><span data-stu-id="23713-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="23713-128">Nom de tous les arguments/paramètres utilisés.</span><span class="sxs-lookup"><span data-stu-id="23713-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="23713-129">Pas les valeurs du client, telles que des chaînes.</span><span class="sxs-lookup"><span data-stu-id="23713-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="23713-130">Nom de fichier de jeu de données haché</span><span class="sxs-lookup"><span data-stu-id="23713-130">Hashed dataset filename</span></span>
- <span data-ttu-id="23713-131">Compartiment de taille de fichier de jeu de données</span><span class="sxs-lookup"><span data-stu-id="23713-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="23713-132">Système d’exploitation et version</span><span class="sxs-lookup"><span data-stu-id="23713-132">Operating system and version</span></span>
- <span data-ttu-id="23713-133">Valeur du paramètre --task : valeurs de catégorie, telles que `regression`, `binary-classification` et `multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="23713-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="23713-134">Version de CLI ML.NET (par exemple, 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="23713-134">ML.NET CLI version (i.e. 0.3.27703.4)</span></span>

<span data-ttu-id="23713-135">Les données sont envoyées de manière sécurisée à des serveurs Microsoft à l’aide de la technologie [Azure Application Insights](https://azure.microsoft.com/services/application-insights/), stockées à un emplacement dont l’accès est strictement limité et utilisées conformément à des contrôles de sécurité stricts à partir de systèmes [Stockage Azure](https://azure.microsoft.com/services/storage/) sécurisés.</span><span class="sxs-lookup"><span data-stu-id="23713-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="23713-136">Points de données non collectés</span><span class="sxs-lookup"><span data-stu-id="23713-136">Data points not collected</span></span>
<span data-ttu-id="23713-137">La fonctionnalité de télémétrie *ne collecte pas* les données suivantes :</span><span class="sxs-lookup"><span data-stu-id="23713-137">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="23713-138">Données personnelles, telles que les noms d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="23713-138">personal data, such as usernames</span></span>
- <span data-ttu-id="23713-139">Noms de fichier de jeu de données</span><span class="sxs-lookup"><span data-stu-id="23713-139">dataset filenames</span></span>
- <span data-ttu-id="23713-140">Données des fichiers de jeu de données</span><span class="sxs-lookup"><span data-stu-id="23713-140">data from dataset files</span></span>

<span data-ttu-id="23713-141">Si vous pensez que la fonctionnalité de télémétrie de la CLI ML.NET collecte des données sensibles ou que les données sont gérées de manière non sécurisée ou incorrecte, soumettez un problème dans le dépôt [ML.NET](https://github.com/dotnet/machinelearning) afin que nous investiguions.</span><span class="sxs-lookup"><span data-stu-id="23713-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="23713-142">Licence</span><span class="sxs-lookup"><span data-stu-id="23713-142">License</span></span>

<span data-ttu-id="23713-143">La distribution Microsoft de la CLI ML.NET est concédée sous licence avec les [Termes du contrat de licence logicielle Microsoft : bibliothèque Microsoft .NET](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="23713-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="23713-144">Pour plus d’informations sur la collecte et le traitement de données, consultez la section intitulée « Données ».</span><span class="sxs-lookup"><span data-stu-id="23713-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="23713-145">Divulgation d’informations</span><span class="sxs-lookup"><span data-stu-id="23713-145">Disclosure</span></span>

<span data-ttu-id="23713-146">Quand vous exécutez pour la première fois une [commande de la CLI ML.NET](../reference/ml-net-cli-reference.md) telle que `mlnet auto-train`, l’outil CLI ML.NET affiche un texte de divulgation qui vous indique comment refuser la télémétrie.</span><span class="sxs-lookup"><span data-stu-id="23713-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="23713-147">Le texte peut varier légèrement selon la version de la CLI que vous exécutez.</span><span class="sxs-lookup"><span data-stu-id="23713-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="23713-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23713-148">See also</span></span>
- [<span data-ttu-id="23713-149">Informations de référence sur l’interface de ligne de commande ML.NET</span><span class="sxs-lookup"><span data-stu-id="23713-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="23713-150">Termes du contrat de licence logiciel Microsoft : bibliothèque Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="23713-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="23713-151">Confidentialité chez Microsoft</span><span class="sxs-lookup"><span data-stu-id="23713-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="23713-152">Déclaration de confidentialité Microsoft</span><span class="sxs-lookup"><span data-stu-id="23713-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
