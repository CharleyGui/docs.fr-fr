---
title: Comment les informations de culture affectent les chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 9cbd3a5b8685178259b76d97919ea097ae72f6ae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401964"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Comment les informations de culture affectent les chaînes dans Visual Basic
Cette page d’aide explique comment Visual Basic utilise les informations de culture pour effectuer des conversions de chaînes et des comparaisons.  
  
## <a name="when-to-use-culture-specific-strings"></a>Quand utiliser des chaînes spécifiques à la culture  
 En règle générale, vous devez utiliser des chaînes spécifiques à la culture pour toutes les données présentées aux utilisateurs et les lire, et utiliser des chaînes invariantes de culture pour les données internes de votre application.  
  
 Par exemple, si votre application demande aux utilisateurs d’entrer une date sous forme de chaîne, elle doit s’attendre à ce que les utilisateurs mettent en forme les chaînes en fonction de leur culture, et l’application doit convertir la chaîne correctement. Si votre application présente ensuite cette date dans son interface utilisateur, elle doit la présenter dans la culture de l’utilisateur.  
  
 Toutefois, si l’application charge la date sur un serveur central, elle doit mettre en forme la chaîne en fonction d’une culture spécifique, afin d’éviter toute confusion entre des formats de date potentiellement différents.  
  
## <a name="culture-sensitive-functions"></a>Fonctions dépendantes de la culture  
 Toutes les fonctions de conversion de chaîne Visual Basic (à l’exception `Str` des `Val` fonctions et) utilisent les informations de culture de l’application pour s’assurer que les conversions et les comparaisons sont appropriées pour la culture de l’utilisateur de l’application.  
  
 Pour utiliser avec succès des fonctions de conversion de chaînes dans les applications qui s’exécutent sur des ordinateurs avec des paramètres de culture différents, vous devez comprendre quelles fonctions utilisent un paramètre de culture spécifique, et qui utilisent le paramètre de culture actuel. Notez que les paramètres de culture de l’application sont, par défaut, hérités des paramètres de culture du système d’exploitation. Pour plus d’informations, consultez fonctions de conversion de type,,,,,, <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> <xref:Microsoft.VisualBasic.Strings.Chr%2A> <xref:Microsoft.VisualBasic.Strings.ChrW%2A> <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Hex%2A> <xref:Microsoft.VisualBasic.Conversion.Oct%2A> et. [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)  
  
 Les `Str` fonctions (convertit des nombres en chaînes) et `Val` (convertit des chaînes en nombres) n’utilisent pas les informations de culture de l’application lors de la conversion entre des chaînes et des nombres. Au lieu de cela, ils reconnaissent uniquement le point (.) comme séparateur décimal valide. Les analogues culturel-Aware de ces fonctions sont les suivants :  
  
- **Conversions qui utilisent la culture actuelle.** Les `CStr` `Format` fonctions et convertissent un nombre en une chaîne, et `CDbl` les `CInt` fonctions et convertissent une chaîne en nombre.  
  
- **Conversions qui utilisent une culture spécifique.** Chaque objet Number a une `ToString(IFormatProvider)` méthode qui convertit un nombre en une chaîne et une `Parse(String, IFormatProvider)` méthode qui convertit une chaîne en nombre. Par exemple, le `Double` type fournit les <xref:System.Double.ToString%28System.IFormatProvider%29> <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> méthodes et.  
  
 Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Conversion.Str%2A> et <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Utilisation d’une culture spécifique  
 Imaginez que vous développez une application qui envoie une date (formatée sous forme de chaîne) à un service Web. Dans ce cas, votre application doit utiliser une culture spécifique pour la conversion de chaînes. Pour illustrer pourquoi, considérez le résultat de l’utilisation de la méthode de la date <xref:System.DateTime.ToString> : Si votre application utilise cette méthode pour mettre en forme la date du 4 juillet 2005, elle retourne « 7/4/2005 12:00:00 AM » lorsqu’elle est exécutée avec la culture États-Unis anglais (en-US), mais retourne « 04.07.2005 00:00:00 » lorsqu’elle est exécutée avec la culture allemand (de-de).  
  
 Lorsque vous devez effectuer une conversion de chaîne dans un format de culture spécifique, vous devez utiliser la `CultureInfo` classe intégrée au .NET Framework. Vous pouvez créer un nouvel `CultureInfo` objet pour une culture spécifique en passant le nom de la culture au <xref:System.Globalization.CultureInfo.%23ctor%2A> constructeur. Les noms de culture pris en charge sont répertoriés dans la <xref:System.Globalization.CultureInfo> page d’aide de la classe.  
  
 Vous pouvez également récupérer une instance de la *culture dite indifférente* à partir de la <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriété. La culture dite indifférente est basée sur la culture anglaise, mais il existe quelques différences. Par exemple, la culture dite indifférente spécifie une horloge de 24 heures au lieu d’une horloge de 12 heures.  
  
 Pour convertir une date en une chaîne de la culture, passez l' <xref:System.Globalization.CultureInfo> objet à la méthode de l’objet de date <xref:System.DateTime.ToString%28System.IFormatProvider%29> . Par exemple, le code suivant affiche « 07/04/2005 00:00:00 », quels que soient les paramètres de culture de l’application.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> Les littéraux de date sont toujours interprétés en fonction de la culture anglaise.  
  
