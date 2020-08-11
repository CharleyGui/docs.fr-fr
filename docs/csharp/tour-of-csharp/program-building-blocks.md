---
title: Les blocs de construction des programmes C#»
description: En savoir plus sur les membres, les expressions et les instructions C#. Les types contiennent des membres que vous écrivez. Ces membres sont générés à partir d’instructions et d’expressions.
ms.date: 08/06/2020
ms.openlocfilehash: de9f634db129ea2ec6f692cabb657f9fe41b2f9c
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88068554"
---
# <a name="program-building-blocks"></a>Blocs de construction de programme

Les types décrits dans l’article précédent sont générés à l’aide de ces blocs de construction : [***les membres, les***](../programming-guide/classes-and-structs/members.md) [ ***expressions***et les ***instructions***](../programming-guide/statements-expressions-operators/index.md).

## <a name="members"></a>Membres

Les membres d’un `class` sont soit des membres ***statiques*** , soit des ***membres d’instance***. Les membres statiques appartiennent à des classes, et les membres d’instance appartiennent à des objets (instances de classes).

La liste suivante fournit une vue d’ensemble des types de membres qu’une classe peut contenir.

- **Constantes**: valeurs constantes associées à la classe
- **Fields**: variables associées à la classe
- **Méthodes**: actions qui peuvent être effectuées par la classe
- **Propriétés**: actions associées à la lecture et à l’écriture des propriétés nommées de la classe
- **Indexeurs**: actions associées à l’indexation d’instances de la classe comme un tableau
- **Événements**: notifications qui peuvent être générées par la classe
- **Opérateurs**: conversions et opérateurs d’expression pris en charge par la classe
- **Constructeurs**: actions requises pour initialiser des instances de la classe ou la classe elle-même
- **Finaliseurs**: actions effectuées avant que les instances de la classe soient définitivement ignorées
- **Types**: types imbriqués déclarés par la classe

## <a name="accessibility"></a>Accessibilité

Chaque membre d’une classe a une accessibilité associée, qui contrôle les zones de texte de programme qui peuvent accéder au membre. Il existe six formes possibles d’accessibilité. Les modificateurs d’accès sont résumés ci-dessous.

- `public`: L’accès n’est pas limité.
- `private`: L’accès est limité à cette classe.
- `protected`: L’accès est limité à cette classe ou aux classes dérivées de cette classe.
- `internal`: L’accès est limité à l’assembly actuel ( `.exe` ou `.dll` ).
- `protected internal`: L’accès est limité à cette classe, aux classes dérivées de cette classe ou aux classes au sein du même assembly.
- `private protected`: L’accès est limité à cette classe ou aux classes dérivées de ce type dans le même assembly.

## <a name="fields"></a>Champs

Un *champ* est une variable qui est associée à une classe ou une instance d’une classe.

Un champ déclaré avec le modificateur static définit un champ statique. Un champ statique identifie exactement un seul emplacement de stockage. Quel que soit le nombre d’instances d’une classe qui sont créées, il n’y a qu’une seule copie d’un champ statique.

Un champ déclaré sans le modificateur static définit un champ d’instance. Chaque instance d’une classe contient une copie distincte de tous les champs d’instance de cette classe.

Dans l’exemple suivant, chaque instance de la `Color` classe a une copie distincte des `r` champs d' `g` instance, et `b` , mais il n’existe qu’une seule copie des `Black` `White` `Red` `Green` `Blue` champs statiques,,, et :

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ColorClassDefinition":::

Comme indiqué dans l’exemple précédent, les *champs en lecture seule* peuvent être déclarés avec un modificateur `readonly`. L’assignation à un champ en lecture seule ne peut se produire que dans le cadre de la déclaration du champ ou dans un constructeur de la même classe.

## <a name="methods"></a>Méthodes

Une *méthode* est un membre qui implémente un calcul ou une action qui peut être effectuée par un objet ou une classe. Les *méthodes statiques* sont accessibles à travers la classe. Les *méthodes d’instance* sont accessibles via des instances de la classe.

