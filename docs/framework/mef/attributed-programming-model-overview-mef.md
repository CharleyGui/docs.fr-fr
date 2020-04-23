---
title: Vue d'ensemble du modèle de programmation par attributs (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
ms.openlocfilehash: c6b1093d2e821a55cc5513b077a270748a780b71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347630"
---
# <a name="attributed-programming-model-overview-mef"></a>Vue d'ensemble du modèle de programmation par attributs (MEF)

Dans Managed Extensibility Framework (MEF), un *modèle de programmation* est une méthode particulière qui permet de définir l'ensemble d'objets conceptuels sur lequel MEF fonctionne. Ces objets conceptuels incluent des composants, des importations et des exportations. MEF utilise ces objets mais ne spécifie pas comment ils doivent être représentés. Par conséquent, une grande variété de modèles de programmation sont possibles, y compris des modèles de programmation personnalisés.

Le modèle de programmation par défaut utilisé dans MEF est le *modèle de programmation avec attributs*. Dans le modèle de programmation avec attributs, les composants, les importations, les exportations et les autres objets sont définis avec des attributs qui décorent les classes .NET Framework ordinaires. Cette rubrique explique comment utiliser les attributs fournis par le modèle de programmation avec attributs pour créer une application MEF.

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a>Concepts de base liés aux importations et exportations

Une *exportation* est une valeur qu'un composant fournit à d'autres composants dans le conteneur, et une *importation* est une spécification exprimée par un composant au conteneur, qui doit être remplie à partir des exportations disponibles. Dans le modèle de programmation avec attributs, les importations et les exportations sont déclarées en décorant des classes ou des membres avec les attributs `Import` et `Export` . L'attribut `Export` peut décorer une classe, un champ, une propriété ou une méthode, tandis que l'attribut `Import` peut décorer un champ, une propriété ou un paramètre de constructeur.

Pour qu'une importation soit mise en correspondance avec une exportation, l'importation et l'exportation doivent avoir le même *contrat*. Le contrat se compose d'une chaîne, appelée *nom de contrat*, et du titre de l'objet exporté ou importé, appelé *type de contrat*. Il faut que le nom de contrat et le type de contrat correspondent tous les deux pour qu'une exportation soit considérée comme satisfaisant une importation particulière.

Un seul ou les deux paramètres de contrat peuvent être implicites ou explicites. Le code suivant illustre une classe qui déclare une importation élémentaire.

```vb
Public Class MyClass1
    <Import()>
    Public Property MyAddin As IMyAddin
End Class
```

```csharp
public class MyClass
{
    [Import]
    public IMyAddin MyAddin { get; set; }
}
```

