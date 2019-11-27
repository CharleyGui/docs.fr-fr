---
title: Objets et classes
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: d45aca8b137f56cf058b63b9286504259c0005eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346703"
---
# <a name="objects-and-classes-in-visual-basic"></a>Objets et classes dans Visual Basic

Un *objet* est une combinaison de code et de données qui peuvent être traités en tant qu’unité. Un objet peut être une partie d’une application, comme une commande ou un formulaire. Une application entière peut également être un objet.

Lorsque vous créez une application dans Visual Basic, vous travaillez constamment avec des objets. Vous pouvez utiliser les objets fournis par Visual Basic, tels que les contrôles, les formulaires et les objets d’accès aux données. Vous pouvez également utiliser des objets d’autres applications au sein de votre application Visual Basic. Vous pouvez même créer vos propres objets et définir des propriétés et des méthodes supplémentaires pour ceux-ci. Les objets se comportent comme des blocs de construction préfabriqués : ils vous permettent d’écrire un fragment de code une seule fois et de le réutiliser maintes fois.

Cette rubrique présente les objets en détail.

## <a name="objects-and-classes"></a>Objets et classes

Chaque objet de Visual Basic est défini par une *classe*. Une classe décrit les variables, les propriétés, les procédures et les événements d’un objet. Les objets sont des instances de classes. Vous pouvez créer autant d’objets que nécessaire dès que vous avez défini une classe.

Pour comprendre la relation entre un objet et sa classe, prenez l’exemple des emporte-pièces et des biscuits. L’emporte-pièce est la classe. Il définit les caractéristiques de chaque biscuit, par exemple la taille et la forme. La classe est utilisée pour créer des objets. Les objets sont les biscuits.

Vous devez créer un objet pour pouvoir accéder à ses membres.

### <a name="to-create-an-object-from-a-class"></a>Pour créer un objet à partir d’une classe

1. Déterminez à partir de quelle classe vous souhaitez créer un objet.

2. Écrivez une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour créer une variable à laquelle vous pouvez assigner une instance de classe. La variable doit être du type de la classe souhaitée.

   ```vb
   Dim nextCustomer As customer
   ```

