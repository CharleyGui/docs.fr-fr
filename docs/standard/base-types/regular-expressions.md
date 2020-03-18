---
title: Expressions régulières du .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pattern-matching with regular expressions, about pattern-matching
- substrings
- searching with regular expressions, about regular expressions
- pattern-matching with regular expressions
- searching with regular expressions
- parsing text with regular expressions
- regular expressions [.NET Framework], about regular expressions
- regular expressions [.NET Framework]
- .NET Framework regular expressions, about
- characters [.NET Framework], regular expressions
- parsing text with regular expressions, overview
- .NET Framework regular expressions
- strings [.NET Framework], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
ms.openlocfilehash: ac034ff37b0b39f41d6f58381286706f9a9ac602
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121701"
---
# <a name="net-regular-expressions"></a>Expressions régulières .NET
Les expressions régulières permettent de traiter un texte de façon puissante, souple et efficace. Grâce à la syntaxe complète des expressions régulières pour la recherche de correspondance avec un modèle, vous pouvez rapidement analyser des volumes importants de texte pour rechercher des modèles de caractères spécifiques, valider le texte pour vous assurer qu'il correspond à un modèle prédéfini (tel qu'une adresse e-mail), extraire, modifier, remplacer ou supprimer des sous-chaînes de texte et ajouter les chaînes extraites à une collection afin de générer un rapport. Pour de nombreuses applications qui traitent des chaînes ou qui analysent de grands blocs de texte, les expressions régulières constituent un outil indispensable.  
  
## <a name="how-regular-expressions-work"></a>Fonctionnement des expressions régulières  
 La pièce maîtresse du traitement d'un texte avec des expressions régulières est le moteur d'expression régulière, représenté par l'objet <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> dans .NET. Au minimum, vous devez fournir au moteur d'expression régulière les deux éléments d'information suivants pour traiter un texte à l'aide d'expressions régulières :  
  
- Le modèle d’expression régulière à identifier dans le texte.  
  
     Dans .NET, les modèles d’expression régulière sont définis par un langage ou une syntaxe spécifique, qui est compatible avec les expressions régulières Perl 5 et ajoute certaines fonctionnalités comme la mise en correspondance de la droite vers la gauche. Pour plus d’informations, consultez [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md).  
  
- Le texte à analyser pour le modèle d’expression régulière.  
  
 Les méthodes de la classe <xref:System.Text.RegularExpressions.Regex> vous permettent d'effectuer les opérations suivantes :  
  
