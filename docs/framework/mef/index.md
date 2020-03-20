---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: 9a601ac860ac3bf81dd01980b020470d3323772f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181284"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

Cette rubrique fournit une vue d'ensemble de Managed Extensibility Framework, qui a été introduit dans le .NET Framework 4.

## <a name="what-is-mef"></a>Présentation de MEF

Le Cadre d’Extétabilité gérée ou MEF est une bibliothèque pour créer des applications légères et extensibles. Elle permet aux développeurs d'applications de découvrir et d'utiliser des extensions sans nécessiter de configuration particulière. Elle permet également aux développeurs d'extensions d'encapsuler du code facilement tout en évitant les dépendances dures et fragiles. De plus, MEF permet de réutiliser des extensions dans une application, mais aussi d'une application à une autre.

## <a name="the-problem-of-extensibility"></a>Le problème de l’extéabilité

Imaginez que vous êtes l'architecte d'une grande application devant fournir une prise en charge pour l'extensibilité. Votre application doit inclure un nombre potentiellement important de petits composants qu'elle est censée créer et exécuter.

Face à ce problème, l'approche la plus simple consiste à inclure les composants sous forme de code source dans votre application et à les appeler directement à partir de votre code. Cette approche comporte plusieurs inconvénients évidents. L'inconvénient majeur est que vous ne pouvez pas ajouter de nouveaux composants sans modifier le code source. Cette restriction est acceptable dans une application web par exemple, mais elle est rédhibitoire dans une application cliente. Autre inconvénient tout aussi problématique, vous risquez de ne pas avoir accès au code source des composants développés par des tiers et, pour la même raison, vous ne pouvez pas leur permettre d'accéder aux vôtres.

Il existe une approche un peu plus élaborée qui consiste à fournir une interface ou un point d'extension pour découpler l'application de ses composants. Dans ce modèle, vous pouvez fournir une interface à implémenter par un composant, et une API pour lui permettre d'interagir avec votre application. Si cette approche résout le problème de l'accès au code source, elle a d'autres inconvénients spécifiques.

Comme l'application n'est pas en mesure de découvrir les composants elle-même, vous devez encore lui indiquer explicitement quels composants sont disponibles et doivent être chargés. Cela peut généralement se faire en inscrivant explicitement les composants disponibles dans un fichier de configuration. Cela implique de vérifier que les composants sont corrects, ce qui complique la maintenance, en particulier si la mise à jour doit normalement être effectuée par l'utilisateur final et non le développeur.

De plus, les composants sont incapables de communiquer entre eux, sauf via les canaux rigides de l'application elle-même. Si l‘architecte de l‘application n‘a pas anticipé la nécessité d‘établir une communication spécifique, la communication est généralement impossible.

Enfin, les développeurs de composants doivent accepter la présence d'une dépendance dure sur l'assembly contenant l'interface qu'ils implémentent. Cette dépendance rend compliquée l'utilisation d'un composant dans plusieurs applications et peut également poser des problèmes quand vous créez une infrastructure de tests pour les composants.

## <a name="what-mef-provides"></a>Ce que le MEF fournit

Au lieu de cette inscription explicite des composants disponibles, MEF permet leur découverte implicite par la *composition*. Un composant MEF, appelé *partie*, spécifie de manière déclarative à la fois ses dépendances (les *importations*) et les fonctionnalités (les *exportations*) qu’il rend disponibles. Lorsqu'une partie est créée, le moteur de composition MEF fournit à ses importations les éléments disponibles des autres parties.

Cette approche résout les problèmes abordés dans la section précédente. Étant donné que les parties MEF spécifient leurs fonctionnalités de façon déclarative, elles sont détectables au moment de l'exécution, ce qui signifie qu'une application peut utiliser des parties sans avoir recours à des références codées en dur ni à des fichiers de configuration fragiles. MEF permet aux applications de découvrir et d'examiner des parties grâce à leurs métadonnées, sans les instancier ni même charger leurs assemblys. Par conséquent, il est inutile de spécifier avec précision quand et comment les extensions doivent être chargées.

