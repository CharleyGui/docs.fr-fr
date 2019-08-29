---
title: -refout (Options du compilateur C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 97cbf540527d0449387b71bb1d97df95b6a4aba4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602502"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="f99da-102">-refout (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f99da-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="f99da-103">L’option **-refout** spécifie un chemin de fichier où l’assembly de référence doit être généré.</span><span class="sxs-lookup"><span data-stu-id="f99da-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="f99da-104">Cela se traduit par `metadataPeStream` dans l’API Emit.</span><span class="sxs-lookup"><span data-stu-id="f99da-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="f99da-105">Cette option correspond à la propriété de projet [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f99da-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="f99da-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f99da-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="f99da-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="f99da-107">Arguments</span></span>

 <span data-ttu-id="f99da-108">`filepath` Chemin de l’assembly de référence.</span><span class="sxs-lookup"><span data-stu-id="f99da-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="f99da-109">Il doit généralement correspondre à celui de l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="f99da-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="f99da-110">La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="f99da-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="f99da-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f99da-111">Remarks</span></span>

<span data-ttu-id="f99da-112">Les assemblys de métadonnées uniquement ont leurs corps de méthode remplacés par un corps `throw null` unique, mais incluent tous les membres à l’exception des types anonymes.</span><span class="sxs-lookup"><span data-stu-id="f99da-112">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="f99da-113">L’utilisation de corps `throw null` (plutôt qu’aucun corps) permet la bonne exécution de PEVerify (et, par voie de conséquence, la validation de la conformité des métadonnées).</span><span class="sxs-lookup"><span data-stu-id="f99da-113">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="f99da-114">Les assemblys de référence incluent un attribut `ReferenceAssembly` de niveau assembly.</span><span class="sxs-lookup"><span data-stu-id="f99da-114">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="f99da-115">Cet attribut peut être spécifié dans la source (le compilateur n’a plus alors besoin de le synthétiser).</span><span class="sxs-lookup"><span data-stu-id="f99da-115">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="f99da-116">En raison de cet attribut, les runtimes refusent de charger les assemblys de référence pour l’exécution (mais ils peuvent toujours être chargés en mode de réflexion uniquement).</span><span class="sxs-lookup"><span data-stu-id="f99da-116">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="f99da-117">Les outils reflétés dans les assemblys doivent absolument charger les assemblys de référence en mode réflexion uniquement, sinon ils reçoivent une erreur de chargement de type de la part du runtime.</span><span class="sxs-lookup"><span data-stu-id="f99da-117">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="f99da-118">En outre, les assemblys de référence suppriment les métadonnées (membres privés) des assemblys de métadonnées uniquement :</span><span class="sxs-lookup"><span data-stu-id="f99da-118">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="f99da-119">Un assembly de référence a uniquement des références pour ce dont il a besoin dans la surface de l’API.</span><span class="sxs-lookup"><span data-stu-id="f99da-119">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="f99da-120">L’assembly réel peut avoir des références supplémentaires relatives à des implémentations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f99da-120">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="f99da-121">Par exemple, l’assembly de référence pour `class C { private void M() { dynamic d = 1; ... } }` ne référence aucun des types requis pour `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="f99da-121">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="f99da-122">Les membres de fonction privés (méthodes, propriétés et événements) sont supprimés si leur suppression n’affecte pas la compilation sensiblement.</span><span class="sxs-lookup"><span data-stu-id="f99da-122">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="f99da-123">S’il n’y a aucun attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, faites de même pour les membres de fonction internes.</span><span class="sxs-lookup"><span data-stu-id="f99da-123">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="f99da-124">Toutefois, tous les types (y compris les types privés ou imbriqués) sont conservés dans les assemblys de référence.</span><span class="sxs-lookup"><span data-stu-id="f99da-124">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="f99da-125">Tous les attributs sont conservés (même les attributs internes).</span><span class="sxs-lookup"><span data-stu-id="f99da-125">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="f99da-126">Toutes les méthodes virtuelles sont conservées.</span><span class="sxs-lookup"><span data-stu-id="f99da-126">All virtual methods are kept.</span></span> <span data-ttu-id="f99da-127">Les implémentations d’interface explicite sont conservées.</span><span class="sxs-lookup"><span data-stu-id="f99da-127">Explicit interface implementations are kept.</span></span> <span data-ttu-id="f99da-128">Les propriétés et les événements implémentés explicitement sont conservés, car leurs accesseurs sont virtuels (et donc conservés).</span><span class="sxs-lookup"><span data-stu-id="f99da-128">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="f99da-129">Tous les champs d’un struct sont conservés.</span><span class="sxs-lookup"><span data-stu-id="f99da-129">All fields of a struct are kept.</span></span> <span data-ttu-id="f99da-130">(Candidat pour une optimisation future de C# 7.1)</span><span class="sxs-lookup"><span data-stu-id="f99da-130">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="f99da-131">Les options `-refout` et [`-refonly`](refonly-compiler-option.md) s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="f99da-131">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="f99da-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f99da-132">See also</span></span>

- [<span data-ttu-id="f99da-133">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="f99da-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f99da-134">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="f99da-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
