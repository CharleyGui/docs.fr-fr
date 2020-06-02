---
title: Objets et classes
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 10e257a1cbc8778565a9838aeef423522f9d2970
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290615"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="4eb30-102">Objets et classes dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4eb30-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="4eb30-103">Un *objet* est une combinaison de code et de données qui peuvent être traités en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="4eb30-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="4eb30-104">Un objet peut être une partie d’une application, comme une commande ou un formulaire.</span><span class="sxs-lookup"><span data-stu-id="4eb30-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="4eb30-105">Une application entière peut également être un objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-105">An entire application can also be an object.</span></span>

<span data-ttu-id="4eb30-106">Lorsque vous créez une application dans Visual Basic, vous travaillez constamment avec des objets.</span><span class="sxs-lookup"><span data-stu-id="4eb30-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="4eb30-107">Vous pouvez utiliser les objets fournis par Visual Basic, tels que les contrôles, les formulaires et les objets d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="4eb30-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="4eb30-108">Vous pouvez également utiliser des objets d’autres applications au sein de votre application Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4eb30-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="4eb30-109">Vous pouvez même créer vos propres objets et définir des propriétés et des méthodes supplémentaires pour ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="4eb30-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="4eb30-110">Les objets se comportent comme des blocs de construction préfabriqués : ils vous permettent d’écrire un fragment de code une seule fois et de le réutiliser maintes fois.</span><span class="sxs-lookup"><span data-stu-id="4eb30-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="4eb30-111">Cette rubrique présente les objets en détail.</span><span class="sxs-lookup"><span data-stu-id="4eb30-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="4eb30-112">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="4eb30-112">Objects and classes</span></span>

<span data-ttu-id="4eb30-113">Chaque objet de Visual Basic est défini par une *classe*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="4eb30-114">Une classe décrit les variables, les propriétés, les procédures et les événements d’un objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="4eb30-115">Les objets sont des instances de classes. Vous pouvez créer autant d’objets que nécessaire dès que vous avez défini une classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="4eb30-116">Pour comprendre la relation entre un objet et sa classe, prenez l’exemple des emporte-pièces et des biscuits.</span><span class="sxs-lookup"><span data-stu-id="4eb30-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="4eb30-117">L’emporte-pièce est la classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-117">The cookie cutter is the class.</span></span> <span data-ttu-id="4eb30-118">Il définit les caractéristiques de chaque biscuit, par exemple la taille et la forme.</span><span class="sxs-lookup"><span data-stu-id="4eb30-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="4eb30-119">La classe est utilisée pour créer des objets.</span><span class="sxs-lookup"><span data-stu-id="4eb30-119">The class is used to create objects.</span></span> <span data-ttu-id="4eb30-120">Les objets sont les biscuits.</span><span class="sxs-lookup"><span data-stu-id="4eb30-120">The objects are the cookies.</span></span>

<span data-ttu-id="4eb30-121">Vous devez créer un objet avant de pouvoir accéder à ses membres, à l’exception des [`Shared`](../../../language-reference/modifiers/shared.md) membres qui sont accessibles sans objet de la classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-121">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="4eb30-122">Créer un objet à partir d’une classe</span><span class="sxs-lookup"><span data-stu-id="4eb30-122">Create an object from a class</span></span>

