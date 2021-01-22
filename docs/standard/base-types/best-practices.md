---
title: Bonnes pratiques pour les expressions régulières dans .NET
description: Découvrez comment créer des expressions régulières effectives et efficaces dans .NET.
ms.date: 06/30/2020
ms.topic: conceptual
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
ms.openlocfilehash: 6a4c1ac5879447d829bcd162f764c33adcbea184
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693148"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>Meilleures pratiques pour les expressions régulières dans .NET

Le moteur d’expression régulière dans .NET est un outil puissant et complet. Il traite le texte en fonction de correspondances de modèle plutôt qu’en comparant et en faisant correspondre le texte littéral. Dans la plupart des cas, il exécute les critères spéciaux de façon rapide et efficace. Toutefois, dans certains cas, le moteur des expressions régulières peut sembler très lent. Dans des cas extrêmes, il semble même cesser de répondre. Il traite en effet peu d'entrées sur une période de plusieurs heures ou même de plusieurs jours.

Cette rubrique décrit quelques-unes des meilleures pratiques que les développeurs peuvent adopter afin de garantir que les expressions régulières atteignent des performances optimales.

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="consider-the-input-source"></a>Prise en compte de la source d’entrée

En général, les expressions régulières peuvent accepter deux types d'entrée : avec contrainte ou sans contrainte. L'entrée avec contrainte est un texte provenant d'une source fiable ou connue, et qui suit un format prédéfini. L'entrée sans contrainte est un texte provenant d'une source non fiable, telle qu'un utilisateur web. Elle ne suit pas forcément un format prédéfini ou attendu.

Les modèles d'expressions régulières sont généralement écrits pour correspondre à une entrée valide. Autrement dit, les développeurs examinent le texte qu'ils souhaitent faire correspondre, puis ils écrivent un modèle d'expression régulière qui lui correspond. Les développeurs déterminent ensuite si ce modèle doit être corrigé ou approfondi en le testant à l'aide de plusieurs éléments d'entrée valides. Lorsque le modèle correspond à toutes les entrées valides supposées, il est déclaré prêt pour la production et peut être intégré à une application finale. Le modèle d'expression régulière est ainsi adapté à la mise en correspondance d'une entrée avec contrainte. Toutefois, il n'est pas adapté à la mise en correspondance d'une entrée sans contrainte.

Pour faire correspondre une entrée sans contrainte, une expression régulière doit pouvoir gérer efficacement trois types de texte :

- Texte correspondant au modèle d’expression régulière.

- Texte ne correspondant pas au modèle d’expression régulière.

- Texte correspondant presque au modèle d’expression régulière.

Le dernier type de texte est problématique pour une expression régulière écrite pour gérer les entrées avec contrainte. Si cette expression régulière repose également sur une [rétroaction](backtracking-in-regular-expressions.md) complète, le traitement d’un texte apparemment anodin par le moteur d’expression régulière risque d’être extrêmement long (dans certains cas, un grand nombre d’heures ou de jours).

> [!WARNING]
> L'exemple suivant utilise une expression régulière sujette à des rétroactions excessives et susceptible de rejeter des adresses e-mail valides. Vous ne devez pas l’utiliser dans une routine de validation d’e-mails. Si vous souhaitez une expression régulière qui valide des adresses e-mail, consultez [Guide pratique : vérifier que des chaînes sont dans un format d’adresse e-mail valide](how-to-verify-that-strings-are-in-valid-email-format.md).

Prenons l'exemple d'une expression régulière très fréquemment utilisée, mais extrêmement problématique, pour la validation de l'alias d'une adresse e-mail. L'expression régulière `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` est écrite pour traiter ce qui est considéré comme une adresse e-mail valide. Cette dernière se compose d'un caractère alphanumérique suivi de zéro, ou de plusieurs caractères (caractères alphanumériques, points ou traits d'union). L'expression régulière doit se terminer par un caractère alphanumérique. Toutefois, comme illustré dans l'exemple suivant, bien que cette expression régulière gère facilement une entrée valide, elle s'avère particulièrement inefficace lorsqu'il s'agit de traiter une entrée presque valide.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]

Comme le montre la sortie de l'exemple, le moteur des expressions régulières traite l'alias de messagerie valide dans un intervalle de temps à peu près identique, indépendamment de sa longueur. En revanche, lorsque l'adresse e-mail presque valide comporte plus de cinq caractères, le temps de traitement est environ doublé pour chaque caractère supplémentaire de la chaîne. Cela signifie qu'une chaîne de 28 caractères presque valide serait traitée en plus d'une heure et qu'une chaîne de 33 caractères presque valide serait traitée en un peu moins d'un jour.

