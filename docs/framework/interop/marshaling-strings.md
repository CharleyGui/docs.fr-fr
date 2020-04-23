---
title: Marshaling de chaînes
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
ms.openlocfilehash: 88b6342038f99bf06fa2986c43f422e63cffd31e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124380"
---
# <a name="marshaling-strings"></a>Marshaling de chaînes
L’appel de code non managé copie les paramètres de chaîne, en les convertissant si nécessaire du format .NET Framework (Unicode) au format non managé (ANSI). Étant donné que les chaînes managées sont immuables, l’appel de code non managé ne les recopie pas de la mémoire non managée vers la mémoire managée au retour de la fonction.  
  
 Le tableau suivant répertorie les options de marshaling pour les chaînes. Il décrit leur utilisation et fournit un lien vers l’exemple .NET Framework correspondant.  
  
|String|Description|Exemple|  
|------------|-----------------|------------|  
|Par valeur.|Passe les structures en tant que paramètres entrants.|[MsgBox](msgbox-sample.md)|  
|Comme résultat.|Retourne les chaînes à partir du code non managé.|[Chaînes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Par référence.|Passe des chaînes en tant que paramètres entrants/sortants avec <xref:System.Text.StringBuilder>.|[Mémoires tampons](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|Dans une structure par valeur.|Passe des chaînes dans une structure qui est un paramètre entrant.|[Structs](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|Dans une structure par référence **(char\*)**.|Passe des chaînes dans une structure qui est un paramètre entrant/sortant. La fonction non managée attend un pointeur vers une mémoire tampon de caractères ; la taille de la mémoire tampon est un membre de la structure.|[Chaînes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Dans une structure par référence **(char[])**.|Passe des chaînes dans une structure qui est un paramètre entrant/sortant. La fonction non managée attend une mémoire tampon de caractères incorporée.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Dans une classe par valeur **(char\*)**.|Passe des chaînes dans une classe (une classe est un paramètre entrant/sortant). La fonction non managée attend un pointeur vers une mémoire tampon de caractères.|[OpenFileDlg](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|Dans une classe par valeur **(Char [])**.|Passe des chaînes dans une classe (une classe est un paramètre entrant/sortant). La fonction non managée attend une mémoire tampon de caractères incorporée.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Comme tableau de chaînes par valeur.|Crée un tableau de chaînes qui est passé par valeur.|[Tableaux](marshaling-different-types-of-arrays.md)|  
|Comme un tableau de structures qui contiennent des chaînes par valeur.|Crée un tableau de structures qui contiennent des chaînes ; le tableau est passé par valeur.|[Tableaux](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Voir aussi

- [Marshaling par défaut pour les chaînes](default-marshaling-for-strings.md)
- [Marshaling de données à l’aide de l’appel de code managé](marshaling-data-with-platform-invoke.md)
- [Marshaling de classes, de structures, et d’unions](marshaling-classes-structures-and-unions.md)
- [Marshaling de différents types de tableaux](marshaling-different-types-of-arrays.md)
- [Exemples divers de marshaling](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
