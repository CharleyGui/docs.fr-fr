---
title: 'Comment : Inspecter le contenu de l’assemblage à l’aide de MetadataLoadContext'
description: Apprenez à utiliser MetadataLoadContext, qui est une API qui vous permet de charger des assemblages .NET à des fins d’inspection.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: a782b2db4fb62cfaedaa6768e2131bda6bec864c
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80229300"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a><span data-ttu-id="dc1da-103">Comment : Inspecter le contenu de l’assemblage à l’aide de MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="dc1da-103">How to: Inspect assembly contents using MetadataLoadContext</span></span>

<span data-ttu-id="dc1da-104">L’API de réflexion en .NET par défaut permet aux développeurs d’inspecter le contenu des assemblages chargés dans le contexte d’exécution principal.</span><span class="sxs-lookup"><span data-stu-id="dc1da-104">The reflection API in .NET by default enables developers to inspect the contents of assemblies loaded into the main execution context.</span></span> <span data-ttu-id="dc1da-105">Cependant, parfois, il n’est pas possible de charger un assemblage dans le contexte d’exécution, par exemple, parce qu’il a été compilé pour une autre plate-forme ou architecture de processeur, ou c’est un assemblage de [référence](reference-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="dc1da-105">However, sometimes it isn't possible to load an assembly into the execution context, for example, because it was compiled for another platform or processor architecture, or it's a [reference assembly](reference-assemblies.md).</span></span> <span data-ttu-id="dc1da-106">L’API <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> vous permet de charger et d’inspecter ces assemblages.</span><span class="sxs-lookup"><span data-stu-id="dc1da-106">The <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> API allows you to load and inspect such assemblies.</span></span> <span data-ttu-id="dc1da-107">Les assemblages <xref:System.Reflection.MetadataLoadContext> chargés dans le sont traités uniquement comme des métadonnées, c’est-à-dire, vous pouvez examiner les types dans l’assemblage, mais vous ne pouvez pas exécuter n’importe quel code contenu en elle.</span><span class="sxs-lookup"><span data-stu-id="dc1da-107">Assemblies loaded into the <xref:System.Reflection.MetadataLoadContext> are treated only as metadata, that is, you can examine types in the assembly, but you can't execute any code contained in it.</span></span> <span data-ttu-id="dc1da-108">Contrairement au contexte d’exécution principal, le <xref:System.Reflection.MetadataLoadContext> n’est pas automatiquement charger les dépendances de l’annuaire actuel; au lieu de cela, il <xref:System.Reflection.MetadataAssemblyResolver> utilise la logique de liaison personnalisée fournie par le passé à elle.</span><span class="sxs-lookup"><span data-stu-id="dc1da-108">Unlike the main execution context, the <xref:System.Reflection.MetadataLoadContext> doesn't automatically load dependencies from the current directory; instead it uses the custom binding logic provided by the <xref:System.Reflection.MetadataAssemblyResolver> passed to it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc1da-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="dc1da-109">Prerequisites</span></span>

<span data-ttu-id="dc1da-110">Pour <xref:System.Reflection.MetadataLoadContext>utiliser, installez le paquet [System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet.</span><span class="sxs-lookup"><span data-stu-id="dc1da-110">To use <xref:System.Reflection.MetadataLoadContext>, install the [System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet package.</span></span> <span data-ttu-id="dc1da-111">Il est pris en charge sur n’importe quel cadre cible .NET Standard 2.0-conforme, par exemple, .NET Core 2.0 ou .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="dc1da-111">It is supported on any .NET Standard 2.0-compliant target framework, for example, .NET Core 2.0 or .NET Framework 4.6.1.</span></span>

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a><span data-ttu-id="dc1da-112">Créer MetadataAssemblyResolver pour MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="dc1da-112">Create MetadataAssemblyResolver for MetadataLoadContext</span></span>

<span data-ttu-id="dc1da-113">Créer <xref:System.Reflection.MetadataLoadContext> les exigences de <xref:System.Reflection.MetadataAssemblyResolver>fournir l’exemple de la .</span><span class="sxs-lookup"><span data-stu-id="dc1da-113">Creating the <xref:System.Reflection.MetadataLoadContext> requires providing the instance of the <xref:System.Reflection.MetadataAssemblyResolver>.</span></span> <span data-ttu-id="dc1da-114">La façon la plus simple d’en fournir une est d’utiliser le <xref:System.Reflection.PathAssemblyResolver>, qui résout les assemblages de la collection donnée de cordes de chemin d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="dc1da-114">The simplest way to provide one is to use the <xref:System.Reflection.PathAssemblyResolver>, which resolves assemblies from the given collection of assembly path strings.</span></span> <span data-ttu-id="dc1da-115">Cette collection, en plus des assemblages que vous souhaitez inspecter directement, devrait également inclure toutes les dépendances nécessaires.</span><span class="sxs-lookup"><span data-stu-id="dc1da-115">This collection, besides assemblies you want to inspect directly, should also include all needed dependencies.</span></span> <span data-ttu-id="dc1da-116">Par exemple, pour lire l’attribut personnalisé situé dans un assemblage externe, vous devez inclure que l’assemblage ou une exception sera jeté.</span><span class="sxs-lookup"><span data-stu-id="dc1da-116">For example, to read the custom attribute located in an external assembly, you should include that assembly or an exception will be thrown.</span></span> <span data-ttu-id="dc1da-117">Dans la plupart des cas, vous devez inclure au moins *l’assemblage de base,* c’est-à-dire l’assemblage contenant des types de système intégrés, tels que <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc1da-117">In most cases, you should include at least the *core assembly*, that is, the assembly containing built-in system types, such as <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dc1da-118">Le code suivant montre <xref:System.Reflection.PathAssemblyResolver> comment créer l’utilisation de la collection composée de l’assemblage inspecté et de l’assemblage de base du temps d’exécution actuel :</span><span class="sxs-lookup"><span data-stu-id="dc1da-118">The following code shows how to create the <xref:System.Reflection.PathAssemblyResolver> using the collection consisting of the inspected assembly and the current runtime's core assembly:</span></span>

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

<span data-ttu-id="dc1da-119">Si vous avez besoin d’accéder à tous les types BCL, vous pouvez inclure tous les assemblages de temps d’exécution dans la collection.</span><span class="sxs-lookup"><span data-stu-id="dc1da-119">If you need access to all BCL types, you can include all runtime assemblies in the collection.</span></span> <span data-ttu-id="dc1da-120">Le code suivant montre <xref:System.Reflection.PathAssemblyResolver> comment créer l’utilisation de la collection composée de l’assemblage inspecté et de tous les assemblages du temps d’exécution actuel :</span><span class="sxs-lookup"><span data-stu-id="dc1da-120">The following code shows how to create the <xref:System.Reflection.PathAssemblyResolver> using the collection consisting of the inspected assembly and all assemblies of the current runtime:</span></span>

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a><span data-ttu-id="dc1da-121">Créer Des métadonnéesLoadContexte</span><span class="sxs-lookup"><span data-stu-id="dc1da-121">Create MetadataLoadContext</span></span>

<span data-ttu-id="dc1da-122">Pour créer <xref:System.Reflection.MetadataLoadContext>le , <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>invoquer son <xref:System.Reflection.MetadataAssemblyResolver> constructeur , en passant le paramètre précédemment créé comme le premier paramètre et le nom d’assemblage de base comme le deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="dc1da-122">To create the <xref:System.Reflection.MetadataLoadContext>, invoke its constructor <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>, passing the previously created <xref:System.Reflection.MetadataAssemblyResolver> as the first parameter and the core assembly name as the second parameter.</span></span> <span data-ttu-id="dc1da-123">Vous pouvez omettre le nom d’assemblage de base, auquel cas le constructeur tentera d’utiliser des noms par défaut : "mscorlib", "System.Runtime", ou "netstandard".</span><span class="sxs-lookup"><span data-stu-id="dc1da-123">You can omit the core assembly name, in which case the constructor will attempt to use default names: "mscorlib", "System.Runtime", or "netstandard".</span></span>

<span data-ttu-id="dc1da-124">Une fois que vous avez créé le contexte, vous <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>pouvez charger des assemblages en elle en utilisant des méthodes telles que .</span><span class="sxs-lookup"><span data-stu-id="dc1da-124">After you've created the context, you can load assemblies into it using methods such as <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>.</span></span> <span data-ttu-id="dc1da-125">Vous pouvez utiliser toutes les API de réflexion sur les assemblages chargés, sauf ceux qui impliquent l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="dc1da-125">You can use all reflection APIs on loaded assemblies except ones that involve code execution.</span></span> <span data-ttu-id="dc1da-126">La <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> méthode implique l’exécution des constructeurs, alors utilisez la méthode à la <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> place lorsque vous avez besoin d’examiner les attributs personnalisés dans le <xref:System.Reflection.MetadataLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="dc1da-126">The <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> method does involve the execution of constructors, so use the <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> method instead when you need to examine custom attributes in the <xref:System.Reflection.MetadataLoadContext>.</span></span>

<span data-ttu-id="dc1da-127">L’échantillon de <xref:System.Reflection.MetadataLoadContext>code suivant crée, charge l’assemblage en elle, et les attributs d’assemblage de sorties dans la console:</span><span class="sxs-lookup"><span data-stu-id="dc1da-127">The following code sample creates <xref:System.Reflection.MetadataLoadContext>, loads the assembly into it, and outputs assembly attributes into the console:</span></span>

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a><span data-ttu-id="dc1da-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc1da-128">Example</span></span>

<span data-ttu-id="dc1da-129">Pour un exemple complet de code, voir [inspecter le contenu de l’assemblage à l’aide de MetadataLoadContext](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).</span><span class="sxs-lookup"><span data-stu-id="dc1da-129">For a complete code example, see [Inspect assembly contents using MetadataLoadContext](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).</span></span>