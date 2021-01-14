---
title: Propriétés AssemblyInfo
description: En savoir plus sur les attributs d’assembly et leur correspondance avec les propriétés MSBuild dans .NET Core 2,1 et versions ultérieures.
ms.topic: reference
ms.date: 01/08/2021
ms.openlocfilehash: a2c431b3fe3da428f21582624ca5f357887e2815
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192889"
---
# <a name="map-assemblyinfo-attributes-to-properties"></a><span data-ttu-id="731cb-103">Mapper les attributs AssemblyInfo aux propriétés</span><span class="sxs-lookup"><span data-stu-id="731cb-103">Map AssemblyInfo attributes to properties</span></span>

<span data-ttu-id="731cb-104">Les [attributs d’assembly](../../standard/assembly/set-attributes.md) qui étaient généralement présents dans un fichier *AssemblyInfo* dans .net Core 2,0 et les versions antérieures sont générés automatiquement à partir des propriétés MSBuild, à partir de .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="731cb-104">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file in .NET Core 2.0 and earlier versions are automatically generated from MSBuild properties, starting in .NET Core 2.1.</span></span>

## <a name="properties-per-attribute"></a><span data-ttu-id="731cb-105">Propriétés par attribut</span><span class="sxs-lookup"><span data-stu-id="731cb-105">Properties per attribute</span></span>

<span data-ttu-id="731cb-106">Comme indiqué dans le tableau suivant, chaque attribut a une propriété correspondante qui contrôle son contenu et un autre qui désactive sa génération :</span><span class="sxs-lookup"><span data-stu-id="731cb-106">As shown in the following table, each attribute has a corresponding property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="731cb-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="731cb-107">Attribute</span></span>                                                      | <span data-ttu-id="731cb-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="731cb-108">Property</span></span>               | <span data-ttu-id="731cb-109">Propriété permettant de désactiver</span><span class="sxs-lookup"><span data-stu-id="731cb-109">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="731cb-110">Remarques :</span><span class="sxs-lookup"><span data-stu-id="731cb-110">Notes:</span></span>

- <span data-ttu-id="731cb-111">`AssemblyVersion` et `FileVersion` la valeur par défaut `$(Version)` sans le suffixe.</span><span class="sxs-lookup"><span data-stu-id="731cb-111">`AssemblyVersion` and `FileVersion` default to the value of `$(Version)` without the suffix.</span></span> <span data-ttu-id="731cb-112">Par exemple, si `$(Version)` est `1.2.3-beta.4`, alors la valeur serait `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="731cb-112">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="731cb-113">`InformationalVersion` utilise par défaut la valeur de `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="731cb-113">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="731cb-114">Si la `$(SourceRevisionId)` propriété est présente, elle est ajoutée à `InformationalVersion` .</span><span class="sxs-lookup"><span data-stu-id="731cb-114">If the `$(SourceRevisionId)` property is present, it's appended to `InformationalVersion`.</span></span> <span data-ttu-id="731cb-115">Vous pouvez désactiver ce comportement à l’aide de `IncludeSourceRevisionInInformationalVersion` .</span><span class="sxs-lookup"><span data-stu-id="731cb-115">You can disable this behavior using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="731cb-116">Les propriétés `Copyright` et `Description` sont également utilisées pour les métadonnées NuGet.</span><span class="sxs-lookup"><span data-stu-id="731cb-116">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="731cb-117">`Configuration`, dont la valeur par défaut `Debug` est, est partagé avec toutes les cibles MSBuild.</span><span class="sxs-lookup"><span data-stu-id="731cb-117">`Configuration`, which defaults to `Debug`, is shared with all MSBuild targets.</span></span> <span data-ttu-id="731cb-118">Vous pouvez le définir par le biais `--configuration` de l’option des `dotnet` commandes, par exemple, [dotnet Pack](../tools/dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="731cb-118">You can set it via the `--configuration` option of `dotnet` commands, for example, [dotnet pack](../tools/dotnet-pack.md).</span></span>

## <a name="generateassemblyinfo"></a><span data-ttu-id="731cb-119">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="731cb-119">GenerateAssemblyInfo</span></span>

<span data-ttu-id="731cb-120">Valeur booléenne qui active ou désactive la génération de AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="731cb-120">A Boolean that enables or disables the AssemblyInfo generation.</span></span> <span data-ttu-id="731cb-121">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="731cb-121">The default value is `true`.</span></span>

## <a name="generatedassemblyinfofile"></a><span data-ttu-id="731cb-122">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="731cb-122">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="731cb-123">Chemin d’accès relatif ou absolu du fichier d’informations de l’assembly généré.</span><span class="sxs-lookup"><span data-stu-id="731cb-123">The relative or absolute path of the generated assembly info file.</span></span> <span data-ttu-id="731cb-124">La valeur par défaut est un fichier nommé *[Project-Name]. AssemblyInfo. [CS | VB]* dans le `$(IntermediateOutputPath)` répertoire (*obj*).</span><span class="sxs-lookup"><span data-stu-id="731cb-124">Defaults to a file named *[project-name].AssemblyInfo.[cs|vb]* in the `$(IntermediateOutputPath)` (*obj*) directory.</span></span>
