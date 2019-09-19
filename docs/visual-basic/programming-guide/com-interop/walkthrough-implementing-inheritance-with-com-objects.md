---
title: 'Procédure pas à pas : Implémentation de l’héritage avec les objets COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 7cbf71d7a2bbd1e94864e785894fdea41d522486
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053331"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Procédure pas à pas : Implémentation de l’héritage avec les objets COM (Visual Basic)

Vous pouvez dériver des classes `Public` Visual Basic à partir de classes d’objets com, y compris celles créées dans les versions antérieures de Visual Basic. Les propriétés et les méthodes des classes héritées d’objets COM peuvent être substituées ou surchargées de la même façon que les propriétés et les méthodes d’une autre classe de base peuvent être substituées ou surchargées. L’héritage à partir d’objets COM est utile lorsque vous avez une bibliothèque de classes existante que vous ne souhaitez pas recompiler.

La procédure suivante indique comment utiliser Visual Basic 6,0 pour créer un objet COM qui contient une classe, puis l’utiliser comme classe de base.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Pour générer l’objet COM utilisé dans cette procédure pas à pas

1. Dans Visual Basic 6,0, ouvrez un nouveau projet de DLL ActiveX. Un projet nommé `Project1` est créé. Il a une classe nommée `Class1`.

2. Dans l' **Explorateur de projets**, cliquez avec le bouton droit sur **Project1**, puis cliquez sur **Propriétés Projet1**. La boîte de dialogue **Propriétés du projet** s’affiche.

3. Dans l’onglet **général** de la boîte de dialogue **Propriétés du projet** , modifiez le nom du `ComObject1` projet en tapant dans le champ **nom du projet** .

4. Dans l' **Explorateur de projets**, cliquez avec `Class1`le bouton droit sur, puis cliquez sur **Propriétés**. La fenêtre **Propriétés** de la classe s’affiche.

5. Remplacez la `Name` valeur de `MathFunctions`la propriété par.

6. Dans l' **Explorateur de projets**, cliquez avec `MathFunctions`le bouton droit sur, puis cliquez sur **afficher le code**. L' **éditeur de code** s’affiche.

7. Ajoutez une variable locale pour contenir la valeur de la propriété :

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. `Let` Ajoutez desprocéduresdepropriété`Get` Property et Property :

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

9. Ajoutez une fonction :

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. Créez et inscrivez l’objet COM en cliquant sur **Make ComObject1. dll** dans le menu **file (fichier** ).

    > [!NOTE]
    > Bien que vous puissiez également exposer une classe créée avec Visual Basic en tant qu’objet COM, ce n’est pas un vrai objet COM et ne peut pas être utilisé dans cette procédure pas à pas. Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).

## <a name="interop-assemblies"></a>Assemblys d’interopérabilité

Dans la procédure suivante, vous allez créer un assembly d’interopérabilité, qui agit comme un pont entre du code non managé (tel qu’un objet COM) et le code managé utilisé par Visual Studio. L’assembly d’interopérabilité créé par Visual Basic gère la plupart des détails de l’utilisation des objets COM, tels que le *marshaling d’interopérabilité*, le processus d’empaquetage des paramètres et les valeurs de retour dans des types de données équivalents lorsqu’ils sont déplacés vers et à partir d’objets com. La référence dans l’application Visual Basic pointe vers l’assembly d’interopérabilité, et non vers l’objet COM réel.

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Pour utiliser un objet COM avec Visual Basic 2005 et versions ultérieures

1. Ouvrez un nouveau projet d’application Windows Visual Basic.

2. Dans le menu **Projet**, cliquez sur **Ajouter une référence**.

     La boîte de dialogue **Ajouter une référence** s’affiche.

3. Dans l’onglet **com** , double-cliquez `ComObject1` dans la liste **nom du composant** , puis cliquez sur **OK**.

4. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

5. Dans le volet **modèles** , cliquez sur **classe**.

     Le nom de fichier par `Class1.vb`défaut,, s’affiche dans le champ **nom** . Modifiez ce champ en MathClass. vb, puis cliquez sur **Ajouter**. Cela crée une classe nommée `MathClass`et affiche son code.

6. Ajoutez le code suivant au début de `MathClass` pour hériter de la classe com.

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. Surchargez la méthode publique de la classe de base en ajoutant le `MathClass`code suivant à :

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. Étendez la classe héritée en ajoutant le code `MathClass`suivant à :

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

La nouvelle classe hérite des propriétés de la classe de base dans l’objet COM, surcharge une méthode et définit une nouvelle méthode pour étendre la classe.

### <a name="to-test-the-inherited-class"></a>Pour tester la classe héritée

1. Ajoutez un bouton à votre formulaire de démarrage, puis double-cliquez dessus pour afficher son code.

2. Dans la procédure du `Click` gestionnaire d’événements du bouton, ajoutez le code suivant pour créer une `MathClass` instance de et appelez les méthodes surchargées :

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. Exécutez le projet en appuyant sur F5.

Lorsque vous cliquez sur le bouton du formulaire, la `AddNumbers` méthode est d’abord appelée `Short` avec des nombres de types de données, et Visual Basic choisit la méthode appropriée à partir de la classe de base. Le deuxième appel à `AddNumbers` est dirigé vers la méthode de surcharge `MathClass`à partir de. Le troisième appel appelle la `SubtractNumbers` méthode, qui étend la classe. La propriété de la classe de base est définie et la valeur est affichée.

## <a name="next-steps"></a>Étapes suivantes

Vous avez peut-être remarqué que la `AddNumbers` fonction surchargée semble avoir le même type de données que la méthode héritée de la classe de base de l’objet com. Cela est dû au fait que les arguments et les paramètres de la méthode de la classe de base sont définis en tant qu’entiers 16 bits dans Visual Basic 6,0, mais qu’ils sont `Short` exposés en tant qu’entiers 16 bits de type dans les versions ultérieures de Visual Basic. La nouvelle fonction accepte les entiers 32 bits et surcharge la fonction de la classe de base.

Lorsque vous travaillez avec des objets COM, veillez à vérifier la taille et les types de données des paramètres. Par exemple, lorsque vous utilisez un objet COM qui accepte un objet de collection Visual Basic 6,0 comme argument, vous ne pouvez pas fournir une collection à partir d’une version plus récente de Visual Basic.

Les propriétés et les méthodes héritées des classes COM peuvent être substituées, ce qui signifie que vous pouvez déclarer une propriété ou une méthode locale qui remplace une propriété ou une méthode héritée d’une classe COM de base. Les règles de substitution des propriétés COM héritées sont similaires aux règles de substitution d’autres propriétés et méthodes, avec les exceptions suivantes :

- Si vous substituez une propriété ou une méthode héritée d’une classe COM, vous devez remplacer toutes les autres propriétés et méthodes héritées.

- Les propriétés qui `ByRef` utilisent des paramètres ne peuvent pas être substituées.

## <a name="see-also"></a>Voir aussi

- [Interopérabilité COM dans les applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short (type de données)](../../../visual-basic/language-reference/data-types/short-data-type.md)
