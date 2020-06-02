---
title: Application des attributs
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 5557da1531eb55c13d1c7540a50b044d1a7b8a1d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276333"
---
# <a name="applying-attributes"></a><span data-ttu-id="b41b8-102">Application des attributs</span><span class="sxs-lookup"><span data-stu-id="b41b8-102">Applying Attributes</span></span>
<span data-ttu-id="b41b8-103">Effectuez la procédure suivante pour appliquer un attribut à un élément de votre code.</span><span class="sxs-lookup"><span data-stu-id="b41b8-103">Use the following process to apply an attribute to an element of your code.</span></span>  
  
1. <span data-ttu-id="b41b8-104">Définissez un nouvel attribut ou utilisez un attribut existant en important son espace de noms à partir de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b41b8-104">Define a new attribute or use an existing attribute by importing its namespace from the .NET Framework.</span></span>  
  
2. <span data-ttu-id="b41b8-105">Appliquez l’attribut à l’élément de code en le plaçant immédiatement avant l’élément.</span><span class="sxs-lookup"><span data-stu-id="b41b8-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>  
  
     <span data-ttu-id="b41b8-106">Chaque langage possède sa propre syntaxe d’attribut.</span><span class="sxs-lookup"><span data-stu-id="b41b8-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="b41b8-107">Dans C++ et C#, l’attribut est entouré par des crochets et séparé de l’élément par un espace blanc, qui peut inclure un saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="b41b8-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="b41b8-108">Dans Visual Basic, l’attribut est entouré par des crochets angulaires et doit se trouver sur la même ligne logique. Le caractère de continuation de ligne peut être utilisé si vous souhaitez un saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="b41b8-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>
  
3. <span data-ttu-id="b41b8-109">Spécifiez des paramètres positionnels et des paramètres nommés pour l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b41b8-109">Specify positional parameters and named parameters for the attribute.</span></span>  
  
     <span data-ttu-id="b41b8-110">Les paramètres positionnels sont requis et doivent précéder les paramètres nommés. Ils correspondent aux paramètres d’un des constructeurs de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b41b8-110">Positional parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="b41b8-111">Les paramètres nommés sont facultatifs et correspondent aux propriétés de lecture/écriture de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b41b8-111">Named parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="b41b8-112">En C++ et C#, spécifiez `name`=`value` pour chaque paramètre facultatif, où `name` est le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b41b8-112">In C++, and C#, specify `name`=`value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="b41b8-113">Dans Visual Basic, spécifiez `name`:=`value`.</span><span class="sxs-lookup"><span data-stu-id="b41b8-113">In Visual Basic, specify `name`:=`value`.</span></span>  
  
 <span data-ttu-id="b41b8-114">L’attribut est émis dans des métadonnées lorsque vous compilez votre code et est disponible pour le common language runtime et toute application ou tout outil personnalisé via les services de réflexion du runtime.</span><span class="sxs-lookup"><span data-stu-id="b41b8-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>  
  
 <span data-ttu-id="b41b8-115">Par convention, tous les noms d’attribut se terminent par Attribute.</span><span class="sxs-lookup"><span data-stu-id="b41b8-115">By convention, all attribute names end with Attribute.</span></span> <span data-ttu-id="b41b8-116">Toutefois, plusieurs langages qui ciblent le runtime, tels que Visual Basic et C#, ne nécessitent pas de spécifier le nom complet d’un attribut.</span><span class="sxs-lookup"><span data-stu-id="b41b8-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="b41b8-117">Par exemple, si vous souhaitez initialiser <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, vous devez uniquement le référencer en tant qu’attribut **obsolète**.</span><span class="sxs-lookup"><span data-stu-id="b41b8-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>  
  
## <a name="applying-an-attribute-to-a-method"></a><span data-ttu-id="b41b8-118">Application d’un attribut à une méthode</span><span class="sxs-lookup"><span data-stu-id="b41b8-118">Applying an Attribute to a Method</span></span>  
 <span data-ttu-id="b41b8-119">L’exemple de code suivant montre comment déclarer **System.ObsoleteAttribute**, qui marque le code comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="b41b8-119">The following code example shows how to declare **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="b41b8-120">La chaîne `"Will be removed in next version"` est passée à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b41b8-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="b41b8-121">Cet attribut provoque un avertissement du compilateur qui affiche la chaîne passée lorsque le code que l’attribut décrit est appelé.</span><span class="sxs-lookup"><span data-stu-id="b41b8-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a><span data-ttu-id="b41b8-122">Application d’attributs au niveau de l’assembly</span><span class="sxs-lookup"><span data-stu-id="b41b8-122">Applying Attributes at the Assembly Level</span></span>  
 <span data-ttu-id="b41b8-123">Si vous souhaitez appliquer un attribut au niveau de l’assembly, utilisez le mot clé **assembly** ( `Assembly` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b41b8-123">If you want to apply an attribute at the assembly level, use the **assembly** (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="b41b8-124">Le code suivant illustre l’attribut **AssemblyTitleAttribute** appliqué au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b41b8-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 <span data-ttu-id="b41b8-125">Lorsque cet attribut est appliqué, la chaîne `"My Assembly"` est placée dans le manifeste de l’assembly dans la partie métadonnées du fichier.</span><span class="sxs-lookup"><span data-stu-id="b41b8-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="b41b8-126">Vous pouvez afficher l’attribut à l’aide du [Désassembleur MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) ou en créant un programme personnalisé pour récupérer l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b41b8-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41b8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b41b8-127">See also</span></span>

- [<span data-ttu-id="b41b8-128">Attributs</span><span class="sxs-lookup"><span data-stu-id="b41b8-128">Attributes</span></span>](index.md)
- [<span data-ttu-id="b41b8-129">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="b41b8-129">Retrieving Information Stored in Attributes</span></span>](retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="b41b8-130">Concepts</span><span class="sxs-lookup"><span data-stu-id="b41b8-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)
- [<span data-ttu-id="b41b8-131">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="b41b8-131">Attributes (C#)</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="b41b8-132">Vue d’ensemble des attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b41b8-132">Attributes overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)