1. <span data-ttu-id="4eb30-123">Déterminez la classe à partir de laquelle vous souhaitez créer un objet, ou définissez votre propre classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-123">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="4eb30-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4eb30-124">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="4eb30-125">Écrivez une [instruction Dim](../../../language-reference/statements/dim-statement.md) pour créer une variable à laquelle vous pouvez assigner une instance de classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-125">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="4eb30-126">La variable doit être du type de la classe souhaitée.</span><span class="sxs-lookup"><span data-stu-id="4eb30-126">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="4eb30-127">Ajoutez le mot clé [New Operator](../../../language-reference/operators/new-operator.md) pour initialiser la variable à une nouvelle instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-127">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="4eb30-128">Vous pouvez désormais accéder aux membres de la classe par le biais de la variable d’objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-128">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="4eb30-129">Si possible, vous devez déclarer la variable comme étant du type de classe que vous avez l’intention de lui attribuer.</span><span class="sxs-lookup"><span data-stu-id="4eb30-129">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="4eb30-130">Il s’agit de la *liaison anticipée*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-130">This is called *early binding*.</span></span> <span data-ttu-id="4eb30-131">Si vous ne connaissez pas le type de classe au moment de la compilation, vous pouvez utiliser la *liaison tardive* en déclarant la variable comme étant de [type de données Object](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="4eb30-131">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="4eb30-132">Toutefois, la liaison tardive peut ralentir les performances et limiter l’accès aux membres de l’objet de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4eb30-132">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="4eb30-133">Pour plus d’informations, consultez [Déclaration des variables objets](../variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4eb30-133">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="4eb30-134">Instances multiples</span><span class="sxs-lookup"><span data-stu-id="4eb30-134">Multiple instances</span></span>

<span data-ttu-id="4eb30-135">Les objets nouvellement créés à partir d’une classe sont souvent identiques.</span><span class="sxs-lookup"><span data-stu-id="4eb30-135">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="4eb30-136">Dès qu’ils existent en tant qu’objets individuels, toutefois, leurs variables et propriétés sont modifiables indépendamment des autres instances.</span><span class="sxs-lookup"><span data-stu-id="4eb30-136">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="4eb30-137">Par exemple, si vous ajoutez trois cases à cocher à un formulaire, chaque objet de case à cocher est une instance de la classe <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="4eb30-137">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="4eb30-138">Les objets <xref:System.Windows.Forms.CheckBox> individuels partagent un ensemble commun de caractéristiques et de fonctionnalités (propriétés, variables, procédures et événements) définies par la classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-138">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="4eb30-139">Toutefois, chacun possède son propre nom, peut être séparément activé et désactivé, et peut être placé dans un autre emplacement sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="4eb30-139">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="4eb30-140">Membres de l’objet</span><span class="sxs-lookup"><span data-stu-id="4eb30-140">Object members</span></span>

<span data-ttu-id="4eb30-141">Un objet est un élément d’une application, représentant une *instance* d’une classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-141">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="4eb30-142">Les champs, propriétés, méthodes et événements sont les blocs de construction des objets et constituent leurs *membres*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-142">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="4eb30-143">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="4eb30-143">Member Access</span></span>

<span data-ttu-id="4eb30-144">Vous accédez à un membre d’un objet en spécifiant, dans l’ordre, le nom de la variable objet, un point (`.`) et le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="4eb30-144">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="4eb30-145">L'exemple suivant définit la propriété <xref:System.Windows.Forms.Control.Text%2A> d’un objet <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="4eb30-145">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="4eb30-146">Liste de membres IntelliSense</span><span class="sxs-lookup"><span data-stu-id="4eb30-146">IntelliSense listing of members</span></span>

<span data-ttu-id="4eb30-147">IntelliSense répertorie les membres d’une classe lorsque vous appelez son option Liste des membres, par exemple lorsque vous tapez un point (`.`) comme opérateur d’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="4eb30-147">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="4eb30-148">Si vous tapez le point après le nom d’une variable déclarée comme une instance de cette classe, IntelliSense répertorie tous les membres de l’instance et aucun des membres partagés.</span><span class="sxs-lookup"><span data-stu-id="4eb30-148">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="4eb30-149">Si vous tapez le point après le nom de la classe, IntelliSense répertorie tous les membres partagés et aucun des membres de l’instance.</span><span class="sxs-lookup"><span data-stu-id="4eb30-149">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="4eb30-150">Pour plus d’informations, consultez [Utilisation d’IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="4eb30-150">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="4eb30-151">Champs et propriétés</span><span class="sxs-lookup"><span data-stu-id="4eb30-151">Fields and properties</span></span>

<span data-ttu-id="4eb30-152">Les *propriétés* et les *champs* sont des informations stockées dans un objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-152">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="4eb30-153">Vous récupérez et définissez leurs valeurs avec des instructions d’assignation de la même façon que vous récupérez et définissez des variables locales dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="4eb30-153">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="4eb30-154">L’exemple suivant récupère la propriété <xref:System.Windows.Forms.Control.Width%2A> et définit la propriété <xref:System.Windows.Forms.Control.ForeColor%2A> d’un objet <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="4eb30-154">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="4eb30-155">Notez qu’un champ est également appelé *variable membre*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-155">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="4eb30-156">Utilisez les procédures de propriété quand :</span><span class="sxs-lookup"><span data-stu-id="4eb30-156">Use property procedures when:</span></span>

- <span data-ttu-id="4eb30-157">Vous devez contrôler quand et comment une valeur est définie ou récupérée.</span><span class="sxs-lookup"><span data-stu-id="4eb30-157">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="4eb30-158">La propriété possède un ensemble bien défini de valeurs qui doivent être validées.</span><span class="sxs-lookup"><span data-stu-id="4eb30-158">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="4eb30-159">La définition de la valeur entraîne une modification perceptible de l’état de l’objet, comme une propriété `IsVisible`.</span><span class="sxs-lookup"><span data-stu-id="4eb30-159">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="4eb30-160">La définition de la propriété entraîne des modifications d’autres variables internes ou des valeurs d’autres propriétés.</span><span class="sxs-lookup"><span data-stu-id="4eb30-160">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="4eb30-161">Un ensemble d’étapes doit être effectué avant que la propriété puisse être définie ou récupérée.</span><span class="sxs-lookup"><span data-stu-id="4eb30-161">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="4eb30-162">Utilisez les champs quand :</span><span class="sxs-lookup"><span data-stu-id="4eb30-162">Use fields when:</span></span>

- <span data-ttu-id="4eb30-163">La valeur est d’un type à validation automatique.</span><span class="sxs-lookup"><span data-stu-id="4eb30-163">The value is of a self-validating type.</span></span> <span data-ttu-id="4eb30-164">Par exemple, une erreur ou la conversion automatique de données se produit si une valeur autre que `True` ou `False` est assignée à une variable `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="4eb30-164">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="4eb30-165">N’importe quelle valeur dans la plage prise en charge par le type de données est valide.</span><span class="sxs-lookup"><span data-stu-id="4eb30-165">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="4eb30-166">Cela est vrai pour de nombreuses propriétés du type `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="4eb30-166">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="4eb30-167">La propriété est un type de données `String`, et il n’existe aucune contrainte quant à la taille ou la valeur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="4eb30-167">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="4eb30-168">Pour plus d’informations, consultez [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4eb30-168">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="4eb30-169">Conservez toujours les champs non constants privés.</span><span class="sxs-lookup"><span data-stu-id="4eb30-169">Always keep the non-constant fields private.</span></span> <span data-ttu-id="4eb30-170">Si vous souhaitez le rendre public, utilisez une propriété à la place.</span><span class="sxs-lookup"><span data-stu-id="4eb30-170">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="4eb30-171">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4eb30-171">Methods</span></span>

<span data-ttu-id="4eb30-172">Une *méthode* est une action que peut effectuer un objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-172">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="4eb30-173">Par exemple, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> est une méthode de l’objet <xref:System.Windows.Forms.ComboBox> qui ajoute une nouvelle entrée à une zone de liste modifiable.</span><span class="sxs-lookup"><span data-stu-id="4eb30-173">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="4eb30-174">L'exemple suivant montre la méthode <xref:System.Windows.Forms.Timer.Start%2A> d’un objet <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="4eb30-174">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="4eb30-175">Notez qu’une méthode est simplement une *procédure* qui est exposée par un objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-175">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="4eb30-176">Pour plus d’informations, consultez [Procédures](../procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="4eb30-176">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="4eb30-177">Événements</span><span class="sxs-lookup"><span data-stu-id="4eb30-177">Events</span></span>

<span data-ttu-id="4eb30-178">Un événement est une action reconnue par un objet, par exemple le fait de cliquer sur la souris ou d’appuyer sur une touche, et pour laquelle vous pouvez écrire du code en réponse.</span><span class="sxs-lookup"><span data-stu-id="4eb30-178">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="4eb30-179">Les événements peuvent se produire à la suite d’une action de l’utilisateur ou du code de programme, ou ils peuvent être provoqués par le système.</span><span class="sxs-lookup"><span data-stu-id="4eb30-179">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="4eb30-180">On dit que le code qui signale un événement le *déclenche* et le code qui y répond le *gère*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-180">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="4eb30-181">Vous pouvez également développer vos propres événements personnalisés pour qu’ils soient déclenchés par vos objets et gérés par d’autres objets.</span><span class="sxs-lookup"><span data-stu-id="4eb30-181">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="4eb30-182">Pour plus d’informations, consultez [Événements](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="4eb30-182">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="4eb30-183">Membres d’instance et membres partagés</span><span class="sxs-lookup"><span data-stu-id="4eb30-183">Instance members and shared members</span></span>

<span data-ttu-id="4eb30-184">Lorsque vous créez un objet à partir d’une classe, le résultat est une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-184">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="4eb30-185">Les membres qui ne sont pas déclarés avec le mot clé [Shared](../../../language-reference/modifiers/shared.md) sont des *membres d’instance*, qui appartiennent strictement à cette instance spécifique.</span><span class="sxs-lookup"><span data-stu-id="4eb30-185">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="4eb30-186">Un membre d’instance dans une instance est indépendant du même membre dans une autre instance de la même classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-186">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="4eb30-187">Par exemple, une variable de membre d’instance peut avoir des valeurs différentes dans différentes instances.</span><span class="sxs-lookup"><span data-stu-id="4eb30-187">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="4eb30-188">Les membres déclarés avec le mot clé `Shared` sont des *membres partagés*, qui appartiennent à la classe dans son ensemble et non à une instance particulière.</span><span class="sxs-lookup"><span data-stu-id="4eb30-188">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="4eb30-189">Un membre partagé n’existe qu’une seule fois, quel que soit le nombre d’instances de sa classe que vous créez, ou même si vous ne créez aucune instance.</span><span class="sxs-lookup"><span data-stu-id="4eb30-189">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="4eb30-190">Une variable de membre partagé, par exemple, n’a qu’une seule valeur, qui est disponible à tout le code qui peut accéder à la classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-190">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="4eb30-191">Accès aux membres non partagés</span><span class="sxs-lookup"><span data-stu-id="4eb30-191">Accessing non-shared members</span></span>

1. <span data-ttu-id="4eb30-192">Assurez-vous que l’objet a été créé à partir de sa classe et assigné à une variable objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-192">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="4eb30-193">Dans l’instruction qui accède au membre, suivez le nom de la variable objet avec l' *opérateur d’accès aux membres* ( `.` ), puis le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="4eb30-193">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="4eb30-194">Accès aux membres partagés</span><span class="sxs-lookup"><span data-stu-id="4eb30-194">Accessing shared members</span></span>

- <span data-ttu-id="4eb30-195">Suivez le nom de la classe avec l' *opérateur d’accès aux membres* ( `.` ), puis le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="4eb30-195">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="4eb30-196">Vous devez toujours accéder à un membre `Shared` de l’objet directement via le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-196">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="4eb30-197">Si vous avez déjà créé un objet à partir de la classe, vous pouvez également accéder à un membre `Shared` à l’aide de la variable de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-197">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="4eb30-198">Différences entre les classes et les modules</span><span class="sxs-lookup"><span data-stu-id="4eb30-198">Differences between classes and modules</span></span>

<span data-ttu-id="4eb30-199">La principale différence entre les classes et les modules est que les classes peuvent être instanciées en tant qu’objets mais pas les modules standard.</span><span class="sxs-lookup"><span data-stu-id="4eb30-199">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="4eb30-200">Étant donné qu’il n’existe qu’une seule copie des données d’un module standard, quand une partie de votre programme transforme une variable publique dans un module standard, toute autre partie du programme reçoit la même valeur si elle lit ensuite cette variable.</span><span class="sxs-lookup"><span data-stu-id="4eb30-200">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="4eb30-201">En revanche, les données d’objet existent séparément pour chaque objet instancié.</span><span class="sxs-lookup"><span data-stu-id="4eb30-201">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="4eb30-202">Une autre différence est que, contrairement aux modules standard, les classes peuvent implémenter des interfaces.</span><span class="sxs-lookup"><span data-stu-id="4eb30-202">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="4eb30-203">Si une classe est marquée avec le modificateur [MustInherit](../../../language-reference/modifiers/mustinherit.md) , elle ne peut pas être instanciée directement.</span><span class="sxs-lookup"><span data-stu-id="4eb30-203">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="4eb30-204">Toutefois, il est toujours différent d’un module, car il peut être hérité alors que les modules ne peuvent pas être hérités.</span><span class="sxs-lookup"><span data-stu-id="4eb30-204">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="4eb30-205">Lorsque le modificateur `Shared` est appliqué à un membre de la classe, il est associé à la classe elle-même au lieu d’une instance particulière dans la classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-205">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="4eb30-206">Le membre est accessible directement via le nom de la classe, de la même façon que les membres du module.</span><span class="sxs-lookup"><span data-stu-id="4eb30-206">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="4eb30-207">Les classes et les modules utilisent également des portées différentes pour leurs membres.</span><span class="sxs-lookup"><span data-stu-id="4eb30-207">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="4eb30-208">Les membres définis dans une classe ont comme portée une instance spécifique de la classe et existent uniquement pendant la durée de vie de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-208">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="4eb30-209">Pour accéder aux membres de la classe en dehors d’une classe, vous devez utiliser des noms de domaine complets sous la forme *Objet*.*Membre*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-209">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="4eb30-210">En revanche, les membres déclarés dans un module sont publiquement accessibles par défaut et sont accessibles par tout code qui peut accéder au module.</span><span class="sxs-lookup"><span data-stu-id="4eb30-210">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="4eb30-211">Cela signifie que les variables dans un module standard sont effectivement des variables globales puisqu’elles sont visibles n’importe où dans votre projet, et qu’elles existent pendant la durée de vie du programme.</span><span class="sxs-lookup"><span data-stu-id="4eb30-211">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="4eb30-212">Réutilisation des classes et des objets</span><span class="sxs-lookup"><span data-stu-id="4eb30-212">Reusing classes and objects</span></span>

<span data-ttu-id="4eb30-213">Les objets vous permettent de déclarer des variables et des procédures une seule fois, puis de les réutiliser à chaque fois que cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="4eb30-213">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="4eb30-214">Par exemple, si vous souhaitez ajouter un vérificateur d’orthographe à une application, vous pouvez définir toutes les variables et fonctions de support pour fournir la fonctionnalité de vérification orthographique.</span><span class="sxs-lookup"><span data-stu-id="4eb30-214">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="4eb30-215">Si vous créez votre vérificateur d’orthographe en tant que classe, vous pouvez ensuite le réutiliser dans d’autres applications en ajoutant une référence à l’assembly compilé.</span><span class="sxs-lookup"><span data-stu-id="4eb30-215">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="4eb30-216">Mieux encore, vous pouvez vous épargner du travail à l’aide d’une classe de vérificateur d’orthographe que quelqu’un d’autre a déjà développé.</span><span class="sxs-lookup"><span data-stu-id="4eb30-216">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="4eb30-217">.NET fournit de nombreux exemples de composants qui peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="4eb30-217">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="4eb30-218">L’exemple suivant utilise la classe <xref:System.TimeZone> dans l’espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="4eb30-218">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="4eb30-219"><xref:System.TimeZone> fournit des membres qui vous permettent de récupérer des informations sur le fuseau horaire de l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="4eb30-219"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="4eb30-220">Dans l’exemple précédent, la première [instruction Dim](../../../language-reference/statements/dim-statement.md) déclare une variable objet de type <xref:System.TimeZone> et lui attribue un objet <xref:System.TimeZone> retourné par la propriété <xref:System.TimeZone.CurrentTimeZone%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb30-220">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="4eb30-221">Relations entre les objets</span><span class="sxs-lookup"><span data-stu-id="4eb30-221">Relationships among objects</span></span>

<span data-ttu-id="4eb30-222">Les objets peuvent être liés entre eux de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="4eb30-222">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="4eb30-223">Les principales sortes de relations sont *hiérarchique* et *imbrication*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-223">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="4eb30-224">Relation hiérarchique</span><span class="sxs-lookup"><span data-stu-id="4eb30-224">Hierarchical relationship</span></span>

<span data-ttu-id="4eb30-225">Lorsque les classes sont dérivées de classes plus fondamentales, elles ont une *relation hiérarchique*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-225">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="4eb30-226">Les hiérarchies de classes sont utiles lors de la description des éléments qui représentent un sous-type d’une classe plus générale.</span><span class="sxs-lookup"><span data-stu-id="4eb30-226">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="4eb30-227">Dans l’exemple suivant, supposons que vous souhaitez définir un type spécial de <xref:System.Windows.Forms.Button> qui agit comme un <xref:System.Windows.Forms.Button> normal, mais expose également une méthode qui inverse les couleurs de premier plan et d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="4eb30-227">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="4eb30-228">Définir une classe dérivée d’une classe déjà existante</span><span class="sxs-lookup"><span data-stu-id="4eb30-228">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="4eb30-229">Utilisez [l’instruction Class](../../../language-reference/statements/class-statement.md) pour définir une classe à partir de laquelle créer l’objet dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="4eb30-229">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="4eb30-230">Vérifiez qu’une instruction `End Class` suit la dernière ligne de code dans votre classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-230">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="4eb30-231">Par défaut, l’environnement de développement intégré (IDE) génère automatiquement une `End Class` lorsque vous entrez une instruction `Class`.</span><span class="sxs-lookup"><span data-stu-id="4eb30-231">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="4eb30-232">Faites suivre immédiatement l’instruction `Class` d’une [instruction Inherits](../../../language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4eb30-232">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="4eb30-233">Spécifiez la classe dont dérive la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-233">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="4eb30-234">Votre nouvelle classe hérite de tous les membres définis par la classe de base.</span><span class="sxs-lookup"><span data-stu-id="4eb30-234">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="4eb30-235">Ajoutez le code pour les membres supplémentaires exposés par votre classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="4eb30-235">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="4eb30-236">Par exemple, vous pouvez ajouter une méthode `ReverseColors` et votre classe dérivée peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="4eb30-236">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="4eb30-237">Si vous créez un objet à partir de la `ReversibleButton` classe, il peut accéder à tous les membres de la <xref:System.Windows.Forms.Button> classe, ainsi qu’à la `ReverseColors` méthode et à tout autre nouveau membre que vous définissez dans `ReversibleButton` .</span><span class="sxs-lookup"><span data-stu-id="4eb30-237">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="4eb30-238">Les classes dérivées héritent des membres de la classe que dont ils dépendent, ce qui vous permet d’ajouter de la complexité au fur et à mesure que vous progressez dans la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="4eb30-238">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="4eb30-239">Pour plus d’informations, consultez [Concepts de base de l’héritage](inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="4eb30-239">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="4eb30-240">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="4eb30-240">Compile the code</span></span>

<span data-ttu-id="4eb30-241">Assurez-vous que le compilateur peut accéder à la classe à partir de laquelle vous souhaitez dériver votre nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-241">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="4eb30-242">Cela peut signifier qualifier complètement son nom, comme dans l’exemple précédent ou identifier son espace de noms dans une [instruction Imports (espace de noms et type .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="4eb30-242">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="4eb30-243">Si la classe se trouve dans un autre projet, vous devrez peut-être ajouter une référence à ce projet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-243">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="4eb30-244">Pour plus d’informations, consultez [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="4eb30-244">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="4eb30-245">Relation d'imbrication</span><span class="sxs-lookup"><span data-stu-id="4eb30-245">Containment relationship</span></span>

<span data-ttu-id="4eb30-246">Les objets peuvent également être liés par une *relation d’imbrication*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-246">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="4eb30-247">Les objets conteneur encapsulent de manière logique d’autres objets.</span><span class="sxs-lookup"><span data-stu-id="4eb30-247">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="4eb30-248">Par exemple, l’objet <xref:System.OperatingSystem> contient de manière logique un objet <xref:System.Version>, qu’il retourne via sa propriété <xref:System.OperatingSystem.Version%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb30-248">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="4eb30-249">Notez que l’objet conteneur ne contient physiquement aucun autre objet.</span><span class="sxs-lookup"><span data-stu-id="4eb30-249">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="4eb30-250">Regroupements</span><span class="sxs-lookup"><span data-stu-id="4eb30-250">Collections</span></span>

<span data-ttu-id="4eb30-251">Un type particulier de relation d’imbrication d’objet est représenté par les *collections*.</span><span class="sxs-lookup"><span data-stu-id="4eb30-251">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="4eb30-252">Les collections sont des groupes d’objets similaires qui peuvent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="4eb30-252">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="4eb30-253">Visual Basic prend en charge une syntaxe spécifique dans le [... Instruction suivante](../../../language-reference/statements/for-each-next-statement.md) qui vous permet d’itérer au sein des éléments d’une collection.</span><span class="sxs-lookup"><span data-stu-id="4eb30-253">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="4eb30-254">En outre, les collections vous permettent souvent d’utiliser un <xref:Microsoft.VisualBasic.Collection.Item%2A> pour récupérer des éléments à l’aide de leur index ou en les associant à une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="4eb30-254">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="4eb30-255">Les collections peuvent être plus faciles à utiliser que les tableaux car elles vous permettent d’ajouter ou de supprimer des éléments sans utiliser d’index.</span><span class="sxs-lookup"><span data-stu-id="4eb30-255">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="4eb30-256">En raison de leur simplicité d’utilisation, les collections sont souvent utilisées pour stocker les formulaires et les commandes.</span><span class="sxs-lookup"><span data-stu-id="4eb30-256">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="4eb30-257">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="4eb30-257">Related topics</span></span>

<span data-ttu-id="4eb30-258">[Procédure pas à pas : définition de classes](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="4eb30-258">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="4eb30-259">Fournit une description pas à pas pour la création d’une classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-259">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="4eb30-260">[Propriétés et méthodes surchargées](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="4eb30-260">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="4eb30-261">Propriétés et méthodes surchargées</span><span class="sxs-lookup"><span data-stu-id="4eb30-261">Overloaded Properties and Methods</span></span>

<span data-ttu-id="4eb30-262">[Notions de base de l’héritage](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="4eb30-262">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="4eb30-263">Présente les modificateurs d’héritage, la substitution des propriétés et des méthodes, MyClass et MyBase.</span><span class="sxs-lookup"><span data-stu-id="4eb30-263">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="4eb30-264">[Durée de vie d’un objet : création et destruction des objets](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="4eb30-264">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="4eb30-265">Explique comment créer et supprimer des instances de classe.</span><span class="sxs-lookup"><span data-stu-id="4eb30-265">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="4eb30-266">[Types anonymes](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="4eb30-266">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="4eb30-267">Décrit comment créer et utiliser les types anonymes, qui vous permettent de créer des objets sans écrire de définition de classe pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="4eb30-267">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="4eb30-268">[Initialiseurs d’objets : types nommés et anonymes](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="4eb30-268">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="4eb30-269">Décrit les initialiseurs d’objets, qui servent à créer des instances de types nommés et anonymes à l’aide d’une expression unique.</span><span class="sxs-lookup"><span data-stu-id="4eb30-269">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="4eb30-270">[Comment : déduire les types et les noms de propriétés dans des déclarations de type anonymes](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="4eb30-270">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="4eb30-271">Explique comment déduire les types et les noms de propriétés dans des déclarations de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="4eb30-271">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="4eb30-272">Fournit des exemples d’inférence possible et impossible.</span><span class="sxs-lookup"><span data-stu-id="4eb30-272">Provides examples of successful and unsuccessful inference.</span></span>
