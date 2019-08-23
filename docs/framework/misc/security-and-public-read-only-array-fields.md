---
title: Sécurité et champs de tableau en lecture seule publics
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d36009fa4fc7b9299708768fe34a75f1fde6797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910739"
---
# <a name="security-and-public-read-only-array-fields"></a>Sécurité et champs de tableau en lecture seule publics
N’utilisez jamais de champs de tableau public en lecture seule à partir de bibliothèques managées pour définir le comportement de limite ou la sécurité de vos applications, car les champs de tableau public en lecture seule peuvent être modifiés.  
  
## <a name="remarks"></a>Notes  
 Certaines classes .NET Framework incluent des champs publics en lecture seule qui contiennent des paramètres de limite spécifiques à la plateforme.  Par exemple, le <xref:System.IO.Path.InvalidPathChars> champ est un tableau qui décrit les caractères qui ne sont pas autorisés dans une chaîne de chemin d’accès de fichier.  De nombreux champs similaires sont présents dans l' .NET Framework.  
  
 Les valeurs des champs publics en lecture seule comme <xref:System.IO.Path.InvalidPathChars> peuvent être modifiées par votre code ou code qui partage le domaine d’application de votre code.  Vous ne devez pas utiliser des champs de tableau public en lecture seule comme celui-ci pour définir le comportement de limite de vos applications.  Si vous le faites, du code malveillant peut modifier les définitions des limites et utiliser votre code de façon inattendue.  
  
 Dans la version 2,0 et les versions ultérieures du .NET Framework, vous devez utiliser des méthodes qui retournent un nouveau tableau au lieu d’utiliser des champs de tableau publics.  Par exemple, au lieu d’utiliser <xref:System.IO.Path.InvalidPathChars> le champ, vous devez utiliser <xref:System.IO.Path.GetInvalidPathChars%2A> la méthode.  
  
 Notez que les types de .NET Framework n’utilisent pas les champs publics pour définir les types de limites en interne.  Au lieu de cela, le .NET Framework utilise des champs privés distincts.  La modification des valeurs de ces champs publics ne modifie pas le comportement des types de .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
