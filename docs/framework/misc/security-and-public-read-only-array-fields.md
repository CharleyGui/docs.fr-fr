---
title: Sécurité et champs de tableau en lecture seule publics
description: Découvrez pourquoi vous devez éviter d’utiliser des champs de tableau en lecture seule publics pour définir le comportement de limite ou la sécurité de vos applications.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 5e499f8052306cd1ad063c9f44a2a0f1d0b365ef
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855736"
---
# <a name="security-and-public-read-only-array-fields"></a>Sécurité et champs de tableau en lecture seule publics

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

N’utilisez jamais de champs de tableau public en lecture seule à partir de bibliothèques managées pour définir le comportement de limite ou la sécurité de vos applications, car les champs de tableau public en lecture seule peuvent être modifiés.  
  
## <a name="remarks"></a>Notes  

Certaines classes .NET incluent des champs publics en lecture seule qui contiennent des paramètres de limite spécifiques à la plateforme. Par exemple, le <xref:System.IO.Path.InvalidPathChars> champ est un tableau qui décrit les caractères qui ne sont pas autorisés dans une chaîne de chemin d’accès de fichier. De nombreux champs similaires sont présents dans .NET.  
  
 Les valeurs des champs publics en lecture seule comme <xref:System.IO.Path.InvalidPathChars> peuvent être modifiées par votre code ou code qui partage le domaine d’application de votre code.  Vous ne devez pas utiliser des champs de tableau public en lecture seule comme celui-ci pour définir le comportement de limite de vos applications.  Si vous le faites, du code malveillant peut modifier les définitions des limites et utiliser votre code de façon inattendue.  
  
 Dans la version 2,0 et les versions ultérieures du .NET Framework, vous devez utiliser des méthodes qui retournent un nouveau tableau au lieu d’utiliser des champs de tableau publics.  Par exemple, au lieu d’utiliser le <xref:System.IO.Path.InvalidPathChars> champ, vous devez utiliser la <xref:System.IO.Path.GetInvalidPathChars%2A> méthode.  
  
 Notez que les types de .NET Framework n’utilisent pas les champs publics pour définir les types de limites en interne.  Au lieu de cela, le .NET Framework utilise des champs privés distincts.  La modification des valeurs de ces champs publics ne modifie pas le comportement des types de .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
