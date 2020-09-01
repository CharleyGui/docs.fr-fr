---
description: -deterministic (Options du compilateur C#)
title: -deterministic (Options du compilateur C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: 9d0bcc2957e5a666c21cdc2ce61e74fc90fe3530
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125824"
---
# <a name="-deterministic"></a><span data-ttu-id="e4932-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="e4932-103">-deterministic</span></span>

<span data-ttu-id="e4932-104">Indique au compilateur de générer un assembly dont la sortie octet-pour-octet est identique dans les compilations pour les entrées identiques.</span><span class="sxs-lookup"><span data-stu-id="e4932-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4932-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4932-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="e4932-106">Notes</span><span class="sxs-lookup"><span data-stu-id="e4932-106">Remarks</span></span>

<span data-ttu-id="e4932-107">Par défaut, le résultat de la compilation d’un ensemble défini d’entrées est unique, étant donné que le compilateur ajoute un horodatage et un GUID qui est généré à partir de nombres aléatoires.</span><span class="sxs-lookup"><span data-stu-id="e4932-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="e4932-108">Utilisez l’option `-deterministic` pour générer un *assembly déterministe*, dont le contenu binaire sera identique dans les compilations tant que l’entrée restera la même.</span><span class="sxs-lookup"><span data-stu-id="e4932-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="e4932-109">Le compilateur considère les entrées suivantes à des fins déterministes :</span><span class="sxs-lookup"><span data-stu-id="e4932-109">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="e4932-110">La séquence des paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e4932-110">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="e4932-111">Le contenu du fichier réponse .rsp du compilateur.</span><span class="sxs-lookup"><span data-stu-id="e4932-111">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="e4932-112">La version précise du compilateur utilisée et ses assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="e4932-112">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="e4932-113">Le chemin de répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="e4932-113">The current directory path.</span></span>
- <span data-ttu-id="e4932-114">Le contenu binaire de tous les fichiers explicitement passés au compilateur directement ou indirectement, notamment :</span><span class="sxs-lookup"><span data-stu-id="e4932-114">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="e4932-115">Fichiers sources</span><span class="sxs-lookup"><span data-stu-id="e4932-115">Source files</span></span>
  - <span data-ttu-id="e4932-116">Assemblys référencés</span><span class="sxs-lookup"><span data-stu-id="e4932-116">Referenced assemblies</span></span>
  - <span data-ttu-id="e4932-117">Modules référencés</span><span class="sxs-lookup"><span data-stu-id="e4932-117">Referenced modules</span></span>
  - <span data-ttu-id="e4932-118">Ressources</span><span class="sxs-lookup"><span data-stu-id="e4932-118">Resources</span></span>
  - <span data-ttu-id="e4932-119">Fichier de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="e4932-119">The strong name key file</span></span>
  - <span data-ttu-id="e4932-120">Fichiers réponse @</span><span class="sxs-lookup"><span data-stu-id="e4932-120">@ response files</span></span>
  - <span data-ttu-id="e4932-121">Analyseurs</span><span class="sxs-lookup"><span data-stu-id="e4932-121">Analyzers</span></span>
  - <span data-ttu-id="e4932-122">Ensembles de règles</span><span class="sxs-lookup"><span data-stu-id="e4932-122">Rulesets</span></span>
  - <span data-ttu-id="e4932-123">Autres fichiers susceptibles d’être utilisés par les analyseurs</span><span class="sxs-lookup"><span data-stu-id="e4932-123">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="e4932-124">La culture actuelle (pour le langage dans lequel les diagnostics et les messages d’exception sont produits).</span><span class="sxs-lookup"><span data-stu-id="e4932-124">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="e4932-125">L’encodage par défaut (ou la page de codes active) si l’encodage n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="e4932-125">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="e4932-126">L’existence, la non-existence et le contenu des fichiers sur les chemins de recherche du compilateur (spécifiés, par exemple, par `-lib` ou `-recurse`).</span><span class="sxs-lookup"><span data-stu-id="e4932-126">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="e4932-127">La plateforme CLR sur laquelle est exécuté le compilateur.</span><span class="sxs-lookup"><span data-stu-id="e4932-127">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="e4932-128">La valeur de `%LIBPATH%`, qui peut affecter le chargement des dépendances de l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="e4932-128">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="e4932-129">Quand les sources sont accessibles à tous, la compilation déterministe peut servir à établir si un fichier binaire est compilé à partir d’une source approuvée.</span><span class="sxs-lookup"><span data-stu-id="e4932-129">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="e4932-130">Il peut aussi être utile dans un système de génération en continu pour déterminer si les étapes de génération qui sont dépendantes des changements apportés à un binaire doivent être exécutées.</span><span class="sxs-lookup"><span data-stu-id="e4932-130">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4932-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4932-131">See also</span></span>

- [<span data-ttu-id="e4932-132">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e4932-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e4932-133">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="e4932-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