Les méthodes peuvent avoir une liste de *paramètres*, qui représentent des valeurs ou des références variables passées à la méthode. Les méthodes ont un *type de retour*, qui spécifie le type de la valeur calculée et retournée par la méthode. Le type de retour d’une méthode est `void` s’il ne retourne pas de valeur.

Comme les types, les méthodes peuvent également être un jeu de paramètres de type pour lesquels les arguments de type doivent être spécifiés lorsque la méthode est appelée. Contrairement aux types, les arguments de type peuvent souvent être déduits à partir des arguments d’un appel de méthode et n’ont pas à être fournis explicitement.

La *signature* d’une méthode doit être unique dans la classe dans laquelle la méthode est déclarée. La signature d’une méthode se compose du nom de la méthode, du nombre de paramètres de type, du nombre, des modificateurs et des types de ses paramètres. La signature d’une méthode n’inclut pas le type de retour.

Quand un corps de méthode est une expression unique, la méthode peut être définie à l’aide d’un format d’expression compact, comme indiqué dans l’exemple suivant :

```csharp
public override ToString() => "This is an object";
```

### <a name="parameters"></a>Paramètres

Les paramètres sont utilisés pour passer des valeurs ou des références variables aux méthodes. Les paramètres d’une méthode obtiennent leurs valeurs réelles à partir des *arguments* qui sont spécifiés lorsque la méthode est appelée. Il existe quatre types de paramètres : les paramètres de valeur, les paramètres de référence, les paramètres de sortie et les tableaux de paramètres.

Un *paramètre de valeur* est utilisé pour passer des arguments en entrée. Un paramètre de valeur correspond à une variable locale qui obtient sa valeur initiale de l’argument qui a été transmis pour le paramètre. Les modifications apportées à un paramètre de valeur n’affectent pas l’argument qui a été transmis pour le paramètre.

Les paramètres de valeur peuvent être facultatifs, en spécifiant une valeur par défaut afin que les arguments correspondants puissent être omis.

Un *paramètre de référence* est utilisé pour passer des arguments par référence. L’argument passé pour un paramètre de référence doit être une variable avec une valeur définie. Pendant l’exécution de la méthode, le paramètre de référence représente le même emplacement de stockage que la variable d’argument. Un paramètre de référence est déclaré avec le modificateur `ref`. L'exemple suivant illustre l'utilisation des paramètres `ref`.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="RefExample":::

Un *paramètre de sortie* est utilisé pour passer des arguments par référence. Il est similaire à un paramètre de référence, sauf qu’il ne nécessite pas d’affecter explicitement une valeur à l’argument fourni par l’appelant. Un paramètre de sortie est déclaré avec le modificateur `out`. L’exemple suivant montre l’utilisation de paramètres `out` à l’aide de la syntaxe introduite dans C# 7.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="OutExample":::

Un *tableau de paramètres* autorise le passage d’un nombre variable d’arguments à une méthode. Un tableau de paramètres est déclaré avec le modificateur `params`. Seul le dernier paramètre d’une méthode peut être un tableau de paramètres, et le type d’un tableau de paramètres doit être un type tableau unidimensionnel. Les `Write` `WriteLine` méthodes et de la <xref:System.Console?displayProperty=nameWithType> classe sont de bons exemples d’utilisation des tableaux de paramètres. Elles sont déclarées comme suit.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ConsoleExtract":::

Dans une méthode qui utilise un tableau de paramètres, le tableau de paramètres se comporte exactement comme un paramètre ordinaire de type tableau. Toutefois, dans un appel d’une méthode avec un tableau de paramètres, il est possible de passer un argument unique du type de tableau de paramètres ou un nombre quelconque d’arguments du type d’élément du tableau de paramètres. Dans ce cas, une instance de tableau est automatiquement créée et initialisée avec les arguments donnés. Cet exemple

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UseParamsArgs":::

revient à écrire ce qui suit.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="CompilerParams":::

### <a name="method-body-and-local-variables"></a>Corps de la méthode et variables locales

Le corps d’une méthode spécifie les instructions à exécuter lorsque la méthode est appelée.