Dans cette importation, l'attribut `Import` n'a pas de type de contrat ni de paramètre de nom de contrat joint. Par conséquent, ces deux paramètres sont déduits de la propriété décorée. Dans ce cas, le type de contrat est `IMyAddin`et le nom de contrat est une chaîne unique créée à partir du type de contrat. (En d'autres termes, le nom de contrat correspond uniquement aux exportations dont les noms sont également déduits du type `IMyAddin`.)

Le code ci-dessous illustre une exportation qui correspond à l'importation précédente.

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

Dans cette exportation, le type de contrat est `IMyAddin` car il est spécifié en tant que paramètre de l'attribut `Export` . Le type exporté doit être identique au type de contrat, dériver du type de contrat ou implémenter le type de contrat s'il s'agit d'une interface. Dans cette exportation, le type `MyLogger` réel implémente l'interface `IMyAddin`. Le nom de contrat est déduit du type de contrat, ce qui signifie que cette exportation correspondra à l'importation précédente.

> [!NOTE]
> Les exportations et importations doivent habituellement être déclarées sur des classes publiques ou des membres publics. D'autres déclarations sont prises en charge, mais l'exportation ou l'importation d'un membre privé, protégé ou interne interrompt le modèle d'isolation pour le composant et n'est donc pas recommandée.

Le type de contrat doit correspondre exactement pour que l'exportation et l'importation soient considérées concordantes. Considérons l'exportation suivante.

```vb
<Export()> 'WILL NOT match the previous import!
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export] //WILL NOT match the previous import!
public class MyLogger : IMyAddin { }
```

Dans cette exportation, le type de contrat est `MyLogger` et non pas `IMyAddin`. Bien que `MyLogger` implémente `IMyAddin`, et pourrait donc être casté en un objet `IMyAddin` , cette exportation ne correspond pas à l'importation précédente, car les types de contrat ne sont pas identiques.

En règle générale, il n'est pas nécessaire de spécifier le nom de contrat et la plupart des contrats doivent être définis en termes de type de contrat et de métadonnées. Toutefois, dans certaines circonstances, il est important de spécifier directement le nom de contrat. Le cas le plus courant est quand une classe exporte plusieurs valeurs qui partagent un type commun, telles que des primitives. Le nom de contrat peut être spécifié comme premier paramètre de l'attribut `Import` ou `Export` . Le code suivant illustre une importation et une exportation avec `MajorRevision`comme nom de contrat spécifié.

```vb
Public Class MyExportClass

    'This one will match
    <Export("MajorRevision")>
    Public ReadOnly Property MajorRevision As Integer
        Get
            Return 4
        End Get
    End Property

    <Export("MinorRevision")>
    Public ReadOnly Property MinorRevision As Integer
        Get
            Return 16
        End Get
    End Property
End Class
```

```csharp
public class MyClass
{
    [Import("MajorRevision")]
    public int MajorRevision { get; set; }
}

public class MyExportClass
{
    [Export("MajorRevision")] //This one will match.
    public int MajorRevision = 4;

    [Export("MinorRevision")]
    public int MinorRevision = 16;
}
```

Si le type de contrat n'est pas spécifié, il est encore déduit du type de l'importation ou de l'exportation. Toutefois, même si le nom de contrat est spécifié explicitement, le type de contrat doit également correspondre exactement pour que l'importation et l'exportation soit considérées concordantes. Par exemple, si le champ `MajorRevision` était une chaîne, les types de contrat déduits ne correspondraient pas et l'exportation ne correspondrait pas à l'importation, bien qu'ils aient le même nom de contrat.

### <a name="importing-and-exporting-a-method"></a>Importation et exportation d'une méthode

L'attribut `Export` peut également décorer une méthode, de la même façon qu'une classe, une propriété ou une fonction. Les exportations de méthode doivent spécifier un type de contrat ou un nom de contrat, car le type ne peut pas être déduit. Le type spécifié peut être un délégué personnalisé ou un type générique, tel que `Func`. La classe suivante exporte une méthode nommée `DoSomething`.

```vb
Public Class MyAddin

    'Explicitly specifying a generic type
    <Export(GetType(Func(Of Integer, String)))>
    Public Function DoSomething(ByVal TheParam As Integer) As String
        Return Nothing 'Function body goes here
    End Function

End Class
```

```csharp
public class MyAddin
{
    //Explicitly specifying a generic type.
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

Dans cette classe, la méthode `DoSomething` accepte un paramètre unique `int` et retourne une `string`. Pour correspondre à cette exportation, le composant d'importation doit déclarer un membre approprié. La classe suivante importe la méthode `DoSomething` .

```vb
Public Class MyClass1

    'Contract name must match!
    <Import()>
    Public Property MajorRevision As Func(Of Integer, String)
End Class
```

```csharp
public class MyClass
{
    [Import] //Contract name must match!
    public Func<int, string> DoSomething { get; set; }
}
```

Pour plus d'informations sur l'utilisation de l'objet `Func<T, T>` , consultez <xref:System.Func%602>.

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a>Types d'importations

MEF prend en charge plusieurs types d'importations, y compris des importations dynamiques, différées, requises et facultatives.

### <a name="dynamic-imports"></a>Importations dynamiques

Dans certains cas, la classe d'importation peut correspondre à des exportations d'un type quelconque, dotées d'un nom de contrat particulier. Dans ce scénario, la classe peut déclarer une *importation dynamique*. L'importation suivante correspond à toute exportation dont le nom de contrat est « TheString ».

```vb
Public Class MyClass1

    <Import("TheString")>
    Public Property MyAddin

End Class
```

```csharp
public class MyClass
{
    [Import("TheString")]
    public dynamic MyAddin { get; set; }
}
```

Quand le type de contrat est déduit du mot clé `dynamic` , il correspond à tout type de contrat. Dans ce cas, une importation doit **toujours** spécifier un nom de contrat à respecter. (Si aucun nom de contrat n’est spécifié, l’importation sera considérée comme ne correspondant à aucune exportation.) Les deux exportations suivantes correspondent à l’importation précédente.

```vb
<Export("TheString", GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class

<Export("TheString")>
Public Class MyToolbar

End Class
```

```csharp
[Export("TheString", typeof(IMyAddin))]
public class MyLogger : IMyAddin { }

[Export("TheString")]
public class MyToolbar { }
```

De toute évidence, la classe d'importation doit être préparée pour traiter un objet de type arbitraire.

### <a name="lazy-imports"></a>Importations différées

Dans certains cas, la classe d'importation peut exiger une référence indirecte à l'objet importé, afin que l'objet ne soit pas instancié immédiatement. Dans ce scénario, la classe peut déclarer une *importation différée* en utilisant un type de contrat `Lazy<T>`. La propriété d'importation suivante déclare une importation différée.

```vb
Public Class MyClass1

    <Import()>
    Public Property MyAddin As Lazy(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [Import]
    public Lazy<IMyAddin> MyAddin { get; set; }
}
```

Du point de vue du moteur de composition, le type de contrat `Lazy<T>` est considéré comme identique au type de contrat `T`. Par conséquent, l'importation précédente correspond à l'exportation suivante.

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

Le nom de contrat et le type de contrat peuvent être spécifiés dans l'attribut `Import` pour une importation différée, comme cela a été décrit plus tôt dans la section « Concepts de base liés aux importations et exportations ».

### <a name="prerequisite-imports"></a>Importations requises

Les composants MEF exportés sont généralement créés par le moteur de composition, en réponse à une demande directe ou au besoin de remplir une importation dotée d'une correspondance. Par défaut, lors de la création d'un composant, le moteur de composition utilise le constructeur sans paramètre. Pour que le moteur utilise un autre constructeur, vous pouvez le marquer avec l'attribut `ImportingConstructor` .

Chaque composant peut faire utiliser un seul constructeur au moteur de composition. Ne fournir aucun constructeur sans paramètre ni aucun attribut `ImportingConstructor`, ou fournir plusieurs attributs `ImportingConstructor`, génère une erreur.

Pour remplir les paramètres d'un constructeur marqué avec l'attribut `ImportingConstructor` , tous ces paramètres sont automatiquement déclarés en tant qu'importations. Il s'agit d'une méthode pratique pour déclarer des importations utilisées pendant l'initialisation des composants. La classe suivante utilise `ImportingConstructor` pour déclarer une importation.

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
    'because the ImportingConstructor
    'attribute is present.
    Public Sub New()

    End Sub

    'This constructor will be used.
    'An import with contract type IMyAddin
    'is declared automatically.
    <ImportingConstructor()>
    Public Sub New(ByVal MyAddin As IMyAddin)
        _theAddin = MyAddin
    End Sub

End Class
```

```csharp
public class MyClass
{
    private IMyAddin _theAddin;

    //Parameterless constructor will NOT be
    //used because the ImportingConstructor
    //attribute is present.
    public MyClass() { }

    //This constructor will be used.
    //An import with contract type IMyAddin is
    //declared automatically.
    [ImportingConstructor]
    public MyClass(IMyAddin MyAddin)
    {
        _theAddin = MyAddin;
    }
}
```

Par défaut, l'attribut `ImportingConstructor` utilise des types de contrat et des noms de contrat déduits pour toutes les importations de paramètres. Il est possible de remplacer cela en décorant les paramètres avec des attributs `Import` , qui peuvent alors définir explicitement le type de contrat et le nom de contrat. Le code ci-dessous illustre un constructeur qui utilise cette syntaxe pour importer une classe dérivée à la place d'une classe parente.

```vb
<ImportingConstructor()>
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)

End Sub
```

```csharp
[ImportingConstructor]
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)
{
    _theAddin = MyAddin;
}
```

En particulier, vous devez être prudent avec les paramètres de collection. Par exemple, si vous spécifiez `ImportingConstructor` sur un constructeur avec un paramètre de type `IEnumerable<int>`, l'importation correspond à une exportation unique de type `IEnumerable<int>`, à la place d'un ensemble d'exportations de type `int`. Pour établir une correspondance avec un ensemble d'exportations de type `int`, vous devez décorer le paramètre avec l'attribut `ImportMany` .

Les paramètres déclarés en tant qu'importations par l'attribut `ImportingConstructor` sont également marqués en tant qu' *importations requises*. MEF permet normalement aux exportations et importations de former un *cycle*. Par exemple, dans un cycle, l’objet A importe l’objet B, qui importe à son tour l’objet A. Dans des circonstances ordinaires, un cycle n’est pas un problème et le conteneur de composition construit les deux objets normalement.

Quand une valeur importée est requise par le constructeur d'un composant, cet objet ne peut pas participer à un cycle. Si l'objet A exige que l'objet B soit construit avant de pouvoir être construit lui-même, et que l'objet B importe l'objet A, il est impossible de résoudre le cycle et une erreur de composition survient. Les importations déclarées sur des paramètres de constructeur sont, par conséquent, des importations prérequises, qui doivent toutes être remplies avant qu'aucune des exportations issues de l'objet qui les requiert puisse être utilisée.

### <a name="optional-imports"></a>Importations facultatives

L'attribut `Import` spécifie une exigence pour que le composant fonctionne. Si une importation ne peut pas être satisfaite, la composition de ce composant échouera et le composant ne sera pas disponible.

Vous pouvez définir une importation comme *facultative* en utilisant la propriété `AllowDefault` . Dans ce cas, la composition fonctionnera même si l’importation ne correspond à aucune exportation disponible, et la propriété d’importation sera définie sur la valeur par défaut pour son type`null` de propriété (pour `false` les propriétés d’objet, pour les valeurs booléennes ou zéro pour les propriétés numériques.) La classe suivante utilise une importation facultative.

```vb
Public Class MyClass1

    <Import(AllowDefault:=True)>
    Public Property thePlugin As Plugin

    'If no matching export is available,
    'thePlugin will be set to null.
End Class
```

```csharp
public class MyClass
{
    [Import(AllowDefault = true)]
    public Plugin thePlugin { get; set; }

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a>Importation de plusieurs objets

L'attribut `Import` sera composé avec succès uniquement lorsqu'il correspondra à une seule exportation. Les autres cas génèrent une erreur de composition. Pour importer plusieurs exportations correspondant au même contrat, utilisez l'attribut `ImportMany` . Les importations marquées de cet attribut sont toujours facultatives. Par exemple, la composition n'échouera pas si aucune exportation correspondante n'est présente. La classe suivante importe un nombre quelconque d'exportations de type `IMyAddin`.

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<IMyAddin> MyAddin { get; set; }
}
```

Il est possible d'accéder au tableau importé en utilisant les méthodes et la syntaxe `IEnumerable<T>` ordinaires. Il est également possible d'utiliser un tableau ordinaire (`IMyAddin[]`) à la place.

Ce modèle peut être très important quand vous l'utilisez en association avec la syntaxe `Lazy<T>` . Par exemple, en utilisant `ImportMany`, `IEnumerable<T>`et `Lazy<T>`, vous pouvez importer des références indirectes à un nombre quelconque d'objets et instancier uniquement ceux qui deviennent nécessaires. La classe suivante illustre ce modèle.

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }
}
```

<a name="avoiding_discovery"></a>

## <a name="avoiding-discovery"></a>Éviter la découverte

Dans certains cas, vous pouvez souhaiter empêcher la découverte d'un composant dans le cadre d'un catalogue. Par exemple, ce composant peut être une classe de base qui ne sera pas utilisée, mais dont les enfants hériteront. Il existe deux façons d'accomplir cela. Vous pouvez utiliser le mot clé `abstract` sur la classe du composant. Les classes abstraites ne fournissent jamais d'exportations, bien qu'elles puissent fournir des exportations héritées aux classes qui dérivent d'elles.

Si la classe ne peut pas être rendue abstraite, vous pouvez la décorer avec l'attribut `PartNotDiscoverable` . Un composant décoré avec cet attribut ne sera inclus dans aucun catalogue. L'exemple suivant illustre ces modèles : `DataOne` sera découvert par le catalogue. Comme `DataTwo` est abstrait, il ne sera pas découvert. Comme `DataThree` utilisait l'attribut `PartNotDiscoverable` , il ne sera pas découvert.

```vb
<Export()>
Public Class DataOne
    'This part will be discovered
    'as normal by the catalog.
