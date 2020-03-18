---
title: Structure des programmes C# - Visite guidée du langage C#
description: Découvrez les composantes élémentaires d’un programme C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156829"
---
# <a name="program-structure"></a><span data-ttu-id="c8051-103">Structure du programme</span><span class="sxs-lookup"><span data-stu-id="c8051-103">Program Structure</span></span>

<span data-ttu-id="c8051-104">Les concepts clés d’organisation en C# sont les ***programmes***, ***espaces de noms***, ***types***, ***membres*** et ***assemblys***.</span><span class="sxs-lookup"><span data-stu-id="c8051-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="c8051-105">Les programmes C++, comme les programmes C, se composent d'un ou plusieurs fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="c8051-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="c8051-106">Les programmes déclarent des types qui contiennent des membres et peuvent être organisés en espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="c8051-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="c8051-107">Les classes et les interfaces sont des exemples de types.</span><span class="sxs-lookup"><span data-stu-id="c8051-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="c8051-108">Les champs, méthodes, propriétés et événements sont des exemples de membres.</span><span class="sxs-lookup"><span data-stu-id="c8051-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="c8051-109">Lorsque les programmes C sont compilés, ils sont physiquement emballés dans des assemblages.</span><span class="sxs-lookup"><span data-stu-id="c8051-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="c8051-110">Les assemblys ont généralement l’extension de fichier `.exe` ou `.dll`, selon qu’elles implémentent des ***applications*** ou des ***bibliothèques***, respectivement.</span><span class="sxs-lookup"><span data-stu-id="c8051-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="c8051-111">Vous pouvez créer un projet de `dotnet new` bibliothèque nommé *acme* à l’aide de la commande :</span><span class="sxs-lookup"><span data-stu-id="c8051-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="c8051-112">Dans ce projet, déclarez une classe nommée `Stack` dans un namespace appelé `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="c8051-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="c8051-113">Le nom qualifié complet de cette classe est `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="c8051-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="c8051-114">La classe contient plusieurs membres : un champ nommé `top`, deux méthodes nommées `Push` et `Pop`, et une classe imbriquée nommée `Entry`.</span><span class="sxs-lookup"><span data-stu-id="c8051-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="c8051-115">La classe `Entry` contient trois membres en plus : un champ nommé `next`, un autre nommé `data` et un constructeur.</span><span class="sxs-lookup"><span data-stu-id="c8051-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="c8051-116">La commande:</span><span class="sxs-lookup"><span data-stu-id="c8051-116">The command:</span></span>

```console
dotnet build
```

<span data-ttu-id="c8051-117">compile l’exemple en tant que bibliothèque (code sans point d’entrée `Main`) et produit un assembly nommé `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="c8051-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="c8051-118">Les assemblys contiennent le code exécutable sous forme d’instructions de langage intermédiaire (IL) et des informations symboliques sous la forme de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c8051-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="c8051-119">Avant son exécution, le compilateur Just-In-Time (JIT) de .NET Common Language Runtime convertit le code IL dans un assemblage en code spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="c8051-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="c8051-120">Étant donné qu’un assemblage est une unité de fonctionnalité auto-décrivant contenant `#include` à la fois du code et des métadonnées, il n’est pas nécessaire de directives et de fichiers d’en-tête dans C.</span><span class="sxs-lookup"><span data-stu-id="c8051-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="c8051-121">Les membres et types publics contenus dans un assembly particulier sont disponibles dans un programme C# par simple référence à cet assembly lors de la compilation du programme.</span><span class="sxs-lookup"><span data-stu-id="c8051-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="c8051-122">Par exemple, ce programme utilise la classe `Acme.Collections.Stack` à partir de l’assembly `acme.dll` :</span><span class="sxs-lookup"><span data-stu-id="c8051-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="c8051-123">Le fichier *csproj* pour le projet du programme précédent doit inclure un nœud de référence `acme.dll` pour le compilateur C pour résoudre les références aux classes de l’assemblée :</span><span class="sxs-lookup"><span data-stu-id="c8051-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="c8051-124">Après cet `dotnet build` ajout, crée un `example.exe`assemblage exécutable nommé , qui, une fois exécuté, produit la sortie:</span><span class="sxs-lookup"><span data-stu-id="c8051-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="c8051-125">C# permet le stockage du texte source d’un programme dans plusieurs fichiers source.</span><span class="sxs-lookup"><span data-stu-id="c8051-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="c8051-126">Lorsqu’un programme C# multifichier est compilé, tous les fichiers source sont traités ensemble et les fichiers source peuvent librement se référencer mutuellement. Sur le plan conceptuel, c’est comme si tous les fichiers source étaient concaténés en un seul fichier volumineux avant d’être traités.</span><span class="sxs-lookup"><span data-stu-id="c8051-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="c8051-127">Les déclarations prospectives ne sont jamais nécessaires dans le C parce que, à quelques exceptions près, l’ordre de déclaration est insignifiant.</span><span class="sxs-lookup"><span data-stu-id="c8051-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="c8051-128">C# ne limite pas un fichier source à la déclaration d’un seul type public et ne nécessite pas non plus que le nom du fichier source corresponde à un type déclaré dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="c8051-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8051-129">[Suivant précédent](index.md)
>[Next](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="c8051-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
