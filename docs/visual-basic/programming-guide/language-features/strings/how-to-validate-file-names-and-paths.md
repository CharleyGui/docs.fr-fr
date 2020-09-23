---
title: 'Guide pratique : valider des noms de fichiers et des chemins d’accès'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: b722222ea8b8088a6b326eef27147c08f8419272
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072650"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="9b749-102">Comment : valider des noms de fichiers et des chemins d’accès en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b749-102">How to: Validate File Names and Paths in Visual Basic</span></span>

<span data-ttu-id="9b749-103">Cet exemple retourne une `Boolean` valeur qui indique si une chaîne représente un nom de fichier ou un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="9b749-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="9b749-104">La validation vérifie si le nom contient des caractères qui ne sont pas autorisés par le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="9b749-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b749-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b749-105">Example</span></span>  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="9b749-106">Cet exemple ne vérifie pas si le nom a placé de manière incorrecte des signes deux-points ou des répertoires sans nom, ou si la longueur du nom dépasse la longueur maximale définie par le système.</span><span class="sxs-lookup"><span data-stu-id="9b749-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="9b749-107">Il ne vérifie pas non plus si l’application a l’autorisation d’accéder à la ressource du système de fichiers avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b749-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b749-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b749-108">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="9b749-109">Validation de chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b749-109">Validating Strings in Visual Basic</span></span>](validating-strings.md)