En plus de spécifier les exportations qui lui sont fournies, une partie peut spécifier ses importations, qui seront remplies par d'autres parties. Cela permet et facilite la communication entre les parties, tout en garantissant une bonne factorisation du code. Par exemple, les services communs à de nombreux composants peuvent être factorisés dans une partie distincte et être facilement modifiés ou remplacés.

Étant donné que le modèle MEF n'a besoin d'aucune dépendance dure sur un assembly d'application particulier, il permet la réutilisation des extensions dans d'autres applications. Cela facilite également le développement d’un atelier de test, indépendant de l’application, pour tester les composants d’extension.

Une application extensible écrite à l'aide de MEF déclare une importation qui peut être remplie par les composants d'extension, et peut aussi déclarer des exportations pour exposer ses services aux extensions. Chaque composant d’extension déclare une exportation et éventuellement des importations. De cette façon, les composants d'extension eux-mêmes sont automatiquement extensibles.

## <a name="where-mef-is-available"></a>Là où le MEF est disponible

MEF fait partie intégrante de .NET Framework 4 et est disponible partout où le .NET Framework est utilisé. Vous pouvez utiliser MEF dans vos applications clientes, si elles utilisent des Windows Forms, WPF ou une autre technologie, ou dans les applications serveur ASP.NET.

## <a name="mef-and-maf"></a>MEF et MAF

Les versions précédentes du .NET Framework ont introduit Managed Add-in Framework (MAF), une infrastructure conçue pour permettre aux applications d’isoler et de gérer des extensions. Le focus de MAF est légèrement plus général que MEF : MAF se concentre sur l’isolement des extensions et le chargement/déchargement des assemblys, tandis que le focus de MEF englobe la détectabilité, l’extensibilité et la portabilité. Les deux infrastructures interagissent de façon transparente et peuvent être utilisées par une même application.

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Une application d’exemple

Le meilleur moyen de découvrir les possibilités de MEF consiste à créer une application MEF simple. Dans cet exemple, vous allez créer une calculatrice très simple nommée SimpleCalculator. L'objectif de SimpleCalculator est de créer une application console qui accepte des commandes arithmétiques de base (de type « 5 + 3 » ou « 6 - 2 ») et retourne des résultats corrects. Grâce à MEF, vous pourrez ajouter de nouveaux opérateurs sans avoir à modifier le code de l'application.

Pour télécharger le code complet pour cet exemple, consultez [l’échantillon SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).

> [!NOTE]
> L'objectif de SimpleCalculator est avant tout de montrer les concepts et la syntaxe de MEF, et non de fournir un scénario d'utilisation réaliste. La plupart des applications qui tirent le meilleur parti de MEF sont plus complexes que SimpleCalculator. Pour obtenir des exemples plus détaillés, consultez [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) sur GitHub.

- Pour commencer, dans Visual Studio, créez un projet Application console et nommez-le `SimpleCalculator`.

- Ajoutez une référence `System.ComponentModel.Composition` à l’assemblage, où réside meF.

- Ouvrez *module1.vb* ou *Program.cs* `Imports` et `using` ajouter `System.ComponentModel.Composition` `System.ComponentModel.Composition.Hosting`ou des instructions pour et . Ces deux espaces de noms contiennent des types MEF dont vous avez besoin pour développer une application extensible.

- Si vous utilisez Visual Basic, ajoutez le mot clé `Public` dans la ligne qui déclare le module `Module1`.

## <a name="composition-container-and-catalogs"></a>Conteneur de composition et catalogues

Le cœur du modèle de composition MEF est le *conteneur de composition*, qui contient toutes les parties disponibles et exécute la composition. La composition est la correspondance entre les importations et les exportations. Pour SimpleCalculator, vous allez utiliser <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, qui est le type de conteneur de composition le plus courant.

Si vous utilisez Visual Basic, ajoutez `Program` une classe publique nommée dans *Module1.vb*.

Ajoutez la ligne `Program` suivante à la classe dans *Module1.vb* ou *Program.cs*:

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