Étant donné que cette expression régulière a été développée en prenant uniquement en considération le format de l'entrée à faire correspondre, elle ne tient pas compte des entrées qui ne correspondent pas au modèle. Une entrée sans contrainte correspondant presque au modèle d'expression régulière risque ainsi de nuire considérablement aux performances.

Pour résoudre ce problème, vous pouvez effectuer les opérations suivantes :

- Lorsque vous développez un modèle, vous devez réfléchir à la manière dont la rétroaction peut affecter les performances du moteur des expressions régulières, en particulier si votre expression régulière est conçue pour traiter des entrées sans contrainte. Pour plus d’informations, consultez la section [prise en décharge de la rétroaction](#take-charge-of-backtracking) .

- Testez intégralement votre expression régulière à l'aide d'entrées non valides et presque valides, ainsi que d'entrées valides. Pour générer de manière aléatoire une entrée pour une expression régulière spécifique, vous pouvez utiliser [Rex](https://www.microsoft.com/research/project/rex-regular-expression-exploration/), l’outil d’exploration d’expressions régulières de Microsoft Research.

## <a name="handle-object-instantiation-appropriately"></a>Gestion correcte de l’instanciation d’objet

Au cœur de. Le modèle objet d’expression régulière du NET est la <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> classe, qui représente le moteur d’expression régulière. Souvent, la façon dont le moteur <xref:System.Text.RegularExpressions.Regex> est utilisé est le facteur principal ayant un impact sur les performances des expressions régulières. La définition d’une expression régulière implique une association étroite entre le moteur des expressions régulières et un modèle d’expression régulière. Ce processus est forcément onéreux, qu’il implique l’instanciation d’un objet <xref:System.Text.RegularExpressions.Regex> en passant à son constructeur un modèle d’expression régulière ou l’appel d’une méthode statique en lui passant le modèle d’expression régulière avec la chaîne à analyser.

> [!NOTE]
> Vous trouverez une présentation plus détaillée des répercussions sur les performances des expressions régulières interprétées et compilées sur la page [Optimiser les performances des expressions régulières, deuxième partie : prendre en charge le retour arrière](/archive/blogs/bclteam/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha) du blog de l'équipe BCL.

Vous pouvez associer le moteur des expressions régulières à un modèle d’expression régulière spécifique, puis utiliser le moteur pour faire correspondre du texte de plusieurs façons :

- Vous pouvez appeler une méthode statique de critères spéciaux, comme <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>. L'instanciation d'un objet d'expression régulière n'est pas nécessaire.

- Vous pouvez instancier un objet <xref:System.Text.RegularExpressions.Regex> et appeler une méthode d'instance de critères spéciaux d'une expression régulière interprétée. Il s’agit de la méthode par défaut pour lier le moteur des expressions régulières à un modèle d’expression régulière. Elle se produit lorsqu'un objet <xref:System.Text.RegularExpressions.Regex> est instancié sans argument `options` incluant l'indicateur <xref:System.Text.RegularExpressions.RegexOptions.Compiled>.

- Vous pouvez instancier un objet <xref:System.Text.RegularExpressions.Regex> et appeler une méthode d'instance de critères spéciaux d'une expression régulière compilée. Les objets d’expression régulière représentent des modèles compilés lorsqu’un objet <xref:System.Text.RegularExpressions.Regex> est instancié avec un argument `options` incluant l’indicateur <xref:System.Text.RegularExpressions.RegexOptions.Compiled>.

- Vous pouvez créer un objet <xref:System.Text.RegularExpressions.Regex> qui a un usage spécial et qui est fortement couplé à un modèle d’expression régulière particulier, le compiler et l’enregistrer dans un assembly autonome. Pour ce faire, appelez la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>.

La façon dont vous appelez les méthodes de correspondance d'expression régulière peut avoir un impact significatif sur votre application. Les sections suivantes expliquent quand utiliser les appels de méthode statique, les expressions régulières interprétées et les expressions régulières compilées afin d'améliorer les performances de votre application.

> [!IMPORTANT]
> La forme de l'appel de méthode (statique, interprétée, compilée) affecte les performances si une même expression régulière est utilisée à plusieurs reprises dans les appels de méthode, ou si une application entraîne l'utilisation intensive d'objets d'expression régulière.

### <a name="static-regular-expressions"></a>Expressions régulières statiques

Les méthodes d'expression régulière statiques sont recommandées pour éviter d'instancier à plusieurs reprises un objet d'expression régulière avec la même expression régulière. Contrairement aux modèles d’expressions régulières utilisés par les objets d’expression régulière, les codes d’opération ou le langage MSIL (Microsoft Intermediate Language) compilé à partir des modèles utilisés dans les appels de méthode statique sont mis en cache en interne par le moteur des expressions régulières.

Par exemple, un gestionnaire d'événements appelle fréquemment une autre méthode pour valider l'entrée d'utilisateur. Ceci se reflète dans le code suivant, dans lequel l'événement <xref:System.Windows.Forms.Button> d'un contrôle <xref:System.Windows.Forms.Control.Click> est utilisé pour appeler une méthode nommée `IsValidCurrency`, qui vérifie si l'utilisateur a entré un symbole monétaire suivi d'au moins un chiffre décimal.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]

L'exemple suivant illustre une implémentation très peu efficace de la méthode `IsValidCurrency`. Notez que chaque appel de méthode réinstancie un objet <xref:System.Text.RegularExpressions.Regex> avec le même modèle. Cela signifie ainsi que le modèle d’expression régulière doit être recompilé chaque fois que la méthode est appelée.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]

Vous devez remplacer ce code peu efficace par un appel à la méthode statique <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType>. De cette manière, un objet <xref:System.Text.RegularExpressions.Regex> n'a pas besoin d'être instancié chaque fois que vous souhaitez appeler une méthode de critères spéciaux. En outre, le moteur des expressions régulières est alors en mesure de récupérer une version compilée de l'expression régulière depuis son cache.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]

Par défaut, les 15 derniers modèles d’expressions régulières statiques utilisés récemment sont mis en cache. Pour les applications qui requièrent un plus grand nombre d'expressions régulières statiques mises en cache, la taille du cache peut être ajustée en définissant la propriété <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType>.

L'expression régulière `\p{Sc}+\s*\d+` utilisée dans cet exemple vérifie que la chaîne d'entrée se compose d'un symbole monétaire et d'au moins un chiffre décimal. Le modèle est défini comme indiqué dans le tableau suivant.

|Modèle|Description|
|-------------|-----------------|
|`\p{Sc}+`|Mettre en correspondance un ou plusieurs caractères dans la catégorie Unicode symbole, devise.|
|`\s*`|Correspond à zéro, un ou plusieurs espaces blancs.|
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|

### <a name="interpreted-vs-compiled-regular-expressions"></a>Expressions régulières interprétées ou compilées

Les modèles d’expressions régulières qui ne sont pas associés au moteur des expressions régulières par la spécification de l’option <xref:System.Text.RegularExpressions.RegexOptions.Compiled> sont interprétés. Lorsqu'un objet d'expression régulière est instancié, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération. Lorsqu'une méthode d'instance est appelée, les codes d'opération sont convertis en langage MSIL et exécutés par le compilateur JIT. De même, lorsqu'une méthode d'expression régulière statique est appelée et que l'expression régulière ne peut pas être récupérée dans le cache, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération et les stocke dans le cache. Il convertit ensuite ces codes d'opération en langage MSIL afin que le compilateur JIT puisse les exécuter. Les expressions régulières interprétées réduisent le temps de démarrage, mais ralentissent le temps d'exécution. Pour cette raison, il est préférable de les utiliser lorsque l'expression régulière est utilisée dans un nombre d'appels de méthode restreint, ou lorsque le nombre exact d'appels de méthodes d'expression régulière est inconnu, mais qu'il est supposé être petit. À mesure que le nombre d'appels de méthode augmente, le ralentissement de la vitesse d'exécution l'emporte sur l'amélioration des performances liée à la réduction du temps de démarrage.

Les modèles d’expressions régulières qui sont associés au moteur des expressions régulières par la spécification de l’option <xref:System.Text.RegularExpressions.RegexOptions.Compiled> sont compilés. Cela signifie que, lorsqu'un objet d'expression régulière est instancié ou lorsqu'une méthode d'expression régulière statique est appelée et que l'expression régulière ne peut pas être récupérée dans le cache, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération intermédiaire, qu'il convertit ensuite en langage MSIL. Lorsqu'une méthode est appelée, le compilateur JIT exécute le MSIL. Contrairement aux expressions régulières interprétées, les expressions régulières compilées augmentent le temps de démarrage, mais elles exécutent plus rapidement les méthodes de critères spéciaux individuelles. En conséquence, l'amélioration des performances due à la compilation de l'expression régulière augmente en fonction du nombre de méthodes d'expression régulières appelées.

Pour résumer, nous vous conseillons d'utiliser des expressions régulières interprétées lorsque vous appelez relativement peu souvent des méthodes d'expression régulières avec une expression régulière spécifique. Nous vous conseillons d'utiliser des expressions régulières compilées lorsque vous appelez relativement souvent des méthodes d'expression régulière avec une expression régulière spécifique. Il est difficile de déterminer le seuil exact auquel le ralentissement de la vitesse d'exécution des expressions normales interprétées l'emporte sur la réduction du temps de démarrage. Il est également difficile de déterminer le seuil auquel le ralentissement du temps de démarrage des expressions régulières compilées l'emporte sur l'amélioration des vitesses d'exécution. Différents facteurs doivent être pris en compte, notamment la complexité des expressions régulières et les données spécifiques qui sont traitées. Pour déterminer si ce sont les expressions régulières interprétées ou compilées qui offrent les meilleures performances pour votre scénario d'application spécifique, vous pouvez utiliser la classe <xref:System.Diagnostics.Stopwatch> pour comparer les durées d'exécution.

L’exemple suivant compare les performances des expressions régulières compilées et interprétées sur la lecture des dix premières phrases et de toutes les phrases du texte de Theodore Dreiser, *The Financier*. Comme l'indique la sortie de l'exemple, lorsque les méthodes de correspondance d'expression régulière sont appelées seulement dix fois, une expression régulière interprétée offre de meilleures performances qu'une expression régulière compilée. Par contre, une expression régulière compilée offre de meilleures performances dans le cas d'un grand nombre d'appels (dans le cas présent, plus de 13 000).

[!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]

Le modèle d'expression régulière utilisé dans l'exemple, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, est défini comme indiqué dans le tableau suivant.

|Modèle|Description|
|-------------|-----------------|
|`\b`|Commencer la correspondance à la limite d'un mot.|
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|
|<code>(\r?\n)&#124;,?\s)</code>|Mettre en correspondance un ou aucun retour chariot suivi d'un caractère de saut de ligne, ou une ou aucune virgule, suivie d'un espace blanc.|
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Mettre en correspondance zéro, une ou plusieurs occurrences d'un ou plusieurs caractères alphabétiques qui sont suivis par un ou aucun retour chariot et un caractère de saut de ligne, ou par une ou aucune virgule, suivie d'un espace blanc.|
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|
|`[.?:;!]`|Mettre en correspondance un point, un point d'interrogation, deux-points, un point-virgule ou un point d'exclamation.|

### <a name="regular-expressions-compiled-to-an-assembly"></a>Expressions régulières : compilées dans un assembly

.NET permet également de créer un assembly contenant des expressions régulières compilées. La baisse de performances des expressions régulières est alors ressentie au moment du design et non au moment de l'exécution. Toutefois, cela engendre également un travail supplémentaire : vous devez définir les expressions régulières à l'avance et les compiler dans un assembly. Le compilateur peut ensuite référencer cet assembly lors de la compilation du code source qui utilise les expressions régulières de l’assembly. Chaque expression régulière compilée dans l'assembly est représentée par une classe qui dérive de <xref:System.Text.RegularExpressions.Regex>.

Pour compiler des expressions régulières dans un assembly, vous appelez la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> et vous lui passez un tableau d'objets <xref:System.Text.RegularExpressions.RegexCompilationInfo> représentant les expressions régulières à compiler, ainsi qu'un objet <xref:System.Reflection.AssemblyName> contenant des informations sur l'assembly à créer.

Nous vous conseillons de compiler les expressions régulières dans un assembly dans les situations suivantes :

- Vous êtes un développeur de composants et vous souhaitez créer une bibliothèque d'expressions régulières réutilisables.

- Vous savez que les méthodes de critères spéciaux de vos expression régulières seront appelées un nombre de fois indéterminé (entre une fois et des dizaines de milliers de fois). Contrairement aux expressions régulières compilées ou interprétées, les expressions régulières qui sont compilées dans des assemblys distincts offrent des performances homogènes, indépendamment du nombre d'appels de méthode.

Si vous utilisez des expressions régulières compilées pour optimiser les performances, vous ne devez pas utiliser la réflexion pour créer l’assembly, charger le moteur des expressions régulières et exécuter ses méthodes de critères spéciaux. Vous devez donc éviter de générer dynamiquement des modèles d’expressions régulières et spécifier les options de critères spéciaux (tels que des critères spéciaux de non respect de la casse) au moment de la création de l’assembly. Vous devez également séparer le code qui crée l'assembly du code qui utilise l'expression régulière.

L'exemple suivant montre comment créer un assembly qui contient une expression régulière compilée. Il crée un assembly nommé `RegexLib.dll` avec une classe d’expression régulière unique, `SentencePattern` , qui contient le modèle d’expression régulière de phrase qui est utilisé dans la section [expressions régulières interprétées et expressions régulières compilées](#interpreted-vs-compiled-regular-expressions) .

[!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]

Lorsque l'exemple est compilé dans un exécutable et qu'il est exécuté, il crée un assembly nommé `RegexLib.dll`. L'expression régulière est représentée par une classe nommée `Utilities.RegularExpressions.SentencePattern`, dérivée de <xref:System.Text.RegularExpressions.Regex>. L'exemple suivant utilise ensuite l'expression régulière compilée pour extraire les phrases du texte de Theodore Dreiser, *The Financier*.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]

## <a name="take-charge-of-backtracking"></a>Prise en charge de la rétroaction

Normalement, le moteur des expressions régulières utilise une progression linéaire pour se déplacer dans une chaîne d’entrée et pour la comparer à un modèle d’expression régulière. Toutefois, lorsque les quantificateurs indéterminés, `*`, `+` et `?`, par exemple, sont utilisés dans un modèle d’expression régulière, le moteur des expressions régulières peut abandonner une partie des correspondances partielles trouvées et revenir à un état précédemment enregistré pour trouver une correspondance pour le modèle entier. Ce processus est appelé « rétroaction ».

> [!NOTE]
> Pour plus d'informations sur le retour arrière, consultez les pages [Informations sur le comportement des expressions régulières](details-of-regular-expression-behavior.md) et [Retour arrière](backtracking-in-regular-expressions.md). Vous trouverez une présentation détaillée du retour arrière sur la page [Optimiser les performances des expressions régulières, deuxième partie : prendre en charge le retour arrière](/archive/blogs/bclteam/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha) du blog de l'équipe BCL.

La prise en charge de la rétroaction confère aux expressions régulières leur puissance et leur flexibilité. La responsabilité de contrôle du fonctionnement du moteur des expressions régulières est alors confiée aux développeurs d'expressions régulières. Souvent, les développeurs ne sont pas conscients de cette responsabilité. Leur utilisation incorrecte de la rétroaction ou leur dépendance vis-à-vis d'une rétroaction excessive a souvent un impact négatif très important sur les performances des expressions régulières. Dans le pire des scénarios, la durée d'exécution peut doubler pour chaque caractère supplémentaire de la chaîne d'entrée. En réalité, lorsque la rétroaction est utilisée de manière excessive, il est facile de créer l'équivalent de programmation d'une boucle sans fin si l'entrée correspond presque au modèle d'expression régulière. Le moteur des expressions régulières peut alors traiter une chaîne d'entrée relativement courte en plusieurs heures, voire en plusieurs jours.

Les performances des applications sont souvent altérées par l'utilisation de la rétroaction, même si ce processus n'est pas essentiel pour une correspondance. Par exemple, l'expression régulière `\b\p{Lu}\w*\b` établit une correspondance entre tous les mots qui commencent par une majuscule, comme indiqué dans le tableau suivant.

|Modèle|Description|
|-|-|
|`\b`|Commencer la correspondance à la limite d'un mot.|
|`\p{Lu}`|Mettre en correspondance une majuscule.|
|`\w*`|Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.|
|`\b`|Terminer la correspondance à la limite d'un mot.|

Étant donné qu'une limite de mot est différente d'un caractère alphabétique et qu'elle n'est pas un sous-ensemble de ce dernier, il est impossible que le moteur des expressions régulières franchisse une limite de mot lors de la mise en correspondance de caractères alphabétiques. Cela signifie que, pour cette expression régulière, une rétroaction ne peut jamais contribuer à la réussite globale d'une correspondance. Elle risque en revanche de diminuer les performances, étant donné que le moteur des expressions régulières doit impérativement enregistrer sont état pour chaque correspondance préliminaire d'un caractère alphabétique trouvée.

Si vous déterminez que la rétroaction n’est pas nécessaire, vous pouvez la désactiver à l’aide de l' `(?>subexpression)` élément de langage, appelé groupe atomique. L'exemple suivant analyse une chaîne d'entrée à l'aide de deux expressions régulières. La première, `\b\p{Lu}\w*\b`, utilise la rétroaction. La seconde, `\b\p{Lu}(?>\w*)\b`, désactive la rétroaction. Comme l'indique la sortie de l'exemple, les résultats obtenus sont identiques.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]