End Class

<Export()>
Public MustInherit Class DataTwo
    'This part will not be discovered
    'by the catalog.
End Class

<PartNotDiscoverable()>
<Export()>
Public Class DataThree
    'This part will also not be discovered
    'by the catalog.
End Class
```

```csharp
[Export]
public class DataOne
{
    //This part will be discovered
    //as normal by the catalog.
}

[Export]
public abstract class DataTwo
{
    //This part will not be discovered
    //by the catalog.
}

[PartNotDiscoverable]
[Export]
public class DataThree
{
    //This part will also not be discovered
    //by the catalog.
}
```

<a name="metadata_and_metadata_views"></a>

## <a name="metadata-and-metadata-views"></a>Métadonnées et vues des métadonnées

Les exportations peuvent fournir des informations supplémentaires sur elles-mêmes, appelées *métadonnées*. Les métadonnées peuvent être utilisées pour acheminer des propriétés de l'objet exporté jusqu'au composant d'importation. Le composant d'importation peut utiliser ces données pour décider quelles exportations utiliser ou pour rassembler des informations sur une exportation sans avoir à la construire. Pour cette raison, une importation doit être différée pour utiliser des métadonnées.

Pour utiliser des métadonnées, vous déclarez en général une interface connue en tant que *vue de métadonnées*, qui déclare les métadonnées qui seront disponibles. L'interface de la vue de métadonnées doit posséder seulement des propriétés et ces dernières doivent posséder des accesseurs `get` . L'interface suivante est un exemple de vue de métadonnées.

```vb
Public Interface IPluginMetadata

    ReadOnly Property Name As String

    <DefaultValue(1)>
    ReadOnly Property Version As Integer

