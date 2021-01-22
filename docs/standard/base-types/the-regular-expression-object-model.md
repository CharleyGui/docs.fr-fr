---
title: Modèle objet d'expression régulière
description: Passez en revue le modèle objet d’expression régulière dans .NET. Utilisez le moteur d’expression régulière, & objets & collections liées à la correspondance, au regroupement & à la capture.
ms.topic: conceptual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, backreferences
- Regex class
- Match class
- pattern-matching with regular expressions, backreferences
- .NET regular expressions, classes
- CaptureCollection class
- Group class
- characters [.NET], backreferences
- substrings
- .NET regular expressions, backreferences
- searching with regular expressions, classes
- backreferences
- Capture class
- repeating groups of characters
- MatchCollection class
- parsing text with regular expressions, backreferences
- regular expressions [.NET]
- characters [.NET], regular expressions
- classes [.NET], regular expression
- regular expressions [.NET], classes
- characters [.NET], metacharacters
- metacharacters, regular expression classes
- metacharacters, backreferences
- parsing text with regular expressions, classes
- regular expressions [.NET], backreferences
- strings [.NET], regular expressions
- pattern-matching with regular expressions, classes
- GroupCollection class
ms.assetid: 49a21470-64ca-4b5a-a889-8e24e3c0af7e
ms.openlocfilehash: 115955f48f0470adf584acf2c2e72680cef105cb
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692563"
---
# <a name="the-regular-expression-object-model"></a>Modèle objet d'expression régulière

<a name="introduction"></a> Cette rubrique décrit le modèle objet utilisé avec les expressions régulières .NET. Il contient les sections suivantes :  
  
