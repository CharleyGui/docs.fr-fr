---
title: 'Procédure pas à pas : Incorporer des types d’assemblys managés dans Visual Studio'
description: Cette procédure pas à pas vous montre comment incorporer des types à partir d’assemblys managés dans .NET à l’aide de Visual Studio. Les types incorporés peuvent prendre en charge l’indépendance des versions.
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 636e5f8095b64cd0f445555c96d00945ccf7eaf8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378989"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>Procédure pas à pas : Incorporer des types d’assemblys managés dans Visual Studio

Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application pour obtenir une indépendance de version. Autrement dit, votre programme peut être écrit pour utiliser des types à partir de n’importe quelle version d’une bibliothèque managée sans devoir être recompilé pour chaque nouvelle version.

L’incorporation de type est fréquemment utilisée avec COM Interop, par exemple pour une application qui utilise des objets Automation de Microsoft Office. L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec différentes versions de Microsoft Office sur plusieurs ordinateurs. Toutefois, vous pouvez également utiliser l’incorporation de type avec des solutions entièrement managées.

Une fois que vous avez spécifié les interfaces publiques qui peuvent être incorporées, vous créez des classes d’exécution qui implémentent ces interfaces. Un programme client peut incorporer les informations de type pour les interfaces au moment du design en référençant l’assembly qui contient les interfaces publiques et en affectant `Embed Interop Types` à la propriété de la référence la valeur `True` . Le programme client peut ensuite charger les instances des objets de Runtime tapés comme ces interfaces. Cela équivaut à utiliser le compilateur de ligne de commande et à référencer l’assembly à l’aide de l' [option de compilateur-Link](../../csharp/language-reference/compiler-options/link-compiler-option.md).

Si vous créez une nouvelle version de votre assembly de Runtime avec nom fort, le programme client n’a pas besoin d’être recompilé. Le programme client continue à utiliser la version de l’assembly de Runtime qui lui est accessible, à l’aide des informations de type incorporées pour les interfaces publiques.

Lors de cette procédure pas à pas, vous allez effectuer les opérations suivantes :

1. Créez un assembly avec nom fort avec une interface publique contenant les informations de type qui peuvent être incorporées.
1. Créez un assembly de Runtime avec nom fort qui implémente l’interface publique.
1. Créer un programme client qui incorpore les informations de type de l’interface publique et crée une instance de la classe à partir de l’assembly runtime.
1. Modifier et régénérer l’assembly runtime.
1. Exécutez le programme client pour voir qu’il utilise la nouvelle version de l’assembly du runtime sans devoir être recompilé.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Conditions et limitations

Vous pouvez incorporer des informations de type à partir d’un assembly dans les conditions suivantes :

- L’assembly expose au moins une interface publique.
- Les interfaces incorporées sont annotées avec des `ComImport` attributs et `Guid` des attributs avec des GUID uniques.
- L’assembly est annoté avec l’attribut `ImportedFromTypeLib` ou l’attribut `PrimaryInteropAssembly` et un attribut `Guid` au niveau de l’assembly. Les modèles de projet Visual C# et Visual Basic incluent par défaut un attribut au niveau de l’assembly `Guid` .

Étant donné que la fonction principale de l’incorporation de type consiste à prendre en charge les assemblys COM Interop, les limitations suivantes s’appliquent quand vous incorporez des informations de type dans une solution entièrement managée :

- Seuls les attributs spécifiques aux COM Interop sont incorporés. Les autres attributs sont ignorés.
- Si un type utilise des paramètres génériques et que le type du paramètre générique est un type incorporé, ce type ne peut pas être utilisé dans les limites d’un assembly. Les exemples de franchissement d’une limite d’assembly incluent l’appel d’une méthode à partir d’un autre assembly ou la dérivation d’un type d’un type défini dans un autre assembly.
- Les constantes ne sont pas incorporées.
- La classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ne prend pas en charge un type incorporé comme clé. Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé comme clé.

## <a name="create-an-interface"></a>Créer une interface

La première étape consiste à créer l’assembly de l’interface d’équivalence de type.

1. Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **créer un nouveau projet** , tapez *bibliothèque de classes* dans la zone **Rechercher des modèles** . Sélectionnez le modèle de bibliothèque de classes C# ou Visual Basic **(.NET Framework)** dans la liste, puis sélectionnez **suivant**.

1. Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceInterface*, puis sélectionnez **créer**. Le nouveau projet est créé.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Class1.cs* ou *Class1. vb* , sélectionnez **Renommer**, puis renommez le fichier de *Class1* en *ISampleInterface*. Répondez **Oui** à l’invite pour renommer la classe en `ISampleInterface` . Cette classe représente l’interface publique de la classe.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **Propriétés**.

1. Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur un emplacement sur votre ordinateur, par exemple *C:\TypeEquivalenceSample*. Vous utilisez le même emplacement dans cette procédure pas à pas.

1. Sélectionnez **signature** dans le volet gauche de l’écran **Propriétés** , puis activez la case à cocher **signer l’assembly** . Dans la liste déroulante **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.

1. Dans la boîte de dialogue **créer une clé de nom fort** , sous **nom du fichier de clé**, tapez *Key. snk*. Désactivez la case à cocher **protéger le fichier de clé avec un mot de passe** , puis sélectionnez **OK**.

1. Ouvrez le fichier de la classe *ISampleInterface* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer l' `ISampleInterface` interface :

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```

   ```vb
   Imports System.Runtime.InteropServices

   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```

1. Dans le menu **Outils** , sélectionnez **créer un GUID**, puis dans la boîte de dialogue créer un **GUID** , sélectionnez **format du Registre**. Sélectionnez **copier**, puis **quitter**.

1. Dans l' `Guid` attribut de votre code, remplacez l’exemple de GUID par le GUID que vous avez copié et supprimez les accolades (**{}**).

1. Dans **Explorateur de solutions**, développez le dossier **Propriétés** et sélectionnez le fichier *AssemblyInfo.cs* ou *AssemblyInfo. vb* . Dans l’éditeur de code, ajoutez l’attribut suivant au fichier :

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **générer**. Le fichier DLL de la bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié, par exemple *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Créer une classe d’exécution

Ensuite, créez la classe d’exécution d’équivalence de type.

1. Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **créer un nouveau projet** , tapez *bibliothèque de classes* dans la zone **Rechercher des modèles** . Sélectionnez le modèle de bibliothèque de classes C# ou Visual Basic **(.NET Framework)** dans la liste, puis sélectionnez **suivant**.

1. Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceRuntime*, puis sélectionnez **créer**. Le nouveau projet est créé.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Class1.cs* ou *Class1. vb* , sélectionnez **Renommer**, puis renommez le fichier de *Class1* en *SampleClass*. Répondez **Oui** à l’invite pour renommer la classe en `SampleClass` . Cette classe implémente l’interface `ISampleInterface`.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.

1. Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur le même emplacement que celui que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple *C:\TypeEquivalenceSample*.

1. Sélectionnez **signature** dans le volet gauche de l’écran **Propriétés** , puis activez la case à cocher **signer l’assembly** . Dans la liste déroulante **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.

1. Dans la boîte de dialogue **créer une clé de nom fort** , sous **nom du fichier de clé**, tapez *Key. snk*. Désactivez la case à cocher **protéger le fichier de clé avec un mot de passe** , puis sélectionnez **OK**.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** , puis sélectionnez **Ajouter**une  >  **référence**.

1. Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez **Parcourir** et accédez au dossier du chemin de sortie. Sélectionnez le fichier *TypeEquivalenceInterface. dll* , sélectionnez **Ajouter**, puis sélectionnez **OK**.

1. Dans **Explorateur de solutions**, développez le dossier **références** et sélectionnez la référence **TypeEquivalenceInterface** . Dans le volet **Propriétés** , affectez à **version spécifique** la **valeur false** si ce n’est pas déjà fait.

1. Ouvrez le fichier de classe *SampleClass* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer la `SampleClass` classe :

   ```csharp
   using System;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }

           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```

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

1. Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **générer**. Le fichier DLL de la bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié.

## <a name="create-a-client-project"></a>Créer un projet client

Enfin, créez un programme client d’équivalence de type qui référence l’assembly d’interface.

1. Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **créer un nouveau projet** , tapez *console* dans la zone **Rechercher des modèles** . Sélectionnez le modèle application console C# ou Visual Basic **(.NET Framework)** dans la liste, puis sélectionnez **suivant**.

1. Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceClient,*, puis sélectionnez **créer**. Le nouveau projet est créé.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceClient,** , puis sélectionnez **Propriétés**.

1. Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur le même emplacement que celui que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple *C:\TypeEquivalenceSample*.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceClient,** , puis sélectionnez **Ajouter**une  >  **référence**.

1. Dans la boîte de dialogue **Gestionnaire de références** , si le fichier **TypeEquivalenceInterface. dll** est déjà listé, sélectionnez-le. Si ce n’est pas le cas, sélectionnez **Parcourir**, accédez au dossier du chemin de sortie, sélectionnez le fichier *TypeEquivalenceInterface. dll* (pas le fichier *TypeEquivalenceRuntime. dll*), puis sélectionnez **Ajouter**. Sélectionnez **OK**.

1. Dans **Explorateur de solutions**, développez le dossier **références** et sélectionnez la référence **TypeEquivalenceInterface** . Dans le volet **Propriétés** , affectez à **incorporer les types d’interopérabilité** la **valeur true**.

1. Ouvrez le fichier *Program.cs* ou *Module1. vb* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer le programme client :

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports System.Reflection
   Imports TypeEquivalenceInterface

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

1. Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.

1. Appuyez sur **CTRL** + **F5** pour générer et exécuter le programme. Notez que la sortie de la console retourne la version de l’assembly **1.0.0.0**.

## <a name="modify-the-interface"></a>Modifier l’interface

À présent, modifiez l’assembly d’interface et modifiez sa version.

1. Dans Visual Studio, sélectionnez **fichier**  >  **ouvrir**  >  un**projet/une solution**, puis ouvrez le projet **TypeEquivalenceInterface** .

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.

1. Sélectionnez **application** dans le volet gauche de l’écran **Propriétés** , puis sélectionnez informations de l' **assembly**.

1. Dans la boîte de dialogue informations de l' **assembly** , modifiez les valeurs version de l' **assembly** et **version du fichier** sur *2.0.0.0*, puis sélectionnez **OK**.

1. Ouvrez le fichier *SampleInterface.cs* ou *SampleInterface. vb* et ajoutez la ligne de code suivante à l' `ISampleInterface` interface :

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **générer**. Une nouvelle version du fichier DLL de la bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération.

## <a name="modify-the-runtime-class"></a>Modifier la classe d’exécution

Modifiez également la classe Runtime et mettez à jour sa version.

1. Dans Visual Studio, sélectionnez **fichier**  >  **ouvrir**  >  un**projet/une solution**, puis ouvrez le projet **TypeEquivalenceRuntime** .

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **Propriétés**.

1. Sélectionnez **application** dans le volet gauche de l’écran **Propriétés** , puis sélectionnez informations de l' **assembly**.

1. Dans la boîte de dialogue informations de l' **assembly** , modifiez les valeurs version de l' **assembly** et **version du fichier** sur *2.0.0.0*, puis sélectionnez **OK**.

1. Ouvrez le fichier *SampleClass.cs* ou *SampleClass. vb* , puis ajoutez le code suivant à la `SampleClass` classe :

   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```

   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```

1. Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **générer**. Une nouvelle version du fichier DLL de la bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération.

## <a name="run-the-updated-client-program"></a>Exécuter le programme client mis à jour

Accédez à l’emplacement du dossier de sortie de la génération et exécutez *TypeEquivalenceClient,. exe*. Notez que la sortie de la console reflète désormais la nouvelle version de l' `TypeEquivalenceRuntime` assembly, *2.0.0.0*, sans le programme en cours de recompilation.

## <a name="see-also"></a>Voir aussi

- [-link (Options du compilateur C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [Guide de programmation C#](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblys dans .NET](index.md)