- Déterminer si le modèle d’expression régulière est présent dans le texte d’entrée en appelant la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>. Pour obtenir un exemple d'utilisation de la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> pour valider un texte, consultez [Comment : vérifier que des chaînes sont dans un format d'adresse de messagerie valide](how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- Récupérer une occurrence, ou toutes les occurrences, de texte qui correspondent au modèle d’expression régulière en appelant la méthode <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>. La première méthode retourne un objet <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> qui fournit des informations sur le texte correspondant. La seconde retourne un objet <xref:System.Text.RegularExpressions.MatchCollection> qui contient un objet <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> pour chaque correspondance trouvée dans le texte analysé.  
  
- Remplacer le texte qui correspond au modèle d’expression régulière en appelant la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>. Pour obtenir des exemples d'utilisation de la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A> pour modifier des formats de date et supprimer des caractères non valides d'une chaîne, consultez [Comment : supprimer des caractères non valides d'une chaîne](how-to-strip-invalid-characters-from-a-string.md) et [Exemple : modification des formats de date](regular-expression-example-changing-date-formats.md).  
  
 Pour obtenir une vue d’ensemble du modèle objet d’expression régulière, consultez [Modèle objet d’expression régulière](the-regular-expression-object-model.md).  
  
 Pour plus d'informations sur le langage d'expression régulière, consultez [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md) ou téléchargez et imprimez l'une des brochures suivantes :  
  
 [Aide-mémoire au format Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Aide-mémoire au format PDF (.pdf)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Exemples d'expressions régulières  
 La classe <xref:System.String> comprend de nombreuses méthodes de recherche et de remplacement de chaîne qui vous permettent de trouver des chaînes littérales dans une chaîne plus grande. Les expressions régulières sont particulièrement utiles quand vous souhaitez trouver une sous-chaîne spécifique dans une chaîne plus grande ou identifier des modèles dans une chaîne, comme le montrent les exemples suivants.  
  
### <a name="example-1-replacing-substrings"></a>Exemple 1 : remplacement de sous-chaînes  
 Supposons qu'une liste de diffusion contient des noms complets, constitués d'un prénom, d'un nom et, parfois, d'un titre (Mr, Mme ou Mlle). Si vous ne souhaitez pas inclure les titres quand vous générez les étiquettes des enveloppes à partir de la liste, vous pouvez utiliser une expression régulière pour supprimer les titres, comme le montre l'exemple suivant.  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Le modèle d’expression régulière `(Mr\.? |Mrs\.? |Miss |Ms\.? )` trouve toute occurrence de « Mr  », « Mr.  », « Mrs  », « Mrs.  », « Miss  », « Ms  » ou « Ms.  ». L'appel de la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> remplace la chaîne mise en correspondance par <xref:System.String.Empty?displayProperty=nameWithType> ; en d'autres termes, il la supprime de la chaîne d'origine.  
  
### <a name="example-2-identifying-duplicated-words"></a>Exemple 2 : identification des mots en double  
 La répétition d'un mot est une erreur de rédaction courante. Vous pouvez utiliser une expression régulière pour identifier les mots en double, comme le montre l'exemple suivant.  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Le modèle d'expression régulière `\b(\w+?)\s\1\b` peut être interprété comme suit :  
  
|||  
|-|-|  
|`\b`|Commencer à la limite d'un mot.|  
|(\w+?)|Correspond à un ou plusieurs caractères alphabétiques, mais le moins de caractères possible. Ensemble, ils forment un groupe identifiable par `\1`.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`\1`|Mettre en correspondance la sous-chaîne égale au groupe nommé `\1`.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
  
 La méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> est appelée avec les options d'expression régulière définies sur <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>. Ainsi, l'opération de mise en correspondance ne fait pas la distinction entre minuscules et majuscules, et l'exemple identifie la sous-chaîne « This this » comme étant une duplication.  
  
 Notez que la chaîne d'entrée comprend la sous-chaîne « this? This ». Toutefois, en raison du signe de ponctuation intermédiaire, cette sous-chaîne n'est pas identifiée comme étant une duplication.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Exemple 3 : création dynamique d'une expression régulière dépendante de la culture  
 L’exemple suivant illustre la puissance des expressions régulières combinée à la souplesse offerte par les fonctionnalités de globalisation de .NET. Il utilise l'objet <xref:System.Globalization.NumberFormatInfo> pour déterminer le format de la devise dans la culture actuelle du système. Ensuite, à partir de cette information, il construit dynamiquement une expression régulière qui extrait du texte les valeurs en devise. Pour chaque correspondance, il extrait le sous-groupe qui contient uniquement la chaîne numérique, le convertit en une valeur <xref:System.Decimal>, puis calcule un total cumulé.  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Sur un ordinateur dont la culture actuelle est anglais-États-Unis (en-US), l'exemple crée dynamiquement l'expression régulière `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Ce modèle d’expression régulière peut être interprété comme suit :  
  
|||  
|-|-|  
|`\$`|Rechercher une occurrence unique du symbole dollar (`$`) dans la chaîne d’entrée. La chaîne du modèle d'expression régulière comprend une barre oblique inverse pour indiquer que le symbole dollar doit être interprété littéralement et non comme une ancre d'expression régulière. (Le `$` symbole seul indiquerait que le moteur d’expression ordinaire devrait essayer de commencer son match à la fin d’une chaîne.) Pour s’assurer que le symbole monétaire de la culture actuelle n’est <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> pas mal interprété comme un symbole d’expression régulière, l’exemple appelle la méthode pour échapper au personnage.|  
|`\s*`|Rechercher zéro occurrence, ou plus, d'un espace blanc.|  
|`[-+]?`|Rechercher zéro ou une occurrence d'un signe positif ou d'un signe négatif.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Les parenthèses externes de cette expression définissent celle-ci en tant que groupe de capture ou que sous-expression. Si une correspondance est trouvée, les informations sur cette partie de la chaîne correspondante peuvent être récupérées du deuxième objet <xref:System.Text.RegularExpressions.Group> dans l'objet <xref:System.Text.RegularExpressions.GroupCollection> retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. (Le premier élément de la collection représente la correspondance entière.)|  
|`[0-9]{0,3}`|Rechercher entre zéro et trois occurrences des chiffres décimaux allant de 0 à 9.|  
|`(,[0-9]{3})*`|Rechercher zéro occurrence, ou plus, d'un séparateur de groupes suivi de trois chiffres décimaux.|  
|`\.`|Rechercher une occurrence unique du séparateur décimal.|  
|`[0-9]+`|Rechercher un ou plusieurs chiffres décimaux.|  
|`(\.[0-9]+)?`|Rechercher zéro ou une occurrence du séparateur décimal suivie d'au moins un chiffre décimal.|  
  
 Si chacun de ces sous-modèles est trouvé dans la chaîne d'entrée, la recherche de correspondance réussit, et un objet <xref:System.Text.RegularExpressions.Match> contenant des informations sur la correspondance est ajouté à l'objet <xref:System.Text.RegularExpressions.MatchCollection>.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Langage d’expression régulière - Référence rapide](regular-expression-language-quick-reference.md)|Fournit des informations sur le jeu de caractères, d'opérateurs et de constructions permettant de définir des expressions régulières.|  
|[Le modèle d’objet d’expression régulière](the-regular-expression-object-model.md)|Fournit des informations et des exemples de code illustrant l'utilisation des classes d'expression régulière.|  
|[Détails du comportement d’expression régulière](details-of-regular-expression-behavior.md)|Fournit des informations sur les fonctionnalités et le comportement des expressions régulières .NET.|  
|[Exemples d'expressions régulières](regular-expression-examples.md)|Fournit des exemples de code illustrant des utilisations courantes des expressions régulières.|  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Expressions régulières - Aide-mémoire (téléchargement au format Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Expressions régulières - Aide-mémoire (téléchargement au format PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