Dans de nombreux cas, la rétroaction est essentielle pour faire correspondre un modèle d’expression régulière à un texte d’entrée. Toutefois, une rétroaction excessive risque d'altérer considérablement les performances et de donner l'impression qu'une application a cessé de répondre. Cela se produit notamment lorsque les quantificateurs sont imbriqués et que le texte correspondant à la sous-expression externe est un sous-ensemble du texte correspondant à la sous-expression interne.

> [!WARNING]
> En plus d’éviter une rétroaction excessive, vous devez utiliser la fonctionnalité de délai d’attente pour garantir qu’une rétroaction excessive n’altère pas considérablement les performances des expressions régulières. Pour plus d’informations, consultez la section [utiliser des valeurs de délai d’attente](#use-time-out-values) .

Par exemple, le modèle d'expression régulière `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` est conçu pour mettre en correspondance un numéro de référence composé d'au moins un caractère alphanumérique. Tous les caractères supplémentaires peuvent être composés d'un caractère alphanumérique, d'un trait d'union, d'un trait de soulignement ou d'un point. Toutefois, le dernier caractère doit impérativement être alphanumérique. Un signe dollar termine le numéro de référence. Dans certains cas, ce modèle d'expression régulière peut présenter des performances médiocres, si les quantificateurs sont imbriqués et que la sous-expression `[0-9A-Z]` est un sous-ensemble de la sous-expression `[-.\w]*`.

Dans ces cas, vous pouvez optimiser les performances des expressions régulières en supprimant les quantificateurs imbriqués et en remplaçant la sous-expression externe par une assertion de préanalyse ou de postanalyse de largeur nulle. Les assertions de préanalyse et de postanalyse sont des points d'ancrage. Elles ne déplacent pas le pointeur dans la chaîne d'entrée, mais elles vérifient en amont et en aval si une condition spécifiée est remplie. Par exemple, l'expression régulière de numéro de référence peut être réécrite sous la forme `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Ce modèle d'expression régulière est défini comme indiqué dans le tableau suivant.

|Modèle|Description|
|-------------|-----------------|
|`^`|Commencer la correspondance au début de la chaîne d'entrée.|
|`[0-9A-Z]`|Mettre en correspondance un caractère alphanumérique. Le numéro de référence doit au minimum comporter ce caractère.|
|`[-.\w]*`|Mettre en correspondance zéro, une ou plusieurs occurrences de tout caractère alphabétique, trait d'union ou point.|
|`\$`|Mettre en correspondance un signe dollar.|
|`(?<=[0-9A-Z])`|Effectuer une préanalyse avancée du signe dollar de fin de s'assurer que le caractère précédent est un caractère alphanumérique.|
|`$`|Terminer la correspondance à la fin de la chaîne d'entrée.|

L'exemple suivant illustre l'utilisation de cette expression régulière pour faire correspondre un tableau pouvant contenir des numéros de référence potentiels.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack4.cs#11)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack4.vb#11)]

Le langage d’expression régulière dans .NET comprend les éléments de langage suivants, que vous pouvez utiliser pour éliminer les quantificateurs imbriqués. Pour plus d’informations, consultez [Constructions de regroupement](grouping-constructs-in-regular-expressions.md).

|Élément du langage|Description|
|----------------------|-----------------|
|`(?=` `subexpression` `)`|Préanalyse positive de largeur nulle. Effectuer une préanalyse de la position actuelle pour déterminer si `subexpression` correspond à la chaîne d'entrée.|
|`(?!` `subexpression` `)`|Préanalyse négative de largeur nulle. Effectuer une préanalyse de la position actuelle pour déterminer si `subexpression` ne correspond pas à la chaîne d'entrée.|
|`(?<=` `subexpression` `)`|Postanalyse positive de largeur nulle. Effectuer une postanalyse de la position actuelle pour déterminer si `subexpression` correspond à la chaîne d'entrée.|
|`(?<!` `subexpression` `)`|Postanalyse négative de largeur nulle. Effectuer une postanalyse de la position actuelle pour déterminer si `subexpression` ne correspond pas à la chaîne d'entrée.|

## <a name="use-time-out-values"></a>Utilisation de valeurs de délai d’attente

Si une expression régulière traite une entrée qui correspond presque au modèle d'expression régulière, elle peut souvent se baser sur une rétroaction excessive, laquelle affecte considérablement ses performances. En plus d'envisager soigneusement l'utilisation de la rétroaction et de tester l'expression régulière sur une entrée presque correspondante, vous devez toujours définir une valeur de délai d'attente pour garantir la minimalisation de l'impact d'une rétroaction excessive, le cas échéant.

L’intervalle de délai d’attente des expressions régulières définit la période pendant laquelle le moteur d’expression régulière recherche une correspondance unique avant d’expirer. L’intervalle de délai d’attente par défaut est, ce qui <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType> signifie que l’expression régulière n’expirera pas. Vous pouvez remplacer cette valeur et définir un intervalle de délai d’attente comme suit :

- En fournissant une valeur de délai d'attente quand vous instanciez un objet <xref:System.Text.RegularExpressions.Regex> en appelant le constructeur <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29>.

- En appelant une méthode de mise en correspondance de modèles statique, telle que <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, qui inclut un paramètre `matchTimeout`.

- Pour les expressions régulières compilées qui sont créées en appelant la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>, en appelant le constructeur ayant un paramètre de type <xref:System.TimeSpan>.

Si vous avez défini un délai d'attente et qu'aucune correspondance n'est trouvée à la fin de cet intervalle, la méthode d'expression régulière lève une exception <xref:System.Text.RegularExpressions.RegexMatchTimeoutException>. Dans votre gestionnaire d'exceptions, vous pouvez choisir de réessayer la mise en correspondance avec un délai d'attente plus long, d'annuler la recherche de correspondance et de supposer l'absence de correspondance, ou encore d'annuler la recherche de correspondance et de consigner les informations sur les exceptions à des fins d'analyse ultérieure.

L'exemple ci-dessous définit une méthode `GetWordData` qui instancie une expression régulière avec un délai d'attente de 350 millisecondes pour calculer le nombre de mots dans un document texte et le nombre moyen de caractères par mot. Si le délai d'attente de l'opération de recherche de correspondance expire, le délai d'attente augmente de 350 millisecondes et l'objet <xref:System.Text.RegularExpressions.Regex> est réinstancié. Si le nouveau délai d'attente dépasse 1 seconde, la méthode lève de nouveau l'exception pour l'appelant.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]

## <a name="capture-only-when-necessary"></a>Capture uniquement quand cela s’avère nécessaire

Les expressions régulières dans .NET prennent en charge plusieurs constructions de regroupement, ce qui vous permet de regrouper un modèle d’expression régulière dans une ou plusieurs sous-expressions. Les constructions de regroupement les plus couramment utilisées dans le langage d’expression régulière .net sont sous- `(` *expression* `)` , qui définit un groupe de capture numéroté et nom sous- `(?<`  `>` *expression* `)` , qui définit un groupe de capture nommé. Les constructions de regroupement sont essentielles pour créer des références arrières et pour définir une sous-expression à laquelle un quantificateur est appliqué.

Toutefois, l'utilisation de ces éléments de langage n'est pas sans effet. Ils entraînent le remplissage de l'objet <xref:System.Text.RegularExpressions.GroupCollection> renvoyé par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> avec les captures nommées ou sans nom les plus récentes. Si une seule construction de regroupement a capturé plusieurs sous-chaînes dans la chaîne d'entrée, elles remplissent également l'objet <xref:System.Text.RegularExpressions.CaptureCollection> renvoyé par la propriété <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> d'un groupe de capture particulier à l'aide de plusieurs objets <xref:System.Text.RegularExpressions.Capture>.

Souvent, les constructions de regroupement sont utilisées dans une expression régulière uniquement pour que les quantificateurs puissent leur être appliqués. Les groupes capturés par ces sous-expressions ne sont alors pas utilisés par la suite. Par exemple, l'expression régulière `\b(\w+[;,]?\s?)+[.?!]` est conçue pour capturer une phrase entière. Le tableau suivant décrit les éléments de langage dans ce modèle d'expression régulière et leur effet sur les <xref:System.Text.RegularExpressions.Match> des objets <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> et les collections <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.

|Modèle|Description|
|-------------|-----------------|
|`\b`|Commencer la correspondance à la limite d'un mot.|
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|
|`[;,]?`|Mettre en correspondance zéro ou une virgule, ou zéro ou un point-virgule.|
|`\s?`|Mettre en correspondance zéro ou un espace blanc.|
|`(\w+[;,]?\s?)+`|Mettre en correspondance une ou plusieurs occurrences d'un ou plusieurs caractères alphabétiques suivis d'une virgule ou d'un point-virgule facultatif suivi d'un espace blanc facultatif. Cela définit le premier groupe de capture. Il est nécessaire pour que la combinaison de plusieurs caractères alphabétiques (autrement dit, un mot) suivis d'un signe de ponctuation facultatif soit répétée jusqu'à ce que le moteur des expressions régulières ait atteint la fin d'une phrase.|
|`[.?!]`|Mettre en correspondance un point, un point d'interrogation ou un point d'exclamation.|

Comme l'indique l'exemple suivant, lorsqu'une correspondance est trouvée, l'objet <xref:System.Text.RegularExpressions.GroupCollection> et l'objet <xref:System.Text.RegularExpressions.CaptureCollection> sont remplis avec des captures de la correspondance. Dans ce cas, le groupe de capture `(\w+[;,]?\s?)` existe afin que le quantificateur `+` puisse lui être appliqué, ce qui permet au modèle d'expression régulière de correspondre à chaque mot d'une phrase. Sinon, elle correspondrait au dernier mot d'une phrase.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]

