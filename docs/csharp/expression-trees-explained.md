---
title: Explication des arborescences d’expressions
description: En savoir plus sur les arborescences d’expressions et leur utilité dans la conversion d’algorithmes pour une exécution externe et une inspection du code avant son exécution.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 12093e9c9246c87cc5ea3aedaca6ba34acacce4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73036991"
---
# <a name="expression-trees-explained"></a>Explication des arborescences d’expressions

[Précédent – Vue d’ensemble](expression-trees.md)

Les arborescences d’expressions sont des structures de données qui définissent du code. Elles sont basées sur les mêmes structures que celles utilisées par un compilateur pour analyser du code et générer la sortie compilée. Lors de la lecture de ce didacticiel, vous remarquerez qu’il existe certaines similitudes entre les arborescences d’expressions et les types utilisés dans les API Roslyn pour générer des [Analyzers et CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Les analyseurs et les codeFixes sont des paquets NuGet qui effectuent une analyse statique sur le code et peuvent suggérer des correctifs potentiels pour un développeur.) Les concepts sont similaires, et le résultat final est une structure de données qui permet l’examen du code source d’une manière significative. Toutefois, les arborescences d’expressions sont basées sur un ensemble de classes et d’API totalement différentdes API Roslyn.

Examinons un exemple simple.
Voici une ligne de code :

```csharp
var sum = 1 + 2;
```

Si vous analysez ceci comme une arborescence d’expressions, l’arborescence contient plusieurs nœuds.
Le nœud extérieur est une instruction de déclaration de variable avec attribution (`var sum = 1 + 2;`). Ce nœud extérieur contient plusieurs nœuds enfants : une déclaration de variable, un opérateur d’assignation et une expression qui représente la partie à droite du signe égal. Cette expression est sous-divisée en expressions qui représentent l’opération d’addition et les opérandes gauche et droit de l’addition.

Penchons-nous un peu plus sur les expressions qui composent la partie à droite du signe égal.
L’expression est `1 + 2`. Il s’agit d’une expression binaire. Plus spécifiquement, il s’agit d’une expression d’addition binaire. Une expression d’addition binaire a deux enfants, représentant les nœuds gauche et droit de l’expression d’addition. Ici, les deux nœuds sont des expressions constantes : l’opérande gauche est la valeur `1`, et l’opérande droit est la valeur `2`.

Visuellement, l’instruction entière est une arborescence. Vous pouvez partir du nœud racine et accéder à chaque nœud dans l’arborescence pour voir le code qui compose l’instruction :

- Instruction de déclaration de variable avec attribution (`var sum = 1 + 2;`)
  - Déclaration de type de variable implicite (`var sum`)
    - Mot clé var implicite (`var`)
    - Déclaration de nom de variable (`sum`)
  - Opérateur d’assignation (`=`)
  - Expression d’addition binaire (`1 + 2`)
    - Opérande gauche (`1`)
    - Opérateur d’addition (`+`)
    - Opérande droit (`2`)

Cela peut sembler compliqué, mais c’est très puissant. Suivant le même processus, vous pouvez décomposer des expressions beaucoup plus complexes. Examinons cette expression :

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

L’expression ci-dessus est aussi une déclaration de variable avec une assignation.
La partie droite de l’assignation est une arborescence beaucoup plus complexe.
Je ne vais pas décomposer cette expression, mais réfléchissez à ce que pourraient être les différents nœuds. Il y a des appels de méthode utilisant l’objet actif comme destinataire, un qui a un récepteur `this` explicite, un autre qui n’en a pas. Il y a des appels de méthode utilisant d’autres objets récepteurs, et des arguments constants de différents types. Pour finir, il y a un opérateur d’addition binaire. En fonction du type de retour de `SecretSauceFunction()` ou `MoreSecretSauce()`, cet opérateur d’addition binaire peut être un appel de méthode à un opérateur d’addition substitué, résolu en un appel de méthode statique à l’opérateur d’addition binaire défini pour une classe.

Malgré cette complexité apparente, l’expression ci-dessus crée une arborescence qui peut être parcourue aussi facilement que le premier exemple. Vous pouvez traverser les nœuds enfants successifs pour rechercher des nœuds terminaux dans l’expression. Les nœuds parents ont des références à leurs enfants, et chaque nœud a une propriété qui décrit le genre de nœud dont il s’agit.

La structure d’une arborescence d’expressions est très cohérente. Une fois que vous maîtrisez les principes de base, vous pouvez comprendre le code le plus complexe quand il est représenté sous forme d’arborescence d’expressions. L’élégance dans la structure de données explique comment le compilateur C# peut analyser les programmes C# les plus complexes et créer une sortie appropriée à partir de ce code source complexe.

Une fois que vous vous serez familiarisé avec la structure des arborescences d’expressions, vous constaterez que les connaissances acquises vous permettront de travailler rapidement avec de nombreux scénarios avancés. Les arborescences d’expressions offrent une puissance incroyable.

Outre la conversion d’algorithmes à exécuter dans d’autres environnements, vous pouvez utiliser des arborescences d’expressions pour simplifier l’écriture d’algorithmes qui inspectent du code avant de l’exécuter. Vous pouvez écrire une méthode dont les arguments sont des expressions, puis examiner ces expressions avant d’exécuter le code. L’arborescence d’expressions est une représentation complète du code : vous pouvez voir les valeurs de n’importe quelle sous-expression.
Vous pouvez voir les noms des méthodes et des propriétés. Vous pouvez voir la valeur de n’importe quelle expression constante.
Vous pouvez également convertir une arborescence d’expressions en délégué exécutable et exécuter le code.

Les API d’arborescences d’expressions vous permettent de créer des arborescences qui représentent presque n’importe quelle construction de code valide. Toutefois, pour simplifier les choses au maximum, certains idiomes C# ne peuvent pas être créés dans une arborescence d’expressions. C’est le cas des expressions asynchrones (utilisant les mots clés `async` et `await`). Si vous avez besoin d’algorithmes asynchrones, vous devez manipuler directement les objets `Task` plutôt que de vous fier à la prise en charge du compilateur. C’est aussi le cas pour la création des boucles. En général, vous les créez à l’aide de boucles `for`, `foreach`, `while` ou `do`. Comme vous le verrez [plus loin dans cette série](expression-trees-building.md), les API d’arborescences d’expressions prennent en charge une expression de boucle unique, avec des expressions `break` et `continue` qui contrôlent la répétition de la boucle.

La seule chose que vous ne pouvez pas faire est de modifier une arborescence d’expressions.  Les arborescences d’expressions sont des structures de données immuables. Si vous souhaitez muter (changer) une expression de l’arborescence, vous devez créer une nouvelle arborescence qui est une copie de l’original, mais avec les modifications souhaitées.

[Suivant – Types de frameworks prenant en charge les arborescences d’expressions](expression-classes.md)
