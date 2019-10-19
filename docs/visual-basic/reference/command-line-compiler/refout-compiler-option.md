---
title: -REFOUT (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582869"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="07434-102">-REFOUT (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07434-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="07434-103">L’option **-refout** spécifie un chemin de fichier où l’assembly de référence doit être généré.</span><span class="sxs-lookup"><span data-stu-id="07434-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="07434-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07434-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="07434-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="07434-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="07434-106">Chemin d’accès et nom de fichier de l’assembly de référence.</span><span class="sxs-lookup"><span data-stu-id="07434-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="07434-107">Il doit généralement se trouver dans un sous-dossier de l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="07434-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="07434-108">La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="07434-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="07434-109">Tous les dossiers de `filepath` doivent exister. le compilateur ne les crée pas.</span><span class="sxs-lookup"><span data-stu-id="07434-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="07434-110">Notes</span><span class="sxs-lookup"><span data-stu-id="07434-110">Remarks</span></span>

<span data-ttu-id="07434-111">Visual Basic prend en charge le commutateur `-refout` à partir de la version 15,3.</span><span class="sxs-lookup"><span data-stu-id="07434-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="07434-112">Les assemblys de référence sont des assemblys de métadonnées uniquement qui contiennent des métadonnées, mais pas de code d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="07434-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="07434-113">Ils incluent des informations sur les types et les membres pour tout sauf les types anonymes.</span><span class="sxs-lookup"><span data-stu-id="07434-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="07434-114">Leurs corps de méthode sont remplacés par une seule instruction `throw null`.</span><span class="sxs-lookup"><span data-stu-id="07434-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="07434-115">La raison de l’utilisation de `throw null` corps de méthode (par opposition à aucun corps) est que PEVerify peut s’exécuter et réussir (validant ainsi l’exhaustivité des métadonnées).</span><span class="sxs-lookup"><span data-stu-id="07434-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="07434-116">Les assemblys de référence incluent un attribut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="07434-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="07434-117">Cet attribut peut être spécifié dans la source (le compilateur n’a plus alors besoin de le synthétiser).</span><span class="sxs-lookup"><span data-stu-id="07434-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="07434-118">En raison de cet attribut, les runtimes refusent de charger des assemblys de référence pour l’exécution (mais ils peuvent toujours être chargés dans un contexte de réflexion uniquement).</span><span class="sxs-lookup"><span data-stu-id="07434-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="07434-119">Les outils qui reflètent sur les assemblys doivent s’assurer qu’ils chargent des assemblys de référence en tant que réflexion uniquement ; dans le cas contraire, le runtime lève une <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="07434-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="07434-120">Les options `-refout` et [`-refonly`](refonly-compiler-option.md) s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="07434-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="07434-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07434-121">See also</span></span>

- [<span data-ttu-id="07434-122">-refonly</span><span class="sxs-lookup"><span data-stu-id="07434-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="07434-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07434-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="07434-124">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="07434-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
