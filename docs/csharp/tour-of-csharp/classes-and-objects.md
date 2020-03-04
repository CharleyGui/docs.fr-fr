---
title: Classes et objets dans C# - Visite guidée du langage C#
description: Vous débutez en C# ? Lire cette vue d’ensemble des classes, des objets et de l’héritage
ms.date: 02/27/2020
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: c178e11b5667905f75538555c8a309e2fdb4a9ef
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159180"
---
# <a name="classes-and-objects"></a>Classes et objets

Les *Classes* sont le type le plus fondamental de C#. Une classe est une structure de données qui combine l’état (champs) et les actions (méthodes et autres fonctions membres) en une seule unité. Une classe fournit une définition pour les *instances* créées dynamiquement de la classe, également appelées *objets*. Les classes prennent en charge *l’héritage* et le *polymorphisme*, des mécanismes par lesquels les *classes dérivées* peuvent étendre et spécialiser les *classes de base*.

Les nouvelles classes sont créées à l’aide des déclarations de classe. Une déclaration de classe commence par un en-tête qui spécifie les attributs et modificateurs de la classe, le nom de la classe, la classe de base (si fournie) et les interfaces implémentées par la classe. L’en-tête est suivi par le corps de la classe, qui se compose d’une liste de déclarations de membres écrites entre les délimiteurs `{` et `}`.

Le code suivant illustre une déclaration d’une classe simple nommée `Point`:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Les instances de classes sont créées à l’aide de l’opérateur `new`, qui alloue la mémoire pour une nouvelle instance, appelle un constructeur pour initialiser l’instance et retourne une référence à l’instance. Les instructions suivantes créent deux objets Point et stockent les références à ces objets dans les deux variables :

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

La mémoire occupée par un objet est automatiquement libérée lorsque l’objet n’est plus accessible. Il n’est ni nécessaire ni possible de libérer explicitement des objets C#dans.

## <a name="members"></a>Membres

Les membres d’une classe sont des membres statiques ou membres d’instance. Les membres statiques appartiennent à des classes, et les membres d’instance appartiennent à des objets (instances de classes).

La liste suivante fournit une vue d’ensemble des types de membres qu’une classe peut contenir.

- Constantes
  - Valeurs constantes associées à la classe
- Champs
  - Variables de la classe
- Méthodes
  - Calculs et les actions qui peuvent être effectués par la classe
- Propriétés
  - Actions associées à la lecture et l’écriture des propriétés nommées de la classe
- Indexeurs
  - Actions liées à l’indexation des instances de la classe comme un tableau
- Événements
  - Les notifications qui peuvent être générées par la classe
- Opérateurs
  - Les opérateurs de conversion et d’expression pris en charge par la classe
- Constructeurs
  - Les actions requises pour initialiser les instances de la classe ou la classe elle-même
- Finaliseurs
  - Actions à effectuer avant que les instances de la classe soient abandonnées de façon définitive
- Types
  - Types imbriqués déclarés par la classe

## <a name="accessibility"></a>Accessibilité

Chaque membre d’une classe a une accessibilité associée, qui contrôle les zones de texte de programme qui peuvent accéder au membre. Il existe six formes possibles d’accessibilité. Les modificateurs d’accès sont résumés ci-dessous.

- `public`
  - L’accès n’est pas limité.
- `protected`
  - L’accès est limité à cette classe ou aux classes dérivées de cette classe.
- `internal`
  - L’accès est limité à l’assembly actuel (. exe,. dll, etc.).
- `protected internal`
  - L’accès est limité à la classe conteneur, aux classes dérivées de la classe conteneur ou aux classes au sein du même assembly.
- `private`
  - L’accès est limité à cette classe.
- `private protected`
  - L’accès est limité à la classe conteneur ou aux classes dérivées du type conteneur dans le même assembly.

## <a name="type-parameters"></a>Paramètres de type

Une définition de classe peut spécifier un jeu de paramètres de type en faisant suivre le nom de classe par une liste de noms de paramètre de type entre crochets. Les paramètres de type peuvent ensuite être utilisés dans le corps des déclarations de classe pour définir les membres de la classe. Dans l’exemple suivant, les paramètres de type de `Pair` sont `TFirst` et `TSecond` :

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Un type de classe déclaré pour prendre des paramètres de type est appelé un *type de classe générique*. Les types struct, interface et Delegate peuvent également être génériques.
Lorsque la classe générique est utilisée, des arguments de type doivent être fournis pour chacun des paramètres de type :

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Un type générique avec des arguments de type fournis, comme `Pair<int,string>` ci-dessus, est appelé un *type construit*.

