---
title: Options de suppression
description: Découvrez comment contrôler le découpage des applications autonomes.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: e36aca3aadb6968f73a439ca985dc410d1bc88d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704654"
---
# <a name="trimming-options"></a><span data-ttu-id="92950-103">Options de suppression</span><span class="sxs-lookup"><span data-stu-id="92950-103">Trimming options</span></span>

<span data-ttu-id="92950-104">Les propriétés et les éléments MSBuild suivants influencent le comportement des [déploiements autonomes tronqués](trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="92950-104">The following MSBuild properties and items influence the behavior of [trimmed self-contained deployments](trim-self-contained.md).</span></span> <span data-ttu-id="92950-105">Certaines des options mentionnent `ILLink` , qui est le nom de l’outil sous-jacent qui implémente la suppression.</span><span class="sxs-lookup"><span data-stu-id="92950-105">Some of the options mention `ILLink`, which is the name of the underlying tool that implements trimming.</span></span> <span data-ttu-id="92950-106">Vous trouverez plus d’informations sur l’outil sous-jacent dans la documentation de l' [éditeur de liens](https://github.com/mono/linker/tree/master/docs).</span><span class="sxs-lookup"><span data-stu-id="92950-106">More information about the underlying tool can be found at the [Linker documentation](https://github.com/mono/linker/tree/master/docs).</span></span>

## <a name="enable-trimming"></a><span data-ttu-id="92950-107">Activer la suppression</span><span class="sxs-lookup"><span data-stu-id="92950-107">Enable trimming</span></span>

- `<PublishTrimmed>true</PublishTrimmed>`

   <span data-ttu-id="92950-108">Activez la suppression lors de la publication, avec les paramètres par défaut définis par le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="92950-108">Enable trimming during publish, with the default settings defined by the SDK.</span></span>

<span data-ttu-id="92950-109">Lors de l’utilisation de `Microsoft.NET.Sdk` , cette opération effectue une suppression au niveau de l’assembly des assemblys du Framework à partir du pack d’exécution netcoreapp.</span><span class="sxs-lookup"><span data-stu-id="92950-109">When using `Microsoft.NET.Sdk`, this will perform assembly-level trimming of the framework assemblies from the netcoreapp runtime pack.</span></span> <span data-ttu-id="92950-110">Le code d’application et les bibliothèques non Framework ne sont pas supprimés.</span><span class="sxs-lookup"><span data-stu-id="92950-110">Application code and non-framework libraries are not trimmed.</span></span> <span data-ttu-id="92950-111">D’autres kits de développement logiciel (SDK) peuvent définir des valeurs par défaut différentes.</span><span class="sxs-lookup"><span data-stu-id="92950-111">Other SDKs may define different defaults.</span></span>

## <a name="trimming-granularity"></a><span data-ttu-id="92950-112">Granularité de suppression</span><span class="sxs-lookup"><span data-stu-id="92950-112">Trimming granularity</span></span>

<span data-ttu-id="92950-113">Les paramètres de granularité suivants contrôlent la façon dont le langage intermédiaire inutilisé de manière agressive est ignoré.</span><span class="sxs-lookup"><span data-stu-id="92950-113">The following granularity settings control how aggressively unused IL is discarded.</span></span> <span data-ttu-id="92950-114">Cela peut être défini en tant que propriété ou en tant que métadonnées sur un [assembly individuel](#trimmed-assemblies).</span><span class="sxs-lookup"><span data-stu-id="92950-114">This can be set as a property, or as metadata on an [individual assembly](#trimmed-assemblies).</span></span>

- `<TrimMode>copyused</TrimMode>`

   <span data-ttu-id="92950-115">Activez la suppression au niveau de l’assembly, qui conservera un assembly entier si une partie de celui-ci est utilisée (de façon comprise de manière statique).</span><span class="sxs-lookup"><span data-stu-id="92950-115">Enable assembly-level trimming, which will keep an entire assembly if any part of it is used (in a statically understood way).</span></span>

- `<TrimMode>link</TrimMode>`

    <span data-ttu-id="92950-116">Activez la suppression au niveau du membre, qui supprime les membres inutilisés des types.</span><span class="sxs-lookup"><span data-stu-id="92950-116">Enable member-level trimming, which removes unused members from types.</span></span>

<span data-ttu-id="92950-117">Les assemblys avec des `<IsTrimmable>true</IsTrimmable>` métadonnées, mais pas explicites `TrimMode` , utilisent le global `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="92950-117">Assemblies with `<IsTrimmable>true</IsTrimmable>` metadata but no explicit `TrimMode` will use the global `TrimMode`.</span></span> <span data-ttu-id="92950-118">La valeur par défaut `TrimMode` de `Microsoft.NET.Sdk` est `copyused` .</span><span class="sxs-lookup"><span data-stu-id="92950-118">The default `TrimMode` for `Microsoft.NET.Sdk` is `copyused`.</span></span>

## <a name="trimmed-assemblies"></a><span data-ttu-id="92950-119">Assemblys tronqués</span><span class="sxs-lookup"><span data-stu-id="92950-119">Trimmed assemblies</span></span>

<span data-ttu-id="92950-120">Lors de la publication d’une application tronquée, le kit de développement logiciel (SDK) calcule un `ItemGroup` appelé `ManagedAssemblyToLink` qui représente le jeu de fichiers à traiter pour la suppression.</span><span class="sxs-lookup"><span data-stu-id="92950-120">When publishing a trimmed app, the SDK computes an `ItemGroup` called `ManagedAssemblyToLink` that represents the set of files to be processed for trimming.</span></span> <span data-ttu-id="92950-121">`ManagedAssemblyToLink` peut avoir des métadonnées qui contrôlent le comportement de suppression par assembly.</span><span class="sxs-lookup"><span data-stu-id="92950-121">`ManagedAssemblyToLink` may have metadata that controls the trimming behavior per assembly.</span></span> <span data-ttu-id="92950-122">Pour définir ces métadonnées, créez une cible qui s’exécute avant la `PrepareForILLink` cible intégrée.</span><span class="sxs-lookup"><span data-stu-id="92950-122">To set this metadata, create a target that runs before the built-in `PrepareForILLink` target.</span></span> <span data-ttu-id="92950-123">L’exemple suivant montre comment activer la suppression de `MyAssembly` .</span><span class="sxs-lookup"><span data-stu-id="92950-123">The following example shows how to enable trimming of `MyAssembly`.</span></span>

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

<span data-ttu-id="92950-124">N’ajoutez pas ou ne supprimez pas d’éléments dans `ManagedAssemblyToLink` , car le kit de développement logiciel (SDK) calcule cet ensemble lors de la publication et s’attend à ce qu’il ne soit pas modifié.</span><span class="sxs-lookup"><span data-stu-id="92950-124">Do not add or remove items to/from `ManagedAssemblyToLink`, because the SDK computes this set during publish and expects it not to change.</span></span> <span data-ttu-id="92950-125">Les métadonnées prises en charge sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="92950-125">The supported metadata is:</span></span>

- `<IsTrimmable>true</IsTrimmable>`

  <span data-ttu-id="92950-126">Contrôle si l’assembly donné est tronqué.</span><span class="sxs-lookup"><span data-stu-id="92950-126">Control whether the given assembly is trimmed.</span></span>

- <span data-ttu-id="92950-127">`<TrimMode>copyused</TrimMode>` ou `<TrimMode>link</TrimMode>`</span><span class="sxs-lookup"><span data-stu-id="92950-127">`<TrimMode>copyused</TrimMode>` or `<TrimMode>link</TrimMode>`</span></span>

  <span data-ttu-id="92950-128">Contrôler la [granularité](#trimming-granularity) de la suppression de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="92950-128">Control the [trimming granularity](#trimming-granularity) of this assembly.</span></span> <span data-ttu-id="92950-129">Cela est prioritaire par rapport au global `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="92950-129">This takes precedence over the global `TrimMode`.</span></span> <span data-ttu-id="92950-130">La définition `TrimMode` d’un assembly implique `<IsTrimmable>true</IsTrimmable>` .</span><span class="sxs-lookup"><span data-stu-id="92950-130">Setting `TrimMode` on an assembly implies `<IsTrimmable>true</IsTrimmable>`.</span></span>

## <a name="root-assemblies"></a><span data-ttu-id="92950-131">Assemblys racines</span><span class="sxs-lookup"><span data-stu-id="92950-131">Root assemblies</span></span>

<span data-ttu-id="92950-132">Tous les assemblys qui n’ont pas `<IsTrimmable>true</IsTrimmable>` sont considérés comme des racines pour l’analyse, ce qui signifie qu’elles sont conservées et toutes leurs dépendances comprises statiquement.</span><span class="sxs-lookup"><span data-stu-id="92950-132">All assemblies that do not have `<IsTrimmable>true</IsTrimmable>` are considered roots for the analysis, which means that they and all of their statically understood dependencies will be kept.</span></span> <span data-ttu-id="92950-133">Les assemblys supplémentaires peuvent être « enracinés » par nom (sans l' `.dll` extension) :</span><span class="sxs-lookup"><span data-stu-id="92950-133">Additional assemblies may be "rooted" by name (without the `.dll` extension):</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a><span data-ttu-id="92950-134">Descripteurs racines</span><span class="sxs-lookup"><span data-stu-id="92950-134">Root descriptors</span></span>

<span data-ttu-id="92950-135">Une autre façon de spécifier des racines pour l’analyse consiste à utiliser un fichier XML qui utilise le [format de descripteur](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)de l’éditeur de liens.</span><span class="sxs-lookup"><span data-stu-id="92950-135">Another way to specify roots for analysis is using an XML file that uses the linker [descriptor format](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span></span> <span data-ttu-id="92950-136">Cela vous permet d’obtenir des membres spécifiques à la racine au lieu d’un assembly entier.</span><span class="sxs-lookup"><span data-stu-id="92950-136">This lets you root specific members instead of a whole assembly.</span></span>

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

<span data-ttu-id="92950-137">Par exemple, `MyRoots.xml` peut être la racine d’une méthode spécifique qui est accessible de manière dynamique par l’application :</span><span class="sxs-lookup"><span data-stu-id="92950-137">For example, `MyRoots.xml` might root a specific method that is dynamically accessed by the application:</span></span>

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a><span data-ttu-id="92950-138">Avertissements d’analyse</span><span class="sxs-lookup"><span data-stu-id="92950-138">Analysis warnings</span></span>

<span data-ttu-id="92950-139">La suppression supprimera IL qui n’est pas accessible de manière statique.</span><span class="sxs-lookup"><span data-stu-id="92950-139">Trimming will remove IL that is not statically reachable.</span></span> <span data-ttu-id="92950-140">Les applications qui utilisent la réflexion ou d’autres modèles qui créent des dépendances dynamiques peuvent être interrompues par la suppression.</span><span class="sxs-lookup"><span data-stu-id="92950-140">Apps that use reflection or other patterns that create dynamic dependencies may be broken by trimming.</span></span> <span data-ttu-id="92950-141">Pour signaler ces modèles :</span><span class="sxs-lookup"><span data-stu-id="92950-141">To warn about such patterns:</span></span>

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    <span data-ttu-id="92950-142">Activez les avertissements d’analyse de découpage.</span><span class="sxs-lookup"><span data-stu-id="92950-142">Enable trim analysis warnings.</span></span>

<span data-ttu-id="92950-143">Cela inclut les avertissements relatifs à l’application entière, y compris votre propre code, votre propre code de bibliothèque et votre code d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="92950-143">This will include warnings about the entire app, including your own code, library code, and framework code.</span></span>

## <a name="warning-versions"></a><span data-ttu-id="92950-144">Versions d’avertissement</span><span class="sxs-lookup"><span data-stu-id="92950-144">Warning versions</span></span>

<span data-ttu-id="92950-145">L’analyse de découpage respecte la [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) propriété qui contrôle la version des avertissements d’analyse dans le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="92950-145">Trim analysis respects the [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) property that controls the version of analysis warnings across the SDK.</span></span> <span data-ttu-id="92950-146">Il existe une autre propriété qui contrôle la version des avertissements d’analyse de suppression indépendamment (comme `WarningLevel` pour le compilateur) :</span><span class="sxs-lookup"><span data-stu-id="92950-146">There is another property that controls the version of trim analysis warnings independently (similar to `WarningLevel` for the compiler):</span></span>

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    <span data-ttu-id="92950-147">Émet uniquement les avertissements du niveau donné ou inférieurs.</span><span class="sxs-lookup"><span data-stu-id="92950-147">Emit only warnings of the given level or lower.</span></span> <span data-ttu-id="92950-148">Cela peut consister `9999` à inclure toutes les versions d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="92950-148">This can be `9999` to include all warning versions.</span></span>

## <a name="suppressing-warnings"></a><span data-ttu-id="92950-149">Supprimer les avertissements</span><span class="sxs-lookup"><span data-stu-id="92950-149">Suppressing warnings</span></span>

<span data-ttu-id="92950-150">Les [codes d’avertissement](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) individuels peuvent être supprimés à l’aide des propriétés MSBuild habituelles respectées par chaîne d’outils, notamment `NoWarn` ,, `WarningsAsErrors` `WarningsNotAsErrors` et `TreatWarningsAsErrors` .</span><span class="sxs-lookup"><span data-stu-id="92950-150">Individual [warning codes](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) can be suppressed using the usual MSBuild properties respected by the toolchain, including `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors`, and `TreatWarningsAsErrors`.</span></span> <span data-ttu-id="92950-151">Il existe une option supplémentaire qui contrôle le comportement de l’avertissement en tant qu’erreur ILLink indépendamment :</span><span class="sxs-lookup"><span data-stu-id="92950-151">There is an additional option that controls the ILLink warn-as-error behavior independently:</span></span>

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    <span data-ttu-id="92950-152">Ne pas traiter les avertissements ILLink comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="92950-152">Don't treat ILLink warnings as errors.</span></span> <span data-ttu-id="92950-153">Cela peut être utile pour éviter d’activer les avertissements d’analyse de suppression dans des erreurs lors du traitement des avertissements du compilateur en tant qu’erreurs de manière globale.</span><span class="sxs-lookup"><span data-stu-id="92950-153">This may be useful to avoid turning trim analysis warnings into errors when treating compiler warnings as errors globally.</span></span>

## <a name="removing-symbols"></a><span data-ttu-id="92950-154">Suppression de symboles</span><span class="sxs-lookup"><span data-stu-id="92950-154">Removing symbols</span></span>

<span data-ttu-id="92950-155">Les symboles sont normalement tronqués pour correspondre aux assemblys tronqués.</span><span class="sxs-lookup"><span data-stu-id="92950-155">Symbols will normally be trimmed to match the trimmed assemblies.</span></span> <span data-ttu-id="92950-156">Vous pouvez également supprimer tous les symboles :</span><span class="sxs-lookup"><span data-stu-id="92950-156">You can also remove all symbols:</span></span>

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    <span data-ttu-id="92950-157">Supprimer les symboles de l’application rognée, y compris les fichiers PDB incorporés et les fichiers PDB séparés.</span><span class="sxs-lookup"><span data-stu-id="92950-157">Remove symbols from the trimmed application, including embedded PDBs and separate PDB files.</span></span> <span data-ttu-id="92950-158">Cela s’applique à la fois au code d’application et à toutes les dépendances qui accompagnent les symboles.</span><span class="sxs-lookup"><span data-stu-id="92950-158">This applies to both the application code and any dependencies that come with symbols.</span></span>

<span data-ttu-id="92950-159">Le kit de développement logiciel (SDK) permet également de désactiver la prise en charge du débogueur à l’aide de la propriété `DebuggerSupport` .</span><span class="sxs-lookup"><span data-stu-id="92950-159">The SDK also makes it possible to disable debugger support using the property `DebuggerSupport`.</span></span> <span data-ttu-id="92950-160">Lorsque la prise en charge du débogueur est désactivée, la suppression supprime automatiquement les symboles (la `TrimmerRemoveSymbols` valeur par défaut est true).</span><span class="sxs-lookup"><span data-stu-id="92950-160">When debugger support is disabled, trimming will remove symbols automatically (`TrimmerRemoveSymbols` will default to true).</span></span>

## <a name="trimming-framework-library-features"></a><span data-ttu-id="92950-161">Suppression des fonctionnalités de la bibliothèque d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="92950-161">Trimming framework library features</span></span>

<span data-ttu-id="92950-162">Plusieurs zones de fonctionnalités des bibliothèques d’infrastructure sont fournies avec les directives de l’éditeur de liens qui permettent de supprimer le code pour les fonctionnalités désactivées.</span><span class="sxs-lookup"><span data-stu-id="92950-162">Several feature areas of the framework libraries come with linker directives that make it possible to remove the code for disabled features.</span></span>

- `<DebuggerSupport>false</DebuggerSupport>`

    <span data-ttu-id="92950-163">Supprimez le code qui permet de meilleures expériences de débogage.</span><span class="sxs-lookup"><span data-stu-id="92950-163">Remove code that enables better debugging experiences.</span></span> <span data-ttu-id="92950-164">Cela [supprimera](#removing-symbols)également les symboles.</span><span class="sxs-lookup"><span data-stu-id="92950-164">This will also [remove symbols](#removing-symbols).</span></span>

- `<EnableUnsafeBinaryFormatterSerialization>false</EnableUnsafeBinaryFormatterSerialization>`

    <span data-ttu-id="92950-165">Supprime la prise en charge de la sérialisation BinaryFormatter.</span><span class="sxs-lookup"><span data-stu-id="92950-165">Remove BinaryFormatter serialization support.</span></span> <span data-ttu-id="92950-166">Pour plus d’informations, consultez [méthodes de sérialisation BinaryFormatter obsolètes](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md).</span><span class="sxs-lookup"><span data-stu-id="92950-166">For more information, see [BinaryFormatter serialization methods are obsolete](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md).</span></span>

- `<EnableUnsafeUTF7Encoding>false</EnableUnsafeUTF7Encoding>`

    <span data-ttu-id="92950-167">Supprimez le code d’encodage UTF-7 non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="92950-167">Remove insecure UTF-7 encoding code.</span></span> <span data-ttu-id="92950-168">Pour plus d’informations, consultez les [chemins de code UTF-7 sont obsolètes](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md).</span><span class="sxs-lookup"><span data-stu-id="92950-168">For more information, see [UTF-7 code paths are obsolete](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md).</span></span>

- `<EventSourceSupport>false</EventSourceSupport>`

    <span data-ttu-id="92950-169">Supprimez la logique ou le code lié à EventSource.</span><span class="sxs-lookup"><span data-stu-id="92950-169">Remove EventSource related code or logic.</span></span>

- `<HttpActivityPropagationSupport>false</HttpActivityPropagationSupport>`

    <span data-ttu-id="92950-170">Supprimez le code relatif à la prise en charge des diagnostics pour System .net. http.</span><span class="sxs-lookup"><span data-stu-id="92950-170">Remove code related to diagnostics support for System.Net.Http.</span></span>

- `<InvariantGlobalization>true</InvariantGlobalization>`

    <span data-ttu-id="92950-171">Supprimer le code et les données spécifiques à la globalisation.</span><span class="sxs-lookup"><span data-stu-id="92950-171">Remove globalization specific code and data.</span></span> <span data-ttu-id="92950-172">Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="92950-172">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

- `<UseSystemResourceKeys>true</UseSystemResourceKeys>`

    <span data-ttu-id="92950-173">Supprimer les messages d’exception pour les `System.*` assemblys.</span><span class="sxs-lookup"><span data-stu-id="92950-173">Strip exception messages for `System.*` assemblies.</span></span> <span data-ttu-id="92950-174">Quand une exception est levée à partir d’un `System.*` assembly, le message est un ID de ressource simplifié au lieu du message complet.</span><span class="sxs-lookup"><span data-stu-id="92950-174">When an exception is thrown from a `System.*` assembly, the message will be a simplified resource ID instead of the full message.</span></span>

 <span data-ttu-id="92950-175">Ces propriétés entraînent la troncation du code associé et désactivent également les fonctionnalités via le fichier [runtimeconfig](../run-time-config/index.md) .</span><span class="sxs-lookup"><span data-stu-id="92950-175">These properties will cause the related code to be trimmed and will also disable features via the [runtimeconfig](../run-time-config/index.md) file.</span></span> <span data-ttu-id="92950-176">Pour plus d’informations sur ces propriétés, y compris les options runtimeconfig correspondantes, consultez [commutateurs de fonctionnalités](https://github.com/dotnet/runtime/blob/master/docs/workflow/trimming/feature-switches.md).</span><span class="sxs-lookup"><span data-stu-id="92950-176">For more information about these properties, including the corresponding runtimeconfig options, see [feature switches](https://github.com/dotnet/runtime/blob/master/docs/workflow/trimming/feature-switches.md).</span></span> <span data-ttu-id="92950-177">Certains kits de développement logiciel (SDK) peuvent avoir des valeurs par défaut pour ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="92950-177">Some SDKs may have default values for these properties.</span></span>