Un corps de méthode peut déclarer des variables qui sont spécifiques à l’appel de la méthode. Ces variables sont appelées *variables locales*. Une déclaration de variable locale spécifie un nom de type, un nom de variable et éventuellement une valeur initiale. L’exemple suivant déclare une variable locale `i` avec une valeur initiale de zéro et une variable locale `j` sans valeur initiale.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="SquaresClass":::

C# requiert qu’une variable locale soit *assignée de manière définitive* avant de pouvoir obtenir sa valeur. Par exemple, si la déclaration de la précédente `i` n’inclut pas de valeur initiale, le compilateur signale une erreur pour les utilisations ultérieures de, `i` car n' `i` est pas définitivement assignée à ces points dans le programme.

Une méthode peut utiliser les instructions `return` pour retourner le contrôle à son appelant. Dans une méthode retournant `void` , les `return` instructions ne peuvent pas spécifier une expression. Dans une méthode avec un type de retour non void, les instructions `return` doivent inclure une expression qui calcule la valeur de retour.

### <a name="static-and-instance-methods"></a>Méthodes statiques et d’instance

Une méthode déclarée avec un `static` modificateur est une *méthode statique*. Une méthode statique ne fonctionne pas sur une instance spécifique et peut uniquement accéder directement aux membres statiques.

Une méthode déclarée sans `static` modificateur est une *méthode d’instance*. Une méthode d’instance opère sur une instance spécifique et peut accéder aux membres statiques et d’instance. L’instance sur laquelle une méthode d’instance a été appelée est explicitement accessible en tant que `this`. Il s’agit d’une erreur qui consiste à faire référence à `this` dans une méthode statique.

La classe `Entity` suivante a à la fois des statiques et des membres d’instance.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="EntityClass":::

Chaque `Entity` instance contient un numéro de série (et probablement d’autres informations qui ne sont pas indiquées ici). Le constructeur `Entity` (qui est similaire à une méthode d’instance) initialise la nouvelle instance avec le numéro de série suivant. Étant donné que le constructeur est un membre d’instance, il est autorisé à accéder à la fois au `_serialNo` champ d’instance et au `s_nextSerialNo` champ statique.

Les méthodes statiques `GetNextSerialNo` et `SetNextSerialNo` peuvent accéder au champ statique `s_nextSerialNo`, mais ce serait une erreur pour eux d’accéder directement au champ d’instance `_serialNo`.

L’exemple suivant illustre l’utilisation de la `Entity` classe.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UsingEntity":::

Les `SetNextSerialNo` `GetNextSerialNo` méthodes statiques et sont appelées sur la classe, tandis que la `GetSerialNo` méthode d’instance est appelée sur des instances de la classe.

### <a name="virtual-override-and-abstract-methods"></a>Méthodes virtuelles, de substitution et abstraites

Lorsqu’une déclaration de méthode d’instance inclut un modificateur `virtual`, la méthode est appelée *méthode virtuelle*. Si aucun modificateur virtuel n’est présent, la méthode est appelée *méthode non virtuelle*.

Lorsqu’une méthode virtuelle est appelée, le *type au moment de l’exécution* de l’instance pour laquelle cet appel prend place détermine l’implémentation de méthode à appeler. Dans un appel de méthode non virtuelle, le *type lors de la compilation* de l’instance est le facteur déterminant.

Une méthode virtuelle peut être *substituée* dans une classe dérivée. Lorsqu’une déclaration de méthode d’instance comprend un modificateur override, la méthode substitue une méthode virtuelle héritée ayant la même signature. La déclaration de méthode virtuelle AA introduit une nouvelle méthode. Une déclaration de méthode override spécialise une méthode virtuelle héritée existante en fournissant une nouvelle implémentation de cette méthode.

Une *méthode abstraite* est une méthode virtuelle sans implémentation. Une méthode abstraite est déclarée avec le `abstract` modificateur et est autorisée uniquement dans une classe abstraite. Une méthode abstraite doit être remplacée dans chaque classe dérivée non abstraite.

L’exemple suivant déclare une classe abstraite, `Expression`, qui représente un nœud d’arborescence de l’expression et trois classes dérivées, `Constant`, `VariableReference` et `Operation`, qui implémentent des nœuds d’arborescence de l’expression pour les références variables, les constantes et les opérations arithmétiques. (Cet exemple est similaire à, mais n’est pas associé aux types d’arborescence d’expression).

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="WorkingWithExpressions":::

