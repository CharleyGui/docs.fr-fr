---
title: Fonctions de chaîne (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 4f6203fd6ae69315e7efaaa3c17bb4132bd175d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930856"
---
# <a name="string-functions-visual-basic"></a>Fonctions de chaîne (Visual Basic)
Le tableau suivant répertorie les fonctions que Visual Basic fournit pour rechercher et manipuler des chaînes.  
  
|Méthode .NET Framework|Description|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Retourne une `Integer` valeur représentant le code de caractère correspondant à un caractère.|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Retourne le caractère associé au code de caractère spécifié.|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Retourne un tableau de base zéro contenant un sous-ensemble `String` d’un tableau en fonction des critères de filtre spécifiés.|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Retourne une chaîne mise en forme conformément aux instructions contenues `String` dans une expression de format.|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Retourne une expression sous forme de valeur monétaire en utilisant le symbole monétaire défini dans le panneau de configuration du système.|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Retourne une expression de chaîne représentant une valeur de date/heure.|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Retourne une expression sous forme de nombre.|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Retourne une expression au format pourcentage (c’est-à-dire multipliée par 100) avec le caractère de fin %.|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Retourne un entier spécifiant la position de début de la première occurrence d’une chaîne dans une autre.|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Retourne la position de la première occurrence d’une chaîne dans une autre, en commençant à partir du côté droit de la chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Retourne une chaîne créée en joignant plusieurs sous-chaînes contenues dans un tableau.|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Retourne une chaîne ou un caractère converti en minuscules.|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Retourne une chaîne contenant un nombre spécifié de caractères à partir du côté gauche d’une chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Retourne un entier qui contient le nombre de caractères dans une chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Retourne une chaîne alignée à gauche contenant la chaîne spécifiée ajustée à la longueur spécifiée.|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Retourne une chaîne contenant une copie d’une chaîne spécifiée sans espaces de début.|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Retourne une chaîne contenant un nombre spécifié de caractères d’une chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Retourne une chaîne dans laquelle une sous-chaîne spécifiée a été remplacée par une autre sous-chaîne, un nombre de fois spécifié.|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Retourne une chaîne contenant un nombre spécifié de caractères à partir de la partie droite d’une chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Retourne une chaîne alignée à droite contenant la chaîne spécifiée ajustée à la longueur spécifiée.|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Retourne une chaîne contenant une copie d’une chaîne spécifiée sans espaces à droite.|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Retourne une chaîne composée du nombre spécifié d’espaces.|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Retourne un tableau unidimensionnel de base zéro contenant un nombre spécifié de sous-chaînes.|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Retourne-1, 0 ou 1, en fonction du résultat d’une comparaison de chaînes.|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Retourne une chaîne convertie comme spécifié.|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Retourne une chaîne ou un objet constitué du caractère spécifié répété le nombre de fois spécifié.|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Retourne une chaîne dans laquelle l’ordre des caractères d’une chaîne spécifiée est inversé.|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Retourne une chaîne contenant une copie d’une chaîne spécifiée sans espaces de début ou de fin.|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Retourne une chaîne ou un caractère contenant la chaîne spécifiée convertie en majuscules.|  
  
 Vous pouvez utiliser l’instruction [option compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) pour définir si les chaînes sont comparées à l’aide d’un ordre de tri de texte sans respect de la`Text`casse déterminé par les paramètres régionaux de votre système ()`Binary`ou par les représentations binaires internes des caractères (). La méthode de comparaison de texte par défaut est `Binary`.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `UCase` fonction pour retourner une version en majuscules d’une chaîne.  
  
 [!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `LTrim` fonction pour supprimer les espaces de début `RTrim` et la fonction pour supprimer les espaces à droite d’une variable de chaîne. Elle utilise la `Trim` fonction pour supprimer les deux types d’espaces.  
  
 [!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]  
  
## <a name="example"></a>Exemples  
 Cet exemple utilise la `Mid` fonction pour retourner un nombre spécifié de caractères à partir d’une chaîne.  
  
 [!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise `Len` pour retourner le nombre de caractères d’une chaîne.  
  
 [!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]  
  
## <a name="example"></a>Exemples  
 Cet exemple utilise la `InStr` fonction pour retourner la position de la première occurrence d’une chaîne dans une autre.  
  
 [!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]  
  
## <a name="example"></a>Exemples  
 Cet exemple montre différentes utilisations de la `Format` fonction pour mettre en forme les `String` valeurs à l’aide des formats et des formats définis par l’utilisateur. Pour le séparateur de date`/`(), le séparateur`:`d’heure () et les indicateurs am/`t` PM `tt`(et), la sortie mise en forme réelle affichée par votre système dépend des paramètres régionaux que le code utilise. Lorsque des heures et des dates sont affichées dans l’environnement de développement, le format d’heure abrégé et le format de date abrégée des paramètres régionaux du code sont utilisés.  
  
> [!NOTE]
> Pour les paramètres régionaux qui utilisent une horloge de 24 heures, les indicateurs AM/PM`t` ( `tt`et) n’affichent rien.  
  
 [!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Voir aussi

- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Membres de la bibliothèque runtime Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)
- [Liste des manipulations de chaînes](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