## <a name="comparing-strings"></a>Comparaison de chaînes  
 Il existe deux situations importantes où les comparaisons de chaînes sont nécessaires :  
  
- **Tri des données à afficher à l’utilisateur.** Utilisez des opérations basées sur la culture actuelle pour que les chaînes soient triées de manière appropriée.  
  
- **Déterminer si deux chaînes internes de l’application correspondent exactement (en général pour des raisons de sécurité).** Utilisez des opérations qui ignorent la culture actuelle.  
  
 Vous pouvez effectuer les deux types de comparaisons avec la <xref:Microsoft.VisualBasic.Strings.StrComp%2A> fonction Visual Basic. Spécifiez l' `Compare` argument facultatif pour contrôler le type de comparaison : `Text` pour la plupart des entrées et sorties `Binary` pour déterminer des correspondances exactes.  
  
 La `StrComp` fonction retourne un entier qui indique la relation entre les deux chaînes comparées en fonction de l’ordre de tri. Une valeur positive pour le résultat indique que la première chaîne est supérieure à la seconde. Un résultat négatif indique que la première chaîne est plus petite et zéro indique l’égalité entre les chaînes.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Vous pouvez également utiliser le partenaire .NET Framework de la `StrComp` fonction, la <xref:System.String.Compare%2A?displayProperty=nameWithType> méthode. Il s’agit d’une méthode statique, surchargée de la classe de chaîne de base. L’exemple suivant illustre l’utilisation de cette méthode :  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Pour un contrôle plus précis de la façon dont les comparaisons sont effectuées, vous pouvez utiliser des surcharges supplémentaires de la <xref:System.String.Compare%2A> méthode. Avec la <xref:System.String.Compare%2A?displayProperty=nameWithType> méthode, vous pouvez utiliser l' `comparisonType` argument pour spécifier le type de comparaison à utiliser.  
  
|Valeur pour l' `comparisonType` argument|Type de comparaison|Quand l’utiliser|  
|---|---|---|  
|`Ordinal`|Comparaison basée sur les octets de composant des chaînes.|Utilisez cette valeur lors de la comparaison des identificateurs respectant la casse, des paramètres liés à la sécurité ou d’autres identificateurs non linguistiques où les octets doivent correspondre exactement.|  
|`OrdinalIgnoreCase`|Comparaison basée sur les octets de composant des chaînes.<br /><br /> `OrdinalIgnoreCase`utilise les informations de culture invariante pour déterminer quand deux caractères diffèrent uniquement par la casse.|Utilisez cette valeur lors de la comparaison des identificateurs qui ne respectent pas la casse, des paramètres liés à la sécurité et des données stockées dans Windows.|  
|`CurrentCulture` ou `CurrentCultureIgnoreCase`|Comparaison basée sur l’interprétation des chaînes dans la culture actuelle.|Utilisez ces valeurs lors de la comparaison des données affichées à l’utilisateur, de la plupart des entrées d’utilisateur et d’autres données nécessitant une interprétation linguistique.|  
|`InvariantCulture` ou `InvariantCultureIgnoreCase`|Comparaison basée sur l’interprétation des chaînes dans la culture dite indifférente.<br /><br /> Cela est différent du `Ordinal` et `OrdinalIgnoreCase` , car la culture dite indifférente traite les caractères en dehors de sa plage acceptée comme des caractères invariants équivalents.|Utilisez ces valeurs uniquement lors de la comparaison de données persistantes ou de l’affichage de données linguistiques pertinentes qui nécessitent un ordre de tri fixe.|  
  
### <a name="security-considerations"></a>Considérations relatives à la sécurité  
 Si votre application prend des décisions de sécurité basées sur le résultat d’une opération de comparaison ou de changement de casse, l’opération doit utiliser la <xref:System.String.Compare%2A?displayProperty=nameWithType> méthode et passer `Ordinal` ou `OrdinalIgnoreCase` pour l' `comparisonType` argument.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Globalization.CultureInfo>
- [Introduction aux chaînes en Visual Basic](introduction-to-strings.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
