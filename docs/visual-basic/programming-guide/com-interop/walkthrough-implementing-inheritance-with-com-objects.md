---
title: 'Procédure pas à pas : Implémentation de l’héritage avec les objets COM'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: bdb891e1a150f0d7b79aefcc3db1f18dc8e84be4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396725"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="11ddc-102">Procédure pas à pas : implémentation de l'héritage avec les objets COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11ddc-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>

<span data-ttu-id="11ddc-103">Vous pouvez dériver des classes Visual Basic à partir de `Public` classes d’objets com, y compris celles créées dans les versions antérieures de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="11ddc-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="11ddc-104">Les propriétés et les méthodes des classes héritées d’objets COM peuvent être substituées ou surchargées de la même façon que les propriétés et les méthodes d’une autre classe de base peuvent être substituées ou surchargées.</span><span class="sxs-lookup"><span data-stu-id="11ddc-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="11ddc-105">L’héritage à partir d’objets COM est utile lorsque vous avez une bibliothèque de classes existante que vous ne souhaitez pas recompiler.</span><span class="sxs-lookup"><span data-stu-id="11ddc-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>

<span data-ttu-id="11ddc-106">La procédure suivante indique comment utiliser Visual Basic 6,0 pour créer un objet COM qui contient une classe, puis l’utiliser comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="11ddc-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="11ddc-107">Pour générer l’objet COM utilisé dans cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="11ddc-107">To build the COM object that is used in this walkthrough</span></span>

1. <span data-ttu-id="11ddc-108">Dans Visual Basic 6,0, ouvrez un nouveau projet de DLL ActiveX.</span><span class="sxs-lookup"><span data-stu-id="11ddc-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="11ddc-109">Un projet nommé `Project1` est créé.</span><span class="sxs-lookup"><span data-stu-id="11ddc-109">A project named `Project1` is created.</span></span> <span data-ttu-id="11ddc-110">Il a une classe nommée `Class1` .</span><span class="sxs-lookup"><span data-stu-id="11ddc-110">It has a class named `Class1`.</span></span>

2. <span data-ttu-id="11ddc-111">Dans l' **Explorateur de projets**, cliquez avec le bouton droit sur **Project1**, puis cliquez sur **Propriétés Projet1**.</span><span class="sxs-lookup"><span data-stu-id="11ddc-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="11ddc-112">La boîte de dialogue **Propriétés du projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="11ddc-112">The **Project Properties** dialog box is displayed.</span></span>

3. <span data-ttu-id="11ddc-113">Dans l’onglet **général** de la boîte de dialogue **Propriétés du projet** , modifiez le nom du projet en tapant `ComObject1` dans le champ **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="11ddc-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>

4. <span data-ttu-id="11ddc-114">Dans l' **Explorateur de projets**, cliquez avec le bouton droit sur `Class1` , puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="11ddc-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="11ddc-115">La fenêtre **Propriétés** de la classe s’affiche.</span><span class="sxs-lookup"><span data-stu-id="11ddc-115">The **Properties** window for the class is displayed.</span></span>

5. <span data-ttu-id="11ddc-116">Remplacez la valeur `Name` de la propriété par `MathFunctions` .</span><span class="sxs-lookup"><span data-stu-id="11ddc-116">Change the `Name` property to `MathFunctions`.</span></span>

6. <span data-ttu-id="11ddc-117">Dans l' **Explorateur de projets**, cliquez avec le bouton droit sur `MathFunctions` , puis cliquez sur **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="11ddc-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="11ddc-118">L' **éditeur de code** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="11ddc-118">The **Code Editor** is displayed.</span></span>

7. <span data-ttu-id="11ddc-119">Ajoutez une variable locale pour contenir la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="11ddc-119">Add a local variable to hold the property value:</span></span>

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. <span data-ttu-id="11ddc-120">Ajoutez `Let` des procédures de propriété Property et Property `Get` :</span><span class="sxs-lookup"><span data-stu-id="11ddc-120">Add Property `Let` and Property `Get` property procedures:</span></span>

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. <span data-ttu-id="11ddc-121">Ajoutez une fonction :</span><span class="sxs-lookup"><span data-stu-id="11ddc-121">Add a function:</span></span>

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. <span data-ttu-id="11ddc-122">Créez et inscrivez l’objet COM en cliquant sur **Make ComObject1. dll** dans le menu **file (fichier** ).</span><span class="sxs-lookup"><span data-stu-id="11ddc-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>

    > [!NOTE]
    > <span data-ttu-id="11ddc-123">Bien que vous puissiez également exposer une classe créée avec Visual Basic en tant qu’objet COM, ce n’est pas un vrai objet COM et ne peut pas être utilisé dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="11ddc-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="11ddc-124">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="11ddc-124">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>

