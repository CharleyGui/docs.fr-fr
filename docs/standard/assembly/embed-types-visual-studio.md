---
title: 'Procédure pas à pas : Intégrer les types d’assemblages gérés dans Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338554"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>Procédure pas à pas : Intégrer les types d’assemblages gérés dans Visual Studio

Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application pour obtenir une indépendance de version. Autrement dit, votre programme peut être écrit pour utiliser des types de n’importe quelle version d’une bibliothèque gérée sans avoir à être recompilé pour chaque nouvelle version.

L’incorporation de type est fréquemment utilisée avec COM Interop, par exemple pour une application qui utilise des objets Automation de Microsoft Office. L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec différentes versions de Microsoft Office sur plusieurs ordinateurs. Cependant, vous pouvez également utiliser l’intégration de type avec des solutions entièrement gérées.

Après avoir spécifé les interfaces publiques qui peuvent être intégrées, vous créez des classes de temps d’exécution qui implémentent ces interfaces. Un programme client peut intégrer les informations de type pour les interfaces au moment de `Embed Interop Types` la conception `True`en faisant référence à l’assemblage qui contient les interfaces publiques et en définissant la propriété de la référence à . Le programme client peut ensuite charger les instances des objets en temps d’exécution tapés comme ces interfaces. Cela équivaut à utiliser le compilateur de la ligne de commande et le référencement de l’assemblage en utilisant [l’option compilateur -lien](../../csharp/language-reference/compiler-options/link-compiler-option.md).

Si vous créez une nouvelle version de votre assemblage de temps d’exécution fort, le programme client n’a pas besoin d’être recompilé. Le programme client continue d’utiliser n’importe quelle version de l’assemblage de temps d’exécution qui lui est disponible, en utilisant les informations de type intégrée pour les interfaces publiques.

Lors de cette procédure pas à pas, vous allez effectuer les opérations suivantes :

1. Créez un assemblage fort avec une interface publique contenant des informations de type qui peuvent être intégrées.
1. Créez un assemblage de temps d’exécution fort qui implémente l’interface publique.
1. Créer un programme client qui incorpore les informations de type de l’interface publique et crée une instance de la classe à partir de l’assembly runtime.
1. Modifier et régénérer l’assembly runtime.
1. Exécutez le programme client pour s’en rendre compte qu’il utilise la nouvelle version de l’assemblage en temps d’exécution sans avoir à être recompilé.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Conditions et limitations

Vous pouvez intégrer des informations de type à partir d’un assemblage dans les conditions suivantes :

- L’assembly expose au moins une interface publique.
- Les interfaces intégrées sont `ComImport` annotées avec des attributs et `Guid` des attributs avec des GUID uniques.
- L’assembly est annoté avec l’attribut `ImportedFromTypeLib` ou l’attribut `PrimaryInteropAssembly` et un attribut `Guid` au niveau de l’assembly. Les modèles de projet Visual C et Visual `Guid` Basic comprennent un attribut de niveau d’assemblage par défaut.

Étant donné que la fonction principale de l’intégration de type est de prendre en charge les assemblages interop COM, les limitations suivantes s’appliquent lorsque vous intégrez des informations de type dans une solution entièrement gérée :

- Seuls les attributs spécifiques à COM interop sont intégrés. D’autres attributs sont ignorés.
- Si un type utilise des paramètres génériques et que le type de paramètre générique est un type intégré, ce type ne peut pas être utilisé à travers une limite d’assemblage. Parmi les exemples de franchissement d’une limite d’assemblage, mentionnons l’appel d’une méthode d’un autre assemblage ou la suppression d’un type d’un type défini dans un autre assemblage.
- Les constantes ne sont pas incorporées.
- La classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ne prend pas en charge un type incorporé comme clé. Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé comme clé.

## <a name="create-an-interface"></a>Créer une interface

La première étape consiste à créer le type d’assemblage d’interface d’équivalence.

1. Dans Visual Studio, sélectionnez **File** > **New** > **Project**.

1. Dans la boîte de dialogue **Créer un nouveau projet,** *type bibliothèque de classe* dans la boîte de recherche **de modèles.** Sélectionnez le modèle de bibliothèque de classe de base visuelle **(.NET Framework)** de la liste, puis sélectionnez **Next**.

1. Dans la configuration de votre nouvelle boîte de dialogue **de projet,** sous **le nom de projet**, *tapez TypeEquivalenceInterface*, puis sélectionnez **Créer**. Le nouveau projet est créé.

