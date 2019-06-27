---
title: Chaînes - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: e193d6a51c3d4f1d81e3b74b1474d0e7cdcfca53
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398126"
---
# <a name="strings-c-programming-guide"></a>Chaînes (Guide de programmation C#)
Une chaîne est un objet de type <xref:System.String> dont la valeur est du texte. En interne, le texte est stocké sous la forme d’une collection séquentielle en lecture seule d’objets <xref:System.Char>. Il n’existe aucun caractère de fin Null à la fin d’une chaîne C# ; par conséquent, une chaîne C# peut contenir n’importe quel nombre de caractères Null incorporés ('\0'). La propriété <xref:System.String.Length%2A> d’une chaîne représente le nombre d’objets `Char` qu’elle contient, et non pas le nombre de caractères Unicode. Pour accéder à des points de code Unicode individuels dans une chaîne, utilisez l’objet <xref:System.Globalization.StringInfo>.  
  
## <a name="string-vs-systemstring"></a>Comparatif entre string et System.String  
 En C#, le mot clé `string` est un alias pour <xref:System.String>. Par conséquent, `String` et `string` sont équivalents et vous pouvez utiliser la convention d’affectation de noms que vous préférez. La classe `String` fournit de nombreuses méthodes pour créer, manipuler et comparer des chaînes en toute sécurité. En outre, le langage C# surcharge certains opérateurs pour simplifier les opérations de chaînes courantes. Pour plus d’informations sur le mot clé, voir [chaîne](../../../csharp/language-reference/keywords/string.md). Pour plus d’informations sur le type et ses méthodes, consultez <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Déclaration et initialisation de chaînes  
 Vous pouvez déclarer et initialiser des chaînes de différentes manières, comme illustré dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Notez que vous n’utilisez pas l’opérateur [new](../../../csharp/language-reference/operators/new-operator.md) pour créer un objet String, excepté lors de l’initialisation de la chaîne avec un tableau de caractères.  
  
 Initialisez une chaîne avec la valeur constante <xref:System.String.Empty> pour créer un objet <xref:System.String> dont la chaîne est de longueur nulle. La représentation de littéral de chaîne d’une chaîne de longueur nulle est "". En initialisant les chaînes avec la valeur <xref:System.String.Empty> au lieu de [null](../../../csharp/language-reference/keywords/null.md), vous pouvez réduire les risques de levée de l’exception <xref:System.NullReferenceException>. Utilisez la méthode statique <xref:System.String.IsNullOrEmpty%28System.String%29> pour vérifier la valeur d’une chaîne avant de tenter d’y accéder.  
  
## <a name="immutability-of-string-objects"></a>Immuabilité des objets String  
 Les objets String sont *immuables* : ils ne peuvent pas être modifiés une fois qu’ils ont été créés. Toutes les méthodes <xref:System.String> et tous les opérateurs C# qui semblent modifier une chaîne retournent en fait les résultats dans un nouvel objet string. Dans l’exemple suivant, lorsque les contenus de `s1` et `s2` sont concaténés pour former une chaîne unique, les deux chaînes d’origine restent inchangées. L’opérateur `+=` crée une nouvelle chaîne qui contient le contenu combiné. Ce nouvel objet est assigné à la variable `s1` et l’objet d’origine qui a été assigné à `s1` est libéré pour la garbage collection, car aucune autre variable ne le référence.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Étant donné qu’une « modification » de chaîne correspond en fait à la création d’une nouvelle chaîne, vous devez être prudent lorsque vous créez des références aux chaînes. Si vous créez une référence à une chaîne, puis « modifiez » la chaîne d’origine, la référence continue à pointer vers l’objet d’origine au lieu du nouvel objet créé lors de la modification de la chaîne. Le code suivant illustre ce comportement :  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Pour plus d’informations sur la création de nouvelles chaînes basées sur des modifications telles que les opérations rechercher-remplacer sur la chaîne d’origine, voir [Guide pratique pour modifier du contenu de chaîne](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Littéraux de chaînes normales et textuelles  
 Utilisez des littéraux de chaînes normales lorsque vous devez incorporer des caractères d’échappement fournis par C#, comme illustré dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Utilisez des chaînes textuelles pour plus de commodité et pour une meilleure lisibilité lorsque le texte de la chaîne contient des barres obliques inverses, par exemple dans les chemins d’accès. Étant donné que les chaînes textuelles conservent les caractères de nouvelle ligne dans le texte de la chaîne, elles peuvent servir à initialiser des chaînes multilignes. Utilisez des guillemets doubles pour incorporer des guillemets dans une chaîne textuelle. L’exemple suivant montre certaines utilisations courantes des chaînes textuelles :  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Séquences d’échappement de chaîne  
  