## <a name="interop-assemblies"></a><span data-ttu-id="11ddc-125">Assemblys d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="11ddc-125">Interop Assemblies</span></span>

<span data-ttu-id="11ddc-126">Dans la procédure suivante, vous allez créer un assembly d’interopérabilité, qui agit comme un pont entre du code non managé (tel qu’un objet COM) et le code managé utilisé par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11ddc-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="11ddc-127">L’assembly d’interopérabilité créé par Visual Basic gère la plupart des détails de l’utilisation des objets COM, tels que le *marshaling d’interopérabilité*, le processus d’empaquetage des paramètres et les valeurs de retour dans des types de données équivalents lorsqu’ils sont déplacés vers et à partir d’objets com.</span><span class="sxs-lookup"><span data-stu-id="11ddc-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="11ddc-128">La référence dans l’application Visual Basic pointe vers l’assembly d’interopérabilité, et non vers l’objet COM réel.</span><span class="sxs-lookup"><span data-stu-id="11ddc-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="11ddc-129">Pour utiliser un objet COM avec Visual Basic 2005 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="11ddc-129">To use a COM object with Visual Basic 2005 and later versions</span></span>

1. <span data-ttu-id="11ddc-130">Ouvrez un nouveau projet d’application Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="11ddc-130">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="11ddc-131">Dans le menu **projet** , cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="11ddc-131">On the **Project** menu, click **Add Reference**.</span></span>

     <span data-ttu-id="11ddc-132">La boîte de dialogue **Ajouter une référence** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="11ddc-132">The **Add Reference** dialog box is displayed.</span></span>

3. <span data-ttu-id="11ddc-133">Dans l’onglet **com** , double-cliquez `ComObject1` dans la liste **nom du composant** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="11ddc-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>

4. <span data-ttu-id="11ddc-134">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="11ddc-134">On the **Project** menu, click **Add New Item**.</span></span>

     <span data-ttu-id="11ddc-135">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="11ddc-135">The **Add New Item** dialog box is displayed.</span></span>

5. <span data-ttu-id="11ddc-136">Dans le volet **modèles** , cliquez sur **classe**.</span><span class="sxs-lookup"><span data-stu-id="11ddc-136">In the **Templates** pane, click **Class**.</span></span>

     <span data-ttu-id="11ddc-137">Le nom de fichier par défaut, `Class1.vb` , s’affiche dans le champ **nom** .</span><span class="sxs-lookup"><span data-stu-id="11ddc-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="11ddc-138">Modifiez ce champ en MathClass. vb, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="11ddc-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="11ddc-139">Cela crée une classe nommée `MathClass` et affiche son code.</span><span class="sxs-lookup"><span data-stu-id="11ddc-139">This creates a class named `MathClass`, and displays its code.</span></span>

6. <span data-ttu-id="11ddc-140">Ajoutez le code suivant au début de `MathClass` pour hériter de la classe com.</span><span class="sxs-lookup"><span data-stu-id="11ddc-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. <span data-ttu-id="11ddc-141">Surchargez la méthode publique de la classe de base en ajoutant le code suivant à `MathClass` :</span><span class="sxs-lookup"><span data-stu-id="11ddc-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. <span data-ttu-id="11ddc-142">Étendez la classe héritée en ajoutant le code suivant à `MathClass` :</span><span class="sxs-lookup"><span data-stu-id="11ddc-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

<span data-ttu-id="11ddc-143">La nouvelle classe hérite des propriétés de la classe de base dans l’objet COM, surcharge une méthode et définit une nouvelle méthode pour étendre la classe.</span><span class="sxs-lookup"><span data-stu-id="11ddc-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>

### <a name="to-test-the-inherited-class"></a><span data-ttu-id="11ddc-144">Pour tester la classe héritée</span><span class="sxs-lookup"><span data-stu-id="11ddc-144">To test the inherited class</span></span>