3. Ajoutez le mot clé [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) pour initialiser la variable à une nouvelle instance de la classe.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Vous pouvez désormais accéder aux membres de la classe par le biais de la variable d’objet.

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> Si possible, vous devez déclarer la variable comme étant du type de classe que vous avez l’intention de lui attribuer. Il s’agit de la *liaison anticipée*. Si vous ne connaissez pas le type de classe au moment de la compilation, vous pouvez utiliser la *liaison tardive* en déclarant la variable comme étant de [type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md). Toutefois, la liaison tardive peut ralentir les performances et limiter l’accès aux membres de l’objet de l’exécution. Pour plus d’informations, consultez [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Plusieurs instances

Les objets nouvellement créés à partir d’une classe sont souvent identiques. Dès qu’ils existent en tant qu’objets individuels, toutefois, leurs variables et propriétés sont modifiables indépendamment des autres instances. Par exemple, si vous ajoutez trois cases à cocher à un formulaire, chaque objet de case à cocher est une instance de la classe <xref:System.Windows.Forms.CheckBox>. Les objets <xref:System.Windows.Forms.CheckBox> individuels partagent un ensemble commun de caractéristiques et de fonctionnalités (propriétés, variables, procédures et événements) définies par la classe. Toutefois, chacun possède son propre nom, peut être séparément activé et désactivé, et peut être placé dans un autre emplacement sur le formulaire.

## <a name="object-members"></a>Membres de l’objet

Un objet est un élément d’une application, représentant une *instance* d’une classe. Les champs, propriétés, méthodes et événements sont les blocs de construction des objets et constituent leurs *membres*.

### <a name="member-access"></a>Accès aux membres

Vous accédez à un membre d’un objet en spécifiant, dans l’ordre, le nom de la variable objet, un point (`.`) et le nom du membre. L'exemple suivant définit la propriété <xref:System.Windows.Forms.Control.Text%2A> d’un objet <xref:System.Windows.Forms.Label>.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>Liste de membres IntelliSense

IntelliSense répertorie les membres d’une classe lorsque vous appelez son option Liste des membres, par exemple lorsque vous tapez un point (`.`) comme opérateur d’accès au membre. Si vous tapez le point après le nom d’une variable déclarée comme une instance de cette classe, IntelliSense répertorie tous les membres de l’instance et aucun des membres partagés. Si vous tapez le point après le nom de la classe, IntelliSense répertorie tous les membres partagés et aucun des membres de l’instance. Pour plus d'informations, consultez [Using IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Champs et propriétés

Les *propriétés* et les *champs* sont des informations stockées dans un objet. Vous récupérez et définissez leurs valeurs avec des instructions d’assignation de la même façon que vous récupérez et définissez des variables locales dans une procédure. L’exemple suivant récupère la propriété <xref:System.Windows.Forms.Control.Width%2A> et définit la propriété <xref:System.Windows.Forms.Control.ForeColor%2A> d’un objet <xref:System.Windows.Forms.Label>.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Notez qu’un champ est également appelé *variable membre*.

Utilisez les procédures de propriété quand :

- Vous devez contrôler quand et comment une valeur est définie ou récupérée.

- La propriété possède un ensemble bien défini de valeurs qui doivent être validées.

- La définition de la valeur entraîne une modification perceptible de l’état de l’objet, comme une propriété `IsVisible`.

- La définition de la propriété entraîne des modifications d’autres variables internes ou des valeurs d’autres propriétés.

- Un ensemble d’étapes doit être effectué avant que la propriété puisse être définie ou récupérée.

Utilisez les champs quand :

- La valeur est d’un type à validation automatique. Par exemple, une erreur ou la conversion automatique de données se produit si une valeur autre que `True` ou `False` est assignée à une variable `Boolean`.

- N’importe quelle valeur dans la plage prise en charge par le type de données est valide. Cela est vrai pour de nombreuses propriétés du type `Single` ou `Double`.

- La propriété est un type de données `String`, et il n’existe aucune contrainte quant à la taille ou la valeur de la chaîne.

- Pour plus d’informations, consultez [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Méthodes

Une *méthode* correspond à une action qu’un objet peut effectuer. Par exemple, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> est une méthode de l’objet <xref:System.Windows.Forms.ComboBox> qui ajoute une nouvelle entrée à une zone de liste modifiable.

L'exemple suivant montre la méthode <xref:System.Windows.Forms.Timer.Start%2A> d’un objet <xref:System.Windows.Forms.Timer>.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Notez qu’une méthode est simplement une *procédure* qui est exposée par un objet.

Pour plus d’informations, consultez [Procédures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Événements

Un événement est une action reconnue par un objet, par exemple le fait de cliquer sur la souris ou d’appuyer sur une touche, et pour laquelle vous pouvez écrire du code en réponse. Les événements peuvent se produire à la suite d’une action de l’utilisateur ou du code de programme, ou ils peuvent être provoqués par le système. On dit que le code qui signale un événement le *déclenche* et le code qui y répond le *gère*.

Vous pouvez également développer vos propres événements personnalisés pour qu’ils soient déclenchés par vos objets et gérés par d’autres objets. Pour plus d'informations, consultez [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Membres d’instance et membres partagés

Lorsque vous créez un objet à partir d’une classe, le résultat est une instance de cette classe. Les membres qui ne sont pas déclarés avec le mot clé [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) sont des *membres d’instance*, qui appartiennent strictement à cette instance spécifique. Un membre d’instance dans une instance est indépendant du même membre dans une autre instance de la même classe. Par exemple, une variable de membre d’instance peut avoir des valeurs différentes dans différentes instances.

Les membres déclarés avec le mot clé `Shared` sont des *membres partagés*, qui appartiennent à la classe dans son ensemble et non à une instance particulière. Un membre partagé n’existe qu’une seule fois, quel que soit le nombre d’instances de sa classe que vous créez, ou même si vous ne créez aucune instance. Une variable de membre partagé, par exemple, n’a qu’une seule valeur, qui est disponible à tout le code qui peut accéder à la classe.

#### <a name="accessing-nonshared-members"></a>Accès aux membres non partagés

##### <a name="to-access-a-nonshared-member-of-an-object"></a>Pour accéder à un membre non partagé d’un objet

1. Assurez-vous que l’objet a été créé à partir de sa classe et assigné à une variable objet.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. Dans l’instruction qui accède au membre, faites suivre le nom de la variable objet de *l’opérateur member-access* (`.`), puis du nom du membre.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Accès aux membres partagés

##### <a name="to-access-a-shared-member-of-an-object"></a>Pour accéder à un membre partagé d’un objet

- Faites suivre le nom de classe de *l’opérateur member-access* (`.`), puis du nom du membre. Vous devez toujours accéder à un membre `Shared` de l’objet directement via le nom de la classe.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- Si vous avez déjà créé un objet à partir de la classe, vous pouvez également accéder à un membre `Shared` à l’aide de la variable de l’objet.

### <a name="differences-between-classes-and-modules"></a>Différences entre les classes et les modules

La principale différence entre les classes et les modules est que les classes peuvent être instanciées en tant qu’objets mais pas les modules standard. Étant donné qu’il n’existe qu’une seule copie des données d’un module standard, quand une partie de votre programme transforme une variable publique dans un module standard, toute autre partie du programme reçoit la même valeur si elle lit ensuite cette variable. En revanche, les données d’objet existent séparément pour chaque objet instancié. Une autre différence est que, contrairement aux modules standard, les classes peuvent implémenter des interfaces.

> [!NOTE]
> Lorsque le modificateur `Shared` est appliqué à un membre de la classe, il est associé à la classe elle-même au lieu d’une instance particulière dans la classe. Le membre est accessible directement via le nom de la classe, de la même façon que les membres du module.

Les classes et les modules utilisent également des portées différentes pour leurs membres. Les membres définis dans une classe ont comme portée une instance spécifique de la classe et existent uniquement pendant la durée de vie de l’objet. Pour accéder aux membres de la classe en dehors d’une classe, vous devez utiliser des noms de domaine complets sous la forme *Objet*.*Membre*.

En revanche, les membres déclarés dans un module sont publiquement accessibles par défaut et sont accessibles par tout code qui peut accéder au module. Cela signifie que les variables dans un module standard sont effectivement des variables globales puisqu’elles sont visibles n’importe où dans votre projet, et qu’elles existent pendant la durée de vie du programme.

## <a name="reusing-classes-and-objects"></a>Réutilisation des classes et des objets

Les objets vous permettent de déclarer des variables et des procédures une seule fois, puis de les réutiliser à chaque fois que cela est nécessaire. Par exemple, si vous souhaitez ajouter un vérificateur d’orthographe à une application, vous pouvez définir toutes les variables et fonctions de support pour fournir la fonctionnalité de vérification orthographique. Si vous créez votre vérificateur d’orthographe en tant que classe, vous pouvez ensuite le réutiliser dans d’autres applications en ajoutant une référence à l’assembly compilé. Mieux encore, vous pouvez vous épargner du travail à l’aide d’une classe de vérificateur d’orthographe que quelqu’un d’autre a déjà développé.

Le .NET Framework fournit de nombreux exemples de composants qui peuvent être utilisés. L’exemple suivant utilise la classe <xref:System.TimeZone> dans l’espace de noms <xref:System>. <xref:System.TimeZone> fournit des membres qui vous permettent de récupérer des informations sur le fuseau horaire de l’ordinateur actuel.

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

Dans l’exemple précédent, la première [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) déclare une variable objet de type <xref:System.TimeZone> et lui attribue un objet <xref:System.TimeZone> retourné par la propriété <xref:System.TimeZone.CurrentTimeZone%2A>.

## <a name="relationships-among-objects"></a>Relations entre les objets

Les objets peuvent être liés entre eux de plusieurs façons. Les principales sortes de relations sont *hiérarchique* et *imbrication*.

### <a name="hierarchical-relationship"></a>Relation hiérarchique

Lorsque les classes sont dérivées de classes plus fondamentales, elles ont une *relation hiérarchique*. Les hiérarchies de classes sont utiles lors de la description des éléments qui représentent un sous-type d’une classe plus générale.

Dans l’exemple suivant, supposons que vous souhaitez définir un type spécial de <xref:System.Windows.Forms.Button> qui agit comme un <xref:System.Windows.Forms.Button> normal, mais expose également une méthode qui inverse les couleurs de premier plan et d’arrière-plan.

#### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Pour définir une classe dérivée d’une classe déjà existante

1. Utilisez [l’instruction Class](../../../../visual-basic/language-reference/statements/class-statement.md) pour définir une classe à partir de laquelle créer l’objet dont vous avez besoin.

   ```vb
   Public Class reversibleButton
   ```

   Vérifiez qu’une instruction `End Class` suit la dernière ligne de code dans votre classe. Par défaut, l’environnement de développement intégré (IDE) génère automatiquement une `End Class` lorsque vous entrez une instruction `Class`.

2. Faites suivre immédiatement l’instruction `Class` d’une [instruction Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md). Spécifiez la classe dont dérive la nouvelle classe.

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   Votre nouvelle classe hérite de tous les membres définis par la classe de base.

3. Ajoutez le code pour les membres supplémentaires exposés par votre classe dérivée. Par exemple, vous pouvez ajouter une méthode `reverseColors` et votre classe dérivée peut se présenter comme suit :

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   Si vous créez un objet à partir de la classe `reversibleButton`, il peut accéder à tous les membres de la classe <xref:System.Windows.Forms.Button>, ainsi qu’à la méthode `reverseColors` et tout autre nouveau membre que vous définissez sur `reversibleButton`.

Les classes dérivées héritent des membres de la classe que dont ils dépendent, ce qui vous permet d’ajouter de la complexité au fur et à mesure que vous progressez dans la hiérarchie. Pour plus d’informations, consultez [Concepts de base de l’héritage](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

### <a name="compiling-the-code"></a>Compilation du code

Assurez-vous que le compilateur peut accéder à la classe à partir de laquelle vous souhaitez dériver votre nouvelle classe. Cela peut signifier qualifier complètement son nom, comme dans l’exemple précédent ou identifier son espace de noms dans une [instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Si la classe se trouve dans un autre projet, vous devrez peut-être ajouter une référence à ce projet. Pour plus d’informations, consultez [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Relation d'imbrication

Les objets peuvent également être liés par une *relation d’imbrication*. Les objets conteneur encapsulent de manière logique d’autres objets. Par exemple, l’objet <xref:System.OperatingSystem> contient de manière logique un objet <xref:System.Version>, qu’il retourne via sa propriété <xref:System.OperatingSystem.Version%2A>. Notez que l’objet conteneur ne contient physiquement aucun autre objet.

#### <a name="collections"></a>Collections

Un type particulier de relation d’imbrication d’objet est représenté par les *collections*. Les collections sont des groupes d’objets similaires qui peuvent être énumérés. Visual Basic prend en charge une syntaxe spécifique dans le [... Instruction suivante](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) qui vous permet d’itérer au sein des éléments d’une collection. En outre, les collections vous permettent souvent d’utiliser un <xref:Microsoft.VisualBasic.Collection.Item%2A> pour récupérer des éléments à l’aide de leur index ou en les associant à une chaîne unique. Les collections peuvent être plus faciles à utiliser que les tableaux car elles vous permettent d’ajouter ou de supprimer des éléments sans utiliser d’index. En raison de leur simplicité d’utilisation, les collections sont souvent utilisées pour stocker les formulaires et les commandes.

## <a name="related-topics"></a>Rubriques connexes

[Procédure pas à pas : définition de Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)\
Fournit une description pas à pas pour la création d’une classe.

[Propriétés et méthodes surchargées](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)\
Propriétés et méthodes surchargées

[Éléments fondamentaux de l’héritage](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)\
Présente les modificateurs d’héritage, la substitution des propriétés et des méthodes, MyClass et MyBase.

[Durée de vie d’un objet : création et destruction des objets](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)\
Explique comment créer et supprimer des instances de classe.

[Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)\
Décrit comment créer et utiliser les types anonymes, qui vous permettent de créer des objets sans écrire de définition de classe pour le type de données.

[Initialiseurs d’objets : types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)\
Décrit les initialiseurs d’objets, qui servent à créer des instances de types nommés et anonymes à l’aide d’une expression unique.

[Comment : déduire les types et les noms de propriétés dans des déclarations de type anonyme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\
Explique comment déduire les types et les noms de propriétés dans des déclarations de types anonymes. Fournit des exemples d’inférence possible et impossible.
