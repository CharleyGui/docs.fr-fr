---
title: Utilisation d’expressions régulières avec le contrôle MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: b997f6f495fca51e888bb995fee0361d29d68048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148282"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Utilisation d'expressions régulières avec le contrôle MaskedTextBox en Visual Basic
Cet exemple montre comment convertir des expressions <xref:System.Windows.Forms.MaskedTextBox> régulières simples pour travailler avec le contrôle.  
  
## <a name="description-of-the-masking-language"></a>Description de la langue de masquage  
 Le <xref:System.Windows.Forms.MaskedTextBox> langage de masquage standard `Masked Edit` est basé sur celui utilisé par le contrôle dans Visual Basic 6.0 et devrait être familier aux utilisateurs qui migrent à partir de cette plate-forme.  
  
 La <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété <xref:System.Windows.Forms.MaskedTextBox> du contrôle précise le masque d’entrée à utiliser. Le masque doit être une chaîne composée d’un ou plusieurs des éléments masquants de la table suivante.  
  
|Élément de masquage|Description|Élément d’expression régulière|  
|---------------------|-----------------|--------------------------------|  
|0|N’importe quel chiffre entre 0 et 9. Entrée requise.|\d|  
|9|Chiffre ou espace. Entrée facultative.|[d]?|  
|#|Chiffre ou espace. Entrée facultative. Si cette position est laissée vide dans le masque, elle sera rendue comme un espace. Les panneaux plus (md) et moins (-) sont autorisés.|?'|  
|L|Lettre ASCII. Entrée requise.|[a-zA-Z]|  
|?|Lettre ASCII. Entrée facultative.|[a-zA-Z]?|  
|&|Caractère. Entrée requise.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Caractère. Entrée facultative.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|Un|Alphanumérique. Entrée facultative.|\W|  
|.|Lieu décimal adapté à la culture.|Non disponible.|  
|,|Culture-approprié milliers placeholder.|Non disponible.|  
|:|Séparateur de temps adapté à la culture.|Non disponible.|  
|/|Séparateur de date de culture appropriée.|Non disponible.|  
|$|Symbole de monnaie adapté à la culture.|Non disponible.|  
|\<|Convertit tous les personnages qui suivent en minuscules.|Non disponible.|  
|>|Convertit tous les personnages qui suivent à uppercase.|Non disponible.|  
|&#124;|Défait un quart de travail précédent vers le haut ou décro lant.|Non disponible.|  
|&#92;|Échappe à un personnage de masque, le transformant en un littéral. "\\\\est la séquence d’évasion pour une barre oblique inverse.|&#92;|  
|Tous les autres personnages.|littéraux. Tous les éléments non-masque <xref:System.Windows.Forms.MaskedTextBox>apparaîtront comme eux-mêmes à l’intérieur .|Tous les autres personnages.|  
  
 Les symboles décimaux (.), millièmes (,), temps (:), date (/), et monnaie ($) par défaut à l’affichage de ces symboles tels que définis par la culture de l’application. Vous pouvez les forcer à afficher des <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> symboles pour une autre culture en utilisant la propriété.  
  
## <a name="regular-expressions-and-masks"></a>Expressions et masques réguliers  
 Bien que vous puissiez utiliser des expressions et des masques réguliers pour valider l’entrée de l’utilisateur, elles ne sont pas totalement équivalentes. Les expressions régulières peuvent exprimer des motifs plus complexes que les masques, mais les masques peuvent exprimer les mêmes informations plus succinctement et dans un format culturellement pertinent.  
  
 Le tableau suivant compare quatre expressions régulières et le masque équivalent pour chacun.  
  
|Expression régulière|Mask|Notes|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|Le `/` caractère dans le masque est un séparateur de date logique, et il apparaîtra à l’utilisateur comme le séparateur de date approprié à la culture actuelle de l’application.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Une date (jour, abréviation du mois et année) en format des États-Unis dans laquelle l’abréviation de trois lettres est affichée avec une lettre supérieure initiale suivie de deux lettres minuscules.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Numéro de téléphone des États-Unis, code régional facultatif. Si l’utilisateur ne souhaite pas entrer les caractères optionnels, il peut soit entrer des espaces, soit placer le pointeur de la souris directement à la position du masque représenté par les 0 premiers.|  
|`$\d{6}.00`|`$999,999.00`|Une valeur de change de l’ordre de 0 à 999999. La monnaie, le millième et les personnages décimaux seront remplacés à l’heure de course par leurs équivalents spécifiques à la culture.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Validation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox, contrôle](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