1. <span data-ttu-id="11ddc-145">Ajoutez un bouton à votre formulaire de démarrage, puis double-cliquez dessus pour afficher son code.</span><span class="sxs-lookup"><span data-stu-id="11ddc-145">Add a button to your startup form, and then double-click it to view its code.</span></span>

2. <span data-ttu-id="11ddc-146">Dans la procédure du `Click` Gestionnaire d’événements du bouton, ajoutez le code suivant pour créer une instance de `MathClass` et appelez les méthodes surchargées :</span><span class="sxs-lookup"><span data-stu-id="11ddc-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. <span data-ttu-id="11ddc-147">Exécutez le projet en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="11ddc-147">Run the project by pressing F5.</span></span>

<span data-ttu-id="11ddc-148">Lorsque vous cliquez sur le bouton du formulaire, la `AddNumbers` méthode est d’abord appelée avec des `Short` nombres de types de données, et Visual Basic choisit la méthode appropriée à partir de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="11ddc-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="11ddc-149">Le deuxième appel à `AddNumbers` est dirigé vers la méthode de surcharge à partir de `MathClass` .</span><span class="sxs-lookup"><span data-stu-id="11ddc-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="11ddc-150">Le troisième appel appelle la `SubtractNumbers` méthode, qui étend la classe.</span><span class="sxs-lookup"><span data-stu-id="11ddc-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="11ddc-151">La propriété de la classe de base est définie et la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="11ddc-151">The property in the base class is set, and the value is displayed.</span></span>

## <a name="next-steps"></a><span data-ttu-id="11ddc-152">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="11ddc-152">Next Steps</span></span>

<span data-ttu-id="11ddc-153">Vous avez peut-être remarqué que la fonction surchargée `AddNumbers` semble avoir le même type de données que la méthode héritée de la classe de base de l’objet com.</span><span class="sxs-lookup"><span data-stu-id="11ddc-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="11ddc-154">Cela est dû au fait que les arguments et les paramètres de la méthode de la classe de base sont définis en tant qu’entiers 16 bits dans Visual Basic 6,0, mais qu’ils sont exposés en tant qu’entiers 16 bits de type `Short` dans les versions ultérieures de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="11ddc-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="11ddc-155">La nouvelle fonction accepte les entiers 32 bits et surcharge la fonction de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="11ddc-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>

<span data-ttu-id="11ddc-156">Lorsque vous travaillez avec des objets COM, veillez à vérifier la taille et les types de données des paramètres.</span><span class="sxs-lookup"><span data-stu-id="11ddc-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="11ddc-157">Par exemple, lorsque vous utilisez un objet COM qui accepte un objet de collection Visual Basic 6,0 comme argument, vous ne pouvez pas fournir une collection à partir d’une version plus récente de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="11ddc-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>

<span data-ttu-id="11ddc-158">Les propriétés et les méthodes héritées des classes COM peuvent être substituées, ce qui signifie que vous pouvez déclarer une propriété ou une méthode locale qui remplace une propriété ou une méthode héritée d’une classe COM de base.</span><span class="sxs-lookup"><span data-stu-id="11ddc-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="11ddc-159">Les règles de substitution des propriétés COM héritées sont similaires aux règles de substitution d’autres propriétés et méthodes, avec les exceptions suivantes :</span><span class="sxs-lookup"><span data-stu-id="11ddc-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>

- <span data-ttu-id="11ddc-160">Si vous substituez une propriété ou une méthode héritée d’une classe COM, vous devez remplacer toutes les autres propriétés et méthodes héritées.</span><span class="sxs-lookup"><span data-stu-id="11ddc-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>

- <span data-ttu-id="11ddc-161">Les propriétés qui utilisent des `ByRef` paramètres ne peuvent pas être substituées.</span><span class="sxs-lookup"><span data-stu-id="11ddc-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>

## <a name="see-also"></a><span data-ttu-id="11ddc-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11ddc-162">See also</span></span>

- [<span data-ttu-id="11ddc-163">Interopérabilité COM dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="11ddc-163">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="11ddc-164">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="11ddc-164">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="11ddc-165">Court (type de données)</span><span class="sxs-lookup"><span data-stu-id="11ddc-165">Short Data Type</span></span>](../../language-reference/data-types/short-data-type.md)
