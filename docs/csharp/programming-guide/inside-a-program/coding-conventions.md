---
title: Conventions de codage C# - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399734"
---
# <a name="c-coding-conventions-c-programming-guide"></a>Conventions de codage C# (Guide de programmation C#)

Les conventions de codage répondent aux objectifs suivants :  
  
- Elles confèrent une apparence cohérente au code, afin que les lecteurs puissent se concentrer sur le contenu, pas sur la disposition.  
  
- Elles permettent aux lecteurs de comprendre le code plus rapidement en formulant des hypothèses selon leur expérience antérieure.  
  
- Elles facilitent la copie, la modification et la gestion du code.  
  
- Elles illustrent les bonnes pratiques en C#.  

Les lignes directrices de cet article sont utilisées par Microsoft pour développer des échantillons et de la documentation.  
  
## <a name="naming-conventions"></a>Conventions de nommage  
  
- Dans les exemples courts qui ne comprennent pas de [directives](../../language-reference/keywords/using-directive.md), utilisez les qualifications d’espace de noms. Si vous savez qu'un espace de noms est importé par défaut dans un projet, vous n'êtes pas obligé de qualifier entièrement les noms à partir de cet espace de noms. Les noms qualifiés peuvent être interrompus après un point (.) s'ils sont trop longs pour contenir sur une ligne unique, comme indiqué dans l'exemple suivant.  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- Vous n'avez pas à modifier les noms des objets qui ont été créés à l'aide des outils du concepteur Visual Studio pour les rendre conformes aux autres directives.  
  
## <a name="layout-conventions"></a>Conventions de disposition  

Une bonne disposition utilise la mise en forme pour souligner la structure de votre code et en faciliter la lecture. Les exemples Microsoft et autres se conforment aux conventions suivantes :  
  