|Séquence d'échappement|Nom du caractère|Encodage Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|Guillemet simple|0x0027|  
|\\"|Guillemet double|0x0022|  
|\\\\ |Barre oblique inverse|0x005C|  
|\0|Null|0x0000|  
|\a|Alerte|0x0007|  
|\b|Retour arrière|0x0008|  
|\f|Saut de page|0x000C|  
|\n|Nouvelle ligne|0x000A|  
|\r|Retour chariot|0x000D|  
|\t|Tabulation horizontale|0x0009|  
|\U|Séquence d’échappement Unicode pour les paires de substitution.|\Unnnnnnnn|  
|\u|Séquence d’échappement Unicode|\u0041 = "A"|  
|\v|Tabulation verticale|0x000B|  
|\x|Séquence d’échappement Unicode similaire à "\u", mais avec une longueur variable.|\x0041 ou \x41 = "A"|  
  
> [!NOTE]
>  Au moment de la compilation, les chaînes textuelles sont converties en chaînes normales avec les mêmes séquences d’échappement. Par conséquent, si vous affichez une chaîne textuelle dans la fenêtre Espion du débogueur, vous verrez les caractères d’échappement qui ont été ajoutés par le compilateur et non la version textuelle de votre code source. Par exemple, la chaîne textuelle @"C:\files.txt" s’affiche dans la fenêtre Espion en tant que "C:\\\files.txt".  
  
## <a name="format-strings"></a>Chaînes de format  
 Une chaîne de format est une chaîne dont le contenu est déterminé de façon dynamique lors de l’exécution. Les chaînes de format sont créées en incorporant des *expressions interpolées* ou des espaces réservés à l’intérieur d’accolades dans une chaîne. Tous les éléments à l’intérieur des accolades (`{...}`) seront convertis en une valeur et affichés sous forme d’une chaîne mise en forme lors de l’exécution. Il existe deux méthodes pour créer des chaînes de format : l’interpolation de chaîne et la mise en forme composite.

### <a name="string-interpolation"></a>Interpolation de chaîne
Disponible dans C# 6.0 et versions ultérieures, les [*chaînes interpolées*](../../language-reference/tokens/interpolated.md) sont identifiées par le caractère spéciale `$` et incluent des expressions interpolées entre accolades. Si vous ne connaissez pas l’interpolation de chaîne, consultez le tutoriel interactif [Interpolation de chaînes en C#](../../tutorials/exploration/interpolated-strings.yml) pour obtenir un aperçu.

Utilisez l’interpolation de chaîne pour améliorer la lisibilité et la maintenance de votre code. L’interpolation de chaîne permet d’obtenir les mêmes résultats que la méthode `String.Format`, mais avec plus de facilité d’utilisation et de clarté.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Mise en forme composite
<xref:System.String.Format%2A?displayProperty=nameWithType> utilise des espaces réservés entre accolades pour créer une chaîne de format. Cet exemple renvoie une sortie similaire à la méthode d’interpolation de chaîne utilisée ci-dessus.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