Les quatre classes précédentes permet de modéliser des expressions arithmétiques. Par exemple, en utilisant des instances de ces classes, l’expression `x + 3` peut être représentée comme suit.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UseExpressions":::

La méthode `Evaluate` d’une instance `Expression` est appelée pour évaluer l’expression donnée et produire une valeur `double`. La méthode prend un argument `Dictionary` qui contient des noms de variables (comme clés des entrées) et des valeurs (comme valeurs des entrées). Comme `Evaluate` est une méthode abstraite, les classes non abstraites dérivées de `Expression` doivent remplacer `Evaluate`.

Une implémentation de `Constant` de `Evaluate` renvoie simplement la constante stockée. Une implémentation de `VariableReference` recherche le nom de variable dans le dictionnaire et renvoie la valeur résultante. Une implémentation de `Operation` évalue d’abord les opérandes de gauche et de droite (en appelant de manière récursive leurs méthodes `Evaluate`), puis effectue l’opération arithmétique donnée.

Le programme suivant utilise les classes `Expression` pour évaluer l’expression `x * (y + 2)` pour différentes valeurs de `x` et `y`.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UsingExpressions":::

### <a name="method-overloading"></a>Surcharge de méthode

La *surcharge* de méthode permet d’avoir plusieurs méthodes dans la même classe avec le même nom, tant qu’elles ont des signatures uniques. Lors de la compilation d’un appel à une méthode surchargée, le compilateur utilise *la résolution de surcharge* pour déterminer la méthode spécifique à appeler. La résolution de surcharge recherche l’unique méthode qui correspond le mieux aux arguments. Si aucune meilleure correspondance ne peut être trouvée, une erreur est signalée. L’exemple suivant montre la résolution de surcharge en action. Le commentaire pour chaque appel de la `UsageExample` méthode indique la méthode appelée.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="Overloading":::

Comme indiqué dans l’exemple, une méthode particulière peut toujours être sélectionnée en effectuant un cast explicite des arguments vers les types de paramètres et les arguments de type exacts.

## <a name="other-function-members"></a>Autres fonctions membres

Les membres qui contiennent du code exécutable sont collectivement regroupés sous les *membres de fonction* d’une classe. La section précédente décrit les méthodes, qui sont les principaux types de fonctions membres. Cette section décrit les autres types de fonctions membres pris en charge par C# : constructeurs, propriétés, indexeurs, événements, opérateurs et finaliseurs.

L’exemple suivant montre une classe générique appelée `MyList<T>` , qui implémente une liste d’objets pouvant être augmentée. La classe contient plusieurs exemples des types les plus courants de membres de fonction.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListExample":::

### <a name="constructors"></a>Constructeurs

C# prend en charge les constructeurs statiques et d’instance. Un *constructeur d’instance* est un membre qui implémente les actions requises pour initialiser une instance d’une classe. Un *constructeur statique* est un membre qui implémente les actions requises pour initialiser une classe lorsqu’elle est chargée pour la première fois.

Un constructeur est déclaré comme une méthode sans aucun type de retour et le même nom que la classe contenante. Si une déclaration de constructeur comprend un `static` modificateur, elle déclare un constructeur statique. Dans le cas contraire, elle déclare un constructeur d’instance.

Les constructeurs d’instance peuvent être surchargés et avoir des paramètres facultatifs. Par exemple, la classe `MyList<T>` déclare un constructeur d’instance avec un seul paramètre `int` facultatif. Les constructeurs d’instance sont appelés en utilisant l’opérateur `new`. Les instructions suivantes allouent deux instances `MyList<string>` à l’aide du constructeur de la classe `MyList` avec et sans l’argument facultatif.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="CreateLists":::

Contrairement aux autres membres, les constructeurs d’instance ne sont pas hérités. Une classe n’a pas de constructeurs d’instance autres que ceux qui sont réellement déclarés dans la classe. Si aucun constructeur d’instance n’est fourni pour une classe, un constructeur vide sans paramètre est fourni automatiquement.

### <a name="properties"></a>Propriétés