End Interface
```

```csharp
public interface IPluginMetadata
{
    string Name { get; }

    [DefaultValue(1)]
    int Version { get; }
}
```

Il est également possible d'utiliser une collection générique, `IDictionary<string, object>`, comme vue de métadonnées, mais cela annule les avantages de la vérification de type et devrait être évité.

En règle générale, toutes les propriétés nommées dans la vue de métadonnées sont requises et toute exportation qui ne les fournit pas sera considérée comme non concordante. L'attribut `DefaultValue` spécifie qu'une propriété est facultative. Si la propriété n'est pas incluse, il lui sera attribué la valeur par défaut spécifiée comme paramètre de `DefaultValue`. Voici deux classes différentes, décorées avec des métadonnées. Ces deux classes correspondent à la vue de métadonnées précédente.

```vb
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class MyLogger
    Implements IPlugin

End Class

'Version is not required because of the DefaultValue
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Disk Writer")>
Public Class DWriter
    Implements IPlugin

End Class
```

```csharp
[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
}

[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Disk Writer")]
    //Version is not required because of the DefaultValue
public class DWriter : IPlugin
{
}
```

Les métadonnées sont exprimées après l'attribut `Export` au moyen de l'attribut `ExportMetadata` . Chaque unité de métadonnées est composée d'une paire nom/valeur. La partie du nom des métadonnées doit correspondre au nom de la propriété appropriée dans la vue de métadonnées, et la valeur sera attribuée à cette propriété.

C'est l'importateur qui spécifie la vue de métadonnées, le cas échéant, qui sera utilisée. Une importation avec des métadonnées est déclarée en tant qu'importation différée, avec l'interface des métadonnées comme second paramètre de type de `Lazy<T,T>`. La classe suivante importe le composant précédent avec les métadonnées.

```vb
Public Class Addin

    <Import()>
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)
End Class
```

```csharp
public class Addin
{
    [Import]
    public Lazy<IPlugin, IPluginMetadata> plugin;
}
```

Dans de nombreux cas, vous souhaiterez associer des métadonnées avec l'attribut `ImportMany` , afin d'analyser les importations disponibles et d'en choisir et instancier une seule, ou de filtrer une collection pour satisfaire une condition donnée. La classe suivante instancie uniquement les objets `IPlugin` ayant une valeur `Name` égale à "Logger".

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
                logger = Plugin.Value
            End If
        Next
        Return logger
    End Function

End Class
```

