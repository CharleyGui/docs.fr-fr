---
title: Documentation de votre code avec le langage XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347439"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="a08b6-102">Documentation de votre code avec le langage XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a08b6-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="a08b6-103">In Visual Basic, you can document your code using XML</span><span class="sxs-lookup"><span data-stu-id="a08b6-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="a08b6-104">Commentaires de documentation XML</span><span class="sxs-lookup"><span data-stu-id="a08b6-104">XML Documentation Comments</span></span>

<span data-ttu-id="a08b6-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span><span class="sxs-lookup"><span data-stu-id="a08b6-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="a08b6-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span><span class="sxs-lookup"><span data-stu-id="a08b6-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="a08b6-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span><span class="sxs-lookup"><span data-stu-id="a08b6-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="a08b6-108">Pour plus d’informations, consultez [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="a08b6-108">For more information, see [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="a08b6-109">The XML file can be consumed or otherwise manipulated as XML.</span><span class="sxs-lookup"><span data-stu-id="a08b6-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="a08b6-110">This file is located in the same directory as the output .exe or .dll file of your project.</span><span class="sxs-lookup"><span data-stu-id="a08b6-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="a08b6-111">XML documentation starts with `'''`.</span><span class="sxs-lookup"><span data-stu-id="a08b6-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="a08b6-112">Le traitement de ces commentaires présente certaines restrictions :</span><span class="sxs-lookup"><span data-stu-id="a08b6-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="a08b6-113">La documentation doit être dans un format XML correct.</span><span class="sxs-lookup"><span data-stu-id="a08b6-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="a08b6-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span><span class="sxs-lookup"><span data-stu-id="a08b6-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="a08b6-115">Les développeurs sont libres de créer leur propre jeu de balises.</span><span class="sxs-lookup"><span data-stu-id="a08b6-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="a08b6-116">There is a recommended set of tags (see "Related Sections" in this topic).</span><span class="sxs-lookup"><span data-stu-id="a08b6-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="a08b6-117">Certaines des balises recommandées ont des significations spéciales :</span><span class="sxs-lookup"><span data-stu-id="a08b6-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="a08b6-118">La balise \<param> est utilisée pour décrire les paramètres.</span><span class="sxs-lookup"><span data-stu-id="a08b6-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="a08b6-119">Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="a08b6-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="a08b6-120">If the verification fails, the compiler issues a warning.</span><span class="sxs-lookup"><span data-stu-id="a08b6-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="a08b6-121">L’attribut `cref` peut être joint à n’importe quelle balise pour fournir une référence à un élément de code.</span><span class="sxs-lookup"><span data-stu-id="a08b6-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="a08b6-122">Le compilateur vérifie l’existence de cet élément de code.</span><span class="sxs-lookup"><span data-stu-id="a08b6-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="a08b6-123">If the verification fails, the compiler issues a warning.</span><span class="sxs-lookup"><span data-stu-id="a08b6-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="a08b6-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span><span class="sxs-lookup"><span data-stu-id="a08b6-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="a08b6-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span><span class="sxs-lookup"><span data-stu-id="a08b6-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a08b6-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a08b6-126">Related Sections</span></span>

<span data-ttu-id="a08b6-127">For details on creating an XML file with documentation comments, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="a08b6-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="a08b6-128">-doc</span><span class="sxs-lookup"><span data-stu-id="a08b6-128">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)

- [<span data-ttu-id="a08b6-129">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="a08b6-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

- [<span data-ttu-id="a08b6-130">Traitement du fichier XML</span><span class="sxs-lookup"><span data-stu-id="a08b6-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [<span data-ttu-id="a08b6-131">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="a08b6-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [<span data-ttu-id="a08b6-132">Outils XML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a08b6-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="a08b6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a08b6-133">See also</span></span>

- [<span data-ttu-id="a08b6-134">Développement d’applications avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a08b6-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="a08b6-135">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a08b6-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
