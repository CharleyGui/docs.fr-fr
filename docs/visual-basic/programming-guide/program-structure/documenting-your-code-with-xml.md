---
title: Documentation de votre code avec le langage XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: f391fb909cfe4de8f27afb24d6db389e2c8cdfae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590927"
---
# <a name="document-your-code-with-xml-visual-basic"></a>Documenter votre code avec XML (Visual Basic)

Dans Visual Basic, vous pouvez documenter votre code à l’aide de XML.

## <a name="xml-documentation-comments"></a>Commentaires sur la documentation XML

Visual Basic offre un moyen simple de créer automatiquement la documentation XML pour les projets. Vous pouvez générer automatiquement un squelette XML pour vos types et membres, puis fournir des résumés, une documentation descriptive pour chaque paramètre et d’autres remarques. Avec l’installation appropriée, la documentation XML est automatiquement émise dans un fichier XML avec le même nom de fichier racine que votre projet. Pour plus d’informations, consultez [-doc](../../reference/command-line-compiler/doc.md).

Le fichier XML peut être consommé ou manipulé en tant que XML. Ce fichier se trouve dans le même répertoire que le fichier. exe ou. dll de sortie de votre projet.

La documentation XML commence par `'''` . Le traitement de ces commentaires présente certaines restrictions :

- La documentation doit être dans un format XML correct. Si le XML n’est pas bien formé, un avertissement est généré et le fichier de documentation contient un commentaire indiquant qu’une erreur a été rencontrée.

- Les développeurs sont libres de créer leur propre jeu de balises. Il existe un ensemble recommandé de balises (consultez [balises de commentaire XML](../../language-reference/xmldoc/index.md)). Certaines des balises recommandées ont des significations spéciales :

  - La \<param> balise est utilisée pour décrire les paramètres. Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation. Si la vérification échoue, le compilateur émet un avertissement.

  - L’attribut `cref` peut être joint à n’importe quelle balise pour fournir une référence à un élément de code. Le compilateur vérifie l’existence de cet élément de code. Si la vérification échoue, le compilateur émet un avertissement. Le compilateur respecte également toutes les `Imports` instructions lors de la recherche d’un type décrit dans l' `cref` attribut.

  - La \<summary> balise est utilisée par IntelliSense dans Visual Studio pour afficher des informations supplémentaires sur un type ou un membre.

## <a name="related-sections"></a>Sections connexes

Pour plus d’informations sur la création d’un fichier XML avec des commentaires de documentation, consultez les rubriques suivantes :

- [-doc](../../reference/command-line-compiler/doc.md)

- [Étiquettes XML pour les commentaires](../../language-reference/xmldoc/index.md)

- [Traitement du fichier XML](processing-the-xml-file.md)

- [Guide pratique : créer une documentation XML](how-to-create-xml-documentation.md)

- [Outils XML dans Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Voir aussi

- [Développement d’applications avec Visual Basic](../../developing-apps/index.md)
- [Guide de programmation Visual Basic](../index.md)
