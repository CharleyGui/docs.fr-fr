---
title: Structure des programmes C# - Visite guidée du langage C#
description: Découvrez les composantes élémentaires d’un programme C#
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5e095e71549ed3eec6c73e6a134fdb5a64fb63c0
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884382"
---
# <a name="program-structure"></a><span data-ttu-id="6ec38-103">Structure du programme</span><span class="sxs-lookup"><span data-stu-id="6ec38-103">Program Structure</span></span>

<span data-ttu-id="6ec38-104">Les concepts clés d’organisation en C# sont les ***programmes***, ***espaces de noms***, ***types***, ***membres*** et ***assemblys***.</span><span class="sxs-lookup"><span data-stu-id="6ec38-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="6ec38-105">Les programmes C++, comme les programmes C, se composent d'un ou plusieurs fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="6ec38-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="6ec38-106">Les programmes déclarent des types qui contiennent des membres et peuvent être organisés en espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="6ec38-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="6ec38-107">Les classes et les interfaces sont des exemples de types.</span><span class="sxs-lookup"><span data-stu-id="6ec38-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="6ec38-108">Les champs, méthodes, propriétés et événements sont des exemples de membres.</span><span class="sxs-lookup"><span data-stu-id="6ec38-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="6ec38-109">Lorsque les programmes C# sont compilés, ils sont physiquement empaquetés dans des assemblys.</span><span class="sxs-lookup"><span data-stu-id="6ec38-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="6ec38-110">Les assemblys ont généralement l’extension de fichier `.exe` ou `.dll`, selon qu’elles implémentent des ***applications*** ou des ***bibliothèques***, respectivement.</span><span class="sxs-lookup"><span data-stu-id="6ec38-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="6ec38-111">L’exemple déclare une classe nommée `Stack` dans un espace de noms appelé `Acme.Collections` :</span><span class="sxs-lookup"><span data-stu-id="6ec38-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="6ec38-112">Le nom qualifié complet de cette classe est `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="6ec38-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="6ec38-113">La classe contient plusieurs membres : un champ nommé `top`, deux méthodes nommées `Push` et `Pop`, et une classe imbriquée nommée `Entry`.</span><span class="sxs-lookup"><span data-stu-id="6ec38-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="6ec38-114">La classe `Entry` contient trois membres en plus : un champ nommé `next`, un autre nommé `data` et un constructeur.</span><span class="sxs-lookup"><span data-stu-id="6ec38-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="6ec38-115">En supposant que le code source de l’exemple est stocké dans le fichier `acme.cs`, la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6ec38-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```console
csc /t:library acme.cs
```

<span data-ttu-id="6ec38-116">compile l’exemple en tant que bibliothèque (code sans point d’entrée `Main`) et produit un assembly nommé `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="6ec38-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ec38-117">Les exemples ci-dessus utilisent `csc` en tant que compilateur de ligne de commande C#.</span><span class="sxs-lookup"><span data-stu-id="6ec38-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="6ec38-118">Ce compilateur est un exécutable Windows.</span><span class="sxs-lookup"><span data-stu-id="6ec38-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="6ec38-119">Pour utiliser C# sur d’autres plateformes, vous devez utiliser les outils pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ec38-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="6ec38-120">L’écosystème .NET Core utilise l’interface graphique `dotnet` pour gérer les versions en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="6ec38-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="6ec38-121">Cela inclut la gestion des dépendances et l’appel du compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="6ec38-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="6ec38-122">Consultez [ce didacticiel](../../core/tutorials/cli-create-console-app.md) pour obtenir une description complète de ces outils sur les plateformes prises en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ec38-122">See [this tutorial](../../core/tutorials/cli-create-console-app.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="6ec38-123">Les assemblys contiennent le code exécutable sous forme d’instructions de langage intermédiaire (IL) et des informations symboliques sous la forme de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6ec38-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="6ec38-124">Avant son exécution, le code de langage intermédiaire dans un assembly est automatiquement converti en code spécifique au processeur par le compilateur juste à temps (JIT) du Common Language Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="6ec38-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="6ec38-125">Comme un assembly est une unité de fonctionnalité autodescriptive contenant du code et des métadonnées, les directives `#include` et les fichiers d’en-tête ne sont pas nécessaires en C#.</span><span class="sxs-lookup"><span data-stu-id="6ec38-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="6ec38-126">Les membres et types publics contenus dans un assembly particulier sont disponibles dans un programme C# par simple référence à cet assembly lors de la compilation du programme.</span><span class="sxs-lookup"><span data-stu-id="6ec38-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="6ec38-127">Par exemple, ce programme utilise la classe `Acme.Collections.Stack` à partir de l’assembly `acme.dll` :</span><span class="sxs-lookup"><span data-stu-id="6ec38-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="6ec38-128">Si le programme est stocké dans le fichier `example.cs`, lorsque `example.cs` est compilé, l’assembly acme.dll peut être référencé à l’aide de l’option de compilateur /r :</span><span class="sxs-lookup"><span data-stu-id="6ec38-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```console
csc /r:acme.dll example.cs
```

<span data-ttu-id="6ec38-129">Cela permet de créer un assembly exécutable nommé `example.exe`, qui, lors de l’exécution, produit la sortie :</span><span class="sxs-lookup"><span data-stu-id="6ec38-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="6ec38-130">C# permet le stockage du texte source d’un programme dans plusieurs fichiers source.</span><span class="sxs-lookup"><span data-stu-id="6ec38-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="6ec38-131">Lorsqu’un programme C# multifichier est compilé, tous les fichiers source sont traités ensemble et les fichiers source peuvent librement se référencer mutuellement. Sur le plan conceptuel, c’est comme si tous les fichiers source étaient concaténés en un seul fichier volumineux avant d’être traités.</span><span class="sxs-lookup"><span data-stu-id="6ec38-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="6ec38-132">Déclarations anticipées ne sont jamais nécessaires en C#, car, à de très rares exceptions près, l’ordre de déclaration n’a pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="6ec38-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="6ec38-133">C# ne limite pas un fichier source à la déclaration d’un seul type public et ne nécessite pas non plus que le nom du fichier source corresponde à un type déclaré dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="6ec38-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6ec38-134">[Précédent](index.md)
>[Suivant](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="6ec38-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