Lorsque vous utilisez des sous-expressions uniquement pour y appliquer des quantificateurs et que le texte capturé ne vous intéresse pas, vous devez désactiver les captures de groupe. Par exemple, l'élément de langage `(?:subexpression)` empêche le groupe auquel il s'applique de capturer les sous-chaînes correspondantes. Dans l'exemple suivant, le modèle d'expression régulière de l'exemple précédent est remplacé par `\b(?:\w+[;,]?\s?)+[.?!]`. Comme l'indique la sortie, le moteur des expressions régulières ne peut pas remplir les collections <xref:System.Text.RegularExpressions.GroupCollection> et <xref:System.Text.RegularExpressions.CaptureCollection>.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]

Vous pouvez désactiver les captures de l'une des façons suivantes :

- Utilisez l'élément de langage `(?:subexpression)`. Cet élément empêche la capture des sous-chaînes correspondantes dans le groupe auquel il s'applique. Il ne désactive pas les captures de la sous-chaîne dans les groupes imbriqués.

- Utilisez l'option <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>. Elle désactive toutes les captures implicites ou sans nom dans le modèle d’expression régulière. Avec cette option, seules les sous-chaînes qui correspondent à des groupes nommés définis avec l'élément de langage `(?<name>subexpression)` peuvent être capturées. L'indicateur <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> peut être passé au paramètre `options` d'un constructeur de classe <xref:System.Text.RegularExpressions.Regex> ou au paramètre `options` d'une méthode correspondante statique <xref:System.Text.RegularExpressions.Regex>.