- Utilisez les paramètres par défaut de l'éditeur de code (retrait intelligent, retrait de quatre caractères, tabulations enregistrées en tant qu'espaces). Pour plus d’informations, consultez [Options, Éditeur de texte, C#, Mise en forme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
- Écrivez une seule instruction par ligne.  
  
- Écrivez une seule déclaration par ligne.  
  
- Si les lignes de continuation ne sont pas mises en retrait automatiquement, indentez-les à l'aide d'un taquet de tabulation (quatre espaces).  
  
- Ajoutez au moins une ligne blanche entre les définitions des méthodes et les définitions des propriétés.  
  
- Utilisez des parenthèses pour rendre apparentes les clauses d'une expression, comme illustré dans le code suivant.  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a>Conventions de commentaires  
  
- Placez le commentaire sur une ligne séparée, pas à la fin d'une ligne de code.  
  
- Commencez le commentaire par une lettre majuscule.  
  
- Terminez le texte de commentaire par un point.  
  
- Insérez un espace entre le délimiteur de commentaire (//) et le texte du commentaire, comme illustré dans l'exemple suivant.  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- Ne créez pas de blocs d'astérisques mis en forme autour des commentaires.  
  
## <a name="language-guidelines"></a>Directives du langage  

Les sections suivantes décrivent les pratiques que l'équipe C# suit pour préparer les exemples de code et autres.  
  
### <a name="string-data-type"></a>String, type de données  
  
- Utilisez une [interpolation de chaîne](../../language-reference/tokens/interpolated.md) pour concaténer les chaînes courtes, comme illustré dans le code suivant.  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- Pour ajouter des chaînes dans des boucles, en particulier lorsque vous travaillez avec une quantité de texte importante, utilisez un objet <xref:System.Text.StringBuilder>.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a>Variables locales implicitement typées  
  
- Utilisez le [typage implicite](../classes-and-structs/implicitly-typed-local-variables.md) pour les variables locales quand le type de la variable est évident à droite de l’assignation ou quand le type précis n’importe pas.  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- N’utilisez pas [var](../../language-reference/keywords/var.md) quand le type n’est pas apparent à droite de l’assignation.  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- Ne vous basez pas sur le nom de la variable pour spécifier son type. Il peut ne pas être correct.  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- Évitez d’utiliser `var` à la place de [dynamic](../../language-reference/builtin-types/reference-types.md).  
  
- Utilisez la saisie implicite pour déterminer le type de variable de boucle [pour](../../language-reference/keywords/for.md) les boucles.  
  
     L'exemple suivant utilise un typage implicite dans une instruction `for`.  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- N’utilisez pas de dactylographie implicite pour déterminer le type de variable de boucle dans les boucles [de avant-premier.](../../language-reference/keywords/foreach-in.md)

     L’exemple suivant utilise la `foreach` saisie explicite dans une déclaration.

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > Veillez à ne pas changer accidentellement un type d’élément de la collection itérable. Par exemple, il est <xref:System.Linq.IQueryable?displayProperty=nameWithType> facile <xref:System.Collections.IEnumerable?displayProperty=nameWithType> de `foreach` passer à dans une déclaration, ce qui modifie l’exécution d’une requête.

### <a name="unsigned-data-type"></a>Type de données non signé  
  
En règle générale, utilisez `int` plutôt que les types non signés. L'utilisation de `int` est commun en C# et il est plus facile d'interagir avec d'autres bibliothèques lorsque vous utilisez `int`.  
  
### <a name="arrays"></a>Tableaux  
  
Utilisez la syntaxe concise lorsque vous initialisez des tableaux sur la ligne de déclaration.  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a>Délégués  
  
Utilisez la syntaxe concise pour créer des instances d'un type délégué.  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>Instructions try-catch et using dans la gestion des exceptions  
  
- Utilisez une instruction [try-catch](../../language-reference/keywords/try-catch.md) pour la plus grande part de la gestion des exceptions.  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- Simplifiez votre code à l’aide de l’instruction [using](../../language-reference/keywords/using-statement.md) C#. Si vous avez une instruction [try-finally](../../language-reference/keywords/try-finally.md) dans laquelle le seul code du bloc `finally` est un appel à la méthode <xref:System.IDisposable.Dispose%2A>, utilisez à la place une instruction `using`.  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a>Opérateurs && et &#124;&#124;  
  
Pour éviter les exceptions et augmenter les [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) performances [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) en sautant des comparaisons inutiles, utilisez au lieu et [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) au lieu de [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) lorsque vous effectuez des comparaisons, comme le montre l’exemple suivant.  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a>New Operator  
  
- Utilisez la forme concise d'instanciation d'objets, avec un typage implicite, comme indiqué dans la déclaration suivante.  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     La ligne précédente est équivalente à la déclaration suivante.  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- Utilisez les initialiseurs d'objets pour simplifier la création d'objet.  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a>Gestion des événements  
  
Si vous définissez un gestionnaire d’événements que vous n’avez pas besoin de supprimer ultérieurement, utilisez une expression lambda.  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a>Membres static  
  
Appelez les membres [static](../../language-reference/keywords/static.md) en utilisant le nom de la classe : *Nom_classe.Membre_statique*. Cette pratique rend le code plus lisible en clarifiant l'accès aux membres static.  Ne qualifiez pas un membre static défini dans une classe de base avec le nom d'une classe dérivée.  Lorsque ce code est compilé, la lisibilité du code est trompeuse et le code peut s'interrompre à l'avenir si vous ajoutez à la classe dérivée un membre static de même nom.  
  
### <a name="linq-queries"></a>Requêtes LINQ  
  
- Utilisez des noms explicites pour les variables de requête. L'exemple suivant utilise `seattleCustomers` pour les clients qui se trouvent à Seattle.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Utilisez des alias pour vous assurer que les noms de propriétés des types anonymes sont correctement écrits en majuscules à l'aide de la casse Pascal.  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus. Par exemple, si votre requête retourne un nom de client et un ID de distributeur, au lieu de les laisser sous la forme `Name` et `ID` dans le résultat, renommez-les pour montrer clairement que `Name` est le nom d'un client et `ID` l'ID d'un distributeur.  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- Utilisez le typage implicite dans la déclaration des variables de requête et des variables de portée.  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- Alignez les clauses de requête sous la clause [from](../../language-reference/keywords/from-clause.md), comme illustré dans les exemples précédents.  
  
- Utilisez les clauses [where](../../language-reference/keywords/where-clause.md) avant les autres clauses de requête pour garantir que les clauses de requête ultérieures opèrent sur l’ensemble de données réduit et filtré.  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- Utilisez plusieurs clauses `from` au lieu d’une clause [join](../../language-reference/keywords/join-clause.md) pour accéder aux collections internes. Par exemple, une collection d'objets `Student` peut contenir chacune une collection de scores de test. Lorsque la requête suivante est exécutée, elle retourne chaque score supérieur à 90, avec le nom de l'étudiant correspondant.  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a>Sécurité  

Suivez les instructions indiquées dans [Instructions de codage sécurisé](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Voir aussi

- [Conventions de codage Visual Basic](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [Instructions de codage sécurisé](../../../standard/security/secure-coding-guidelines.md)
