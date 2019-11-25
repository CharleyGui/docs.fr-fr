---
title: 'How to: Validate File Names and Paths'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: cc4d275d469860aa19c45ca0fe0401b709b42d82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344367"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Comment : valider des noms de fichiers et des chemins d’accès en Visual Basic
This example returns a `Boolean` value that indicates whether a string represents a file name or path. The validation checks if the name contains characters that are not allowed by the file system.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length. It also does not check if the application has permission to access the file-system resource with the specified name.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Validation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
