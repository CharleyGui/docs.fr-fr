---
title: 'Procédure pas à pas : Incorporer des types provenant d’assemblys managés dans Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 0c0de529a0005c9dbaf1f8d0f25957b217280e31
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753025"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>Procédure pas à pas : Incorporer des types provenant d’assemblys managés dans Visual Studio (Visual Basic)

Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application pour obtenir une indépendance de version. Autrement dit, votre programme peut être écrit de façon à ce qu’il utilise des types de plusieurs versions d’une bibliothèque managée sans que vous n’ayez à effectuer de recompilation pour chaque version.

L’incorporation de type est fréquemment utilisée avec COM Interop, par exemple pour une application qui utilise des objets Automation de Microsoft Office. L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec différentes versions de Microsoft Office sur plusieurs ordinateurs. Toutefois, vous pouvez également utiliser l’incorporation de type avec une solution totalement managée.

Les informations de type peuvent être incorporées à partir d’un assembly doté des caractéristiques suivantes :

- L’assembly expose au moins une interface publique.

- Les interfaces incorporées sont annotées avec un attribut `ComImport` et un attribut `Guid` (et un GUID unique).

- L’assembly est annoté avec l’attribut `ImportedFromTypeLib` ou l’attribut `PrimaryInteropAssembly` et un attribut `Guid` au niveau de l’assembly. (Par défaut, les modèles de projet Visual Basic incluent un niveau de l’assembly `Guid` attribut.)

Après avoir spécifié les interfaces publiques qui peuvent être incorporées, vous pouvez créer des classes runtime qui implémentent ces interfaces. Un programme client peut ensuite incorporer les informations de type pour ces interfaces au moment de la conception en référençant l’assembly qui contient les interfaces publiques et en affectant à la propriété `Embed Interop Types` de la référence la valeur `True`. Cela revient à utiliser le compilateur de ligne de commande et à référencer l’assembly à l’aide de l’option de compilateur `/link`. Le programme client peut ensuite charger des instances de vos objets d’exécution possédant le même type que ces interfaces. Si vous créez une version de votre assembly runtime avec nom fort, le programme client n’a pas besoin d’être recompilé avec l’assembly runtime mis à jour. En revanche, le programme client continue d’utiliser la version de l’assembly runtime disponible avec les informations de type incorporées pour les interfaces publiques.

Étant donné que la fonction principale de l’incorporation de type est de prendre en charge l’incorporation d’informations de type à partir d’assemblys COM Interop, les limitations suivantes s’appliquent quand vous incorporez des informations de type dans une solution totalement managée :

- Seuls les attributs spécifiques à COM Interop sont incorporés ; les autres attributs sont ignorés.

- Si un type utilise des paramètres génériques et que le type du paramètre générique est un type incorporé, ce type ne peut pas être utilisé au-delà de la limite de l’assembly. Les exemples de passage de la limite de l’assembly incluent l’appel d’une méthode à partir d’un autre assembly ou la dérivation d’un type à partir d’un type défini dans un autre assembly.

- Les constantes ne sont pas incorporées.

- La classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ne prend pas en charge un type incorporé comme clé. Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé comme clé.

 Dans cette procédure pas à pas, vous exécuterez les étapes suivantes :

- Créer un assembly avec nom fort doté d’une interface publique contenant des informations de type qui peuvent être incorporées.

- Créer un assembly runtime avec nom fort qui implémente cette interface publique.

- Créer un programme client qui incorpore les informations de type de l’interface publique et crée une instance de la classe à partir de l’assembly runtime.

- Modifier et régénérer l’assembly runtime.

- Exécuter le programme client pour constater que la nouvelle version de l’assembly runtime est utilisée sans devoir recompiler le programme client.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a>Création d’une interface

### <a name="to-create-the-type-equivalence-interface-project"></a>Pour créer le projet d’interface d’équivalence des types

1. Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné. Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**. Dans la zone **Nom**, tapez `TypeEquivalenceInterface`, puis cliquez sur **OK**. Le nouveau projet est créé.

3. Dans **l’Explorateur de solutions**, cliquez sur le fichier Class1.vb et cliquez sur **renommer**. Renommez le fichier `ISampleInterface.vb` et appuyez sur Entrée. Quand vous renommez le fichier, la classe est également renommée `ISampleInterface`. Cette classe représente l’interface publique pour la classe.

4. Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Propriétés**. Cliquez sur l’onglet **Compiler**. Affectez au chemin de sortie un emplacement valide sur votre ordinateur de développement, tel que `C:\TypeEquivalenceSample`. Cet emplacement sera également utilisé dans une étape ultérieure de cette procédure pas à pas.

5. Tout en modifiant les propriétés de projet, cliquez sur l’onglet **Signature**. Sélectionnez l’option **Signer l’assembly**. Dans la liste **Choisir un fichier de clé de nom fort**, cliquez sur **<Nouveau...>** . Dans la zone **Nom du fichier de clé**, tapez `key.snk`. Décochez la case **Protéger mon fichier de clé par un mot de passe**. Cliquez sur **OK**.

6. Ouvrez le fichier ISampleInterface.vb. Ajoutez le code suivant au fichier de classe ISampleInterface pour créer l’interface ISampleInterface.

    ```vb
    Imports System.Runtime.InteropServices

    <ComImport()>
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
    Public Interface ISampleInterface
        Sub GetUserInput()
        ReadOnly Property UserInput As String
    End Interface
    ```

7. Dans le menu **Outils**, cliquez sur **Créer un Guid**. Dans la boîte de dialogue **Créer un Guid**, cliquez sur **Format du Registre**, puis sur **Copier**. Cliquez sur **Quitter**.

8. Dans l’attribut `Guid`, supprimez l’exemple de GUID et collez le GUID que vous avez copié à partir de la boîte de dialogue **Créer un Guid**. Supprimez les accolades ({}) du GUID copié.

9. Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.

10. Dans **l’Explorateur de solutions**, développez le **mon projet** dossier. Double-cliquez sur le AssemblyInfo.vb. Ajoutez l’attribut suivant au fichier.

    ```vb
    <Assembly: ImportedFromTypeLib("")>
    ```

    Enregistrez le fichier.

11. Enregistrez le projet.

12. Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Générer**. Le fichier .dll de bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).

## <a name="creating-a-runtime-class"></a>Création d’une classe runtime

### <a name="to-create-the-type-equivalence-runtime-project"></a>Pour créer le projet d’exécution d’équivalence des types

1. Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné. Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**. Dans la zone **Nom**, tapez `TypeEquivalenceRuntime`, puis cliquez sur **OK**. Le nouveau projet est créé.

3. Dans **l’Explorateur de solutions**, cliquez sur le fichier Class1.vb et cliquez sur **renommer**. Renommez le fichier `SampleClass.vb` et appuyez sur Entrée. Quand vous renommez le fichier, la classe est également renommée `SampleClass`. Cette classe va implémenter l’interface `ISampleInterface`.

4. Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Propriétés**. Cliquez sur l’onglet **Compiler**. Affectez au chemin de sortie le même emplacement que celui que vous avez utilisé dans le projet TypeEquivalenceInterface, par exemple `C:\TypeEquivalenceSample`.

5. Tout en modifiant les propriétés de projet, cliquez sur l’onglet **Signature**. Sélectionnez l’option **Signer l’assembly**. Dans la liste **Choisir un fichier de clé de nom fort**, cliquez sur **<Nouveau...>** . Dans la zone **Nom du fichier de clé**, tapez `key.snk`. Décochez la case **Protéger mon fichier de clé par un mot de passe**. Cliquez sur **OK**.

6. Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Ajouter une référence**. Cliquez sur l’onglet **Parcourir** et recherchez le dossier du chemin de sortie. Sélectionnez le fichier TypeEquivalenceInterface.dll et cliquez sur **OK**.

7. Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.

8. Dans l’**Explorateur de solutions**, développez le dossier **Références**. Sélectionnez la référence TypeEquivalenceInterface. Dans la fenêtre Propriétés de la référence TypeEquivalenceInterface, affectez à la propriété **Version spécifique** la valeur **False**.

9. Ajoutez le code suivant au fichier de classe SampleClass pour créer la classe SampleClass.

    ```vb
    Imports TypeEquivalenceInterface

    Public Class SampleClass
        Implements ISampleInterface

        Private p_UserInput As String
        Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
            Get
                Return p_UserInput
            End Get
        End Property

        Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
            Console.WriteLine("Please enter a value:")
            p_UserInput = Console.ReadLine()
        End Sub
    End Class
    ```

10. Enregistrez le projet.

11. Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Générer**. Le fichier .dll de bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).

## <a name="creating-a-client-project"></a>Création d’un projet client

