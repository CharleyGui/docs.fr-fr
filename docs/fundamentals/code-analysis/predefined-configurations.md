---
title: Fichiers de configuration prédéfinis (analyse du code)
description: En savoir plus sur l’utilisation de fichiers editorconfig et d’ensembles de règles prédéfinis pour cibler des types spécifiques d’analyse du code.
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "96587690"
---
# <a name="predefined-configuration-files"></a><span data-ttu-id="8a6c9-103">Fichiers de configuration prédéfinis</span><span class="sxs-lookup"><span data-stu-id="8a6c9-103">Predefined configuration files</span></span>

<span data-ttu-id="8a6c9-104">Des fichiers EditorConfig et des [ensembles de règles](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) prédéfinis sont disponibles, ce qui vous permet d’activer rapidement et facilement une catégorie de règles de qualité du code, telles que des règles de sécurité ou de conception.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-104">Predefined EditorConfig and [rule set](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) files are available that make it quick and easy to enable a category of code quality rules, such as security or design rules.</span></span> <span data-ttu-id="8a6c9-105">En activant une catégorie spécifique de règles, vous pouvez identifier des problèmes ciblés et des conditions spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-105">By enabling a specific category of rules, you can identify targeted issues and specific conditions.</span></span> <span data-ttu-id="8a6c9-106">Pour accéder à ces fichiers prédéfinis, installez le package de l’analyseur NuGet [Microsoft. CodeAnalysis. netanalyzer](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) .</span><span class="sxs-lookup"><span data-stu-id="8a6c9-106">To access these predefined files, install the [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer package.</span></span>

<span data-ttu-id="8a6c9-107">[Microsoft. CodeAnalysis. Netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) comprend des fichiers EditorConfig prédéfinis et des ensembles de règles pour les catégories de règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a6c9-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) includes predefined EditorConfig files and rule sets for the following rule categories:</span></span>

- <span data-ttu-id="8a6c9-108">Toutes les règles</span><span class="sxs-lookup"><span data-stu-id="8a6c9-108">All rules</span></span>
- <span data-ttu-id="8a6c9-109">Dataflow</span><span class="sxs-lookup"><span data-stu-id="8a6c9-109">Dataflow</span></span>
- <span data-ttu-id="8a6c9-110">Conception</span><span class="sxs-lookup"><span data-stu-id="8a6c9-110">Design</span></span>
- <span data-ttu-id="8a6c9-111">Documentation</span><span class="sxs-lookup"><span data-stu-id="8a6c9-111">Documentation</span></span>
- <span data-ttu-id="8a6c9-112">Globalisation</span><span class="sxs-lookup"><span data-stu-id="8a6c9-112">Globalization</span></span>
- <span data-ttu-id="8a6c9-113">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="8a6c9-113">Interoperability</span></span>
- <span data-ttu-id="8a6c9-114">Maintenabilité</span><span class="sxs-lookup"><span data-stu-id="8a6c9-114">Maintainability</span></span>
- <span data-ttu-id="8a6c9-115">Dénomination</span><span class="sxs-lookup"><span data-stu-id="8a6c9-115">Naming</span></span>
- <span data-ttu-id="8a6c9-116">Performances</span><span class="sxs-lookup"><span data-stu-id="8a6c9-116">Performance</span></span>
- <span data-ttu-id="8a6c9-117">Porté depuis FxCop</span><span class="sxs-lookup"><span data-stu-id="8a6c9-117">Ported from FxCop</span></span>
- <span data-ttu-id="8a6c9-118">Fiabilité</span><span class="sxs-lookup"><span data-stu-id="8a6c9-118">Reliability</span></span>
- <span data-ttu-id="8a6c9-119">Sécurité</span><span class="sxs-lookup"><span data-stu-id="8a6c9-119">Security</span></span>
- <span data-ttu-id="8a6c9-120">Usage</span><span class="sxs-lookup"><span data-stu-id="8a6c9-120">Usage</span></span>

<span data-ttu-id="8a6c9-121">Chacune de ces catégories de règles a un fichier de EditorConfig ou d’ensemble de règles pour :</span><span class="sxs-lookup"><span data-stu-id="8a6c9-121">Each of those categories of rules has an EditorConfig or rule set file to:</span></span>