Les *propriétés* sont une extension naturelle des champs. Les deux sont des membres nommés avec des types associés, et la syntaxe pour accéder aux champs et propriétés est la même. Toutefois, contrairement aux champs, les propriétés ne désignent pas les emplacements de stockage. Au lieu de cela, les propriétés ont des *accesseurs* qui spécifient les instructions exécutées lorsque leurs valeurs sont lues ou écrites.

Une propriété est déclarée comme un champ, sauf que la déclaration se termine par un accesseur Get ou un accesseur Set écrit entre les délimiteurs `{` et `}` au lieu de se terminer par un point-virgule. Une propriété qui a un accesseur get et un accesseur set est une *propriété en lecture-écriture*, une propriété qui possède uniquement un accesseur get est une *propriété en lecture seule*, et une propriété qui possède uniquement un accesseur set est une *propriété en écriture seule*.

Un accesseur get correspond à une méthode sans paramètre avec une valeur de retour du type de la propriété. Un accesseur set correspond à une méthode avec un paramètre unique nommé valeur et aucun type de retour. L’accesseur Get calcule la valeur de la propriété. L’accesseur Set fournit une nouvelle valeur pour la propriété. Lorsque la propriété est la cible d’une assignation, ou l’opérande de `++` ou `--` , l’accesseur Set est appelé. Dans les autres cas où la propriété est référencée, l’accesseur Get est appelé.

 Lorsqu’une propriété est référencée en tant que cible d’une assignation ou qu’opérande de ++ ou --, l’accesseur set est appelé avec un argument qui fournit la nouvelle valeur.

La classe `MyList<T>` déclare deux propriétés, `Count` et `Capacity`, qui sont respectivement en lecture seule et en lecture-écriture. Le code suivant est un exemple d’utilisation de ces propriétés :

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="AccessProperties":::

C# prend en charge les propriétés d’instance et les propriétés statiques, similaires aux champs et aux méthodes. Les propriétés statiques sont déclarées avec le modificateur static, et les propriétés d’instance sont déclarées sans.

Le ou les accesseurs d’une propriété peuvent être virtuels. Lorsqu’une déclaration de propriété inclut un modificateur `virtual`, `abstract` ou `override`, elle s’applique aux accesseurs de la propriété.

### <a name="indexers"></a>Indexeurs

Un *indexeur* est un membre qui permet l’indexation des objets de la même façon en tant que tableau. Un indexeur est déclaré comme une propriété, sauf que le nom du membre est `this`, suivi d’une liste de paramètres écrits entre les délimiteurs `[` et `]`. Les paramètres sont disponibles dans le ou les accesseurs de l’indexeur. Similaires aux propriétés, les indexeurs peuvent être en lecture-écriture, en lecture seule et en écriture seule, et les accesseurs d’un indexeur peuvent être virtuels.

La classe `MyList<T>` déclare un indexeur en lecture-écriture unique qui prend un paramètre `int`. L’indexeur rend possible l’indexation des instances `MyList<T>` avec des valeurs `int`. Par exemple :

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListAddition":::

Les indexeurs peuvent être surchargés. Une classe peut déclarer plusieurs indexeurs tant que le nombre ou les types de leurs paramètres diffèrent.

### <a name="events"></a>Événements

Un *événement* est un membre qui permet à une classe ou un objet de fournir des notifications. Un événement est déclaré comme un champ, sauf que la déclaration comprend un `event` mot clé et que le type doit être un type délégué.

Dans une classe qui déclare un membre d’événement, l’événement se comporte de la même façon qu’un champ d’un type délégué (à condition que l’événement ne soit pas abstrait et ne déclare pas d’accesseurs). Le champ stocke une référence à un délégué qui représente les gestionnaires d’événements qui ont été ajoutés à l’événement. Si aucun gestionnaire d’événements n’est présent, le champ est `null`.

La classe `MyList<T>` déclare un membre d’événement unique appelé `Changed`, qui indique qu’un nouvel élément a été ajouté à la liste. L’événement Changed est déclenché par la méthode virtuelle `OnChanged`, qui vérifie si l’événement est `null` (ce qui signifie qu’aucun gestionnaire n’est présent). La notion de déclenchement d’un événement est équivalente précisément à l’appel du délégué représenté par l’événement. Il n’existe aucune construction de langage spéciale pour déclencher des événements.