```csharp
public class User
{
    [ImportMany]
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a>Héritage des importations et exportations

Si une classe hérite d'un composant, elle peut également devenir un composant. Les importations sont toujours héritées par les sous-classes. Par conséquent, une sous-classe d'un composant est toujours un composant, avec les mêmes importations que sa classe parente.

Les exportations déclarées à l'aide de l'attribut `Export` ne sont pas héritées par les sous-classes. Toutefois, un composant peut s'exporter lui-même en utilisant l'attribut `InheritedExport` . Les sous-classes du composant hériteront et fourniront la même exportation, y compris le nom de contrat et le type de contrat. À la différence d'un attribut `Export` , `InheritedExport` peut être appliqué uniquement au niveau de la classe et non pas au niveau du membre. Par conséquent, les exportations au niveau d'un membre ne peuvent jamais être héritées.

Les quatre classes suivantes illustrent les principes de l'héritage des importations et des exportations. `NumTwo` hérite de `NumOne`, si bien que `NumTwo` importera `IMyData`. Les exportations ordinaires ne sont pas héritées, si bien que `NumTwo` n'exportera rien. `NumFour` hérite de `NumThree`. Comme `NumThree` a utilisé `InheritedExport`, `NumFour` possède une exportation dotée du type de contrat `NumThree`. Les exportations au niveau d'un membre ne sont jamais héritées, si bien que `IMyData` n'est pas exporté.

```vb
<Export()>
Public Class NumOne
    <Import()>
    Public Property MyData As IMyData
End Class

Public Class NumTwo
    Inherits NumOne

    'Imports are always inherited, so NumTwo will
    'Import IMyData

    'Ordinary exports are not inherited, so
    'NumTwo will NOT export anything.  As a result it
    'will not be discovered by the catalog!

End Class

<InheritedExport()>
Public Class NumThree

    <Export()>
    Public Property MyData As IMyData

    'This part provides two exports, one of
    'contract type NumThree, and one of
    'contract type IMyData.

End Class

Public Class NumFour
    Inherits NumThree

    'Because NumThree used InheritedExport,
    'this part has one export with contract
    'type NumThree.

    'Member-level exports are never inherited,
    'so IMyData is not exported.

End Class
```

```csharp
[Export]
public class NumOne
{
    [Import]
    public IMyData MyData { get; set; }
}

public class NumTwo : NumOne
{
    //Imports are always inherited, so NumTwo will
    //import IMyData.

    //Ordinary exports are not inherited, so
    //NumTwo will NOT export anything. As a result it
    //will not be discovered by the catalog!
}

[InheritedExport]
public class NumThree
{
    [Export]
    Public IMyData MyData { get; set; }

