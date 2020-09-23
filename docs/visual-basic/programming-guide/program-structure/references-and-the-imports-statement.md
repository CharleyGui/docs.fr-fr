---
title: Références et instruction Imports
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 13f250e1b015e5a821da83e557033bc878a8a3b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097902"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="cc705-102">Références et l'instruction Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc705-102">References and the Imports Statement (Visual Basic)</span></span>

<span data-ttu-id="cc705-103">Vous pouvez rendre des objets externes disponibles pour votre projet en sélectionnant la commande **Ajouter une référence** dans le menu **projet** .</span><span class="sxs-lookup"><span data-stu-id="cc705-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="cc705-104">Les références dans Visual Basic peuvent pointer vers des assemblys, comme les bibliothèques de types, mais contiennent davantage d’informations.</span><span class="sxs-lookup"><span data-stu-id="cc705-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="cc705-105">Instruction Imports</span><span class="sxs-lookup"><span data-stu-id="cc705-105">The Imports Statement</span></span>  

 <span data-ttu-id="cc705-106">Les assemblys incluent un ou plusieurs espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="cc705-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="cc705-107">Lorsque vous ajoutez une référence à un assembly, vous pouvez également ajouter une `Imports` instruction à un module qui contrôle la visibilité des espaces de noms de cet assembly dans le module.</span><span class="sxs-lookup"><span data-stu-id="cc705-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="cc705-108">L' `Imports` instruction fournit un contexte d’étendue qui vous permet d’utiliser uniquement la partie de l’espace de noms nécessaire pour fournir une référence unique.</span><span class="sxs-lookup"><span data-stu-id="cc705-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="cc705-109">L' `Imports` instruction a la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="cc705-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="cc705-110">`Aliasname` fait référence à un nom abrégé que vous pouvez utiliser dans le code pour faire référence à un espace de noms importé.</span><span class="sxs-lookup"><span data-stu-id="cc705-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="cc705-111">`Namespace` est un espace de noms disponible via une référence de projet, par le biais d’une définition dans le projet ou par le biais d’une `Imports` instruction précédente.</span><span class="sxs-lookup"><span data-stu-id="cc705-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="cc705-112">Un module peut contenir un nombre quelconque d' `Imports` instructions.</span><span class="sxs-lookup"><span data-stu-id="cc705-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="cc705-113">Ils doivent apparaître après toutes les `Option` instructions, le cas échéant, mais avant tout autre code.</span><span class="sxs-lookup"><span data-stu-id="cc705-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc705-114">Ne confondez pas les références de projet avec l' `Imports` instruction ou l' `Declare` instruction.</span><span class="sxs-lookup"><span data-stu-id="cc705-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="cc705-115">Les références de projet rendent des objets externes, tels que des objets dans les assemblys, accessibles aux projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc705-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="cc705-116">L' `Imports` instruction est utilisée pour simplifier l’accès aux références de projet, mais ne fournit pas l’accès à ces objets.</span><span class="sxs-lookup"><span data-stu-id="cc705-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="cc705-117">L' `Declare` instruction permet de déclarer une référence à une procédure externe dans une bibliothèque de liens dynamiques (dll).</span><span class="sxs-lookup"><span data-stu-id="cc705-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="cc705-118">Utilisation d’alias avec l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="cc705-118">Using Aliases with the Imports Statement</span></span>  

 <span data-ttu-id="cc705-119">Grâce à l' `Imports` instruction, il est plus facile d’accéder aux méthodes des classes en éliminant le besoin de taper explicitement les noms complets des références.</span><span class="sxs-lookup"><span data-stu-id="cc705-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="cc705-120">Les alias vous permettent d’assigner un nom plus convivial à une seule partie d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cc705-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="cc705-121">Par exemple, la séquence de retour chariot/saut de ligne qui provoque l’affichage d’une seule partie du texte sur plusieurs lignes fait partie du <xref:Microsoft.VisualBasic.ControlChars> module dans l' <xref:Microsoft.VisualBasic?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cc705-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="cc705-122">Pour utiliser cette constante dans un programme sans alias, vous devez taper le code suivant :</span><span class="sxs-lookup"><span data-stu-id="cc705-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="cc705-123">`Imports` les instructions doivent toujours être les premières lignes qui suivent immédiatement les `Option` instructions d’un module.</span><span class="sxs-lookup"><span data-stu-id="cc705-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="cc705-124">Le fragment de code suivant montre comment importer et assigner un alias au <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module :</span><span class="sxs-lookup"><span data-stu-id="cc705-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="cc705-125">Les futures références à cet espace de noms peuvent être beaucoup plus courtes :</span><span class="sxs-lookup"><span data-stu-id="cc705-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="cc705-126">Si une `Imports` instruction n’inclut pas de nom d’alias, les éléments définis dans l’espace de noms importé peuvent être utilisés dans le module sans qualification.</span><span class="sxs-lookup"><span data-stu-id="cc705-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="cc705-127">Si le nom d’alias est spécifié, il doit être utilisé en tant que qualificateur pour les noms contenus dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cc705-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc705-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc705-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="cc705-129">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc705-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="cc705-130">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="cc705-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="cc705-131">Imports, instruction (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="cc705-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
