---
title: Options de suppression
description: Découvrez comment contrôler le découpage des applications autonomes.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: 5597d4cdb9e8e96dcec6545e039d43295ca991bd
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142256"
---
# <a name="trimming-options"></a><span data-ttu-id="f09f0-103">Options de suppression</span><span class="sxs-lookup"><span data-stu-id="f09f0-103">Trimming options</span></span>

<span data-ttu-id="f09f0-104">Les propriétés et les éléments MSBuild suivants influencent le comportement des [déploiements autonomes tronqués](trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="f09f0-104">The following MSBuild properties and items influence the behavior of [trimmed self-contained deployments](trim-self-contained.md).</span></span> <span data-ttu-id="f09f0-105">Certaines des options mentionnent `ILLink` , qui est le nom de l’outil sous-jacent qui implémente la suppression.</span><span class="sxs-lookup"><span data-stu-id="f09f0-105">Some of the options mention `ILLink`, which is the name of the underlying tool that implements trimming.</span></span> <span data-ttu-id="f09f0-106">Pour plus d’informations sur l' `ILLink` outil en ligne de commande, consultez [options de illink](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span><span class="sxs-lookup"><span data-stu-id="f09f0-106">More information about the `ILLink` command-line tool can be found at [illink options](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

## <a name="enable-trimming"></a><span data-ttu-id="f09f0-107">Activer la suppression</span><span class="sxs-lookup"><span data-stu-id="f09f0-107">Enable trimming</span></span>

- `<PublishTrimmed>true</PublishTrimmed>`

   <span data-ttu-id="f09f0-108">Activez la suppression lors de la publication, avec les paramètres par défaut définis par le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="f09f0-108">Enable trimming during publish, with the default settings defined by the SDK.</span></span>

<span data-ttu-id="f09f0-109">Lors de l’utilisation de `Microsoft.NET.Sdk` , cette opération effectue une suppression au niveau de l’assembly des assemblys du Framework à partir du pack d’exécution netcoreapp.</span><span class="sxs-lookup"><span data-stu-id="f09f0-109">When using `Microsoft.NET.Sdk`, this will perform assembly-level trimming of the framework assemblies from the netcoreapp runtime pack.</span></span> <span data-ttu-id="f09f0-110">Le code d’application et les bibliothèques non Framework ne sont pas supprimés.</span><span class="sxs-lookup"><span data-stu-id="f09f0-110">Application code and non-framework libraries are not trimmed.</span></span> <span data-ttu-id="f09f0-111">D’autres kits de développement logiciel (SDK) peuvent définir des valeurs par défaut différentes.</span><span class="sxs-lookup"><span data-stu-id="f09f0-111">Other SDKs may define different defaults.</span></span>

## <a name="trimming-granularity"></a><span data-ttu-id="f09f0-112">Granularité de suppression</span><span class="sxs-lookup"><span data-stu-id="f09f0-112">Trimming granularity</span></span>

<span data-ttu-id="f09f0-113">Les paramètres de granularité suivants contrôlent la façon dont le langage intermédiaire inutilisé de manière agressive est ignoré.</span><span class="sxs-lookup"><span data-stu-id="f09f0-113">The following granularity settings control how aggressively unused IL is discarded.</span></span> <span data-ttu-id="f09f0-114">Cela peut être défini en tant que propriété ou en tant que métadonnées sur un [assembly individuel](#Trimmed-assemblies).</span><span class="sxs-lookup"><span data-stu-id="f09f0-114">This can be set as a property, or as metadata on an [individual assembly](#Trimmed-assemblies).</span></span>

- `<TrimMode>copyused</TrimMode>`

   <span data-ttu-id="f09f0-115">Activez la suppression au niveau de l’assembly, qui conservera un assembly entier si une partie de celui-ci est utilisée (de façon interprétée de manière statique).</span><span class="sxs-lookup"><span data-stu-id="f09f0-115">Enable assembly-level trimming, which will keep an entire assembly if any part of it is used (in a statically-understood way).</span></span>

- `<TrimMode>link</TrimMode>`

    <span data-ttu-id="f09f0-116">Activez la suppression au niveau du membre, qui supprime les membres inutilisés des types.</span><span class="sxs-lookup"><span data-stu-id="f09f0-116">Enable member-level trimming, which removes unused members from types.</span></span>

<span data-ttu-id="f09f0-117">Les assemblys avec des `<IsTrimmable>true</IsTrimmable>` métadonnées, mais pas explicites `TrimMode` , utilisent le global `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="f09f0-117">Assemblies with `<IsTrimmable>true</IsTrimmable>` metadata but no explicit `TrimMode` will use the global `TrimMode`.</span></span> <span data-ttu-id="f09f0-118">La valeur par défaut `TrimMode` de `Microsoft.NET.Sdk` est `copyused` .</span><span class="sxs-lookup"><span data-stu-id="f09f0-118">The default `TrimMode` for `Microsoft.NET.Sdk` is `copyused`.</span></span>

## <a name="trimmed-assemblies"></a><span data-ttu-id="f09f0-119">Assemblys tronqués</span><span class="sxs-lookup"><span data-stu-id="f09f0-119">Trimmed assemblies</span></span>

<span data-ttu-id="f09f0-120">Lors de la publication d’une application tronquée, le kit de développement logiciel (SDK) calcule un `ItemGroup` appelé `ManagedAssemblyToLink` qui représente le jeu de fichiers à traiter pour la suppression.</span><span class="sxs-lookup"><span data-stu-id="f09f0-120">When publishing a trimmed app, the SDK computes an `ItemGroup` called `ManagedAssemblyToLink` that represents the set of files to be processed for trimming.</span></span> <span data-ttu-id="f09f0-121">`ManagedAssemblyToLink` peut avoir des métadonnées qui contrôlent le comportement de suppression par assembly.</span><span class="sxs-lookup"><span data-stu-id="f09f0-121">`ManagedAssemblyToLink` may have metadata that controls the trimming behavior per assembly.</span></span> <span data-ttu-id="f09f0-122">Pour définir ces métadonnées, créez une cible qui s’exécute avant la `PrepareForILLink` cible intégrée.</span><span class="sxs-lookup"><span data-stu-id="f09f0-122">To set this metadata, create a target that runs before the built-in `PrepareForILLink` target.</span></span> <span data-ttu-id="f09f0-123">Cet exemple montre comment activer la suppression des `MyAssembly` éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f09f0-123">This example shows how to enable trimming of `MyAssembly`:</span></span>

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

<span data-ttu-id="f09f0-124">N’ajoutez pas ou ne supprimez pas d’éléments dans `ManagedAssemblyToLink` , car le kit de développement logiciel (SDK) calcule cet ensemble lors de la publication et s’attend à ce qu’il ne soit pas modifié.</span><span class="sxs-lookup"><span data-stu-id="f09f0-124">Do not add or remove items to/from `ManagedAssemblyToLink`, because the SDK computes this set during publish and expects it not to change.</span></span> <span data-ttu-id="f09f0-125">Les métadonnées prises en charge sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f09f0-125">The supported metadata is:</span></span>

- `<IsTrimmable>true</IsTrimmable>`

  <span data-ttu-id="f09f0-126">Contrôle si l’assembly donné est tronqué.</span><span class="sxs-lookup"><span data-stu-id="f09f0-126">Control whether the given assembly is trimmed.</span></span>

- <span data-ttu-id="f09f0-127">`<TrimMode>copyused</TrimMode>` ou `<TrimMode>link</TrimMode>`</span><span class="sxs-lookup"><span data-stu-id="f09f0-127">`<TrimMode>copyused</TrimMode>` or `<TrimMode>link</TrimMode>`</span></span>

  <span data-ttu-id="f09f0-128">Contrôler la [granularité](#Trimming-granularity) de la suppression de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="f09f0-128">Control the [trimming granularity](#Trimming-granularity) of this assembly.</span></span> <span data-ttu-id="f09f0-129">Cela est prioritaire par rapport au global `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="f09f0-129">This takes precedence over the global `TrimMode`.</span></span> <span data-ttu-id="f09f0-130">La définition `TrimMode` d’un assembly implique `<IsTrimmable>true</IsTrimmable>` .</span><span class="sxs-lookup"><span data-stu-id="f09f0-130">Setting `TrimMode` on an assembly implies `<IsTrimmable>true</IsTrimmable>`.</span></span>

## <a name="root-assemblies"></a><span data-ttu-id="f09f0-131">Assemblys racines</span><span class="sxs-lookup"><span data-stu-id="f09f0-131">Root assemblies</span></span>

<span data-ttu-id="f09f0-132">Tous les assemblys qui n’ont pas de `<IsTrimmable>true</IsTrimmable>` données sont considérés comme des racines pour l’analyse, ce qui signifie qu’elles sont conservées et toutes leurs dépendances comprises statiquement.</span><span class="sxs-lookup"><span data-stu-id="f09f0-132">All assemblies which do not have `<IsTrimmable>true</IsTrimmable>` are considered roots for the analysis, which means that they and all of their statically understood dependencies will be kept.</span></span> <span data-ttu-id="f09f0-133">Les assemblys supplémentaires peuvent être « enracinés » par nom (sans l' `.dll` extension) :</span><span class="sxs-lookup"><span data-stu-id="f09f0-133">Additional assemblies may be "rooted" by name (without the `.dll` extension):</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a><span data-ttu-id="f09f0-134">Descripteurs racines</span><span class="sxs-lookup"><span data-stu-id="f09f0-134">Root descriptors</span></span>

<span data-ttu-id="f09f0-135">Une autre façon de spécifier des racines pour l’analyse consiste à utiliser un fichier XML qui utilise le [format de descripteur](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)de l’éditeur de liens.</span><span class="sxs-lookup"><span data-stu-id="f09f0-135">Another way to specify roots for analysis is using an XML file that uses the linker [descriptor format](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span></span> <span data-ttu-id="f09f0-136">Cela vous permet d’obtenir des membres spécifiques à la racine au lieu d’un assembly entier.</span><span class="sxs-lookup"><span data-stu-id="f09f0-136">This lets you root specific members instead of a whole assembly.</span></span>

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

<span data-ttu-id="f09f0-137">Par exemple, `MyRoots.xml` peut être la racine d’une méthode spécifique qui est accessible de manière dynamique par l’application :</span><span class="sxs-lookup"><span data-stu-id="f09f0-137">For example, `MyRoots.xml` might root a specific method that is dynamically accessed by the application:</span></span>

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a><span data-ttu-id="f09f0-138">Avertissements d’analyse</span><span class="sxs-lookup"><span data-stu-id="f09f0-138">Analysis warnings</span></span>

<span data-ttu-id="f09f0-139">La suppression supprimera IL qui n’est pas accessible de manière statique.</span><span class="sxs-lookup"><span data-stu-id="f09f0-139">Trimming will remove IL that is not statically reachable.</span></span> <span data-ttu-id="f09f0-140">Les applications qui utilisent la réflexion ou d’autres modèles qui créent des dépendances dynamiques peuvent être interrompues par la suppression.</span><span class="sxs-lookup"><span data-stu-id="f09f0-140">Apps that use reflection or other patterns that create dynamic dependencies may be broken by trimming.</span></span> <span data-ttu-id="f09f0-141">Pour signaler ces modèles :</span><span class="sxs-lookup"><span data-stu-id="f09f0-141">To warn about such patterns:</span></span>

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    <span data-ttu-id="f09f0-142">Activez les avertissements d’analyse de découpage.</span><span class="sxs-lookup"><span data-stu-id="f09f0-142">Enable trim analysis warnings.</span></span>

<span data-ttu-id="f09f0-143">Cela inclut les avertissements relatifs à l’application entière, y compris votre propre code, votre propre code de bibliothèque et votre code d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="f09f0-143">This will include warnings about the entire app, including your own code, library code, and framework code.</span></span>

## <a name="warning-versions"></a><span data-ttu-id="f09f0-144">Versions d’avertissement</span><span class="sxs-lookup"><span data-stu-id="f09f0-144">Warning versions</span></span>

<span data-ttu-id="f09f0-145">L’analyse de découpage respecte la [`AnalysisLevel`](../project-sdk/msbuild-props.md#AnalysisLevel) propriété qui contrôle la version des avertissements d’analyse dans le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="f09f0-145">Trim analysis respects the [`AnalysisLevel`](../project-sdk/msbuild-props.md#AnalysisLevel) property that controls the version of analysis warnings across the SDK.</span></span> <span data-ttu-id="f09f0-146">Il existe une autre propriété qui contrôle la version des avertissements d’analyse de suppression indépendamment (comme `WarningLevel` pour le compilateur) :</span><span class="sxs-lookup"><span data-stu-id="f09f0-146">There is another property that controls the version of trim analysis warnings independently (similar to `WarningLevel` for the compiler):</span></span>

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    <span data-ttu-id="f09f0-147">Émet uniquement les avertissements du niveau donné ou inférieurs.</span><span class="sxs-lookup"><span data-stu-id="f09f0-147">Emit only warnings of the given level or lower.</span></span> <span data-ttu-id="f09f0-148">Cela peut consister `9999` à inclure toutes les versions d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="f09f0-148">This can be `9999` to include all warning versions.</span></span>

## <a name="suppressing-warnings"></a><span data-ttu-id="f09f0-149">Supprimer les avertissements</span><span class="sxs-lookup"><span data-stu-id="f09f0-149">Suppressing warnings</span></span>

<span data-ttu-id="f09f0-150">Les [codes d’avertissement](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) individuels peuvent être supprimés à l’aide des propriétés MSBuild habituelles respectées par chaîne d’outils, notamment `NoWarn` ,, `WarningsAsErrors` `WarningsNotAsErrors` et `TreatWarningsAsErrors` .</span><span class="sxs-lookup"><span data-stu-id="f09f0-150">Individual [warning codes](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) can be suppressed using the usual MSBuild properties respected by the toolchain, including `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors`, and `TreatWarningsAsErrors`.</span></span> <span data-ttu-id="f09f0-151">Il existe une option supplémentaire qui contrôle le comportement de l’avertissement en tant qu’erreur ILLink indépendamment :</span><span class="sxs-lookup"><span data-stu-id="f09f0-151">There is an additional option that controls the ILLink warn-as-error behavior independently:</span></span>

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    <span data-ttu-id="f09f0-152">Ne pas traiter les avertissements ILLink comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="f09f0-152">Don't treat ILLink warnings as errors.</span></span> <span data-ttu-id="f09f0-153">Cela peut être utile pour éviter d’activer les avertissements d’analyse de suppression dans des erreurs lors du traitement des avertissements du compilateur en tant qu’erreurs de manière globale.</span><span class="sxs-lookup"><span data-stu-id="f09f0-153">This may be useful to avoid turning trim analysis warnings into errors when treating compiler warnings as errors globally.</span></span>

## <a name="removing-symbols"></a><span data-ttu-id="f09f0-154">Suppression de symboles</span><span class="sxs-lookup"><span data-stu-id="f09f0-154">Removing symbols</span></span>

<span data-ttu-id="f09f0-155">Les symboles sont normalement tronqués pour correspondre aux assemblys tronqués.</span><span class="sxs-lookup"><span data-stu-id="f09f0-155">Symbols will normally be trimmed to match the trimmed assemblies.</span></span> <span data-ttu-id="f09f0-156">Vous pouvez également supprimer tous les symboles :</span><span class="sxs-lookup"><span data-stu-id="f09f0-156">You can also remove all symbols:</span></span>

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    <span data-ttu-id="f09f0-157">Supprimer les symboles de l’application rognée, y compris les fichiers PDB incorporés et les fichiers PDB séparés.</span><span class="sxs-lookup"><span data-stu-id="f09f0-157">Remove symbols from the trimmed application, including embedded PDBs and separate PDB files.</span></span> <span data-ttu-id="f09f0-158">Cela s’applique à la fois au code d’application et à toutes les dépendances qui accompagnent les symboles.</span><span class="sxs-lookup"><span data-stu-id="f09f0-158">This applies to both the application code and any dependencies that come with symbols.</span></span>

<span data-ttu-id="f09f0-159">Le kit de développement logiciel (SDK) permet également de désactiver la prise en charge du débogueur à l’aide de la propriété `DebuggerSupport` .</span><span class="sxs-lookup"><span data-stu-id="f09f0-159">The SDK also makes it possible to disable debugger support using the property `DebuggerSupport`.</span></span> <span data-ttu-id="f09f0-160">Lorsque la prise en charge du débogueur est désactivée, la suppression supprime automatiquement les symboles (la `TrimmerRemoveSymbols` valeur par défaut est true).</span><span class="sxs-lookup"><span data-stu-id="f09f0-160">When debugger support is disabled, trimming will remove symbols automatically (`TrimmerRemoveSymbols` will default to true).</span></span>