    //This part provides two exports, one of
    //contract type NumThree, and one of
    //contract type IMyData.
}

public class NumFour : NumThree
{
    //Because NumThree used InheritedExport,
    //this part has one export with contract
    //type NumThree.

    //Member-level exports are never inherited,
    //so IMyData is not exported.
}
```

Si des métadonnées sont associées à un attribut `InheritedExport` , elles seront également héritées. (Pour plus d’informations, consultez la section « métadonnées et vues de métadonnées » précédentes.) Les métadonnées héritées ne peuvent pas être modifiées par la sous-classe. Toutefois, en redéclarant l'attribut `InheritedExport` avec les mêmes nom de contrat et type de contrat, mais avec de nouvelles métadonnées, la sous-classe peut remplacer les métadonnées héritées par de nouvelles métadonnées. La classe suivante illustre ce principe. Le composant `MegaLogger` hérite de `Logger` et inclut l'attribut `InheritedExport` . Comme `MegaLogger` redéclare de nouvelles métadonnées nommées Status, il n'hérite pas les métadonnées Name et Version de `Logger`.

```vb
<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class Logger
    Implements IPlugin

    'Exports with contract type IPlugin
    'and metadata "Name" and "Version".
End Class

Public Class SuperLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Name" and "Version", exactly the same
    'as the Logger class.

End Class

<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Status", "Green")>
Public Class MegaLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Status" only. Re-declaring
    'the attribute replaces all metadata.

End Class
```

```csharp
[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version".
}

public class SuperLogger : Logger
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version", exactly the same
    //as the Logger class.
}

[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Status", "Green")]
public class MegaLogger : Logger        {
    //Exports with contract type IPlugin and
    //metadata "Status" only. Re-declaring
    //the attribute replaces all metadata.
}
```

Lors de la redéclaration de l'attribut `InheritedExport` pour remplacer les métadonnées, assurez-vous que les types de contrat sont les mêmes. (Dans l’exemple précédent, `IPlugin` est le type de contrat.) Si elles diffèrent, au lieu de se substituer, le deuxième attribut crée une deuxième exportation indépendante à partir de la partie. En règle générale, cela signifie que vous devez spécifier explicitement le type de contrat quand vous remplacez un attribut `InheritedExport` , comme illustré dans l'exemple précédent.

Comme les interfaces ne peuvent pas être instanciées directement, elles ne peuvent généralement pas être décorées avec des attributs `Export` ou `Import` . Toutefois, une interface peut être décorée avec un attribut `InheritedExport` au niveau de l'interface et cette exportation, ainsi que toutes les métadonnées associées, sera héritée par toutes les classes d'implémentation. Toutefois, l'interface elle-même ne sera pas disponible en tant que composant.

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a>Attributs d'exportation personnalisés

Il est possible d'étendre les attributs d'exportation élémentaires, `Export` et `InheritedExport`, pour inclure des métadonnées en tant que propriétés d'attribut. Cette technique est utile pour appliquer des métadonnées similaires à de nombreux composants ou pour créer une arborescence d'héritage des attributs de métadonnées.

Un attribut personnalisé peut spécifier le type de contrat, le nom de contrat ou d'autres métadonnées. Pour définir un attribut personnalisé, une classe qui hérite d' `ExportAttribute` (ou d' `InheritedExportAttribute`) doit être décorée avec l'attribut `MetadataAttribute` . La classe suivante définit un attribut personnalisé.

```vb
<MetadataAttribute()>
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>
Public Class MyAttribute
    Inherits ExportAttribute

    Public Property MyMetadata As String

    Public Sub New(ByVal myMetadata As String)
        MyBase.New(GetType(IMyAddin))

        myMetadata = myMetadata
    End Sub

End Class
```

```csharp
[MetadataAttribute]
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]
public class MyAttribute : ExportAttribute
{
    public MyAttribute(string myMetadata)
        : base(typeof(IMyAddin))
    {
        MyMetadata = myMetadata;
    }

