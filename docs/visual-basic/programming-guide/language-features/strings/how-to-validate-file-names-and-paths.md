---
title: 'Comment : valider des noms de fichiers et des chemins d’accès'
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
Cet exemple retourne une valeur `Boolean` qui indique si une chaîne représente un nom de fichier ou un chemin d’accès. La validation vérifie si le nom contient des caractères qui ne sont pas autorisés par le système de fichiers.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Cet exemple ne vérifie pas si le nom a placé de manière incorrecte des signes deux-points ou des répertoires sans nom, ou si la longueur du nom dépasse la longueur maximale définie par le système. Il ne vérifie pas non plus si l’application a l’autorisation d’accéder à la ressource du système de fichiers avec le nom spécifié.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Validation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
