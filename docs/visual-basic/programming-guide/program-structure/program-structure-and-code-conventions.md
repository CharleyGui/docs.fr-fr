---
title: Structure de programme et conventions de code
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: ee61c676f3ff554267f6659453ec55e45df69aee
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072117"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="dfb2d-102">Structure de programme et conventions de codage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfb2d-102">Program Structure and Code Conventions (Visual Basic)</span></span>

<span data-ttu-id="dfb2d-103">Cette section présente la structure de programme Visual Basic classique, fournit un programme de Visual Basic simple, « Hello, World », et traite des conventions de code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="dfb2d-104">Les conventions de code sont des suggestions qui se concentrent pas sur la logique d’un programme, mais sur sa structure et son apparence physiques.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="dfb2d-105">Le fait de les suivre rend votre code plus facile à lire, à comprendre et à entretenir.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="dfb2d-106">Les conventions de code peuvent inclure, entre autres :</span><span class="sxs-lookup"><span data-stu-id="dfb2d-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="dfb2d-107">Formats standardisés pour l’étiquetage et la commentaires du code.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="dfb2d-108">Instructions relatives à l’espacement, à la mise en forme et à la mise en retrait du code.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="dfb2d-109">Conventions d’affectation des noms pour les objets, les variables et les procédures.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="dfb2d-110">Les rubriques suivantes présentent un ensemble d’instructions de programmation pour Visual Basic programmes, ainsi que des exemples d’utilisation correcte.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dfb2d-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dfb2d-111">In This Section</span></span>  

 [<span data-ttu-id="dfb2d-112">Structure d'un programme Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfb2d-112">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="dfb2d-113">Fournit une vue d’ensemble des éléments qui composent un programme Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="dfb2d-114">Procédure Main dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfb2d-114">Main Procedure in Visual Basic</span></span>](main-procedure.md)  
 <span data-ttu-id="dfb2d-115">Décrit la procédure qui sert de point de départ et de contrôle global pour votre application.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="dfb2d-116">Références et instruction Imports</span><span class="sxs-lookup"><span data-stu-id="dfb2d-116">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)  
 <span data-ttu-id="dfb2d-117">Explique comment référencer des objets dans d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="dfb2d-118">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfb2d-118">Namespaces in Visual Basic</span></span>](namespaces.md)  
 <span data-ttu-id="dfb2d-119">Décrit comment les espaces de noms organisent les objets dans les assemblys.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="dfb2d-120">Conventions d'affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfb2d-120">Visual Basic Naming Conventions</span></span>](naming-conventions.md)  
 <span data-ttu-id="dfb2d-121">Contient des instructions générales pour nommer des procédures, des constantes, des variables, des arguments et des objets.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="dfb2d-122">Conventions de codage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfb2d-122">Visual Basic Coding Conventions</span></span>](coding-conventions.md)  
 <span data-ttu-id="dfb2d-123">Examine les instructions utilisées dans le développement des exemples dans cette documentation.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="dfb2d-124">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="dfb2d-124">Conditional Compilation</span></span>](conditional-compilation.md)  
 <span data-ttu-id="dfb2d-125">Décrit comment compiler des blocs de code particuliers de manière sélective tout en dirigeant le compilateur pour ignorer d’autres.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="dfb2d-126">Procédure : Diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="dfb2d-126">How to: Break and Combine Statements in Code</span></span>](how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="dfb2d-127">Montre comment diviser des instructions longues en plusieurs lignes et combiner des instructions courtes sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="dfb2d-128">Procédure : Réduire et masquer des sections de code</span><span class="sxs-lookup"><span data-stu-id="dfb2d-128">How to: Collapse and Hide Sections of Code</span></span>](how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="dfb2d-129">Montre comment réduire et masquer des sections de code dans l’éditeur de code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="dfb2d-130">Procédure : Étiqueter des instructions</span><span class="sxs-lookup"><span data-stu-id="dfb2d-130">How to: Label Statements</span></span>](how-to-label-statements.md)  
 <span data-ttu-id="dfb2d-131">Montre comment marquer une ligne de code pour l’identifier pour une utilisation avec des instructions telles que `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="dfb2d-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="dfb2d-132">Caractères spéciaux dans le code</span><span class="sxs-lookup"><span data-stu-id="dfb2d-132">Special Characters in Code</span></span>](special-characters-in-code.md)  
 <span data-ttu-id="dfb2d-133">Montre comment et où utiliser des caractères non numériques et non alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="dfb2d-134">Commentaires dans le code</span><span class="sxs-lookup"><span data-stu-id="dfb2d-134">Comments in Code</span></span>](comments-in-code.md)  
 <span data-ttu-id="dfb2d-135">Explique comment ajouter des commentaires descriptifs à votre code.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="dfb2d-136">Mots clés comme noms d’éléments dans le code</span><span class="sxs-lookup"><span data-stu-id="dfb2d-136">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)  
 <span data-ttu-id="dfb2d-137">Décrit comment utiliser des crochets ( `[]` ) pour délimiter les noms de variables qui sont également Visual Basic Mots clés.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="dfb2d-138">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="dfb2d-138">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)  
 <span data-ttu-id="dfb2d-139">Décrit les différentes façons de faire référence aux éléments d’un programme Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="dfb2d-140">Restrictions liées à Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfb2d-140">Visual Basic Limitations</span></span>](limitations.md)  
 <span data-ttu-id="dfb2d-141">Décrit la suppression des limites de codage connues dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dfb2d-142">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="dfb2d-142">Related Sections</span></span>  

 [<span data-ttu-id="dfb2d-143">Conventions typographiques et de code</span><span class="sxs-lookup"><span data-stu-id="dfb2d-143">Typographic and Code Conventions</span></span>](../../language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="dfb2d-144">Fournit des conventions de codage standard pour Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="dfb2d-145">Écriture de code</span><span class="sxs-lookup"><span data-stu-id="dfb2d-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="dfb2d-146">Décrit les fonctionnalités qui facilitent l’écriture et la gestion de votre code.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-146">Describes features that make it easier for you to write and manage your code.</span></span>