Les clients réagissent aux événements via les *gestionnaires d’événements*. Les gestionnaires d’événements sont joints à l’aide de l’opérateur `+=` et supprimés à l’aide de l’opérateur `-=`. L'exemple suivant joint un gestionnaire d'événements à l'événement `Changed` d’un `MyList<string>`.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="RespondToEvents":::

Pour les scénarios avancés où le contrôle du stockage sous-jacent d’un événement est souhaité, une déclaration d’événement peut fournir explicitement des `add` `remove` accesseurs et, qui sont similaires à l' `set` accesseur d’une propriété.

### <a name="operators"></a>Opérateurs

Un *opérateur* est un membre qui définit la signification de l’application d’un opérateur d’expression particulière aux instances d’une classe. Trois types d’opérateurs peuvent être définis : les opérateurs unaires, les opérateurs binaires et les opérateurs de conversion. Tous les opérateurs doivent être déclarés comme `public` et `static`.

La `MyList<T>` classe déclare deux opérateurs, `operator ==` et `operator !=` . Ces opérateurs substitués donnent une nouvelle signification aux expressions qui appliquent ces opérateurs aux `MyList` instances. Plus précisément, les opérateurs définissent l’égalité de deux `MyList<T>` instances en comparant chacun des objets contenus à l’aide de leurs `Equals` méthodes. L’exemple suivant utilise l’opérateur `==` pour comparer deux instances de `MyList<int>`.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListAddition":::

La première `Console.WriteLine` génère `True`, car les deux listes contiennent le même nombre d’objets avec les mêmes valeurs dans le même ordre. Si `MyList<T>` n’avait pas défini `operator ==`, la première `Console.WriteLine` aurait affiché `False`, car `a` et `b` référencent des instances `MyList<int>` différentes.

### <a name="finalizers"></a>Finaliseurs

Un *finaliseur* est un membre qui implémente les actions requises pour finaliser une instance d’une classe. En règle générale, un finaliseur est nécessaire pour libérer des ressources non managées. Les finaliseurs ne peuvent pas avoir de paramètres, ils ne peuvent pas avoir de modificateurs d’accessibilité et ils ne peuvent pas être appelés explicitement. Le finaliseur pour une instance est appelé automatiquement lors du nettoyage de la mémoire (garbage collection). Pour plus d’informations, consultez l’article sur les [finaliseurs](../programming-guide/classes-and-structs/destructors.md).

Le récupérateur de mémoire est libre de déterminer quand collecter des objets et exécuter des finaliseurs. Plus précisément, le minutage des appels du finaliseur n’est pas déterministe, et les finaliseurs peuvent être exécutés sur n’importe quel thread. Pour ces raisons et d’autres, les classes doivent implémenter des finaliseurs uniquement lorsqu’aucune des autres solutions n’est envisageable.

L’instruction `using` fournit une meilleure approche pour la destruction d’objets.

## <a name="expressions"></a>Expressions

Les *expressions* sont construites à partir de *d’opérandes* et *d’opérateurs*. Les opérateurs d’une expression indiquent les opérations à appliquer aux opérandes. Parmi les exemples d’opérateurs figurent `+`, `-`, `*`, `/` et `new`. Les littéraux, les champs, les variables locales et les expressions sont des exemples d’opérandes.

Quand une expression contient plusieurs opérateurs, la *priorité* des opérateurs contrôle l’ordre dans lequel ils sont évalués. Par exemple, l’expression `x + y * z` est évaluée comme `x + (y * z)`, car l’opérateur `*` a une priorité plus élevée que `+`.

Lorsqu’un opérande se produit entre deux opérateurs de même priorité, *l’associativité* des opérateurs détermine l’ordre dans lequel les opérations sont effectuées :

