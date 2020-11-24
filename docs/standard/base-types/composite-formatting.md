---
title: Mise en forme composite
description: En savoir plus sur la mise en forme composite .NET, qui prend comme entrée une liste d’objets et une chaîne de format composite, contenant du texte fixe avec des espaces réservés indexés.
ms.date: 10/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parameter specifiers
- strings [.NET], alignment
- format specifiers, composite formatting
- strings [.NET], composite
- composite formatting
- objects [.NET], formatting multiple objects
ms.assetid: 87b7d528-73f6-43c6-b71a-f23043039a49
ms.openlocfilehash: a0252d013ee6cf7cba7f953fc8a1e2c66c510ca7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683951"
---
# <a name="composite-formatting"></a>Mise en forme composite

La fonctionnalité de mise en forme composite du .NET utilise une liste d’objets et une chaîne de format composite comme entrée. Une chaîne de format composite se compose de texte fixe mélangé à des espaces réservés indexés, appelés éléments de format, qui correspondent aux objets de la liste. L'opération de mise en forme produit une chaîne résultante qui se compose du texte fixe d'origine mélangé à la représentation sous forme de chaîne des objets de la liste.  
  
> [!IMPORTANT]
> Au lieu d’utiliser des chaînes de format composite, vous pouvez utiliser des *chaînes interpolées* si le langage et la version du langage que vous utilisez les prennent en charge. Une chaîne interpolée est une chaîne contenant des *expressions interpolées*. Chaque expression interpolée est résolue avec la valeur de l’expression et incluse dans la chaîne du résultat quand la chaîne est affectée. Pour plus d’informations, consultez [interpolation de chaîne (référence C#)](../../csharp/language-reference/tokens/interpolated.md) et [chaînes interpolées (référence Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).

La fonctionnalité de mise en forme composite est prise en charge par les méthodes suivantes :  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, qui retourne une chaîne de résultat mise en forme.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, qui ajoute une chaîne de résultat mise en forme à un objet <xref:System.Text.StringBuilder>.
- Certaines surcharges de la méthode <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, qui affichent une chaîne de résultat mise en forme sur la console.  
  
- Certaines surcharges de la méthode <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType>, qui écrivent la chaîne de résultat mise en forme dans un flux ou un fichier. Les classes dérivées de <xref:System.IO.TextWriter>, telles que <xref:System.IO.StreamWriter> et <xref:System.Web.UI.HtmlTextWriter>, partagent également ces fonctionnalités.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, qui génère un message mis en forme pour les écouteurs Trace.  
  
- Les méthodes <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> qui génèrent des messages mis en forme pour les écouteurs Trace.  
  
- La méthode <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, qui écrit une méthode à caractère informatif pour les écouteurs Trace.  
  
## <a name="composite-format-string"></a>Chaîne de format composite  

 Une chaîne de format composite et une liste d'objets sont utilisées comme arguments des méthodes qui prennent en charge la fonctionnalité de mise en forme composite. Une chaîne de format composite est constituée de zéro, une ou plusieurs séquences de texte fixe mélangées à un ou plusieurs éléments de format. Le texte fixe correspond à toute chaîne que vous choisissez, et chaque élément de format correspond à un objet ou une structure boxed dans la liste. La fonctionnalité de mise en forme composite retourne une nouvelle chaîne résultante, dans laquelle chaque élément de format est remplacé par la représentation sous forme de chaîne de l’objet correspondant dans la liste.  
  
 Prenons le fragment de code <xref:System.String.Format%2A> suivant.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Le texte fixe est `Name =` et `, hours =`. Les éléments de format sont `{0}`, dont l’index est 0, ce qui correspond à l’objet `name`, et `{1:hh}`, dont l’index est 1, ce qui correspond à l’objet `DateTime.Now`.  
  
## <a name="format-item-syntax"></a>Syntaxe des éléments de format  

 Chaque élément de format prend la forme suivante et comprend les composants suivants :  
  
 `{`*index*[ `,` *alignement*] [ `:` *FormatString*]`}`  
  
 Les accolades correspondantes (« { » et « } ») sont nécessaires.  
  
### <a name="index-component"></a>Composant d'index  

 Le composant obligatoire *index*, également appelé « spécificateur de paramètre », est un nombre à partir de 0 qui permet d’identifier un élément correspondant dans la liste des objets. En d'autres termes, l'élément de format dont le spécificateur de format est 0 met en forme le premier objet de la liste, l'élément de format dont le spécificateur de paramètres est 1 met en forme le deuxième objet de la liste, etc. L’exemple suivant comprend quatre spécificateurs de paramètres, numérotés de 0 à 3, pour représenter les nombres premiers inférieurs à 10 :  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Plusieurs éléments de format peuvent faire référence au même élément de la liste d'objets en indiquant le même spécificateur de paramètre. Par exemple, vous pouvez mettre en forme la même valeur numérique au format hexadécimal, scientifique et numérique en spécifiant une chaîne de format composite telle que : « 0x {0:X} {0:E} {0:N} », comme le montre l’exemple suivant.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Chaque élément de format peut faire référence à n'importe quel objet de la liste. Par exemple, s’il y a trois objets, vous pouvez mettre en forme le deuxième, le premier et le troisième objet en spécifiant une chaîne de format composite telle que : « {1} {0} {2} ». Un objet qui n'est pas référencé par un élément de format est ignoré. Une <xref:System.FormatException> est levée au moment de l’exécution si un spécificateur de paramètres désigne un élément situé en dehors des limites de la liste d’objets.  
  
### <a name="alignment-component"></a>Composant d'alignement  

 Le composant facultatif *alignment* est un entier signé indiquant la largeur préférée du champ mis en forme. Si la valeur du composant *alignment* est inférieure à la longueur de la chaîne mise en forme, *alignment* est ignoré et la longueur de la chaîne mise en forme est utilisée comme largeur de champ. Les données mises en forme dans le champ sont alignées à droite si *alignment* est positif et alignées à gauche si *alignment* est négatif. Si un remplissage est nécessaire, des espaces blancs sont utilisés. La virgule est obligatoire si *alignment* est spécifié.  
  
 L'exemple suivant définit deux tableaux, l'un contenant les noms des employés et l'autre contenant les heures qu'ils ont prestées sur une période de deux semaines. La chaîne de format composite aligne les noms à gauche dans un champ de 20 caractères et aligne leurs heures à droite dans un champ de 5 caractères. Notez que la chaîne de format standard "N1" est également utilisée pour mettre les heures sous la forme d'un nombre avec une décimale.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Composant de chaîne de format  

 Le composant facultatif *formatString* est une chaîne de format appropriée pour le type d’objet mis en forme. Spécifiez une chaîne de format numérique standard ou personnalisée si l'objet correspondant est une valeur numérique, une chaîne de format de date et d'heure standard ou personnalisée si l'objet correspondant est un objet <xref:System.DateTime>, ou une [chaîne de format d'énumération](enumeration-format-strings.md) si l'objet correspondant est une valeur d'énumération. Si *formatString* n’est pas spécifié, le spécificateur de format général (« G ») pour un type numérique, de date et d’heure ou d’énumération est utilisé. Le point est obligatoire si *formatString* est spécifié.  
  
 Le tableau suivant répertorie les types ou catégories de types de la bibliothèque de classes .NET qui prennent en charge un ensemble prédéfini de chaînes de format, et fournit des liens vers les rubriques qui répertorient les chaînes de format prises en charge. Notez que la mise en forme de chaînes est un mécanisme extensible qui permet de définir de nouvelles chaînes de format pour tous les types existants et de définir un ensemble de chaînes de format pris en charge par un type défini par l'application. Pour plus d'informations, consultez les rubriques sur l'interface <xref:System.IFormattable> et <xref:System.ICustomFormatter>.  
  
|Type ou catégorie de type|Consultez|  
|---------------------------|---------|  
|Types de date et d'heure (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Chaînes de format de date et d'heure standard](standard-date-and-time-format-strings.md)<br /><br /> [Chaînes de format de date et d'heure personnalisées](custom-date-and-time-format-strings.md)|  
|Types d'énumération (tous les types dérivés de <xref:System.Enum?displayProperty=nameWithType>)|[Chaînes de format d'énumération](enumeration-format-strings.md)|  
|Types numériques (<xref:System.Numerics.BigInteger>, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>)|[Chaînes de format numériques standard](standard-numeric-format-strings.md)<br /><br /> [Chaînes de format numériques personnalisées](custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Chaînes de format TimeSpan standard.](standard-timespan-format-strings.md)<br /><br /> [Chaînes de format TimeSpan personnalisées](custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Accolades d'échappement  

 Les accolades ouvrantes et fermantes sont interprétées comme le début et la fin d'un élément de format. Par conséquent, vous devez utiliser une séquence d'échappement pour afficher une accolade ouvrante ou fermante littérale. Spécifiez deux accolades ouvrantes (« {{ ») dans le texte fixe pour afficher une accolade ouvrante (« { ») ou deux accolades fermantes (« }} ») pour afficher une accolade fermante (« } »). Les accolades d'un élément de format sont interprétées séquentiellement dans l'ordre dans lequel elles sont rencontrées. L'interprétation des accolades imbriquées n'est pas prise en charge.  
  
 La façon dont les accolades d'échappement sont interprétées peut générer des résultats inattendus. Par exemple, considérez l'élément de format « {{{0:D}}} » destiné à afficher une accolade ouvrante, une valeur numérique mise en forme en tant que nombre décimal et une accolade fermante. Toutefois, l'élément de format est réellement interprété de la manière suivante :  
  
1. Les deux premières accolades ouvrantes (« {{ ») font l'objet d'un échappement et produisent une accolade ouvrante.  
  
2. Les trois caractères suivants (« {0: ») sont interprétés comme le début d'un élément de format.  
  
3. Le caractère suivant (« D ») devrait être interprété comme le spécificateur de format numérique standard Decimal, mais les deux accolades d'échappement suivantes (« }} ») produisent une seule accolade. Comme la chaîne résultante (« D} ») n'est pas un spécificateur de format numérique standard, elle est interprétée comme une chaîne de mise en forme personnalisée qui sous-entend l'affichage de la chaîne littérale « D} ».  
  
4. La dernière accolade (« } ») est interprétée comme la fin de l'élément de format.  
  
5. Le résultat final affiché est la chaîne littérale, « {D} ». La valeur numérique qui devait être mise en forme n'est pas affichée.  
  
 Pour éviter une mauvaise interprétation des accolades d'échappement et des éléments de format, mettez en forme séparément les accolades et l'élément de format. Autrement dit, dans la première opération de formatage, affichez une accolade ouvrante littérale, dans l'opération suivante, affichez le résultat de l'élément de format, puis dans la dernière opération, affichez une accolade fermante littérale. L'exemple suivant illustre cette approche.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Ordre de traitement  

 Si l'appel à la méthode de mise en forme composite comprend un argument <xref:System.IFormatProvider> dont la valeur n'est pas `null`, le runtime appelle sa méthode <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> pour demander une implémentation de <xref:System.ICustomFormatter>. Si la méthode est en mesure de retourner une implémentation de <xref:System.ICustomFormatter>, elle est mise en cache durant l’appel de la méthode de mise en forme composite.
  
 Chaque valeur de la liste de paramètres qui correspond à un élément de mise en forme est convertie en une chaîne de la manière suivante :  
  
1. Si la valeur à mettre en forme est `null`, une chaîne vide <xref:System.String.Empty?displayProperty=nameWithType> est retournée.  
  
2. Si une implémentation de <xref:System.ICustomFormatter> est disponible, le runtime appelle sa méthode <xref:System.ICustomFormatter.Format%2A>. Il passe à la méthode la valeur *formatString* de l’élément de mise en forme, s’il en existe une, ou `null` si ce n’est pas le cas, ainsi que l’implémentation de <xref:System.IFormatProvider>. Si l’appel à la méthode <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> retourne `null`, l’exécution se poursuit à l’étape suivante. Sinon, le résultat de l’appel à <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> est retourné.
  
3. Si la valeur implémente l'interface <xref:System.IFormattable>, la méthode de l'interface <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> est appelée. La valeur *formatString*, s’il en existe une dans l’élément de mise en forme, est passée à la méthode, ou bien la valeur `null` si ce n’est pas le cas. L'argument <xref:System.IFormatProvider> est déterminé comme suit :  
  
    - Pour une valeur numérique, si une méthode de mise en forme composite avec l’argument non null <xref:System.IFormatProvider> est appelée, le runtime demande un objet <xref:System.Globalization.NumberFormatInfo> de sa méthode <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>. S’il ne peut pas en fournir un, si la valeur de l’argument est `null` ou si la méthode de mise en forme composite n’a pas de paramètre <xref:System.IFormatProvider>, l’objet <xref:System.Globalization.NumberFormatInfo> de la culture actuelle du thread est utilisé.  
  
    - Pour une valeur de date et d’heure, si une méthode de mise en forme composite avec l’argument non null <xref:System.IFormatProvider> est appelée, le runtime demande un objet <xref:System.Globalization.DateTimeFormatInfo> de sa méthode <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>. S’il ne peut pas en fournir un, si la valeur de l’argument est `null` ou si la méthode de mise en forme composite n’a pas de paramètre <xref:System.IFormatProvider>, l’objet <xref:System.Globalization.DateTimeFormatInfo> de la culture actuelle du thread est utilisé.  
  
    - Pour les objets d'autres types, si une méthode de mise en forme composite est appelée avec un argument <xref:System.IFormatProvider>, sa valeur est transmise directement à l'implémentation de <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType>. Dans le cas contraire, `null` est transmis à l’implémentation de <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType>.  
  
4. La méthode `ToString` sans paramètre du type, qui remplace <xref:System.Object.ToString?displayProperty=nameWithType> ou hérite du comportement de la classe de base, est appelée. Dans ce cas, la chaîne de format spécifiée par le composant *formatString* dans l’élément de mise en forme, si elle est présente, est ignorée.  
  
 L'alignement est appliqué une fois les précédentes étapes effectuées.  
  
## <a name="code-examples"></a>Exemples de code  

 L'exemple suivant illustre une chaîne créée à l'aide de la mise en forme composite et une autre chaîne créée à l'aide de la méthode `ToString` d'un objet. Les deux types de mise en forme produisent des résultats équivalents.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 En supposant que le jour actuel soit un jeudi du mois de mai, la valeur des deux chaînes de l'exemple précédent est `Thursday May` dans la culture américaine.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> présente les mêmes fonctionnalités que <xref:System.String.Format%2A?displayProperty=nameWithType>. La seule différence entre les deux méthodes est que <xref:System.String.Format%2A?displayProperty=nameWithType> retourne son résultat sous la forme d'une chaîne, alors que <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> écrit le résultat dans le flux de sortie associé à l'objet <xref:System.Console>. L'exemple suivant utilise la méthode <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> pour mettre en forme la valeur de `MyInt` en une valeur monétaire.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 L'exemple suivant illustre la mise en forme de plusieurs objets, y compris la mise en forme d'un objet de deux manières différentes.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 L'exemple suivant illustre l'utilisation de l'alignement lors de la mise en forme. Les arguments mis en forme sont placés entre des barres verticales (&#124;) pour mettre en évidence l’alignement en résultant.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Console.WriteLine%2A>
- <xref:System.String.Format%2A?displayProperty=nameWithType>
- [Interpolation de chaîne (C#)](../../csharp/language-reference/tokens/interpolated.md)
- [Interpolation de chaîne (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- [Mise en forme des types](formatting-types.md)
- [Chaînes de format numériques standard](standard-numeric-format-strings.md)
- [Chaînes de format numériques personnalisées](custom-numeric-format-strings.md)
- [Chaînes de format de date et d'heure standard](standard-date-and-time-format-strings.md)
- [Chaînes de format de date et d'heure personnalisées](custom-date-and-time-format-strings.md)
- [Chaînes de format TimeSpan standard.](standard-timespan-format-strings.md)
- [Chaînes de format TimeSpan personnalisées](custom-timespan-format-strings.md)
- [Chaînes de format d'énumération](enumeration-format-strings.md)