Pour plus d’informations sur la mise en forme des types .NET, consultez [Mise en forme des types dans .NET](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Sous-chaînes  
 Une sous-chaîne est une séquence de caractères qui est contenue dans une chaîne. Utilisez la méthode <xref:System.String.Substring%2A> pour créer une chaîne à partir d’une partie de la chaîne d’origine. Vous pouvez rechercher une ou plusieurs occurrences d’une sous-chaîne en utilisant la méthode <xref:System.String.IndexOf%2A>. Utilisez la méthode <xref:System.String.Replace%2A> pour remplacer toutes les occurrences d’une sous-chaîne spécifiée par une nouvelle chaîne. Comme la méthode <xref:System.String.Substring%2A>, <xref:System.String.Replace%2A> retourne en fait une nouvelle chaîne et ne modifie pas la chaîne d’origine. Pour plus d’informations, consultez [Guide pratique pour rechercher des chaînes](../../how-to/search-strings.md) et [Guide pratique pour modifier le contenu des chaînes](../../how-to/modify-string-contents.md).  
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#9)]  
  
## <a name="accessing-individual-characters"></a>Accès aux caractères individuels  
 Vous pouvez utiliser la notation de tableau avec une valeur d’index pour obtenir un accès en lecture seule aux caractères individuels, comme dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 Si les méthodes<xref:System.String> ne fournissent pas la fonctionnalité nécessaire pour modifier les caractères individuels d’une chaîne, vous pouvez utiliser un objet <xref:System.Text.StringBuilder> pour modifier les caractères individuels « sur place », puis créer une chaîne pour stocker les résultats en utilisant les méthodes <xref:System.Text.StringBuilder>. Dans l’exemple suivant, supposons que vous devez modifier la chaîne d’origine d’une façon particulière, puis stocker les résultats pour une utilisation ultérieure :  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Chaînes Null et chaînes vides  
 Une chaîne vide est une instance d’un objet <xref:System.String?displayProperty=nameWithType> qui contient zéro caractère. Les chaînes vides sont souvent utilisées dans divers scénarios de programmation pour représenter un champ de texte vide. Vous pouvez appeler des méthodes sur des chaînes vides, car ce sont des objets <xref:System.String?displayProperty=nameWithType>. Les chaînes vides sont initialisées comme suit :  
  
```  
string s = String.Empty;  
```  
  
 En revanche, une chaîne null ne fait pas référence à une instance d’un objet <xref:System.String?displayProperty=nameWithType>, et toute tentative pour appeler une méthode sur une chaîne null lève une exception <xref:System.NullReferenceException>. Toutefois, vous pouvez utiliser des chaînes Null dans les opérations de comparaison et de concaténation avec d’autres chaînes. Les exemples suivants illustrent certains cas dans lesquels une référence à une chaîne Null provoque ou non la levée d’une exception :  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Utilisation de StringBuilder pour créer rapidement une chaîne  
 Les opérations Strings dans .NET sont hautement optimisées et, dans la plupart des cas, n’ont pas d’incidence significative sur les performances. Toutefois, dans certains scénarios, notamment dans le cas de boucles serrées qui s’exécutent plusieurs centaines voire milliers de fois, les opérations String peuvent affecter les performances. La classe <xref:System.Text.StringBuilder> crée un tampon de chaîne qui offre de meilleures performances si votre programme exécute de nombreuses manipulations de chaînes. La chaîne <xref:System.Text.StringBuilder> vous permet également de réassigner des caractères individuels, une fonctionnalité non prise en charge par les types de données string intégrés. Ce code, par exemple, modifie le contenu d’une chaîne sans créer de nouvelle chaîne :  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 Dans cet exemple, un objet <xref:System.Text.StringBuilder> est utilisé pour créer une chaîne à partir d’un ensemble de types numériques :  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Chaînes, méthodes d’extension et LINQ  
 Étant donné que le type <xref:System.String> implémente <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser les méthodes d’extension définies dans la classe <xref:System.Linq.Enumerable> sur des chaînes. Pour éviter une surcharge visuelle, ces méthodes sont exclues d’IntelliSense pour le type <xref:System.String>, mais elles restent néanmoins disponibles. Vous pouvez également utiliser des expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sur les chaînes. Pour plus d’informations, consultez [LINQ et Strings](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Guide pratique pour modifier le contenu des chaînes](../../how-to/modify-string-contents.md)|Illustre les techniques permettant de transformer des chaînes et de modifier le contenu de chaînes.|  
|[Guide pratique pour comparer des chaînes](../../how-to/compare-strings.md)|Montre comment effectuer des comparaisons de chaînes ordinales et spécifiques à la culture.|  
|[Guide pratique pour concaténer plusieurs chaînes](../../how-to/concatenate-multiple-strings.md)|Illustre différentes manières de joindre plusieurs chaînes pour en former une.|
|[Guide pratique pour analyser des chaînes à l’aide de String.Split](../../how-to/parse-strings-using-split.md)|Contient un exemple de code qui illustre l’utilisation de la méthode `String.Split` pour analyser des chaînes.|  
|[Guide pratique pour rechercher des chaînes](../../how-to/search-strings.md)|Explique comment rechercher du texte ou des modèles spécifiques dans des chaînes.|  
|[Guide pratique pour déterminer si une chaîne représente une valeur numérique](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Montre comment analyser une chaîne en toute sécurité pour déterminer si elle possède une valeur numérique valide.|  
|[Interpolation de chaîne](../../language-reference/tokens/interpolated.md)|Décrit la fonctionnalité d’interpolation de chaîne qui fournit une syntaxe pratique pour les chaînes de format.|
|[Opérations de chaînes de base](../../../../docs/standard/base-types/basic-string-operations.md)|Fournit des liens vers des rubriques utilisant les méthodes <xref:System.String?displayProperty=nameWithType> et <xref:System.Text.StringBuilder?displayProperty=nameWithType> pour effectuer des opérations de chaînes de base.|  
|[Parsing Strings](../../../standard/base-types/parsing-strings.md)|Décrit comment convertir des représentations sous forme de chaîne de types de base .NET en instances de types correspondants.|  
|[Analyse des chaînes de date et d’heure dans .NET](../../../standard/base-types/parsing-datetime.md)|Montre comment convertir une chaîne telle que « 24/01/2008 » en objet <xref:System.DateTime?displayProperty=nameWithType>.|  
|[Comparaison de chaînes](../../../../docs/standard/base-types/comparing.md)|Inclut des informations sur la façon de comparer des chaînes et fournit des exemples en C# et Visual Basic.|  
|[Utilisation de la classe StringBuilder](../../../standard/base-types/stringbuilder.md)|Explique comment créer et modifier des objets string dynamiques avec la classe <xref:System.Text.StringBuilder>.|  
|[LINQ et chaînes](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|Fournit des informations sur l’exécution de différentes opérations sur des chaînes à l’aide de requêtes LINQ.|  
|[Guide de programmation C#](../../../csharp/programming-guide/index.md)|Fournit des liens vers des rubriques qui expliquent les constructions de programmation en C#.|  