- Utilisez l'option `n` dans l'élément de langage `(?imnsx)`. Cette option désactive toutes les captures implicites ou sans nom à partir du point où l’élément apparaît dans le modèle d’expression régulière. Les captures sont désactivées jusqu’à la fin du modèle ou jusqu’à ce que l’option `(-n)` active les captures implicites ou sans nom. Pour plus d'informations, consultez [Miscellaneous Constructs](miscellaneous-constructs-in-regular-expressions.md).

- Utilisez l'option `n` dans l'élément de langage `(?imnsx:subexpression)`. Cette option désactive toutes les captures implicites ou sans nom dans `subexpression`. Les captures effectuées par les groupes de capture imbriqués implicites ou sans nom sont également désactivées.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Comportement détaillé des expressions régulières](details-of-regular-expression-behavior.md)|Aborde l’implémentation du moteur d’expression régulière dans .NET. Cette rubrique traite de la flexibilité des expressions régulières. Elle explique la responsabilité du développeur pour que le fonctionnement efficace et fiable du moteur des expressions régulières soit garanti.|
|[Rétroaction](backtracking-in-regular-expressions.md)|Aborde la rétroaction et la façon dont elle affecte les performances des expressions régulières, ainsi que les éléments de langage, qui offrent des alternatives à la rétroaction.|
|[Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)|Décrit les éléments du langage d’expression régulière dans .NET et propose des liens vers la documentation détaillée pour chaque élément de langage.|
