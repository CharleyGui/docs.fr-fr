---
title: Documentation de votre code avec le langage XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 58c8716450fd8310b81050c86dc297c5b7527761
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524509"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="18d79-102">Documentation de votre code avec le langage XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18d79-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="18d79-103">Dans Visual Basic, vous pouvez documenter votre code à l’aide de XML</span><span class="sxs-lookup"><span data-stu-id="18d79-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="18d79-104">Commentaires de documentation XML</span><span class="sxs-lookup"><span data-stu-id="18d79-104">XML Documentation Comments</span></span>

<span data-ttu-id="18d79-105">Visual Basic offre un moyen simple de créer automatiquement la documentation XML pour les projets.</span><span class="sxs-lookup"><span data-stu-id="18d79-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="18d79-106">Vous pouvez générer automatiquement un squelette XML pour vos types et membres, puis fournir des résumés, une documentation descriptive pour chaque paramètre et d’autres remarques.</span><span class="sxs-lookup"><span data-stu-id="18d79-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="18d79-107">Avec l’installation appropriée, la documentation XML est automatiquement émise dans un fichier XML portant le même nom que votre projet et l’extension. Xml.</span><span class="sxs-lookup"><span data-stu-id="18d79-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="18d79-108">Pour plus d’informations, consultez [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="18d79-108">For more information, see [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="18d79-109">Le fichier XML peut être consommé ou manipulé en tant que XML.</span><span class="sxs-lookup"><span data-stu-id="18d79-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="18d79-110">Ce fichier se trouve dans le même répertoire que le fichier. exe ou. dll de sortie de votre projet.</span><span class="sxs-lookup"><span data-stu-id="18d79-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="18d79-111">La documentation XML commence par `'''`.</span><span class="sxs-lookup"><span data-stu-id="18d79-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="18d79-112">Le traitement de ces commentaires présente certaines restrictions :</span><span class="sxs-lookup"><span data-stu-id="18d79-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="18d79-113">La documentation doit être dans un format XML correct.</span><span class="sxs-lookup"><span data-stu-id="18d79-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="18d79-114">Si le XML n’est pas bien formé, un avertissement est généré et le fichier de documentation contient un commentaire indiquant qu’une erreur a été rencontrée.</span><span class="sxs-lookup"><span data-stu-id="18d79-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="18d79-115">Les développeurs sont libres de créer leur propre jeu de balises.</span><span class="sxs-lookup"><span data-stu-id="18d79-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="18d79-116">Il existe un ensemble recommandé de balises (voir « sections connexes » dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="18d79-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="18d79-117">Certaines des balises recommandées ont des significations spéciales :</span><span class="sxs-lookup"><span data-stu-id="18d79-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="18d79-118">La balise \<param> est utilisée pour décrire les paramètres.</span><span class="sxs-lookup"><span data-stu-id="18d79-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="18d79-119">Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="18d79-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="18d79-120">Si la vérification échoue, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="18d79-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="18d79-121">L’attribut `cref` peut être joint à n’importe quelle balise pour fournir une référence à un élément de code.</span><span class="sxs-lookup"><span data-stu-id="18d79-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="18d79-122">Le compilateur vérifie l’existence de cet élément de code.</span><span class="sxs-lookup"><span data-stu-id="18d79-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="18d79-123">Si la vérification échoue, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="18d79-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="18d79-124">Le compilateur respecte également les instructions de `Imports` lors de la recherche d’un type décrit dans l’attribut `cref`.</span><span class="sxs-lookup"><span data-stu-id="18d79-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="18d79-125">La balise \<summary > est utilisée par IntelliSense dans Visual Studio pour afficher des informations supplémentaires sur un type ou un membre.</span><span class="sxs-lookup"><span data-stu-id="18d79-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="18d79-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="18d79-126">Related Sections</span></span>

<span data-ttu-id="18d79-127">Pour plus d’informations sur la création d’un fichier XML avec des commentaires de documentation, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="18d79-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="18d79-128">-doc</span><span class="sxs-lookup"><span data-stu-id="18d79-128">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)

- [<span data-ttu-id="18d79-129">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="18d79-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

- [<span data-ttu-id="18d79-130">Traitement du fichier XML</span><span class="sxs-lookup"><span data-stu-id="18d79-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [<span data-ttu-id="18d79-131">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="18d79-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [<span data-ttu-id="18d79-132">Outils XML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="18d79-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="18d79-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18d79-133">See also</span></span>

- [<span data-ttu-id="18d79-134">Développement d’applications avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18d79-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="18d79-135">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18d79-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