    public string MyMetadata { get; private set; }
}
```

Cette classe définit un attribut personnalisé nommé `MyAttribute` avec le type de contrat `IMyAddin` et certaines métadonnées nommées `MyMetadata`. Toutes les propriétés figurant dans une classe marquée avec l'attribut `MetadataAttribute` sont considérées comme des métadonnées définies dans l'attribut personnalisé. Les deux déclarations suivantes sont équivalentes.

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

Dans la première déclaration, le type de contrat et les métadonnées sont explicitement définis. Dans la seconde déclaration, le type de contrat et les métadonnées sont implicites dans l'attribut personnalisé. Notamment dans les cas où une grande quantité de métadonnées identiques doivent être appliquées à de nombreux composants (par exemple, les informations d'auteur ou de copyright), l'utilisation d'un attribut personnalisé permet d'économiser beaucoup de temps et d'éviter la duplication. En outre, des arborescences d'héritage des attributs personnalisés peuvent être créées pour permettre les variations.

Pour créer des métadonnées facultatives dans un attribut personnalisé, vous pouvez utiliser l'attribut `DefaultValue` . Quand cet attribut est appliqué à une propriété dans une classe d'attributs personnalisée, il spécifie que la propriété décorée est facultative et n'est pas tenue d'être fournie par un exportateur. Si aucune valeur n'est fournie pour la propriété, il lui sera attribué la valeur par défaut pour son type de propriété (habituellement `null`, `false`ou 0.)

<a name="creation_policies"></a>

## <a name="creation-policies"></a>Stratégies de création

Quand un composant spécifie une importation et qu'une composition est effectuée, le conteneur de composition essaie de trouver une exportation correspondante. S'il parvient à mettre en correspondance l'importation et une exportation, le membre d'importation est défini sur une instance de l'objet exporté. L'origine de cette instance est contrôlée par la *stratégie de création*du composant d'exportation.

Les deux stratégies de création possibles sont *partagée* et *non partagée*. Un composant doté d'une stratégie de création partagée sera partagé entre chaque importation dans le conteneur pour un composant avec ce contrat. Quand le moteur de composition trouve une correspondance et doit définir une propriété d'importation, il instancie une nouvelle copie du composant seulement si aucune n'existe encore. Dans le cas contraire, il fournit la copie existante. Cela signifie que de nombreux objets peuvent avoir des références au même composant. De tels composants ne doivent pas s'appuyer sur l'état interne susceptible d'être modifié à partir de nombreux emplacements. Cette stratégie est appropriée pour les composants statiques, les composants qui fournissent des services et les composants qui consomment beaucoup de mémoire ou d'autres ressources.

Un composant doté de la stratégie de création non partagée est créé chaque fois qu'une importation correspondante est trouvée pour l'une de ses exportations. Une nouvelle copie est donc instanciée pour chaque importation dans le conteneur qui correspond à l'un des contrats exportés du composant. L'état interne de ces copies ne sera pas partagé. Cette stratégie est appropriée pour les composants pour lesquels chaque importation exige son propre état interne.

L'importation et l'exportation peuvent spécifier la stratégie de création d'un composant, parmi les valeurs `Shared`, `NonShared`et `Any`. La valeur par défaut est `Any` pour les importations et les exportations. Une exportation qui spécifie `Shared` ou `NonShared` correspondra uniquement à une importation qui spécifie la même chose ou `Any`. De même, une importation qui spécifie `Shared` ou `NonShared` correspondra uniquement à une exportation qui spécifie la même chose ou `Any`. Des importations et des exportations dotées de stratégies de création incompatibles ne sont pas considérées comme concordantes, de la même façon qu'une importation et une exportation dont les noms de contrat ou les types de contrat ne correspondent pas. Si l'importation et l'exportation spécifient `Any`, ou ne spécifient pas de stratégie de création et sont dotées par défaut de la stratégie `Any`, la stratégie de création sera partagée par défaut.

L'exemple suivant illustre des importations et des exportations qui spécifient des stratégies de création. `PartOne` ne spécifie aucune stratégie de création. La valeur par défaut est donc `Any`. `PartTwo` ne spécifie aucune stratégie de création. La valeur par défaut est donc `Any`. Comme l'importation et l'exportation présentent la valeur par défaut `Any`, `PartOne` est partagé. `PartThree` spécifie une stratégie de création `Shared` , de sorte que `PartTwo` et `PartThree` partageront la même copie de `PartOne`. `PartFour` spécifie une stratégie de création `NonShared` , de sorte que `PartFour` ne sera pas partagé dans `PartFive`. `PartSix` spécifie une stratégie de création `NonShared` . `PartFive` et `PartSix` recevront chacun des copies distinctes de `PartFour`. `PartSeven` spécifie une stratégie de création `Shared` . Comme il n'existe aucun `PartFour` exporté avec une stratégie de création `Shared`, l'importation `PartSeven` ne correspond à rien et ne sera pas remplie.

```vb
<Export()>
Public Class PartOne
    'The default creation policy for an export is Any.
End Class

Public Class PartTwo

    <Import()>
    Public Property partOne As PartOne

    'The default creation policy for an import is Any.
    'If both policies are Any, the part will be shared.

End Class

Public Class PartThree

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partOne As PartOne

    'The Shared creation policy is explicitly specified.
    'PartTwo and PartThree will receive references to the
    'SAME copy of PartOne.

End Class

<Export()>
<PartCreationPolicy(CreationPolicy.NonShared)>
Public Class PartFour
    'The NonShared creation policy is explicitly specified.
End Class

Public Class PartFive

    <Import()>
    Public Property partFour As PartFour

    'The default creation policy for an import is Any.
    'Since the export's creation policy was explicitly
    'defined, the creation policy for this property will
    'be non-shared.

