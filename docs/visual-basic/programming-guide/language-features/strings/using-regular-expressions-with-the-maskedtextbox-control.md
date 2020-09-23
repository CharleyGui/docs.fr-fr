---
title: Utilisation d’expressions régulières avec le contrôle MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 493da7b8583b5cc73a9832afa81b7b1d84742f2d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072429"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Utilisation d'expressions régulières avec le contrôle MaskedTextBox en Visual Basic

Cet exemple montre comment convertir des expressions régulières simples pour qu’elles fonctionnent avec le <xref:System.Windows.Forms.MaskedTextBox> contrôle.  
  
## <a name="description-of-the-masking-language"></a>Description du langage de masquage  

 Le <xref:System.Windows.Forms.MaskedTextBox> langage de masquage standard est basé sur celui utilisé par le `Masked Edit` contrôle dans Visual Basic 6,0 et doit être familiarisé avec les utilisateurs qui migrent à partir de cette plateforme.  
  
 La <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété du <xref:System.Windows.Forms.MaskedTextBox> contrôle spécifie le masque de saisie à utiliser. Le masque doit être une chaîne composée d’un ou plusieurs des éléments de masquage du tableau suivant.  
  
|Élément de masquage|Description|Élément d’expression régulière|  
|---------------------|-----------------|--------------------------------|  
|0|Tout chiffre compris entre 0 et 9. Entrée obligatoire.|\d|  
|9|Chiffre ou espace. Entrée facultative.|[\d] ?|  
|#|Chiffre ou espace. Entrée facultative. Si cette position est laissée vide dans le masque, elle est rendue sous la forme d’un espace. Les signes plus (+) et moins (-) sont autorisés.|[\d +-] ?|  
|L|Lettre ASCII. Entrée obligatoire.|[a-zA-Z]|  
|?|Lettre ASCII. Entrée facultative.|[a-zA-Z] ?|  
|&|Caractère. Entrée obligatoire.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Caractère. Entrée facultative.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Comportant. Entrée facultative.|\W|  
|.|Espace réservé décimal approprié à la culture.|Non disponible.|  
|,|Espace réservé des milliers approprié à la culture.|Non disponible.|  
|:|Séparateur horaire approprié à la culture.|Non disponible.|  
|/|Séparateur de date approprié à la culture.|Non disponible.|  
|$|Symbole monétaire approprié à la culture.|Non disponible.|  
|\<|Convertit tous les caractères qui suivent en minuscules.|Non disponible.|  
|>|Convertit tous les caractères qui suivent en majuscules.|Non disponible.|  
|&#124;|Annule un décalage précédent vers le haut ou vers le haut.|Non disponible.|  
|&#92;|Échappe un caractère de masque, en le transformant en littéral. " \\ \\ " est la séquence d’échappement d’une barre oblique inverse.|&#92;|  
|Tous les autres caractères.|littéraux. Tous les éléments qui ne sont pas des masques apparaissent comme eux-mêmes dans <xref:System.Windows.Forms.MaskedTextBox> .|Tous les autres caractères.|  
  
 Les symboles décimal (.), millièmes (,), heure ( :), date (/) et devise ($) affichent par défaut les symboles tels que définis par la culture de l’application. Vous pouvez les forcer à afficher des symboles pour une autre culture à l’aide de la <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> propriété.  
  
## <a name="regular-expressions-and-masks"></a>Expressions régulières et masques  

 Bien que vous puissiez utiliser des expressions régulières et des masques pour valider l’entrée d’utilisateur, ils ne sont pas complètement équivalents. Les expressions régulières peuvent exprimer des modèles plus complexes que les masques, mais les masques peuvent exprimer les mêmes informations de façon plus succincte et dans un format culturellement pertinent.  
  
 Le tableau suivant compare quatre expressions régulières et le masque équivalent pour chacune d’elles.  
  
|Expression régulière|Mask|Notes|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|Le `/` caractère dans le masque est un séparateur de date logique, et il apparaît à l’utilisateur comme séparateur de date approprié à la culture actuelle de l’application.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Date (jour, abréviation du mois et année) au format États-Unis dans lequel l’abréviation du mois à trois lettres s’affiche avec une lettre majuscule initiale suivie de deux lettres minuscules.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Numéro de téléphone États-Unis, indicatif de zone facultatif. Si l’utilisateur ne souhaite pas entrer les caractères facultatifs, il peut entrer des espaces ou placer le pointeur de la souris directement à la position dans le masque représenté par le premier 0.|  
|`$\d{6}.00`|`$999,999.00`|Valeur monétaire comprise entre 0 et 999999. Les caractères monétaires, millième et décimal sont remplacés au moment de l’exécution par leurs équivalents spécifiques à la culture.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Validation de chaînes en Visual Basic](validating-strings.md)
- [MaskedTextBox, contrôle](/dotnet/desktop/winforms/controls/maskedtextbox-control-windows-forms)