### <a name="to-create-the-type-equivalence-client-project"></a>Pour créer le projet client d’équivalence des types

1. Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné. Sélectionnez **Application console** dans le volet **Modèles**. Dans la zone **Nom**, tapez `TypeEquivalenceClient`, puis cliquez sur **OK**. Le nouveau projet est créé.

3. Cliquez avec le bouton droit sur le projet TypeEquivalenceClient, puis cliquez sur **Propriétés**. Cliquez sur l’onglet **Compiler**. Affectez au chemin de sortie le même emplacement que celui que vous avez utilisé dans le projet TypeEquivalenceInterface, par exemple `C:\TypeEquivalenceSample`.

4. Cliquez avec le bouton droit sur le projet TypeEquivalenceClient, puis cliquez sur **Ajouter une référence**. Cliquez sur l’onglet **Parcourir** et recherchez le dossier du chemin de sortie. Sélectionnez le fichier TypeEquivalenceInterface.dll (pas le fichier TypeEquivalenceRuntime.dll) et cliquez sur **OK**.

5. Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.

6. Dans l’**Explorateur de solutions**, développez le dossier **Références**. Sélectionnez la référence TypeEquivalenceInterface. Dans la fenêtre Propriétés de la référence TypeEquivalenceInterface, affectez à la propriété **Incorporer les types d’interopérabilité** la valeur **True**.

7. Ajoutez le code suivant au fichier Module1.vb pour créer le programme client.

    ```vb
    Imports TypeEquivalenceInterface
    Imports System.Reflection

    Module Module1

        Sub Main()
            Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
            Dim sampleClass As ISampleInterface = CType( _
                sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
            sampleClass.GetUserInput()
            Console.WriteLine(sampleClass.UserInput)
            Console.WriteLine(sampleAssembly.GetName().Version)
            Console.ReadLine()
        End Sub

    End Module
    ```

8. Appuyez sur CTRL+F5 pour générer et exécuter le programme.

## <a name="modifying-the-interface"></a>Modification de l’interface

### <a name="to-modify-the-interface"></a>Pour modifier l’interface

1. Dans Visual Studio, dans le menu **Fichier**, pointez sur **Ouvrir**, puis cliquez sur **Projet/Solution**.

2. Dans la boîte de dialogue **Ouvrir un projet**, cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Propriétés**. Cliquez sur l’onglet **Application** . Cliquez sur le bouton **Informations de l’assembly**. Remplacez les valeurs de **Version de l’assembly** et **Version de fichier** par `2.0.0.0`.

3. Ouvrez le fichier ISampleInterface.vb. Ajoutez la ligne de code suivante à l’interface ISampleInterface.

    ```vb
    Function GetDate() As Date
    ```

    Enregistrez le fichier.

4. Enregistrez le projet.

5. Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Générer**. Une nouvelle version du fichier .dll de bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).

## <a name="modifying-the-runtime-class"></a>Modification de la classe runtime

### <a name="to-modify-the-runtime-class"></a>Pour modifier la classe runtime

1. Dans Visual Studio, dans le menu **Fichier**, pointez sur **Ouvrir**, puis cliquez sur **Projet/Solution**.

2. Dans la boîte de dialogue **Ouvrir un projet**, cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Propriétés**. Cliquez sur l’onglet **Application** . Cliquez sur le bouton **Informations de l’assembly**. Remplacez les valeurs de **Version de l’assembly** et **Version de fichier** par `2.0.0.0`.

3. Ouvrez le fichier SampleClass.vb. Ajoutez les lignes de code suivantes à la classe SampleClass.

    ```vb
    Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
        Return Now
    End Function
    ```

    Enregistrez le fichier.

4. Enregistrez le projet.

5. Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Générer**. Une version mise à jour du fichier .dll de bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération précédemment spécifié (par exemple, C:\TypeEquivalenceSample).

6. Dans l’Explorateur de fichiers, ouvrez le dossier du chemin de sortie (par exemple, C:\TypeEquivalenceSample). Double-cliquez sur le fichier TypeEquivalenceClient.exe pour exécuter le programme. Le programme reflète la nouvelle version de l’assembly TypeEquivalenceRuntime sans aucune recompilation.

## <a name="see-also"></a>Voir aussi

- [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
- [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)
- [Programmation à l’aide d’assemblys](../../../../framework/app-domains/programming-with-assemblies.md)
- [Assemblys dans .NET](../../../../standard/assembly/index.md)