End Class

Public Class PartSix

    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>
    Public Property partFour As PartFour

    'Both import and export specify matching creation
    'policies.  PartFive and PartSix will each receive
    'SEPARATE copies of PartFour, each with its own
    'internal state.

End Class

Public Class PartSeven

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partFour As PartFour

    'A creation policy mismatch.  Because there is no
    'exported PartFour with a creation policy of Shared,
    'this import does not match anything and will not be
    'filled.

End Class
```

```csharp
[Export]
public class PartOne
{
    //The default creation policy for an export is Any.
}

public class PartTwo
{
    [Import]
    public PartOne partOne { get; set; }

    //The default creation policy for an import is Any.
    //If both policies are Any, the part will be shared.
}

public class PartThree
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartOne partOne { get; set; }

    //The Shared creation policy is explicitly specified.
    //PartTwo and PartThree will receive references to the
    //SAME copy of PartOne.
}

[Export]
[PartCreationPolicy(CreationPolicy.NonShared)]
public class PartFour
{
    //The NonShared creation policy is explicitly specified.
}

public class PartFive
{
    [Import]
    public PartFour partFour { get; set; }

    //The default creation policy for an import is Any.
    //Since the export's creation policy was explicitly
    //defined, the creation policy for this property will
    //be non-shared.
}

public class PartSix
{
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]
    public PartFour partFour { get; set; }

    //Both import and export specify matching creation
    //policies.  PartFive and PartSix will each receive
    //SEPARATE copies of PartFour, each with its own
    //internal state.
}

public class PartSeven
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartFour partFour { get; set; }

    //A creation policy mismatch.  Because there is no
    //exported PartFour with a creation policy of Shared,
    //this import does not match anything and will not be
    //filled.
}
```

<a name="life_cycle_and_disposing"></a>

## <a name="life-cycle-and-disposing"></a>Cycle de vie et suppression

Comme les composants sont hébergés dans le conteneur de composition, leur cycle de vie peut être plus complexe que celui d'objets ordinaires. Les composants peuvent implémenter deux interfaces importantes liées au cycle de vie : `IDisposable` et `IPartImportsSatisfiedNotification`.

Les composants pour lesquels des opérations doivent être effectuées au moment de l'arrêt ou qui ont besoin de libérer des ressources doivent implémenter `IDisposable`, comme d'habitude pour les objets .NET Framework. Toutefois, étant donné que le conteneur crée et tient à jour des références aux composants, seul le conteneur qui détient un composant doit appeler la méthode `Dispose` sur ce dernier. Le conteneur lui-même implémente `IDisposable`et, dans le cadre de son nettoyage dans `Dispose` , il appellera `Dispose` sur tous les composants qu'il détient. Pour cette raison, vous devez toujours supprimer le conteneur de composition quand lui et tous les composants qu'il détient ne sont plus requis.

Pour les conteneurs de composition durables, la consommation de mémoire par les composants dotés d'une stratégie de création non partagée peut devenir un problème. Ces composants non partagés peuvent être créés plusieurs fois et ne seront pas supprimés temps que le conteneur lui-même ne le sera pas. Pour gérer cela, le conteneur fournit la méthode `ReleaseExport` . L'appel de cette méthode sur une exportation non partagée supprime cette exportation du conteneur de composition et supprime ce dernier. Les composants utilisés seulement par l'exportation supprimée, et ainsi de suite jusqu'au bas de l'arborescence, sont également supprimés. De cette manière, les ressources peuvent être récupérées sans que le conteneur de composition lui-même soit supprimé.

`IPartImportsSatisfiedNotification` contient une méthode nommée `OnImportsSatisfied`. Cette méthode est appelée par le conteneur de composition sur tous les composants qui implémentent l'interface, une fois la composition terminée et les importations du composant prêtes à l'emploi. Les composants sont créés par le moteur de composition pour remplir les importations des autres composants. Avant que les importations d'un composant aient été définies, vous ne pouvez pas effectuer d'initialisation qui manipule ou s'appuie sur des valeurs importées dans le constructeur du composant, à moins que ces valeurs aient été spécifiées en tant que composants prérequis à l'aide de l'attribut `ImportingConstructor` . Ceci est normalement la méthode conseillée mais, dans certains cas, l'injection de constructeur peut ne pas être disponible. Dans ce cas, il est possible d'effectuer l'initialisation dans `OnImportsSatisfied`et le composant doit implémenter `IPartImportsSatisfiedNotification`.

## <a name="see-also"></a>Voir aussi

- [Vidéo Channel 9 : Ouvrir vos applications avec Managed Extensibility Framework](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [Vidéo Channel 9 : Managed Extensibility Framework (MEF) 2.0](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