* À l’exception des opérateurs d’assignation et de fusion Null, tous les opérateurs binaires sont *associatifs à gauche*, ce qui signifie que les opérations sont effectuées de gauche à droite. Par exemple, `x + y + z` est évalué comme étant `(x + y) + z`.
* Les opérateurs d’assignation, les opérateurs de fusion Null `??` et `??=` l’opérateur conditionnel `?:` sont *associatifs à droite*, ce qui signifie que les opérations sont exécutées de droite à gauche. Par exemple, `x = y = z` est évalué comme étant `x = (y = z)`.

La priorité et l’associativité peuvent être contrôlées à l’aide de parenthèses. Par exemple, `x + y * z` multiplie d’abord `y` par `z`, puis ajoute le résultat à `x`, mais `(x + y) * z` ajoute d’abord `x` et `y`, puis multiplie le résultat par `z`.

La plupart des opérateurs peuvent être [*surchargés*](../language-reference/operators/operator-overloading.md). La surcharge d’opérateur autorise la spécification d’implémentations d’opérateurs définies par l’utilisateur pour les opérations où l’un des deux opérandes ou les deux sont d’un type classe ou struct défini par l’utilisateur.

C# met à votre disposition de nombreux opérateurs pour effectuer des opérations [arithmétiques](../language-reference/operators/arithmetic-operators.md), [logiques](../language-reference/operators/boolean-logical-operators.md), [au niveau du bit et de décalage](../language-reference/operators/bitwise-and-shift-operators.md) et des comparaisons d’[égalité](../language-reference/operators/equality-operators.md) et d’[ordre](../language-reference/operators/comparison-operators.md) .

Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](../language-reference/operators/index.md).

## <a name="statements"></a>Instructions

Les actions d’un programme sont exprimées à l’aide *d’instructions*. C# prend en charge plusieurs types d’instructions, dont plusieurs sont définies en termes d’instructions incorporées.

- Un *bloc* autorise l’écriture de plusieurs instructions dans les contextes où une seule instruction est autorisée. Un bloc se compose d’une liste d’instructions écrites entre les délimiteurs `{` et `}`.
- Les *instructions de déclaration* sont utilisées pour déclarer des variables locales et des constantes.
- Les *instructions d’expression* sont utilisées pour évaluer des expressions. Les expressions qui peuvent être utilisées en tant qu’instructions comprennent les appels de méthode, les allocations d’objet avec l’opérateur `new`, les affectations avec `=` et les opérateurs d’assignation composée, les opérations d’incrémentation et de décrémentation à l’aide des opérateurs `++` et `--` et les expressions `await`.
- Les *instructions de sélection* sont utilisées pour sélectionner un nombre d’instructions possibles pour l’exécution en fonction de la valeur d’une expression. Ce groupe contient les `if` `switch` instructions et.
- Les *instructions d’itération* servent à exécuter à plusieurs reprises une instruction incorporée. Ce groupe contient les `while` `do` instructions,, `for` et `foreach` .
- Les *instructions de saut* sont utilisées pour transférer le contrôle. Ce groupe contient les `break` `continue` instructions,, `goto` , `throw` , `return` et `yield` .
- L’instruction `try`...`catch` est utilisée pour intercepter les exceptions qui se produisent pendant l’exécution d’un bloc, et l’instruction `try`...`finally` permet de spécifier que le code de finalisation est toujours exécuté, qu’une exception se soit produite ou non.
- Les instructions `checked` et `unchecked` permettent de contrôler le contexte de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.
- L’instruction `lock` est utilisée pour obtenir le verrou d’exclusion mutuelle pour un objet donné, exécuter une instruction, puis libérer le verrou.
- L’instruction `using` est utilisée pour obtenir une ressource, exécuter une instruction puis supprimer cette ressource.

La liste suivante répertorie les types d’instructions qui peuvent être utilisés :

* Déclaration de variable locale.
* Déclaration de constante locale.
* Instruction d’expression.
* `if`gestion.
* `switch`gestion.
* `while`gestion.
* `do`gestion.
* `for`gestion.
* `foreach`gestion.
* `break`gestion.
* `continue`gestion.
* `goto`gestion.
* `return`gestion.
* `yield`gestion.
* `throw`instructions et `try` instructions.
* `checked``unchecked`instructions et.
* `lock`gestion.
* `using`gestion.

>[!div class="step-by-step"]
>[Précédent](types.md) 
> [Suivant](features.md)