Pour découvrir les parties disponibles, les conteneurs de composition utilisent un *catalogue*. Un catalogue est un objet qui rend disponibles les parties découvertes dans une source. MEF propose des catalogues pour la découverte des parties dans un type, un assembly ou un répertoire fourni. Les développeurs d'applications peuvent facilement créer des catalogues pour découvrir des parties dans d'autres sources, telles qu'un service web.

Ajoutez le constructeur suivant à la classe `Program` :

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

L'appel à <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> indique au conteneur de composition qu'il doit composer un ensemble spécifique de parties (dans ce cas, l'instance actuelle de `Program`). Toutefois, rien ne se produira à ce stade, puisque `Program` n'a pas d'importations à remplir.

## <a name="imports-and-exports-with-attributes"></a>Importations et exportations avec attributs

Tout d'abord, `Program` doit importer une calculatrice. Cela permet de séparer les problèmes d'interface utilisateur, comme l'entrée et la sortie console qui iront dans `Program`, de la logique de la calculatrice.

Ajoutez le code suivant à la classe `Program` :

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

Notez que la déclaration de l'objet `calculator` n'est pas inhabituelle, mais qu'elle est décorée avec l'attribut <xref:System.ComponentModel.Composition.ImportAttribute>. Cet attribut déclare qu'un élément est une importation, c'est-à-dire qu'il sera rempli par le moteur de composition quand l'objet sera composé.

Chaque importation a un *contrat* qui détermine à quelles exportations elle doit être associée. Le contrat peut être une chaîne explicitement spécifiée ou il peut être généré automatiquement par MEF à partir d'un type donné (dans ce cas, l'interface `ICalculator`). Toute exportation déclarée avec un contrat correspondant effectuera cette importation. Le type de l'objet `calculator` est ici `ICalculator`, mais ce n'est pas une obligation. Le contrat est indépendant du type de l'objet d'importation. (Dans ce cas, vous pouvez ignorer `typeof(ICalculator)`. MEF déduira automatiquement que le contrat est basé sur le type de l'importation, sauf si vous spécifiez un type explicitement.)

Ajoutez cette interface très simple au module ou à l'espace de noms `SimpleCalculator` :

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

Vous venez de définir `ICalculator`, vous avez besoin maintenant d'une classe qui l'implémente. Ajoutez la classe suivante au module ou à l'espace de noms `SimpleCalculator` :

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

Voici l'exportation qui correspondra à l'importation dans `Program`. Pour que l'exportation corresponde à l'importation, l'exportation doit avoir le même contrat. Une exportation avec un contrat basé sur `typeof(MySimpleCalculator)` engendrerait une incompatibilité, et l'importation ne serait pas remplie ; les contrats doivent correspondre exactement.

Comme le conteneur de composition sera rempli avec toutes les parties disponibles dans cet assembly, la partie `MySimpleCalculator` sera disponible. Quand le constructeur de `Program` exécutera la composition sur l'objet `Program`, son importation sera remplie avec un objet `MySimpleCalculator` qui sera créé à cet effet.

La couche d'interface utilisateur (`Program`) n'a besoin d'aucune autre information. Vous pouvez donc remplir le reste de la logique d'interface utilisateur dans la méthode `Main`.

Ajoutez le code suivant à la méthode `Main` :

```vb
Sub Main()
    ' Composition is performed in the constructor.
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    // Composition is performed in the constructor.
    var p = new Program();
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 Ce code lit simplement une ligne d'entrée et appelle la fonction `Calculate` de l'interface `ICalculator` dans le résultat, qu'il réécrit dans la console. C'est le seul code dont vous avez besoin dans `Program`. Tout le reste du processus s'effectuera dans les parties.

## <a name="further-imports-and-importmany"></a>Importations supplémentaires et ImportMany

Pour que SimpleCalculator soit extensible, il doit importer une liste d'opérations. Un attribut <xref:System.ComponentModel.Composition.ImportAttribute> standard est rempli par une seule exportation <xref:System.ComponentModel.Composition.ExportAttribute>. Si plusieurs exportations sont disponibles, le moteur de composition génère une erreur. Pour créer une importation qui peut être remplie par un nombre indéfini d'exportations, utilisez l'attribut <xref:System.ComponentModel.Composition.ImportManyAttribute>.

Ajoutez la propriété operations suivante à la classe `MySimpleCalculator` :

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<xref:System.Lazy%602> est un type fourni par MEF pour contenir des références indirectes à des exportations. Ici, en plus de l’objet exporté lui-même, vous obtenez des *métadonnées d’exportation*, ou des informations qui décrivent l’objet exporté. Chaque <xref:System.Lazy%602> contient un objet `IOperation` représentant une opération réelle et un objet `IOperationData` représentant ses métadonnées.

Ajoutez les interfaces simples suivantes au module ou à l'espace de noms `SimpleCalculator` :

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 Dans ce cas, les métadonnées de chaque opération sont le symbole \*qui représente cette opération, comme le site de l’opération, comme le site de l’opération, et ainsi de suite. Pour rendre l'addition disponible, ajoutez la classe suivante au module ou à l'espace de noms `SimpleCalculator` :

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

L'attribut <xref:System.ComponentModel.Composition.ExportAttribute> fonctionne comme auparavant. L'attribut <xref:System.ComponentModel.Composition.ExportMetadataAttribute> joint des métadonnées à cette exportation, sous la forme d'une paire nom-valeur. La classe `Add` implémente `IOperation`, mais aucune classe implémentant `IOperationData` n'est explicitement définie. En fait, MEF crée implicitement une classe en lui attribuant des propriétés basées sur les noms des métadonnées fournies. (C'est l'une des différentes méthodes permettant d'accéder aux métadonnées dans MEF.)

La composition dans MEF est *récursive*. Vous avez composé explicitement l'objet `Program`, qui a importé un `ICalculator` de type `MySimpleCalculator`. Ensuite, `MySimpleCalculator` importe une collection d'objets `IOperation`. Cette importation sera remplie quand `MySimpleCalculator` sera créé, en même temps que les importations de `Program`. Si la classe `Add` a déclaré une importation supplémentaire, celle-ci devra également être remplie, et ainsi de suite. Une importation non remplie provoque une erreur de composition. (Toutefois, il est possible de déclarer que des importations sont facultatives ou de leur affecter des valeurs par défaut.)

## <a name="calculator-logic"></a>Logique de la calculatrice

Après avoir mis en place les différentes parties, il reste simplement à définir la logique de la calculatrice elle-même. Ajoutez le code suivant à la classe `MySimpleCalculator` pour implémenter la méthode `Calculate` :

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(string input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input);
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

Les étapes initiales analysent la chaîne d'entrée dans les opérandes de gauche et de droite, et un caractère d'opérateur. Dans la boucle `foreach`, chaque membre de la collection `operations` est examiné. Ces objets sont de type <xref:System.Lazy%602>, et leurs valeurs de métadonnées et d'objet exporté sont accessibles respectivement via la propriété <xref:System.Lazy%602.Metadata%2A> et la propriété <xref:System.Lazy%601.Value%2A>. Dans ce cas, si la propriété `Symbol` découverte de l'objet `IOperationData` est une correspondance, la calculatrice appelle la méthode `Operate` de l'objet `IOperation` et retourne le résultat.

Pour terminer la calculatrice, vous devez également définir une méthode d'assistance qui retourne la position du premier caractère non numérique dans une chaîne. Ajoutez la méthode d'assistance suivante à la classe `MySimpleCalculator` :

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

Vous devez maintenant être en mesure de compiler et d'exécuter le projet. Dans Visual Basic, assurez-vous d'avoir ajouté le mot clé `Public` au module `Module1`. Dans la fenêtre de console, tapez une addition, par exemple « 5 + 3 », et la calculatrice retourne le résultat. L’utilisation d’un autre opérateur entraîne l’affichage du message .

## <a name="extending-simplecalculator-using-a-new-class"></a>Étendre SimpleCalculator à l’aide d’une nouvelle classe

La calculatrice fonctionne. Vous pouvez maintenant ajouter facilement une nouvelle opération. Ajoutez la classe suivante au module ou à l'espace de noms `SimpleCalculator` :

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

Compilez et exécutez le projet. Tapez une soustraction, par exemple « 5-3 ». La calculatrice prend désormais en charge la soustraction ainsi que l'addition.

## <a name="extending-simplecalculator-using-a-new-assembly"></a>Extension SimpleCalculator à l’aide d’un nouvel assemblage

L'ajout de classes au code source est une opération relativement simple, mais MEF permet de rechercher des parties en dehors de la source d'une application. Pour découvrir cette possibilité, vous devez modifier SimpleCalculator pour qu'il recherche des parties dans un répertoire et dans son propre assembly, en ajoutant un catalogue <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.

Ajoutez un nouveau répertoire nommé `Extensions` au projet SimpleCalculator. Assurez-vous de l'ajouter au niveau du projet et pas au niveau de la solution. Ajoutez ensuite un nouveau projet de bibliothèque de classes, appelé `ExtendedOperations`, à la solution. Le nouveau projet sera compilé dans un assembly distinct.

Ouvrez le concepteur de propriétés de projet pour le projet ExtendedOperations et cliquez sur **l’onglet Compile** ou **Build.** Changer le **chemin de sortie Build** ou le chemin de **sortie** pour pointer vers le répertoire Extensions dans le répertoire du projet SimpleCalculator *(. 'SimpleCalculator’Extensions\\*).

 Dans *Module1.vb* ou *Program.cs*, ajoutez la `Program` ligne suivante au constructeur :

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

Remplacez le chemin d’accès de l’exemple par le chemin d’accès à votre répertoire Extensions. (Ce chemin d'accès absolu sert uniquement au débogage. Dans une application de production, vous utiliseriez un chemin relatif.) Le <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> va maintenant ajouter toutes les pièces trouvées dans les assemblages dans le répertoire Extensions au récipient de composition.

Dans le projet ExtendedOperations, ajoutez des références à SimpleCalculator et à System.ComponentModel.Composition. Dans le fichier de classe ExtendedOperations, ajoutez une instruction `Imports` ou `using` pour System.ComponentModel.Composition. Dans Visual Basic, ajoutez également une instruction `Imports` pour SimpleCalculator. Ajoutez ensuite la classe suivante au fichier de classe ExtendedOperations :

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

Notez que l'attribut <xref:System.ComponentModel.Composition.ExportAttribute> doit avoir le même type que <xref:System.ComponentModel.Composition.ImportAttribute> pour que le contrat corresponde.

Compilez et exécutez le projet. Testez le nouvel opérateur Mod (%).

## <a name="conclusion"></a>Conclusion

Cette rubrique a couvert les concepts de base de MEF.

- Parties, catalogues et conteneur de composition

     Les parties et le conteneur de composition sont les blocs de construction élémentaires d'une application MEF. Une partie est un objet qui importe ou exporte une valeur, y compris lui-même. Un catalogue fournit une collection de parties disponibles dans une source donnée. Le conteneur de composition utilise les parties fournies par un catalogue pour exécuter la composition, la liaison d’importations à des exportations.

- Importations et exportations

     Les importations et les exportations sont un moyen de communication utilisé par les composants. Lors d'une importation, le composant spécifie qu'il a besoin d'une valeur ou d'un objet en particulier et, lors d'une exportation, il indique la disponibilité d'une valeur. Chaque importation est associée à une liste d'exportations par l'intermédiaire de son contrat.

## <a name="next-steps"></a>Étapes suivantes

Pour télécharger le code complet pour cet exemple, consultez [l’échantillon SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).

 Pour obtenir plus d’informations et des exemples de code, consultez [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef). Pour obtenir une liste des types MEF, consultez l'espace de noms <xref:System.ComponentModel.Composition?displayProperty=nameWithType>.
