---
title: Génération et compilation de code source dynamique
description: Compilez et générez le code source dynamique dans .NET avec le Code Document Object Model (CodeDOM). Les éléments CodeDOM sont liés pour former un graphique CodeDOM.
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
ms.openlocfilehash: 3cdd89ac9745f6af133ca683afff64283f2727d1
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475097"
---
# <a name="compile-and-generate-dynamic-source-code"></a><span data-ttu-id="7122a-104">Compiler et générer du code source dynamique</span><span class="sxs-lookup"><span data-stu-id="7122a-104">Compile and generate dynamic source code</span></span>

<span data-ttu-id="7122a-105">Le .NET Framework inclut un mécanisme appelé CodeDOM (Code Document Object Model) qui permet aux développeurs d’émettre du code source pour générer du code source dans plusieurs langages de programmation au moment de l’exécution, en fonction d’un modèle unique qui représente le code à restituer.</span><span class="sxs-lookup"><span data-stu-id="7122a-105">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
<span data-ttu-id="7122a-106">Pour représenter le code source, les éléments CodeDOM sont liés entre eux pour former une structure de données appelée graphique CodeDOM, qui modélise la structure d’un code source.</span><span class="sxs-lookup"><span data-stu-id="7122a-106">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
<span data-ttu-id="7122a-107">L’espace de noms <xref:System.CodeDom?displayProperty=fullName> définit les types qui peuvent représenter la structure logique du code source, indépendamment d’un langage de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="7122a-107">The <xref:System.CodeDom?displayProperty=fullName> namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="7122a-108">L’espace de noms <xref:System.CodeDom.Compiler?displayProperty=fullName> définit les types pour la génération du code source à partir des graphiques CodeDOM et la gestion de la compilation du code source dans les langages pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7122a-108">The <xref:System.CodeDom.Compiler?displayProperty=fullName> namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="7122a-109">Les fournisseurs de compilateurs ou les développeurs peuvent étendre l’ensemble des langages pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7122a-109">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
<span data-ttu-id="7122a-110">La modélisation de code source indépendante du langage peut s’avérer précieuse quand un programme a besoin de générer du code source pour un modèle de programme dans plusieurs langages ou pour un langage cible indéterminé.</span><span class="sxs-lookup"><span data-stu-id="7122a-110">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="7122a-111">Par exemple, certains concepteurs utilisent le CodeDOM comme interface d’abstraction de langage pour produire du code source dans le langage de programmation approprié, si la prise en charge CodeDOM de ce langage est disponible.</span><span class="sxs-lookup"><span data-stu-id="7122a-111">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
<span data-ttu-id="7122a-112">Le .NET Framework inclut des générateurs et des compilateurs de code pour <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider> et <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="7122a-112">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7122a-113">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="7122a-113">In this section</span></span>

- [<span data-ttu-id="7122a-114">Utilisation du CodeDOM</span><span class="sxs-lookup"><span data-stu-id="7122a-114">Using the CodeDOM</span></span>](using-the-codedom.md)

  <span data-ttu-id="7122a-115">Décrit les utilisations courantes et illustre la création d’un graphique d’objet simple à l’aide du CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="7122a-115">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
- [<span data-ttu-id="7122a-116">Générer le code source et compiler un programme à partir d’un graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="7122a-116">Generate Source Code and Compile a Program from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)  

  <span data-ttu-id="7122a-117">Décrit comment générer du code source et compiler le code généré avec un compilateur externe à l’aide de classes définies dans l’espace de noms `System.CodeDom.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="7122a-117">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
- [<span data-ttu-id="7122a-118">Guide pratique pour créer un fichier de documentation XML à l’aide de CodeDOM</span><span class="sxs-lookup"><span data-stu-id="7122a-118">How to: Create an XML Documentation File Using CodeDOM</span></span>](how-to-create-an-xml-documentation-file-using-codedom.md)  

  <span data-ttu-id="7122a-119">Décrit comment utiliser CodeDOM pour générer du code avec des commentaires de documentation XML, et compiler le code généré afin qu’il crée la sortie de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="7122a-119">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
- [<span data-ttu-id="7122a-120">Guide pratique pour créer une classe à l’aide de CodeDOM</span><span class="sxs-lookup"><span data-stu-id="7122a-120">How to: Create a Class Using CodeDOM</span></span>](how-to-create-a-class-using-codedom.md)  

  <span data-ttu-id="7122a-121">Décrit comment utiliser CodeDOM pour générer une classe contenant des champs, des propriétés, une méthode, un constructeur et un point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7122a-121">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7122a-122">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="7122a-122">Reference</span></span>  

- <xref:System.CodeDom>  

  <span data-ttu-id="7122a-123">Définit les éléments qui représentent des éléments de code dans les langages de programmation qui ciblent le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="7122a-123">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
- <xref:System.CodeDom.Compiler>  

  <span data-ttu-id="7122a-124">Définit les interfaces de génération et de compilation du code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7122a-124">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7122a-125">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="7122a-125">Related sections</span></span>  

- <span data-ttu-id="7122a-126">La [référence rapide CodeDom](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) offre aux développeurs un moyen rapide de rechercher les éléments CodeDOM qui représentent des éléments de code source.</span><span class="sxs-lookup"><span data-stu-id="7122a-126">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
