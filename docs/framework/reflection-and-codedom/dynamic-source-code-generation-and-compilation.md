---
title: Génération et compilation de code source dynamique
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
ms.openlocfilehash: a7e341bb5bfb5b4648a222409951275169a29b79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130253"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="91c7a-102">Génération et compilation de code source dynamique</span><span class="sxs-lookup"><span data-stu-id="91c7a-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="91c7a-103">Le .NET Framework inclut un mécanisme appelé CodeDOM (Code Document Object Model) qui permet aux développeurs d’émettre du code source pour générer du code source dans plusieurs langages de programmation au moment de l’exécution, en fonction d’un modèle unique qui représente le code à restituer.</span><span class="sxs-lookup"><span data-stu-id="91c7a-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="91c7a-104">Pour représenter le code source, les éléments CodeDOM sont liés entre eux pour former une structure de données appelée graphique CodeDOM, qui modélise la structure d’un code source.</span><span class="sxs-lookup"><span data-stu-id="91c7a-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="91c7a-105">L’espace de noms `System.CodeDom` définit les types qui peuvent représenter la structure logique du code source, indépendamment d’un langage de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="91c7a-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="91c7a-106">L’espace de noms `System.CodeDom.Compiler` définit les types pour la génération du code source à partir des graphiques CodeDOM et la gestion de la compilation du code source dans les langages pris en charge.</span><span class="sxs-lookup"><span data-stu-id="91c7a-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="91c7a-107">Les fournisseurs de compilateurs ou les développeurs peuvent étendre l’ensemble des langages pris en charge.</span><span class="sxs-lookup"><span data-stu-id="91c7a-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="91c7a-108">La modélisation de code source indépendante du langage peut s’avérer précieuse quand un programme a besoin de générer du code source pour un modèle de programme dans plusieurs langages ou pour un langage cible indéterminé.</span><span class="sxs-lookup"><span data-stu-id="91c7a-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="91c7a-109">Par exemple, certains concepteurs utilisent le CodeDOM comme interface d’abstraction de langage pour produire du code source dans le langage de programmation approprié, si la prise en charge CodeDOM de ce langage est disponible.</span><span class="sxs-lookup"><span data-stu-id="91c7a-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="91c7a-110">Le .NET Framework inclut des générateurs et des compilateurs de code pour <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider> et <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="91c7a-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91c7a-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="91c7a-111">In This Section</span></span>  
 [<span data-ttu-id="91c7a-112">Utilisation du CodeDOM</span><span class="sxs-lookup"><span data-stu-id="91c7a-112">Using the CodeDOM</span></span>](using-the-codedom.md)  
 <span data-ttu-id="91c7a-113">Décrit les utilisations courantes et illustre la création d’un graphique d’objet simple à l’aide du CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="91c7a-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="91c7a-114">Génération de code source et compilation d’un programme à partir d’un graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="91c7a-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="91c7a-115">Décrit comment générer du code source et compiler le code généré avec un compilateur externe à l’aide de classes définies dans l’espace de noms `System.CodeDom.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="91c7a-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="91c7a-116">Guide pratique pour créer un fichier de documentation XML à l’aide de CodeDOM</span><span class="sxs-lookup"><span data-stu-id="91c7a-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="91c7a-117">Décrit comment utiliser CodeDOM pour générer du code avec des commentaires de documentation XML, et compiler le code généré afin qu’il crée la sortie de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="91c7a-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="91c7a-118">Guide pratique pour créer une classe à l’aide de CodeDOM</span><span class="sxs-lookup"><span data-stu-id="91c7a-118">How to: Create a Class Using CodeDOM</span></span>](how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="91c7a-119">Décrit comment utiliser CodeDOM pour générer une classe contenant des champs, des propriétés, une méthode, un constructeur et un point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="91c7a-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="91c7a-120">Reference</span><span class="sxs-lookup"><span data-stu-id="91c7a-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="91c7a-121">Définit les éléments qui représentent des éléments de code dans les langages de programmation qui ciblent le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="91c7a-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="91c7a-122">Définit les interfaces de génération et de compilation du code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="91c7a-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="91c7a-123">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="91c7a-123">Related Sections</span></span>  
 <span data-ttu-id="91c7a-124">[Aide-mémoire de CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91c7a-124">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>  
 <span data-ttu-id="91c7a-125">Fournit aux développeurs un moyen de trouver rapidement des éléments CodeDOM qui représentent des éléments du code source.</span><span class="sxs-lookup"><span data-stu-id="91c7a-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