1. Dans **Solution Explorer**, cliquez à droite sur le fichier *Class1.cs* ou *Class1.vb,* **sélectionnez Rename**, et renommez le fichier de *classe1* à *ISampleInterface*. Répondre **Oui** à l’invite de également `ISampleInterface`renommer la classe à . Cette classe représente l’interface publique de la classe.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface,** puis sélectionnez **Propriétés**.

1. Sélectionnez **Construire** sur la vitre gauche de l’écran **Propriétés,** et définissez le **chemin de sortie** à un emplacement sur votre ordinateur, tels que *C: 'TypeEquivalenceSample*. Vous utilisez le même emplacement tout au long de cette procédure pas à pas.

1. Sélectionnez **Signature** sur la vitre gauche de l’écran **Propriétés,** puis sélectionnez le Signe de la case à cocher **d’assemblage.** Dans le dropdown pour **Choisissez un fichier clé de nom fort**, sélectionnez **Nouveau**.

1. Dans le **dialogue Create Strong Name Key,** sous le nom de fichier **Key**, type *key.snk*. Déséllectez le **Fichier Protégez mon fichier clé avec une** case à cocher par mot de passe, puis sélectionnez **OK**.

1. Ouvrez le fichier de classe *ISampleInterface* dans l’éditeur de `ISampleInterface` code, et remplacez son contenu par le code suivant pour créer l’interface :

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

1. Sur le menu **Tools,** sélectionnez **Create Guid**, et dans la boîte de dialogue **Create GUID,** sélectionnez **Format d’enregistrement**. Sélectionnez **La copie,** puis sélectionnez **Exit**.