## <a name="base-classes"></a>Classes de base

Une déclaration de classe peut spécifier une classe de base en faisant suivre les paramètres de nom et de type de classe par un signe deux-points et le nom de la classe de base. L’omission d’une spécification de classe de base revient à dériver du type `object`. Dans l'exemple suivant, la classe de base de `Point3D` est `Point`, et la classe de base de `Point` est `object` :

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Une classe hérite des membres de sa classe de base. L’héritage signifie qu’une classe contient implicitement tous les membres de sa classe de base, à l’exception des constructeurs d’instance et statiques et des finaliseurs de la classe de base. Une classe dérivée peut ajouter de nouveaux membres aux membres qu’elle hérite, mais elle ne peut pas supprimer la définition d’un membre hérité. Dans l’exemple précédent, `Point3D` hérite des champs `x` et `y` de `Point`, et chaque instance de `Point3D` contient trois champs, `x`, `y` et `z`.

Il existe une conversion implicite d’un type de classe vers un de ses types de classe de base. Une variable d’un type de classe peut référencer une instance de cette classe ou une instance de toute classe dérivée. Par exemple, pour les déclarations de classe précédentes, une variable de type `Point` peut faire référence à un objet `Point` ou `Point3D` :

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Champs

Un *champ* est une variable qui est associée à une classe ou une instance d’une classe.

Un champ déclaré avec le modificateur static définit un champ statique. Un champ statique identifie exactement un seul emplacement de stockage. Quel que soit le nombre d’instances d’une classe qui sont créées, il n’y a qu’une seule copie d’un champ statique.

Un champ déclaré sans le modificateur static définit un champ d’instance. Chaque instance d’une classe contient une copie distincte de tous les champs d’instance de cette classe.

Dans l’exemple suivant, chaque instance de la classe `Color` dispose d’une copie distincte des champs d’instance `r`, `g`et `b`, mais il n’existe qu’une seule copie des champs statiques `Black`, `White`, `Red`, `Green`et `Blue` :

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Comme indiqué dans l’exemple précédent, les *champs en lecture seule* peuvent être déclarés avec un modificateur `readonly`. L’affectation à un champ `readonly` peut survenir uniquement dans le cadre de la déclaration du champ ou dans un constructeur de la même classe.

## <a name="methods"></a>Méthodes

Une *méthode* est un membre qui implémente un calcul ou une action qui peut être effectuée par un objet ou une classe. Les *méthodes statiques* sont accessibles à travers la classe. Les *méthodes d’instance* sont accessibles via des instances de la classe.

Les méthodes peuvent avoir une liste de *paramètres*, qui représentent des valeurs ou des références variables passées à la méthode et un *type de retour*, qui spécifie le type de la valeur calculée et retournée par la méthode. Le type de retour d’une méthode est `void` s’il ne retourne pas de valeur.

Comme les types, les méthodes peuvent également être un jeu de paramètres de type pour lesquels les arguments de type doivent être spécifiés lorsque la méthode est appelée. Contrairement aux types, les arguments de type peuvent souvent être déduits à partir des arguments d’un appel de méthode et n’ont pas à être fournis explicitement.

La *signature* d’une méthode doit être unique dans la classe dans laquelle la méthode est déclarée. La signature d’une méthode se compose du nom de la méthode, du nombre de paramètres de type et du nombre, des modificateurs et des types de ses paramètres. La signature d’une méthode n’inclut pas le type de retour.

### <a name="parameters"></a>Paramètres

Les paramètres sont utilisés pour passer des valeurs ou des références variables aux méthodes. Les paramètres d’une méthode obtiennent leurs valeurs réelles à partir des *arguments* qui sont spécifiés lorsque la méthode est appelée. Il existe quatre types de paramètres : les paramètres de valeur, les paramètres de référence, les paramètres de sortie et les tableaux de paramètres.

Un *paramètre de valeur* est utilisé pour passer des arguments en entrée. Un paramètre de valeur correspond à une variable locale qui obtient sa valeur initiale de l’argument qui a été transmis pour le paramètre. Les modifications apportées à un paramètre de valeur n’affectent pas l’argument qui a été transmis pour le paramètre.

