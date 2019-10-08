---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: 6a83b636dd83534788f3a38971e0fef2919314f5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005634"
---
# <a name="-deterministic"></a><span data-ttu-id="3c0a2-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="3c0a2-102">-deterministic</span></span>

<span data-ttu-id="3c0a2-103">Indique au compilateur de générer un assembly dont la sortie octet-pour-octet est identique dans les compilations pour les entrées identiques.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="3c0a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c0a2-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="3c0a2-105">Notes</span><span class="sxs-lookup"><span data-stu-id="3c0a2-105">Remarks</span></span>

<span data-ttu-id="3c0a2-106">Par défaut, le résultat de la compilation d’un ensemble défini d’entrées est unique, étant donné que le compilateur ajoute un horodatage et un GUID qui est généré à partir de nombres aléatoires.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="3c0a2-107">Utilisez l’option `-deterministic` pour générer un *assembly déterministe*, dont le contenu binaire sera identique dans les compilations tant que l’entrée restera la même.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="3c0a2-108">Le compilateur considère les entrées suivantes à des fins déterministes :</span><span class="sxs-lookup"><span data-stu-id="3c0a2-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="3c0a2-109">La séquence des paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="3c0a2-110">Le contenu du fichier réponse .rsp du compilateur.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="3c0a2-111">La version précise du compilateur utilisée et ses assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="3c0a2-112">Le chemin de répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-112">The current directory path.</span></span>
- <span data-ttu-id="3c0a2-113">Le contenu binaire de tous les fichiers explicitement passés au compilateur directement ou indirectement, notamment :</span><span class="sxs-lookup"><span data-stu-id="3c0a2-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="3c0a2-114">Fichiers sources</span><span class="sxs-lookup"><span data-stu-id="3c0a2-114">Source files</span></span>
  - <span data-ttu-id="3c0a2-115">Assemblys référencés</span><span class="sxs-lookup"><span data-stu-id="3c0a2-115">Referenced assemblies</span></span>
  - <span data-ttu-id="3c0a2-116">Modules référencés</span><span class="sxs-lookup"><span data-stu-id="3c0a2-116">Referenced modules</span></span>
  - <span data-ttu-id="3c0a2-117">Ressources</span><span class="sxs-lookup"><span data-stu-id="3c0a2-117">Resources</span></span>
  - <span data-ttu-id="3c0a2-118">Fichier de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="3c0a2-118">The strong name key file</span></span>
  - <span data-ttu-id="3c0a2-119">Fichiers réponse @</span><span class="sxs-lookup"><span data-stu-id="3c0a2-119">@ response files</span></span>
  - <span data-ttu-id="3c0a2-120">Analyseurs</span><span class="sxs-lookup"><span data-stu-id="3c0a2-120">Analyzers</span></span>
  - <span data-ttu-id="3c0a2-121">Ensembles de règles</span><span class="sxs-lookup"><span data-stu-id="3c0a2-121">Rulesets</span></span>
  - <span data-ttu-id="3c0a2-122">Autres fichiers susceptibles d’être utilisés par les analyseurs</span><span class="sxs-lookup"><span data-stu-id="3c0a2-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="3c0a2-123">La culture actuelle (pour le langage dans lequel les diagnostics et les messages d’exception sont produits).</span><span class="sxs-lookup"><span data-stu-id="3c0a2-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="3c0a2-124">L’encodage par défaut (ou la page de codes active) si l’encodage n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="3c0a2-125">L’existence, la non-existence et le contenu des fichiers sur les chemins de recherche du compilateur (spécifiés, par exemple, par `/lib` ou `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="3c0a2-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="3c0a2-126">La plateforme CLR sur laquelle est exécuté le compilateur.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="3c0a2-127">La valeur de `%LIBPATH%`, qui peut affecter le chargement des dépendances de l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="3c0a2-128">Quand les sources sont accessibles à tous, la compilation déterministe peut servir à établir si un fichier binaire est compilé à partir d’une source approuvée.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="3c0a2-129">Il peut aussi être utile dans un système de génération en continu pour déterminer si les étapes de génération qui sont dépendantes des changements apportés à un binaire doivent être exécutées.</span><span class="sxs-lookup"><span data-stu-id="3c0a2-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c0a2-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c0a2-130">See also</span></span>

- [<span data-ttu-id="3c0a2-131">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c0a2-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3c0a2-132">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="3c0a2-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
