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
# <a name="documenting-your-code-with-xml-visual-basic"></a>Documentation de votre code avec le langage XML (Visual Basic)

In Visual Basic, you can document your code using XML

## <a name="xml-documentation-comments"></a>Commentaires de documentation XML

Visual Basic provides an easy way to automatically create XML documentation for projects. You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks. With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension. Pour plus d’informations, consultez [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

The XML file can be consumed or otherwise manipulated as XML. This file is located in the same directory as the output .exe or .dll file of your project.

XML documentation starts with `'''`. Le traitement de ces commentaires présente certaines restrictions :

- La documentation doit être dans un format XML correct. If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.

- Les développeurs sont libres de créer leur propre jeu de balises. There is a recommended set of tags (see "Related Sections" in this topic). Certaines des balises recommandées ont des significations spéciales :

  - La balise \<param> est utilisée pour décrire les paramètres. Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation. If the verification fails, the compiler issues a warning.

  - L’attribut `cref` peut être joint à n’importe quelle balise pour fournir une référence à un élément de code. Le compilateur vérifie l’existence de cet élément de code. If the verification fails, the compiler issues a warning. The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.

  - The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.

## <a name="related-sections"></a>Rubriques connexes

For details on creating an XML file with documentation comments, see the following topics:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)

- [Traitement du fichier XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Outils XML dans Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Voir aussi

- [Développement d’applications avec Visual Basic](../../../visual-basic/developing-apps/index.md)
- [Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md)