Les paramètres de valeur peuvent être facultatifs, en spécifiant une valeur par défaut afin que les arguments correspondants puissent être omis.

Un *paramètre de référence* est utilisé pour passer des arguments par référence. L’argument passé pour un paramètre de référence doit être une variable avec une valeur définie et, pendant l’exécution de la méthode, le paramètre de référence représente le même emplacement de stockage que la variable d’argument. Un paramètre de référence est déclaré avec le modificateur `ref`. L'exemple suivant illustre l'utilisation des paramètres `ref`.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

Un *paramètre de sortie* est utilisé pour passer des arguments par référence. Il est similaire à un paramètre de référence, sauf qu’il ne nécessite pas d’affecter explicitement une valeur à l’argument fourni par l’appelant. Un paramètre de sortie est déclaré avec le modificateur `out`. L’exemple suivant montre l’utilisation de paramètres `out` à l’aide de la syntaxe introduite dans C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

Un *tableau de paramètres* autorise le passage d’un nombre variable d’arguments à une méthode. Un tableau de paramètres est déclaré avec le modificateur `params`. Seul le dernier paramètre d’une méthode peut être un tableau de paramètres, et le type d’un tableau de paramètres doit être un type tableau unidimensionnel. Les méthodes Write et WriteLine de la classe <xref:System.Console?displayProperty=nameWithType> sont de bons exemples d’utilisation des tableaux de paramètres. Elles sont déclarées comme suit.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

Dans une méthode qui utilise un tableau de paramètres, le tableau de paramètres se comporte exactement comme un paramètre ordinaire de type tableau. Toutefois, dans un appel d’une méthode avec un tableau de paramètres, il est possible de passer un argument unique du type de tableau de paramètres ou un nombre quelconque d’arguments du type d’élément du tableau de paramètres. Dans ce cas, une instance de tableau est automatiquement créée et initialisée avec les arguments donnés. Cet exemple

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

revient à écrire ce qui suit.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Corps de la méthode et variables locales

Le corps d’une méthode spécifie les instructions à exécuter lorsque la méthode est appelée.

Un corps de méthode peut déclarer des variables qui sont spécifiques à l’appel de la méthode. Ces variables sont appelées *variables locales*. Une déclaration de variable locale spécifie un nom de type, un nom de variable et éventuellement une valeur initiale. L’exemple suivant déclare une variable locale `i` avec une valeur initiale de zéro et une variable locale `j` sans valeur initiale.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# requiert qu’une variable locale soit *assignée de manière définitive* avant de pouvoir obtenir sa valeur. Par exemple, si la déclaration de la `i` précédente n’inclut pas de valeur initiale, le compilateur signale une erreur pour les utilisations suivantes de `i`, car `i` n’est pas définitivement assignée à ces points dans le programme.

Une méthode peut utiliser les instructions `return` pour retourner le contrôle à son appelant. Dans une méthode qui retourne `void`, les instructions `return` ne peuvent pas spécifier une expression. Dans une méthode avec un type de retour non void, les instructions `return` doivent inclure une expression qui calcule la valeur de retour.

### <a name="static-and-instance-methods"></a>Méthodes statiques et d’instance

Une méthode déclarée avec un modificateur statique est une *méthode statique*. Une méthode statique ne fonctionne pas sur une instance spécifique et peut uniquement accéder directement aux membres statiques.

Une méthode déclarée sans un modificateur statique est une *méthode d’instance*. Une méthode d’instance opère sur une instance spécifique et peut accéder aux membres statiques et d’instance. L’instance sur laquelle une méthode d’instance a été appelée est explicitement accessible en tant que `this`. Il s’agit d’une erreur qui consiste à faire référence à `this` dans une méthode statique.

La classe `Entity` suivante a à la fois des statiques et des membres d’instance.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Chaque `Entity` instance contient un numéro de série (et probablement d’autres informations qui ne sont pas indiquées ici). Le constructeur `Entity` (qui est similaire à une méthode d’instance) initialise la nouvelle instance avec le numéro de série suivant. Étant donné que le constructeur est un membre d’instance, il est autorisé à accéder à la fois au champ d’instance `serialNo` et au champ statique `nextSerialNo`.

Les méthodes statiques `GetNextSerialNo` et `SetNextSerialNo` peuvent accéder au champ statique `nextSerialNo`, mais ce serait une erreur pour eux d’accéder directement au champ d’instance `serialNo`.