- <span data-ttu-id="8a6c9-122">Activer toutes les règles de la catégorie (et désactiver toutes les autres règles)</span><span class="sxs-lookup"><span data-stu-id="8a6c9-122">Enable all the rules in the category (and disable all other rules)</span></span>
- <span data-ttu-id="8a6c9-123">Utilisez la gravité par défaut de chaque règle et activez le paramètre par défaut (et désactivez toutes les autres règles).</span><span class="sxs-lookup"><span data-stu-id="8a6c9-123">Use each rule's default severity and enabled by default setting (and disable all other rules)</span></span>

> [!TIP]
> <span data-ttu-id="8a6c9-124">La catégorie « toutes les règles » dispose d’un EditorConfig ou d’un fichier d’ensemble de règles supplémentaire pour désactiver toutes les règles.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-124">The "all rules" category has an additional EditorConfig or rule set file to disable all rules.</span></span> <span data-ttu-id="8a6c9-125">Utilisez ce fichier pour supprimer rapidement les avertissements ou erreurs de l’analyseur dans un projet.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-125">Use this file to quickly get rid of any analyzer warnings or errors in a project.</span></span>

## <a name="predefined-editorconfig-files"></a><span data-ttu-id="8a6c9-126">Fichiers EditorConfig prédéfinis</span><span class="sxs-lookup"><span data-stu-id="8a6c9-126">Predefined EditorConfig files</span></span>

<span data-ttu-id="8a6c9-127">Les fichiers EditorConfig prédéfinis pour le package de l’analyseur Microsoft. CodeAnalysis. netanalyzer se trouvent dans le sous-répertoire *EditorConfig* de l’emplacement où le package NuGet a été installé.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-127">The predefined EditorConfig files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *editorconfig* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="8a6c9-128">Par exemple, le fichier EditorConfig pour activer toutes les règles de sécurité se trouve à l’emplacement suivant : *EditorConfig/SecurityRulesEnabled/. EditorConfig*.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-128">For example, the EditorConfig file to enable all security rules is located at *editorconfig/SecurityRulesEnabled/.editorconfig*.</span></span>

<span data-ttu-id="8a6c9-129">Copiez le fichier *. editorconfig* choisi dans le répertoire racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-129">Copy the chosen *.editorconfig* file to your project's root directory.</span></span>

## <a name="predefined-rule-sets"></a><span data-ttu-id="8a6c9-130">Ensembles de règles prédéfinis</span><span class="sxs-lookup"><span data-stu-id="8a6c9-130">Predefined rule sets</span></span>

<span data-ttu-id="8a6c9-131">Les fichiers d’ensemble de règles prédéfinis pour le package de l’analyseur Microsoft. CodeAnalysis. netanalyzer sont situés *dans le sous* -répertoire RuleSet de où le package NuGet a été installé.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-131">The predefined rule set files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *rulesets* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="8a6c9-132">Par exemple, le fichier d’ensemble de règles permettant d’activer toutes les règles de sécurité se trouve dans *RuleSet/SecurityRulesEnabled. RuleSet*.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-132">For example, the rule set file to enable all security rules is located at *rulesets/SecurityRulesEnabled.ruleset*.</span></span> <span data-ttu-id="8a6c9-133">Copiez un ou plusieurs ensembles de règles et collez-les dans le répertoire qui contient votre projet.</span><span class="sxs-lookup"><span data-stu-id="8a6c9-133">Copy one or more of the rule sets and paste them in the directory that contains your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a6c9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a6c9-134">See also</span></span>

- [<span data-ttu-id="8a6c9-135">Configuration des analyseurs</span><span class="sxs-lookup"><span data-stu-id="8a6c9-135">Analyzer configuration</span></span>](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [<span data-ttu-id="8a6c9-136">Options de règle de style de code .NET pour EditorConfig</span><span class="sxs-lookup"><span data-stu-id="8a6c9-136">.NET code style rule options for EditorConfig</span></span>](code-style-rule-options.md)
