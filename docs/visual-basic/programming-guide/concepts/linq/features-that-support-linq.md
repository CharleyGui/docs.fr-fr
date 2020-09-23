---
title: Fonctionnalités prenant en charge LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: bd63cd36c1f85fd89349293a71ecc5b281165380
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078304"
---
# <a name="visual-basic-features-that-support-linq"></a>Fonctionnalités Visual Basic prenant en charge LINQ

LINQ (Language-Integrated Query) fait référence à la technologie de Visual Basic qui prend en charge la syntaxe de requête et d’autres constructions de langage directement dans le langage. Avec LINQ, vous n’avez pas besoin d’apprendre un nouveau langage pour effectuer des requêtes sur une source de données externe. Vous pouvez interroger des données dans des bases de données relationnelles, des magasins XML ou des objets à l’aide de Visual Basic. Cette intégration des fonctionnalités de requête dans le langage permet la vérification au moment de la compilation des erreurs de syntaxe et de la cohérence des types. Cette intégration garantit également que vous connaissez déjà la plupart des éléments que vous devez savoir pour écrire des requêtes riches et variées dans Visual Basic.  
  
 Les sections suivantes décrivent les constructions de langage qui prennent en charge LINQ avec suffisamment de détails pour vous permettre de commencer à lire la documentation de présentation, des exemples de code et des exemples d’applications. Vous pouvez également cliquer sur les liens pour obtenir des explications plus détaillées sur la façon dont les fonctionnalités de langage sont réunies pour activer la fonctionnalité de requête intégrée. Un bon point de départ est la [procédure pas à pas : écriture de requêtes dans Visual Basic](walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Expressions de requête  

 Les expressions de requête dans Visual Basic peuvent être exprimées dans une syntaxe déclarative similaire à celle de SQL ou de XQuery. Au moment de la compilation, la syntaxe de requête est convertie en appels de méthode à l’implémentation d’un fournisseur LINQ des méthodes d’extension d’opérateur de requête standard. Les applications contrôlent les opérateurs de requête standard qui sont dans la portée en spécifiant l’espace de noms approprié avec une `Imports` instruction. La syntaxe d’une expression de requête Visual Basic se présente comme suit :  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 Pour plus d’informations, consultez [Introduction à LINQ dans Visual Basic](../../language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Variables implicitement typées  

 Au lieu de spécifier explicitement un type lorsque vous déclarez et initialisez une variable, vous pouvez permettre au compilateur de déduire et d’assigner le type. On parle alors d' *inférence de type local*.  
  
 Les variables dont les types sont déduits sont fortement typées, tout comme les variables dont vous spécifiez explicitement le type. L’inférence de type local fonctionne uniquement lorsque vous définissez une variable locale à l’intérieur d’un corps de méthode. Pour plus d’informations, consultez [instruction Option Infer](../../../language-reference/statements/option-infer-statement.md) et [inférence de type local](../../language-features/variables/local-type-inference.md).  
  
 L’exemple suivant illustre l’inférence de type local. Pour utiliser cet exemple, vous devez affecter `Option Infer` à la valeur `On` .  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 L’inférence de type local permet également de créer des types anonymes, qui sont décrits plus loin dans cette section et sont nécessaires pour les requêtes LINQ.  
  
 Dans l’exemple LINQ suivant, l’inférence de type se produit si `Option Infer` a la valeur `On` ou `Off` . Une erreur de compilation se produit si `Option Infer` est `Off` et `Option Strict` est `On` .  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>Initialiseurs d'objets  

 Les initialiseurs d’objets sont utilisés dans les expressions de requête lorsque vous devez créer un type anonyme pour contenir les résultats d’une requête. Elles peuvent également être utilisées pour initialiser des objets de types nommés en dehors des requêtes. À l’aide d’un initialiseur d’objet, vous pouvez initialiser un objet sur une seule ligne sans appeler explicitement un constructeur. En supposant que vous ayez une classe nommée `Customer` qui a des `Name` Propriétés et publiques `Phone` , ainsi que d’autres propriétés, un initialiseur d’objet peut être utilisé de cette manière :  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 Pour plus d’informations, consultez [initialiseurs d’objets : types nommés et anonymes](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Types anonymes  

 Les types anonymes offrent un moyen pratique de regrouper temporairement un ensemble de propriétés dans un élément que vous souhaitez inclure dans un résultat de requête. Cela vous permet de choisir n’importe quelle combinaison de champs disponibles dans la requête, dans n’importe quel ordre, sans définir un type de données nommé pour l’élément.  
  
 Un *type anonyme* est construit dynamiquement par le compilateur. Le nom du type est assigné par le compilateur et peut changer à chaque nouvelle compilation. Par conséquent, le nom ne peut pas être utilisé directement. Les types anonymes sont initialisés de la façon suivante :  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 Pour plus d’informations, consultez [types anonymes](../../language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Méthodes d’extension  

 Les méthodes d’extension vous permettent d’ajouter des méthodes à un type de données ou à une interface à partir de l’extérieur de la définition. Cette fonctionnalité vous permet, en effet, d’ajouter de nouvelles méthodes à un type existant sans réellement modifier le type. Les opérateurs de requête standard sont eux-mêmes un ensemble de méthodes d’extension qui fournissent des fonctionnalités de requête LINQ pour tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601> . Autres extensions pour <xref:System.Collections.Generic.IEnumerable%601> inclure <xref:System.Linq.Enumerable.Count%2A> , <xref:System.Linq.Enumerable.Union%2A> et <xref:System.Linq.Enumerable.Intersect%2A> .  
  
 La méthode d’extension suivante ajoute une méthode Print à la <xref:System.String> classe.  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 La méthode est appelée comme une méthode d’instance ordinaire de <xref:System.String> :  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 Pour plus d’informations, consultez [Méthodes d’extension](../../language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Expressions lambda  

 Une expression lambda est une fonction sans nom qui calcule et retourne une valeur unique. Contrairement aux fonctions nommées, une expression lambda peut être définie et exécutée en même temps. L’exemple suivant affiche 4.  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 Vous pouvez assigner la définition d’expression lambda à un nom de variable, puis utiliser le nom pour appeler la fonction. L’exemple suivant affiche également 4.  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 Dans LINQ, les expressions lambda sont sous-jacentes de nombreux opérateurs de requête standard. Le compilateur crée des expressions lambda pour capturer les calculs définis dans les méthodes de requête fondamentales telles que `Where` , `Select` ,, `Order By` `Take While` et autres.  
  
 Par exemple, le code suivant définit une requête qui retourne tous les étudiants d’une liste d’étudiants.  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 La définition de la requête est compilée dans du code similaire à l’exemple suivant, qui utilise deux expressions lambda pour spécifier les arguments pour `Where` et `Select` .  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 L’une ou l’autre version peut être exécutée à l’aide d’une `For Each` boucle :  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 Pour plus d’informations, consultez [expressions lambda](../../language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (Visual Basic)](index.md)
- [Mise en route de LINQ dans Visual Basic](getting-started-with-linq.md)
- [LINQ et chaînes (Visual Basic)](linq-and-strings.md)
- [Instruction Option Infer](../../../language-reference/statements/option-infer-statement.md)
- [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)