L’exemple suivant illustre l’utilisation de la classe d’entité.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Les méthodes statiques `SetNextSerialNo` et `GetNextSerialNo` sont appelées sur la classe, tandis que la méthode d’instance `GetSerialNo` est appelée sur des instances de la classe.

### <a name="virtual-override-and-abstract-methods"></a>Méthodes virtuelles, de substitution et abstraites

Lorsqu’une déclaration de méthode d’instance inclut un modificateur `virtual`, la méthode est appelée *méthode virtuelle*. Si aucun modificateur virtuel n’est présent, la méthode est appelée *méthode non virtuelle*.

Lorsqu’une méthode virtuelle est appelée, le *type au moment de l’exécution* de l’instance pour laquelle cet appel prend place détermine l’implémentation de méthode à appeler. Dans un appel de méthode non virtuelle, le *type lors de la compilation* de l’instance est le facteur déterminant.

Une méthode virtuelle peut être *substituée* dans une classe dérivée. Lorsqu’une déclaration de méthode d’instance comprend un modificateur override, la méthode substitue une méthode virtuelle héritée ayant la même signature. Là où une déclaration de méthode virtuelle présente une nouvelle méthode, une déclaration de méthode de substitution spécialise une méthode virtuelle héritée existante en fournissant une nouvelle implémentation de cette méthode.

Une *méthode abstraite* est une méthode virtuelle sans implémentation. Une méthode abstraite est déclarée avec le modificateur abstract et est autorisée uniquement dans une classe qui est également déclarée comme étant abstract. Une méthode abstraite doit être remplacée dans chaque classe dérivée non abstraite.

L’exemple suivant déclare une classe abstraite, `Expression`, qui représente un nœud d’arborescence de l’expression et trois classes dérivées, `Constant`, `VariableReference` et `Operation`, qui implémentent des nœuds d’arborescence de l’expression pour les références variables, les constantes et les opérations arithmétiques. (Cet exemple est similaire à, mais ne doit pas être confondu avec les types d’arborescence d’expression).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Les quatre classes précédentes permet de modéliser des expressions arithmétiques. Par exemple, en utilisant des instances de ces classes, l’expression `x + 3` peut être représentée comme suit.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

La méthode `Evaluate` d’une instance `Expression` est appelée pour évaluer l’expression donnée et produire une valeur `double`. La méthode prend un argument `Dictionary` qui contient des noms de variables (comme clés des entrées) et des valeurs (comme valeurs des entrées). Comme `Evaluate` est une méthode abstraite, les classes non abstraites dérivées de `Expression` doivent remplacer `Evaluate`.

Une implémentation de `Constant` de `Evaluate` renvoie simplement la constante stockée. Une implémentation de `VariableReference` recherche le nom de variable dans le dictionnaire et renvoie la valeur résultante. Une implémentation de `Operation` évalue d’abord les opérandes de gauche et de droite (en appelant de manière récursive leurs méthodes `Evaluate`), puis effectue l’opération arithmétique donnée.