- [Le moteur des expressions régulières](#Engine)  
  
- [Objets MatchCollection et match](#Match_and_MCollection)  
  
- [Collection de groupes](#GroupCollection)  
  
- [Groupe capturé](#the_captured_group)  
  
- [Collection de captures](#CaptureCollection)  
  
- [Capture individuelle](#the_individual_capture)  
  
<a name="Engine"></a>

## <a name="the-regular-expression-engine"></a>Moteur d'expression régulière  

 Le moteur d’expression régulière dans .NET est représenté par la classe <xref:System.Text.RegularExpressions.Regex>. Le moteur d’expression régulière prend en charge l’analyse et la compilation d’une expression régulière, ainsi que les opérations qui mettent en correspondance le modèle d’expression régulière avec une chaîne d’entrée. Le moteur est le composant central du modèle objet des expressions régulières .NET.  
  
 Vous pouvez utiliser le moteur d'expression régulière de deux façons :  
  
- En appelant les méthodes statiques de la classe <xref:System.Text.RegularExpressions.Regex>. Les paramètres des méthodes comprennent la chaîne d'entrée et le modèle d'expression régulière. Le moteur d'expression régulière met en cache les expressions régulières utilisées dans les appels de méthode statique ; les appels répétés de méthodes d'expression régulière statiques qui utilisent la même expression régulière offrent donc des performances relativement bonnes.  
  
- En instanciant un objet <xref:System.Text.RegularExpressions.Regex>, via la transmission d'une expression régulière au constructeur de classe. Dans ce cas, l'objet <xref:System.Text.RegularExpressions.Regex> est immuable (lecture seule) et représente un moteur d'expression régulière étroitement lié à une expression régulière unique. Comme les expressions régulières utilisées par les instances de <xref:System.Text.RegularExpressions.Regex> ne sont pas mises en cache, vous ne devez pas instancier un objet <xref:System.Text.RegularExpressions.Regex> plusieurs fois avec la même expression régulière.  
  
 Vous pouvez appeler les méthodes de la classe <xref:System.Text.RegularExpressions.Regex> pour effectuer les opérations suivantes :  
  
- Déterminer si une chaîne correspond à un modèle d'expression régulière.  
  
- Extraire une correspondance unique ou la première correspondance.  
  
- Extraire toutes les correspondances.  
  
- Remplacer une sous-chaîne mise en correspondance.  
  
- Fractionner une chaîne spécifique en un tableau de chaînes.  
  
 Ces opérations sont décrites en détail dans les sections suivantes.  
  
### <a name="matching-a-regular-expression-pattern"></a>Mise en correspondance d'un modèle d'expression régulière  

 La méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> retourne `true` si la chaîne correspond au modèle, `false` sinon. La méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> est souvent utilisée pour valider une entrée de chaîne. Par exemple, le code suivant s'assure qu'une chaîne correspond à un numéro de sécurité sociale valide au États-Unis.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Le modèle d'expression régulière `^\d{3}-\d{2}-\d{4}$` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Mettre en correspondance le début de la chaîne d'entrée.|  
|`\d{3}`|Mettre en correspondance trois chiffres décimaux.|  
|`-`|Mettre en correspondance un trait d'union.|  
|`\d{2}`|Mettre en correspondance deux chiffres décimaux.|  
|`-`|Mettre en correspondance un trait d'union.|  
|`\d{4}`|Mettre en correspondance quatre chiffres décimaux.|  
|`$`|Mettre en correspondance la fin de la chaîne d'entrée.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Extraction d'une correspondance unique ou de la première correspondance  

 La méthode <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> retourne un objet <xref:System.Text.RegularExpressions.Match> qui contient des informations sur la première sous-chaîne qui correspond à un modèle d'expression régulière. Si la propriété `Match.Success` retourne `true`, indiquant alors qu'une correspondance a été trouvée, vous pouvez récupérer les informations sur les correspondances suivantes en appelant la méthode <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>. Ces appels de méthode peuvent se poursuivre jusqu'à ce que la propriété `Match.Success` retourne `false`. Par exemple, le code suivant utilise la méthode <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> pour rechercher la première occurrence d'un mot en double dans une chaîne. Il appelle ensuite la méthode <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> pour rechercher les occurrences supplémentaires éventuelles. L'exemple examine la propriété `Match.Success` après chaque appel de méthode pour déterminer si la mise en correspondance actuelle a réussi et si elle doit être suivie d'un appel de la méthode <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Le modèle d'expression régulière `\b(\w+)\W+(\1)\b` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.|  
|`\W+`|Mettre en correspondance un ou plusieurs caractères non alphabétiques.|  
|`(\1)`|Mettre en correspondance la première chaîne capturée. Il s'agit du deuxième groupe de capture.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
### <a name="extracting-all-matches"></a>Extraction de toutes les correspondances  

 La méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> retourne un objet <xref:System.Text.RegularExpressions.MatchCollection> qui contient des informations sur toutes les correspondances trouvées par le moteur d'expression régulière dans la chaîne d'entrée. Ainsi, l'exemple précédent peut être réécrit pour appeler la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A> au lieu des méthodes <xref:System.Text.RegularExpressions.Regex.Match%2A> et <xref:System.Text.RegularExpressions.Match.NextMatch%2A>.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Remplacement d'une sous-chaîne mise en correspondance  

 La méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> remplace chaque sous-chaîne mise en correspondance par le modèle d'expression régulière par une chaîne ou un modèle d'expression régulière spécifique, puis retourne la chaîne d'entrée entière avec les remplacements. Par exemple, le code suivant ajoute le symbole de devise des États-Unis avant un nombre décimal dans une chaîne.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Le modèle d'expression régulière `\b\d+\.\d{2}\b` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|  
|`\.`|Mettre en correspondance un point.|  
|`\d{2}`|Mettre en correspondance deux chiffres décimaux.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
 Le modèle de remplacement `$$$&` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Chaîne de remplacement|  
|-------------|------------------------|  
|`$$`|Caractère du signe dollar ($).|  
|`$&`|Sous-chaîne entière mise en correspondance.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Fractionnement d'une chaîne spécifique en un tableau de chaînes  

 La méthode <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> fractionne la chaîne d'entrée aux positions définies par une correspondance d'expression régulière. Par exemple, le code suivant place les éléments d'une liste numérotée dans un tableau de chaînes.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Le modèle d'expression régulière `\b\d{1,2}\.\s` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`\d{1,2}`|Mettre en correspondance un ou deux chiffres décimaux.|  
|`\.`|Mettre en correspondance un point.|  
|`\s`|Mettre en correspondance un espace blanc.|  
  
<a name="Match_and_MCollection"></a>

## <a name="the-matchcollection-and-match-objects"></a>Objets MatchCollection et Match  

 Les méthodes d'expression régulière retournent deux objets qui font partie du modèle objet d'expression régulière : l'objet <xref:System.Text.RegularExpressions.MatchCollection> et l'objet <xref:System.Text.RegularExpressions.Match>.  
  
<a name="the_match_collection"></a>

### <a name="the-match-collection"></a>Collection de correspondances  

 La méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> retourne un objet <xref:System.Text.RegularExpressions.MatchCollection> qui contient des objets <xref:System.Text.RegularExpressions.Match> représentant toutes les correspondances trouvées par le moteur d'expression régulière, dans l'ordre dans lequel elles se produisent dans la chaîne d'entrée. En l'absence de correspondance, la méthode retourne un objet <xref:System.Text.RegularExpressions.MatchCollection> sans membres. La propriété <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> vous permet d'accéder à des membres spécifiques de la collection en fonction de leur index, qui est compris entre zéro et la valeur de la propriété <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> moins une unité. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> est l'indexeur de la collection (en C#) et la propriété par défaut (en Visual Basic).  
  
 Par défaut, l'appel de la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> utilise une évaluation tardive pour remplir l'objet <xref:System.Text.RegularExpressions.MatchCollection>. L'accès aux propriétés qui nécessitent une collection entièrement remplie, telles que les propriétés <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> et <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType>, peut affecter les performances. Nous vous recommandons donc d'accéder à la collection en utilisant l'objet <xref:System.Collections.IEnumerator> retourné par la méthode <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType>. Des constructions propres au langage, comme `For Each` en Visual Basic et `foreach` en C#, encapsulent l'interface <xref:System.Collections.IEnumerator> de la collection.  
  
 L'exemple suivant utilise la méthode <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> pour remplir un objet <xref:System.Text.RegularExpressions.MatchCollection> avec toutes les correspondances trouvées dans une chaîne d'entrée. L’exemple énumère la collection, copie les correspondances dans un tableau de chaînes et enregistre les positions de caractère dans un tableau d’entiers.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>

### <a name="the-match"></a>Classe Match  

 La classe <xref:System.Text.RegularExpressions.Match> représente le résultat d'une correspondance d'expression régulière unique. Vous pouvez accéder aux objets <xref:System.Text.RegularExpressions.Match> de deux façons :  
  
- En les récupérant de l'objet <xref:System.Text.RegularExpressions.MatchCollection> retourné par la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>. Pour récupérer des objets <xref:System.Text.RegularExpressions.Match> spécifiques, itérez la collection en utilisant une construction `foreach` (en C#) ou `For Each`...`Next` (en Visual Basic), ou utilisez la propriété <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> pour récupérer un objet <xref:System.Text.RegularExpressions.Match> spécifique en fonction de son index ou de son nom. Vous pouvez également récupérer des objets <xref:System.Text.RegularExpressions.Match> spécifiques de la collection en itérant la collection à partir des valeurs d'index, qui peuvent aller de zéro au nombre d'objets dans la collection moins une unité. Toutefois, cette méthode ne tire pas parti de l'évaluation tardive, car elle accède à la propriété <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType>.  
  
     L'exemple suivant récupère des objets <xref:System.Text.RegularExpressions.Match> spécifiques d'un objet <xref:System.Text.RegularExpressions.MatchCollection> en itérant la collection à l'aide de la construction `foreach` ou `For Each`...`Next`. L'expression régulière met simplement en correspondance la chaîne « abc » dans la chaîne d'entrée.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- En appelant la méthode <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>, qui retourne un objet <xref:System.Text.RegularExpressions.Match> représentant la première correspondance dans une chaîne ou dans une partie d'une chaîne. Vous pouvez déterminer si la correspondance a été trouvée en récupérant la valeur de la propriété `Match.Success`. Pour récupérer les objets <xref:System.Text.RegularExpressions.Match> qui représentent les correspondances suivantes, appelez la méthode <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> de manière répétée, jusqu'à ce que la propriété `Success` de l'objet <xref:System.Text.RegularExpressions.Match> retourné ait pour valeur `false`.  
  
     L'exemple suivant utilise les méthodes <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> et <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> pour mettre en correspondance la chaîne « abc » dans la chaîne d'entrée.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Deux propriétés de la classe <xref:System.Text.RegularExpressions.Match> retournent des objets de collection :  
  
- La propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> retourne un objet <xref:System.Text.RegularExpressions.GroupCollection> qui contient des informations sur les sous-chaînes correspondant aux groupes de capture dans le modèle d'expression régulière.  
  
- La propriété `Match.Captures` retourne un objet <xref:System.Text.RegularExpressions.CaptureCollection> dont l'utilisation est limitée. La collection n'est pas remplie dans le cas d'un objet <xref:System.Text.RegularExpressions.Match> dont la propriété `Success` a pour valeur `false`. Sinon, elle contient un objet <xref:System.Text.RegularExpressions.Capture> unique qui possède les mêmes informations que l'objet <xref:System.Text.RegularExpressions.Match>.  
  
 Pour plus d’informations sur ces objets, consultez les sections [La collection de groupes](#GroupCollection) et [La collection de captures](#CaptureCollection) plus avant dans cette rubrique.  
  
 Deux propriétés supplémentaires de la classe <xref:System.Text.RegularExpressions.Match> fournissent des informations sur la correspondance. La propriété `Match.Value` retourne la sous-chaîne de la chaîne d'entrée qui correspond au modèle d'expression régulière. La propriété `Match.Index` retourne la position de début en base zéro de la chaîne mise en correspondance dans la chaîne d'entrée.  
  
 En outre, la classe <xref:System.Text.RegularExpressions.Match> possède deux méthodes de mise en correspondance de modèle :  
  
- La méthode <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> trouve la correspondance après la correspondance représentée par l'objet <xref:System.Text.RegularExpressions.Match> actuel, puis retourne un objet <xref:System.Text.RegularExpressions.Match> représentant cette correspondance.  
  
- La méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> effectue une opération de remplacement spécifique sur la chaîne mise en correspondance et retourne le résultat.  
  
 L'exemple suivant utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> pour ajouter un symbole $ et un espace avant chaque nombre comprenant deux chiffres fractionnaires.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Le modèle d'expression régulière `\b\d+(,\d{3})*\.\d{2}\b` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|  
|`(,\d{3})*`|Mettre en correspondance zéro occurrence, ou plus, d'une virgule suivie de trois chiffres décimaux.|  
|`\.`|Mettre en correspondance le séparateur décimal.|  
|`\d{2}`|Mettre en correspondance deux chiffres décimaux.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
 Le modèle de remplacement `$$ $&` indique que la sous-chaîne mise en correspondance doit être remplacée par un symbole dollar ($) (modèle `$$`), suivi d'un espace et de la valeur de la correspondance (modèle `$&`).  
  
 [Retour au début](#introduction)  
  
<a name="GroupCollection"></a>

## <a name="the-group-collection"></a>Collection de groupes  

 La propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> retourne un objet <xref:System.Text.RegularExpressions.GroupCollection> qui contient des objets <xref:System.Text.RegularExpressions.Group> représentant des groupes capturés dans une même correspondance. Le premier objet <xref:System.Text.RegularExpressions.Group> de la collection (index 0) représente la correspondance entière. Chaque objet qui suit représente le résultat d'un groupe de capture spécifique.  
  
 Vous pouvez récupérer des objets <xref:System.Text.RegularExpressions.Group> spécifiques dans la collection en utilisant la propriété <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType>. Vous pouvez récupérer les groupes sans nom en fonction de leur position ordinale dans la collection, et les groupes nommés en fonction de leur nom ou de leur position ordinale. Les captures sans nom apparaissent en premier dans la collection et sont indexées de la gauche vers la droite dans l'ordre dans lequel elles figurent dans le modèle d'expression régulière. Les captures nommées sont indexées après les captures sans nom, de la gauche vers la droite dans l’ordre dans lequel elles apparaissent dans le modèle d’expression régulière. Pour déterminer les groupes numérotés disponibles dans la collection retournée pour une méthode de mise en correspondance d'expression régulière particulière, vous pouvez appeler la méthode d'instance <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType>. Pour déterminer les groupes nommés disponibles dans la collection, vous pouvez appeler la méthode d'instance <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType>. Les deux méthodes sont particulièrement utiles dans les opérations générales qui analysent les correspondances trouvées par une expression régulière.  
  
 La propriété <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> représente l'indexeur de la collection en C# et la propriété par défaut de l'objet de collection en Visual Basic. Cela signifie que les différents objets <xref:System.Text.RegularExpressions.Group> sont accessibles en fonction de leur index (ou nom, dans le cas des groupes nommés) comme suit :  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 L'exemple suivant définit une expression régulière qui utilise des constructions de regroupement pour capturer les mois, jour et année d'une date.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Le modèle d'expression régulière `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(\d{1,2})`|Mettre en correspondance un ou deux chiffres décimaux. Il s'agit du deuxième groupe de capture.|  
|`,`|Mettre en correspondance une virgule.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(\d{4})`|Mettre en correspondance quatre chiffres décimaux. Il s'agit du troisième groupe de capture.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
 [Retour au début](#introduction)  
  
<a name="the_captured_group"></a>

## <a name="the-captured-group"></a>Groupe capturé  

 La classe <xref:System.Text.RegularExpressions.Group> représente le résultat d'un groupe de capture spécifique. Les objets de groupe qui représentent les groupes de capture définis dans une expression régulière sont retournés par la propriété <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> de l'objet <xref:System.Text.RegularExpressions.GroupCollection> retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. La propriété <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> représente l'indexeur (en C#) et la propriété par défaut (en Visual Basic) de la classe <xref:System.Text.RegularExpressions.Group>. Vous pouvez également récupérer des membres spécifiques en itérant la collection à l'aide de la construction `foreach` ou `For Each`. La section précédente propose un exemple.  
  
 L'exemple suivant utilise des constructions de regroupement imbriquées pour capturer des sous-chaînes en groupes. Le modèle d'expression régulière `(a(b))c` met en correspondance la chaîne « abc ». Il affecte la sous-chaîne « ab » au premier groupe de capture, et la sous-chaîne « b » au second groupe de capture.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 L'exemple suivant utilise des constructions de regroupement nommées pour capturer des sous-chaînes dans une chaîne qui contient des données au format « NOM_DONNÉES:VALEUR », que l'expression régulière fractionne au niveau du symbole deux-points (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Le modèle d'expression régulière `^(?<name>\w+):(?<value>\w+)` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Commencer la correspondance au début de la chaîne d'entrée.|  
|`(?<name>\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Le nom de ce groupe de capture est `name`.|  
|`:`|Mettre en correspondance un symbole deux-points.|  
|`(?<value>\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Le nom de ce groupe de capture est `value`.|  
  
 Les propriétés de la classe <xref:System.Text.RegularExpressions.Group> fournissent des informations sur le groupe capturé : la propriété `Group.Value` contient la sous-chaîne capturée, la propriété `Group.Index` indique la position de début du groupe capturé dans le texte d'entrée, la propriété `Group.Length` contient la longueur du texte capturé et la propriété `Group.Success` indique si une correspondance a été trouvée entre une sous-chaîne et le modèle défini par le groupe de capture.  
  
 L'application de quantificateurs à un groupe (pour plus d'informations, consultez [Quantificateurs](quantifiers-in-regular-expressions.md)) modifie la relation d'une capture par groupe de capture de deux façons :  
  
- Si le quantificateur `*` ou `*?` (qui spécifie zéro correspondance, ou plus) est appliqué à un groupe, un groupe de capture peut ne pas avoir de correspondance dans la chaîne d'entrée. En l'absence de texte capturé, les propriétés de l'objet <xref:System.Text.RegularExpressions.Group> sont définies comme indiqué dans le tableau suivant.  
  
    |Propriété de groupe|Valeur|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     L'exemple suivant illustre cette situation. Dans le modèle d'expression régulière `aaa(bbb)*ccc`, le premier groupe de capture (la sous-chaîne « bbb ») peut être mis en correspondance zéro fois, ou plus. Comme la chaîne d’entrée « aaaccc » correspond au modèle, le groupe de capture ne possède pas de correspondance.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Les quantificateurs peuvent mettre en correspondance plusieurs occurrences d'un modèle défini par un groupe de capture. Dans ce cas, les propriétés `Value` et `Length` d'un objet <xref:System.Text.RegularExpressions.Group> ne contiennent des informations que sur la dernière sous-chaîne capturée. Par exemple, l'expression régulière suivante met en correspondance une phrase unique qui se termine par un point. Elle utilise deux constructions de regroupement : la première capture des mots individuels ainsi qu'un espace blanc, tandis que la seconde capture des mots individuels. Comme le montre le résultat de l'exemple, bien que l'expression régulière parvienne à capturer une phrase entière, le second groupe capture uniquement le dernier mot.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Retour au début](#introduction)  
  
<a name="CaptureCollection"></a>

## <a name="the-capture-collection"></a>Collection de captures  

 L'objet <xref:System.Text.RegularExpressions.Group> ne contient des informations que sur la dernière capture. Toutefois, l'ensemble complet des captures effectuées par un groupe de capture est récupérable de l'objet <xref:System.Text.RegularExpressions.CaptureCollection> retourné par la propriété <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>. Chaque membre de la collection est un objet <xref:System.Text.RegularExpressions.Capture> qui représente une capture effectuée par ce groupe de capture, dans l'ordre dans lequel ils ont été capturés (donc, dans l'ordre dans lequel les chaînes capturées ont été mises en correspondance de la gauche vers la droite dans la chaîne d'entrée). Vous pouvez récupérer des objets <xref:System.Text.RegularExpressions.Capture> spécifiques de la collection de deux façons :  
  
- En itérant la collection à l’aide d’une construction telle que `foreach` (en C#) ou `For Each` (en Visual Basic).  
  
- En utilisant la propriété <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> pour récupérer un objet spécifique en fonction de son index. La propriété <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> représente l'indexeur (en C#) ou la propriété par défaut de l'objet <xref:System.Text.RegularExpressions.CaptureCollection> (en Visual Basic).  
  
 Si aucun quantificateur n'est appliqué à un groupe de capture, l'objet <xref:System.Text.RegularExpressions.CaptureCollection> contient un objet <xref:System.Text.RegularExpressions.Capture> unique qui présente peu d'intérêt, car il fournit des informations sur la même correspondance que son objet <xref:System.Text.RegularExpressions.Group>. Si un quantificateur est appliqué à un groupe de capture, l'objet <xref:System.Text.RegularExpressions.CaptureCollection> contient toutes les captures effectuées par le groupe de capture, et le dernier membre de la collection représente la même capture que l'objet <xref:System.Text.RegularExpressions.Group>.  
  
 Par exemple, si vous utilisez le modèle d'expression régulière `((a(b))c)+` (où le quantificateur + spécifie une ou plusieurs correspondances) pour capturer des correspondances dans la chaîne « abcabcabc », l'objet <xref:System.Text.RegularExpressions.CaptureCollection> de chaque objet <xref:System.Text.RegularExpressions.Group> contient trois membres.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 L'exemple suivant utilise l'expression régulière `(Abc)+` pour trouver une ou plusieurs occurrences consécutives de la chaîne « Abc » dans la chaîne « XYZAbcAbcAbcXYZAbcAb ». L'exemple montre comment utiliser la propriété <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> pour retourner plusieurs groupes de sous-chaînes capturées.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Retour au début](#introduction)  
  
<a name="the_individual_capture"></a>

## <a name="the-individual-capture"></a>Capture individuelle  

 La classe <xref:System.Text.RegularExpressions.Capture> contient le résultat d'une capture de sous-expression unique. La propriété <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> contient le texte mis en correspondance, tandis que la propriété <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> indique la position, en base zéro, dans la chaîne d'entrée à laquelle commence la sous-chaîne mise en correspondance.  
  
 L'exemple suivant analyse une chaîne d'entrée pour récupérer la température de certaines villes. Une virgule (« , ») sépare chaque ville de sa température, tandis qu'un point-virgule (« ; ») sépare les données de chaque ville. La chaîne d'entrée entière représente une correspondance unique. Dans le modèle d'expression régulière `((\w+(\s\w+)*),(\d+);)+`, qui permet d'analyser la chaîne, le nom de la ville est affecté au deuxième groupe de capture, tandis que la température est attribuée au quatrième groupe de capture.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 L'expression régulière est définie comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
|`(\s\w+)*`|Mettre en correspondance zéro occurrence, ou plus, d'un espace blanc suivi d'un ou plusieurs caractères alphabétiques. Ce modèle met en correspondance les noms de ville composés de plusieurs mots. Il s'agit du troisième groupe de capture.|  
|`(\w+(\s\w+)*)`|Mettre en correspondance un ou plusieurs caractères alphabétiques suivis de zéro occurrence, ou plus, d'un espace blanc et d'un ou plusieurs caractères alphabétiques. Il s'agit du deuxième groupe de capture.|  
|`,`|Mettre en correspondance une virgule.|  
|`(\d+)`|Mettre en correspondance un ou plusieurs chiffres. Il s'agit du quatrième groupe de capture.|  
|`;`|Mettre en correspondance un point-virgule.|  
|`((\w+(\s\w+)*),(\d+);)+`|Mettre en correspondance le modèle représentant un mot suivi d’un nombre quelconque de mots supplémentaires, d’une virgule, d’un ou plusieurs chiffres et d’un point-virgule, une ou plusieurs fois. Il s'agit du premier groupe de capture.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Text.RegularExpressions>
- [Expressions régulières .NET](regular-expressions.md)
- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
