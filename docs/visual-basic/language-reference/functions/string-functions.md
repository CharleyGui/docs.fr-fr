---
title: Fonctions de chaîne
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 778e57eadd75baf1aabd100f9d8d41a490f79a04
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406286"
---
# <a name="string-functions-visual-basic"></a>Fonctions de chaîne (Visual Basic)

Le tableau suivant répertorie les fonctions fournies par Visual Basic dans la <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> classe pour rechercher et manipuler des chaînes. Ils peuvent être considérés comme des fonctions intrinsèques Visual Basic ; autrement dit, il n’est pas nécessaire de les appeler comme des membres explicites d’une classe, comme le montrent les exemples. Des méthodes supplémentaires et, dans certains cas, des méthodes complémentaires, sont disponibles dans la <xref:System.String?displayProperty=nameWithType> classe.

|Méthode .NET Framework|Description|
|---------------------------|-----------------|
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Retourne une `Integer` valeur représentant le code de caractère correspondant à un caractère.|
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Retourne le caractère associé au code de caractère spécifié.|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Retourne un tableau de base zéro et contenant un sous-ensemble d'un tableau de chaînes (`String`) basé sur des critères de filtre spécifiés.|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Retourne une chaîne mise en forme conformément aux instructions contenues dans une expression `String` de format.|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Retourne une expression sous forme de valeur monétaire utilisant le symbole monétaire défini dans le Panneau de configuration du système.|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Retourne une expression de chaîne représentant une valeur de date/d'heure.|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Retourne une expression sous forme de nombre.|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Retourne une expression au format pourcentage (c’est-à-dire multipliée par 100) avec le caractère de fin %.|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Retourne un entier spécifiant la position de début de la première occurrence d'une chaîne à l'intérieur d'une autre.|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Retourne la position de la première occurrence d'une chaîne dans une autre, à partir du côté droit de la chaîne.|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Retourne une chaîne créée par la jonction de plusieurs sous-chaînes contenues dans un tableau.|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Retourne une chaîne ou un caractère converti en lettres minuscules.|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Retourne une chaîne contenant un nombre spécifié de caractères en partant de la gauche d'une chaîne.|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Retourne un entier qui contient le nombre de caractères dans une chaîne.|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Retourne une chaîne alignée à gauche contenant la chaîne spécifiée ajustée à la longueur spécifiée.|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Retourne une chaîne contenant une copie d’une chaîne spécifiée sans espaces de début.|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Retourne une chaîne contenant un nombre spécifié de caractères d’une chaîne.|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Retourne une chaîne dans laquelle une sous-chaîne spécifiée a été remplacée par une autre sous-chaîne, un nombre de fois déterminé.|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Retourne une chaîne contenant un nombre spécifié de caractères depuis la partie droite d'une chaîne.|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Retourne une chaîne alignée à droite contenant la chaîne spécifiée ajustée à la longueur spécifiée.|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Retourne une chaîne contenant une copie d’une chaîne spécifiée sans espaces à droite.|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Retourne une chaîne composée d'un nombre spécifié d'espaces.|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Retourne un tableau à une dimension de base zéro et contenant le nombre spécifié de sous-chaînes.|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Retourne -1, 0 ou 1, à partir du résultat d'une comparaison de chaînes.|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Retourne une chaîne convertie comme spécifié.|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Retourne une chaîne ou un objet constitué du caractère spécifié répété le nombre de fois spécifié.|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Retourne une chaîne dans laquelle l'ordre des caractères d'une chaîne donnée a été inversé.|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Retourne une chaîne contenant une copie d’une chaîne spécifiée sans espaces de début ou de fin.|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Retourne une chaîne ou un caractère contenant la chaîne spécifiée convertie en majuscules.|

Vous pouvez utiliser l’instruction [option compare](../statements/option-compare-statement.md) pour définir si les chaînes sont comparées à l’aide d’un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système ( `Text` ) ou par les représentations binaires internes des caractères ( `Binary` ). La méthode de comparaison de texte par défaut est `Binary`.

## <a name="example-ucase"></a>Exemple : UCase

L'exemple suivant utilise la fonction `UCase` pour retourner une version en majuscules d'une chaîne.
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a>Exemple : LTrim

Cet exemple utilise la fonction `LTrim` pour supprimer les espaces à gauche et la fonction `RTrim` pour supprimer les espaces à droite d'une variable chaîne. Il utilise la fonction `Trim` pour supprimer les deux types d'espaces.

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a>Exemple : Mid

Cet exemple utilise la `Mid` fonction pour retourner un nombre spécifié de caractères à partir d’une chaîne.

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a>Exemple : Len

L'exemple suivant utilise la fonction `Len` pour retourner le nombre de caractères d'une chaîne.

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a>Exemple : InStr

L'exemple suivant utilise la fonction `InStr` pour retourner la position de la première occurrence d'une chaîne à l'intérieur d'une autre.

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a>Exemple : format

L'exemple suivant illustre différentes utilisations de la fonction `Format` pour mettre en forme des valeurs utilisant à la fois les formats `String` et les formats définis par l'utilisateur. Pour le séparateur de date (`/`), le séparateur d'heure (`:`) et les indicateurs AM/PM (`t` et `tt`), le résultat réel mis en forme affiché par votre système dépend des paramètres régionaux utilisés par le code. Lorsque les heures et les dates sont affichées dans l'environnement de développement, les formats d'heure abrégée et de date courte des paramètres régionaux de code sont utilisés.

> [!NOTE]
> Pour paramètres régionaux configurés avec une horloge au format 24 heures, les indicateurs AM/PM (`t` et `tt`) n'affichent rien.

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a>Voir aussi

- [Mots clés](../keywords/index.md)
- [Membres de la bibliothèque runtime Visual Basic](../runtime-library-members.md)
- [Liste des manipulations de chaîne](../keywords/string-manipulation-summary.md)
- [System. String, méthodes de classe](xref:System.String#methods)