1. Dans `Guid` l’attribut de votre code, remplacez l’échantillon GUID par le GUID que vous avez copié, et retirez les accolades **(**.

1. Dans **Solution Explorer**, étendre le dossier **Propriétés** et sélectionnez le fichier *AssemblyInfo.cs* ou *AssemblyInfo.vb.* Dans l’éditeur de code, ajoutez l’attribut suivant au fichier :

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface** et sélectionnez **Build**. Le fichier DLL de bibliothèque de classe est compilé et enregistré sur le chemin de sortie de construction spécifié, par exemple *C : 'TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Créer une classe de temps d’exécution

Ensuite, créez la classe de runtime d’équivalence type.

1. Dans Visual Studio, sélectionnez **File** > **New** > **Project**.

1. Dans la boîte de dialogue **Créer un nouveau projet,** *type bibliothèque de classe* dans la boîte de recherche **de modèles.** Sélectionnez le modèle de bibliothèque de classe de base visuelle **(.NET Framework)** de la liste, puis sélectionnez **Next**.

1. Dans la configuration de votre nouvelle boîte de dialogue **de projet,** sous **le nom de projet**, type *TypeEquivalenceRuntime*, puis sélectionnez **Créer**. Le nouveau projet est créé.

1. Dans **Solution Explorer**, cliquez à droite sur le fichier *Class1.cs* ou *Class1.vb,* **sélectionnez Rename**, et renommez le fichier de *Class1* à *SampleClass*. Répondre **Oui** à l’invite de également `SampleClass`renommer la classe à . Cette classe implémente l’interface `ISampleInterface`.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.

1. Sélectionnez **Construire** sur le volet gauche de l’écran **Propriétés,** puis définir le **chemin de sortie** au même endroit que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple, *C: 'TypeEquivalenceSample*.

1. Sélectionnez **Signature** sur la vitre gauche de l’écran **Propriétés,** puis sélectionnez le Signe de la case à cocher **d’assemblage.** Dans le dropdown pour **Choisissez un fichier clé de nom fort**, sélectionnez **Nouveau**.

1. Dans le **dialogue Create Strong Name Key,** sous le nom de fichier **Key**, type *key.snk*. Déséllectez le **Fichier Protégez mon fichier clé avec une** case à cocher par mot de passe, puis sélectionnez **OK**.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceRuntime** et **sélectionnez Ajouter** > **référence**.

1. Dans le dialogue **de Reference Manager,** **sélectionnez Parcourir** et naviguez vers le dossier de sortie. Sélectionnez le fichier *TypeEquivalenceInterface.dll,* sélectionnez **Ajouter,** puis sélectionnez **OK**.

1. Dans **Solution Explorer**, élargissez le dossier **Références** et sélectionnez la référence **TypeEquivalenceInterface.** Dans le volet **Propriétés,** définissez **la version spécifique** à **False** si ce n’est pas déjà le cas.

1. Ouvrez le fichier de classe *SampleClass* dans l’éditeur de `SampleClass` code et remplacez son contenu par le code suivant pour créer la classe :

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

1. Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceRuntime** et sélectionnez **Build**. Le fichier DLL de bibliothèque de classe est compilé et enregistré sur le chemin de sortie de construction spécifié.

## <a name="create-a-client-project"></a>Créer un projet client

Enfin, créez un programme client d’équivalence type qui fait référence à l’assemblage de l’interface.

1. Dans Visual Studio, sélectionnez **File** > **New** > **Project**.

1. Dans la boîte de dialogue **Créer un nouveau projet,** *typez la console* dans la boîte de recherche de **modèles.** Sélectionnez le modèle C ou Visual Basic **Console App (.NET Framework)** de la liste, puis sélectionnez **Next**.

1. Dans la configuration de votre nouvelle boîte de dialogue **de projet,** sous **le nom de projet**, type *TypeEquivalenceClient*, puis sélectionnez **Créer**. Le nouveau projet est créé.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceClient** et sélectionnez **Propriétés**.

1. Sélectionnez **Construire** sur le volet gauche de l’écran **Propriétés,** puis définir le **chemin de sortie** au même endroit que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple, *C: 'TypeEquivalenceSample*.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceClient** et **sélectionnez Ajouter** > **référence**.

1. Dans le dialogue **du gestionnaire de référence,** si le fichier **TypeEquivalenceInterface.dll** est déjà répertorié, sélectionnez-le. Si ce n’est pas le cas, **sélectionnez Parcourir,** naviguez vers le dossier de sortie, sélectionnez le fichier *TypeEquivalenceInterface.dll* (pas le *TypeEquivalenceRuntime.dll*), et sélectionnez **Ajouter**. Sélectionnez **OK**.

1. Dans **Solution Explorer**, élargissez le dossier **Références** et sélectionnez la référence **TypeEquivalenceInterface.** Dans le volet **Propriétés,** mettre **Embed Interop Types** à **True**.

1. Ouvrez le *fichier Program.cs* ou *Module1.vb* dans l’éditeur de code, et remplacez son contenu par le code suivant pour créer le programme client :

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

1. Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.

1. Appuyez sur **Ctrl**+**F5** pour construire et exécuter le programme. Notez que la sortie de la console renvoie la version d’assemblage **1.0.0.0**.

## <a name="modify-the-interface"></a>Modifier l’interface

Maintenant, modifiez l’assemblage de l’interface et modifiez sa version.

1. Dans Visual Studio, sélectionnez **File** > **Open** > **Project/Solution**et ouvrez le projet **TypeEquivalenceInterface.**

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.

1. Sélectionnez **l’application** sur le volet gauche de l’écran **propriétés,** puis sélectionnez **l’information d’assemblage**.

1. Dans la boîte de dialogue **d’information de l’Assemblée,** modifiez les valeurs de la **version de l’Assemblée** et **de la version Fichier** à *2.0.0.0*, puis sélectionnez **OK**.

1. Ouvrez le *fichier SampleInterface.cs* ou *SampleInterface.vb,* et ajoutez la `ISampleInterface` ligne de code suivante à l’interface :

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface** et sélectionnez **Build**. Une nouvelle version du fichier DLL de bibliothèque de classe est compilée et enregistrée sur le chemin de sortie de construction.

## <a name="modify-the-runtime-class"></a>Modifier la classe de temps d’exécution

Modifiez également la classe de temps d’exécution et mettez à jour sa version.

1. Dans Visual Studio, sélectionnez **File** > **Open** > **Project/Solution**et ouvrez le projet **TypeEquivalenceRuntime.**

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceRuntime** et sélectionnez **propriétés**.

1. Sélectionnez **l’application** sur le volet gauche de l’écran **propriétés,** puis sélectionnez **l’information d’assemblage**.

1. Dans la boîte de dialogue **d’information de l’Assemblée,** modifiez les valeurs de la **version de l’Assemblée** et **de la version Fichier** à *2.0.0.0*, puis sélectionnez **OK**.

1. Ouvrez le fichier *SampleClass.cs* ou *SampleClass.vb,* et ajoutez `SampleClass` le code suivant à la classe :

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

1. Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceRuntime** et sélectionnez **Build**. Une nouvelle version du fichier DLL de bibliothèque de classe est compilée et enregistrée sur le chemin de sortie de construction.

## <a name="run-the-updated-client-program"></a>Exécuter le programme client mis à jour

Aller à l’emplacement du dossier de sortie de construction et exécuter *TypeEquivalenceClient.exe*. Notez que la sortie de la `TypeEquivalenceRuntime` console reflète désormais la nouvelle version de l’assemblage, *2.0.0.0*, sans que le programme soit recompilé.

## <a name="see-also"></a>Voir aussi

- [-link (Options du compilateur C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-lien (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [Guide de programmation CMD](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblys dans .NET](index.md)