Le programme suivant utilise les classes `Expression` pour évaluer l’expression `x * (y + 2)` pour différentes valeurs de `x` et `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Surcharge de méthode

La *surcharge* de méthode permet d’avoir plusieurs méthodes dans la même classe avec le même nom, tant qu’elles ont des signatures uniques. Lors de la compilation d’un appel à une méthode surchargée, le compilateur utilise *la résolution de surcharge* pour déterminer la méthode spécifique à appeler. La résolution de surcharge trouve la méthode qui correspond le mieux aux arguments ou signale une erreur si aucune meilleure correspondance ne peut être trouvée. L’exemple suivant montre la résolution de surcharge en action. Le commentaire pour chaque appel de la méthode `UsageExample` indique la méthode appelée.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Comme le montre l’exemple, une méthode particulière peut toujours être sélectionnée en effectuant un cast explicite des arguments aux types de paramètres exacts et/ou en fournissant explicitement les arguments de type.

## <a name="other-function-members"></a>Autres fonctions membres

Les membres qui contiennent du code exécutable sont collectivement regroupés sous les *membres de fonction* d’une classe. La section précédente décrit les méthodes, qui sont les principaux types de fonctions membres. Cette section décrit les autres types de fonctions membres pris en charge par C# : constructeurs, propriétés, indexeurs, événements, opérateurs et finaliseurs.

L’exemple suivant montre une classe générique appelée `MyList<T>`, qui implémente une liste d’objets pouvant être augmentée. La classe contient plusieurs exemples des types les plus courants de membres de fonction.

> [!NOTE]
> Cet exemple crée une classe `MyList`, ce qui n’est pas la même chose que la classe <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> standard .NET. S’il ne permet pas de remplacer cette classe, il illustre en revanche les concepts nécessaires à cette visite guidée.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Constructeurs

C# prend en charge les constructeurs statiques et d’instance. Un *constructeur d’instance* est un membre qui implémente les actions requises pour initialiser une instance d’une classe. Un *constructeur statique* est un membre qui implémente les actions requises pour initialiser une classe lorsqu’elle est chargée pour la première fois.

Un constructeur est déclaré comme une méthode sans aucun type de retour et le même nom que la classe contenante. Si une déclaration de constructeur comprend un modificateur static, elle déclare un constructeur statique. Dans le cas contraire, elle déclare un constructeur d’instance.

Les constructeurs d’instance peuvent être surchargés et avoir des paramètres facultatifs. Par exemple, la classe `MyList<T>` déclare un constructeur d’instance avec un seul paramètre `int` facultatif. Les constructeurs d’instance sont appelés en utilisant l’opérateur `new`. Les instructions suivantes allouent deux instances `MyList<string>` à l’aide du constructeur de la classe `MyList` avec et sans l’argument facultatif.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Contrairement à d’autres membres, les constructeurs d’instance ne sont pas hérités et une classe n’a pas de constructeurs d’instance autres que ceux réellement déclarés dans la classe. Si aucun constructeur d’instance n’est fourni pour une classe, un constructeur vide sans paramètre est fourni automatiquement.

### <a name="properties"></a>Propriétés

Les *propriétés* sont une extension naturelle des champs. Les deux sont des membres nommés avec des types associés, et la syntaxe pour accéder aux champs et propriétés est la même. Toutefois, contrairement aux champs, les propriétés ne désignent pas les emplacements de stockage. Au lieu de cela, les propriétés ont des *accesseurs* qui spécifient les instructions à exécuter lorsque les valeurs sont lues ou écrites.

Une propriété est déclarée comme un champ, sauf que la déclaration se termine avec un accesseur get et/ou un accesseur set écrit entre les délimiteurs `{` et `}` au lieu de se terminer par un point-virgule. Une propriété qui a un accesseur get et un accesseur set est une *propriété en lecture-écriture*, une propriété qui possède uniquement un accesseur get est une *propriété en lecture seule*, et une propriété qui possède uniquement un accesseur set est une *propriété en écriture seule*.

Un accesseur get correspond à une méthode sans paramètre avec une valeur de retour du type de la propriété. Sauf en tant que cible d’une assignation, lorsqu’une propriété est référencée dans une expression, l’accesseur get de la propriété est appelé pour calculer la valeur de la propriété.

Un accesseur set correspond à une méthode avec un paramètre unique nommé valeur et aucun type de retour. Lorsqu’une propriété est référencée en tant que cible d’une assignation ou qu’opérande de ++ ou --, l’accesseur set est appelé avec un argument qui fournit la nouvelle valeur.

La classe `MyList<T>` déclare deux propriétés, `Count` et `Capacity`, qui sont respectivement en lecture seule et en lecture-écriture. Le code suivant est un exemple d’utilisation de ces propriétés :

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

C# prend en charge les propriétés d’instance et les propriétés statiques, similaires aux champs et aux méthodes. Les propriétés statiques sont déclarées avec le modificateur static, et les propriétés d’instance sont déclarées sans.

Le ou les accesseurs d’une propriété peuvent être virtuels. Lorsqu’une déclaration de propriété inclut un modificateur `virtual`, `abstract` ou `override`, elle s’applique aux accesseurs de la propriété.

### <a name="indexers"></a>Indexeurs

Un *indexeur* est un membre qui permet l’indexation des objets de la même façon en tant que tableau. Un indexeur est déclaré comme une propriété, sauf que le nom du membre est `this`, suivi d’une liste de paramètres écrits entre les délimiteurs `[` et `]`. Les paramètres sont disponibles dans le ou les accesseurs de l’indexeur. Similaires aux propriétés, les indexeurs peuvent être en lecture-écriture, en lecture seule et en écriture seule, et les accesseurs d’un indexeur peuvent être virtuels.

La classe `MyList<T>` déclare un indexeur en lecture-écriture unique qui prend un paramètre `int`. L’indexeur rend possible l’indexation des instances `MyList<T>` avec des valeurs `int`. Par exemple :

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Les indexeurs peuvent être surchargés, ce qui signifie qu’une classe peut déclarer plusieurs indexeurs tant que le nombre ou les types de leurs paramètres diffèrent.

### <a name="events"></a>Événements

Un *événement* est un membre qui permet à une classe ou un objet de fournir des notifications. Un événement est déclaré comme un champ, sauf que la déclaration inclut un mot-clé d’événement et que le type doit être un type délégué.

Dans une classe qui déclare un membre d’événement, l’événement se comporte de la même façon qu’un champ d’un type délégué (à condition que l’événement ne soit pas abstrait et ne déclare pas d’accesseurs). Le champ stocke une référence à un délégué qui représente les gestionnaires d’événements qui ont été ajoutés à l’événement. Si aucun gestionnaire d’événements n’est présent, le champ est `null`.

La classe `MyList<T>` déclare un membre d’événement unique appelé `Changed`, qui indique qu’un nouvel élément a été ajouté à la liste. L’événement Changed est déclenché par la méthode virtuelle `OnChanged`, qui vérifie si l’événement est `null` (ce qui signifie qu’aucun gestionnaire n’est présent). La notion de déclenchement d’un événement est équivalente à l’appel de délégué représenté par l’événement. Par conséquent, il n’existe aucune construction de langage particulière pour déclencher des événements.

Les clients réagissent aux événements via les *gestionnaires d’événements*. Les gestionnaires d’événements sont joints à l’aide de l’opérateur `+=` et supprimés à l’aide de l’opérateur `-=`. L'exemple suivant joint un gestionnaire d'événements à l'événement `Changed` d’un `MyList<string>`.

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Pour les scénarios avancés où le contrôle du stockage sous-jacent d’un événement est souhaité, une déclaration d’événement peut fournir explicitement des accesseurs `add` et `remove`, qui sont similaires à l’accesseur `set` d’une propriété.

### <a name="operators"></a>Opérateurs

Un *opérateur* est un membre qui définit la signification de l’application d’un opérateur d’expression particulière aux instances d’une classe. Trois types d’opérateurs peuvent être définis : les opérateurs unaires, les opérateurs binaires et les opérateurs de conversion. Tous les opérateurs doivent être déclarés comme `public` et `static`.

La classe `MyList<T>` déclare deux opérateurs, `operator ==` et `operator !=`, et donne donc une nouvelle signification aux expressions qui appliquent ces opérateurs aux instances `MyList`. Plus précisément, les opérateurs définissent l’égalité de deux instances `MyList<T>` comme la comparaison de chacun des objets contenus à l’aide de leurs méthodes Equals. L’exemple suivant utilise l’opérateur `==` pour comparer deux instances de `MyList<int>`.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

La première `Console.WriteLine` génère `True`, car les deux listes contiennent le même nombre d’objets avec les mêmes valeurs dans le même ordre. Si `MyList<T>` n’avait pas défini `operator ==`, la première `Console.WriteLine` aurait affiché `False`, car `a` et `b` référencent des instances `MyList<int>` différentes.

### <a name="finalizers"></a>Finaliseurs

Un *finaliseur* est un membre qui implémente les actions requises pour finaliser une instance d’une classe. Les finaliseurs ne peuvent pas avoir de paramètres, ils ne peuvent pas avoir de modificateurs d’accessibilité et ils ne peuvent pas être appelés explicitement. Le finaliseur pour une instance est appelé automatiquement lors du nettoyage de la mémoire (garbage collection).

Le récupérateur de mémoire est libre de déterminer quand collecter des objets et exécuter des finaliseurs. Plus précisément, le minutage des appels du finaliseur n’est pas déterministe, et les finaliseurs peuvent être exécutés sur n’importe quel thread. Pour ces raisons et d’autres, les classes doivent implémenter des finaliseurs uniquement lorsqu’aucune des autres solutions n’est envisageable.

L’instruction `using` fournit une meilleure approche pour la destruction d’objets.

> [!div class="step-by-step"]
> [Précédent](statements.md)
> [Suivant](arrays.md)
