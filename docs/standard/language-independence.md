---
title: Indépendance du langage et composants indépendants du langage
description: Découvrez comment développer dans un des nombreux langages pris en charge dans .NET, tels que C#, C++/CLI, F#, IronPython, VB, Visual COBOL et PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 813558299b40e0b90e8047f22b788c8f1419eb5e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504652"
---
# <a name="language-independence-and-language-independent-components"></a>Indépendance du langage et composants indépendants du langage

.NET est indépendant du langage. Cela signifie qu’en tant que développeur, vous pouvez développer dans un des nombreux langages qui ciblent des implémentations de .NET, comme C#, F# et Visual Basic. Vous pouvez accéder aux types et aux membres des bibliothèques de classes développées pour des implémentations de .NET sans avoir à connaître le langage dans lequel ils ont été initialement écrits ni à suivre les conventions du langage d’origine. Si vous êtes un développeur de composants, votre composant est accessible par n’importe quelle application .NET, quelle que soit sa langue.

> [!NOTE]
> Cette première partie de cet article traite de la création de composants indépendants du langage, c’est-à-dire de composants qui peuvent être utilisés par des applications écrites dans n’importe quel langage. Vous pouvez également créer un composant ou une application unique à partir de code source écrit dans plusieurs langages. Consultez [Interopérabilité multilingue](#cross-language-interoperability) dans la deuxième partie de cet article.

Pour interagir entièrement avec d’autres objets écrits dans un langage quelconque, les objets ne doivent exposer aux appelants que les fonctionnalités communes à tous les langages. Cet ensemble commun de fonctionnalités est défini par la spécification CLS (Common Language Specification), qui est un ensemble de règles qui s’appliquent aux assemblys générés. La spécification CLS (Common Language Specification) est définie dans la Partition I, clauses 7 à 11 du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Si votre composant est conforme à la spécification CLS, il est garanti d'être conforme CLS et accessible à partir du code dans les assemblys écrits dans n'importe quel langage de programmation qui prend en charge la spécification CLS. Vous pouvez déterminer si votre composant est conforme à la spécification CLS (Common Language Specification) au moment de la compilation en appliquant l’attribut [CSLCompliantAttribute](xref:System.CLSCompliantAttribute) à votre code source. Pour plus d’informations, consultez [Attribut CLSCompliantAttribute](#the-clscompliantattribute-attribute).

## <a name="cls-compliance-rules"></a>Règles de conformité CLS

Cette section présente les règles de création d'un composant conforme à CLS. Pour obtenir une liste complète des règles, consultez la Partition I, clause 11 du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> La spécification CLS (Common Language Specification) présente chaque règle de conformité CLS telle qu'elle s'applique aux consommateurs (les développeurs qui accèdent par programme à un composant conforme CLS), aux infrastructures (les développeurs qui utilisent un compilateur de langage pour créer des bibliothèques conformes CLS) et aux extendeurs (les développeurs qui créent un outil tel qu'un compilateur de langage ou un analyseur de code qui crée des composants conformes CLS). Cet article se concentre sur les règles applicables aux infrastructures. Notez, toutefois, que certaines des règles qui s’appliquent aux extendeurs peuvent également s’appliquer aux assemblys créés à l’aide de [Reflection. Emit](xref:System.Reflection.Emit).

Pour concevoir un composant indépendant du langage, vous n'avez qu'à appliquer les règles de conformité CLS à l'interface publique de votre composant. Votre implémentation privée n'a pas besoin d'être conforme à la spécification.

> [!IMPORTANT]
> Les règles de conformité CLS s'appliquent uniquement à l'interface publique d'un composant, pas à son implémentation privée.

Par exemple, les entiers non signés autres que [Byte](xref:System.Byte) ne sont pas conformes CLS. Étant donné que la classe `Person` de l’exemple suivant expose une propriété `Age` de type [UInt16](xref:System.UInt16), le code suivant affiche un avertissement du compilateur.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

Vous pouvez rendre la classe Person conforme CLS en remplaçant le type `UInt16` de la propriété `Age` par [Int16](xref:System.Int16), qui est un entier signé 16 bits conforme CLS. Il n'est pas nécessaire de modifier le type du champ privé `personAge`.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

L'interface publique d'une bibliothèque inclut les éléments suivants :

* Définitions des classes publiques.

* Définitions des membres publics des classes publiques et définitions des membres accessibles aux classes dérivées (à savoir, membres protégés).

* Paramètres et types de retour des méthodes publiques des classes publiques, et paramètres et types de retour des méthodes accessibles aux classes dérivées.

Les règles de conformité CLS sont répertoriées dans le tableau suivant. Le texte des règles est repris mot pour mot du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), qui est protégé par copyright 2012 par Ecma International. Vous trouverez des informations plus détaillées sur ces règles dans les sections suivantes.

Category | Consultez | Règle | Numéro de règle
-------- | --- | ---- | -----------
Accessibilité | [Accessibilité des membres](#member-accessibility) | L'accessibilité ne devra pas être changée lors du remplacement de méthodes héritées, sauf en cas de remplacement d'une méthode héritée d'un assembly différent avec accessibilité `family-or-assembly`. Dans ce cas, le remplacement devra posséder l'accessibilité `family`. | 10
Accessibilité | [Accessibilité des membres](#member-accessibility) | La visibilité et l'accessibilité des types et des membres seront déterminées de telle sorte que les types utilisés dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, une méthode publique qui est visible à l'extérieur de son assembly n'aura pas d'argument dont le type est visible uniquement dans l'assembly. La visibilité et l'accessibilité des types composant un type générique instancié utilisé dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, un type générique instancié présent dans la signature d'un membre qui est visible à l'extérieur de l'assembly n'aura pas d'argument générique dont le type est visible uniquement dans l'assembly. | 12
Tableaux | [Tableaux](#arrays) | Les tableaux auront des éléments avec un type conforme à CLS, et toutes les dimensions du tableau auront des limites inférieures égales à zéro. Seul le fait qu'un élément soit un tableau et le type d'élément du tableau seront requis pour distinguer les surcharges. Lorsque la surcharge est basée sur deux ou plusieurs types tableau, les types d’éléments doivent être des types nommés. | 16
Attributs | [Attributs](#attributes) | Les attributs doivent être de type [System.Attribute](xref:System.Attribute) ou d’un type hérité de celui-ci. | 41
Attributs | [Attributs](#attributes) | La spécification CLS autorise uniquement un sous-ensemble des encodages d'attributs personnalisés. Les seuls types qui doivent apparaître dans ces codages sont (voir Partition IV) : [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double) et tout type d’énumération reposant sur un type entier de base conforme CLS. | 34
Attributs | [Attributs](#attributes) | La spécification CLS n'autorise pas les modificateurs obligatoires visibles publiquement (`modreq`, voir Partition II), mais autorise les modificateurs facultatifs (`modopt`, voir Partition II) qu'elle ne comprend pas. | 35
Constructeurs | [Constructeurs](#constructors) | Un constructeur d'objet appellera un constructeur d'instance de sa classe de base avant tout accès aux données d'instance héritées. (Cela ne s'applique pas aux types de valeurs, qui n'ont pas besoin de constructeurs.)  | 21
Constructeurs | [Constructeurs](#constructors) | Un constructeur d'objet ne sera pas appelé sauf dans le cadre de la création d'un objet, et un objet ne sera pas initialisé deux fois. | 22
Énumérations | [Énumérations](#enumerations) | Le type sous-jacent d'une énumération devra être un type d'entier CLS intégré, le nom du champ devra être « valeur__ » et ce champ devra être marqué `RTSpecialName`. |  7
Énumérations | [Énumérations](#enumerations) | Il existe deux sortes distinctes d’énumérations, signalées par la présence ou l’absence de l’attribut personnalisé [System.FlagsAttribute](xref:System.FlagsAttribute) (voir Partition IV, Library). L'un représente des valeurs entières nommées ; l'autre représente les indicateurs binaires nommés qui peuvent être combinés pour générer une valeur sans nom. La valeur d'une `enum` n'est pas limitée aux valeurs spécifiées. |  8
Énumérations | [Énumérations](#enumerations) | Les champs static littéraux d’une énumération auront le type de l’énumération elle-même. |  9
Événements | [Événements](#events) | Les méthodes qui implémentent un événement doivent être marquées `SpecialName` dans les métadonnées. |29
Événements | [Événements](#events) | L’accessibilité d’un événement et de ses accesseurs sera identique. |30
Événements | [Événements](#events) | Les méthodes `add` et `remove` d'un événement devront toutes les deux être présentes ou absentes. |31
Événements | [Événements](#events) | Les `add` `remove` méthodes et d’un événement doivent chacune accepter un paramètre dont le type définit le type de l’événement et qui doit être dérivé de [System. Delegate](xref:System.Delegate). |32
Événements | [Événements](#events) | Les événements adhéreront à un modèle d’attribution de nom spécifique. L’attribut SpecialName dont il est question dans la règle 29 de la spécification CLS doit être ignoré dans les comparaisons de noms appropriées et doit respecter les règles d’identificateur.  |33
Exceptions | [Exceptions](#exceptions) | Les objets levés doivent être de type [System.Exception](xref:System.Exception) ou d’un type hérité de celui-ci. Néanmoins, les méthodes conformes à CLS ne sont pas requises pour bloquer la propagation d'autres types d'exceptions. | 40
Général | [Règles de conformité CLS](#cls-compliance-rules) | Les règles CLS s'appliquent uniquement aux éléments d'un type qui sont accessibles ou visibles en dehors de l'assembly de définition. | 1
Général | [Règles de conformité CLS](#cls-compliance-rules) | Les membres de types non conformes à CLS ne seront pas marqués comme conformes à CLS. | 2
Génériques | [Types et membres génériques](#generic-types-and-members) | Les types imbriqués devront posséder au moins autant de paramètres génériques que le type englobant. Les paramètres génériques d'un type imbriqué ont la même position que les paramètres génériques du type englobant correspondant.  | 42
Génériques | [Types et membres génériques](#generic-types-and-members) | Le nom d’un type générique devra encoder le nombre de paramètres de type déclarés sur le type non imbriqué ou récemment introduits dans le type s’il est imbriqué, selon les règles définies ci-dessus. | 43
Génériques | [Types et membres génériques](#generic-types-and-members) | Un type générique devra redéclarer les contraintes suffisantes afin de garantir que les contraintes sur le type de base ou les interfaces seraient satisfaites par les contraintes de type générique. | 44
Génériques | [Types et membres génériques](#generic-types-and-members) | Les types utilisés comme contraintes sur les paramètres génériques devront eux-mêmes être conformes à CLS. | 45
Génériques | [Types et membres génériques](#generic-types-and-members) | La visibilité et l'accessibilité des membres (y compris des types imbriqués) d'un type générique instancié devront être définies dans l'instanciation spécifique plutôt que dans la déclaration générale du type générique. Sachant cela, les règles de visibilité et d'accessibilité de la règle 12 de la spécification CLS s'appliquent toujours. | 46
Génériques | [Types et membres génériques](#generic-types-and-members) | À chaque méthode générique abstraite ou virtuelle doit correspondre une implémentation concrète (non abstraite) par défaut | 47
Interfaces | [Interfaces](#interfaces) | Les interfaces conformes à CLS ne devront pas nécessiter la définition de méthodes non conformes à CLS pour pouvoir les implémenter. | 18
Interfaces | [Interfaces](#interfaces) | Les interfaces conformes à CLS ne devront pas définir de méthodes statiques ni de champs. | 19
Membres | [Membres de types en général](#type-members-in-general) | Les méthodes et les champs static globaux ne sont pas conformes CLS. | 36
Membres | -- | La valeur d'un champ statique littéral est spécifiée via l'utilisation de métadonnées d'initialisation de champ. Un littéral conforme à CLS doit avoir une valeur spécifiée dans les métadonnées d'initialisation de champ qui est exactement du même type que le littéral (ou du type sous-jacent, si ce littéral est une `enum`). | 13
Membres | [Membres de types en général](#type-members-in-general) | La contrainte vararg ne fait pas partie de la spécification CLS, et la seule convention d’appel prise en charge par la spécification CLS est la convention d’appel managée standard. | 15
Conventions d’affectation de noms | [Conventions d’affectation de noms](#naming-conventions) | Les assemblys doivent suivre l’Annexe 7 du Rapport technique 15 de la norme Unicode 3.0 régissant l’ensemble des caractères autorisés pour lancer les identificateurs et être inclus dans ces derniers. Cette annexe est disponible en ligne sous [Unicode Normalization Forms](https://unicode.org/reports/tr15/) (Formes de normalisation Unicode). Les identificateurs doivent être dans un format canonique défini par la forme C de normalisation Unicode. Dans le cadre de la spécification CLS, deux identificateurs sont les mêmes si leurs mappages en minuscules (comme spécifié par les mappages en minuscules un-à-un insensibles aux paramètres régionaux Unicode) sont identiques. Autrement dit, pour que deux identificateurs soient considérés comme différents dans le cadre de la spécification CLS, ils doivent être différenciés par d’autres éléments que leur casse. Toutefois, pour remplacer une définition héritée, l’infrastructure CLI nécessite l’utilisation de l’encodage exact de la déclaration d’origine. | 4
Surcharge | [Conventions d’affectation de noms](#naming-conventions) | Tous les noms introduits dans une portée conforme CLS doivent être distincts, indépendamment de leur type, sauf quand les noms sont identiques et résolus par surcharge. Par exemple, alors que CTS autorise un type à utiliser le même nom pour une méthode et un champ, CLS ne l’autorise pas. | 5
Surcharge | [Conventions d’affectation de noms](#naming-conventions) | Les champs et les types imbriqués seront distincts par comparaison d'identificateurs seule, même si CTS autorise la distinction de signatures différentes. Les méthodes, les propriétés et les événements qui ont le même nom (par comparaison d’identificateur) ne doivent pas différer uniquement par le type de retour, sauf dans les cas spécifiés dans la règle CLS 39 | 6
Surcharge | [Surcharges](#overloads) | Seules les propriétés et les méthodes peuvent être surchargées. | 37
Surcharge | [Surcharges](#overloads) |Les propriétés et les méthodes peuvent être surchargées en fonction du nombre et des types de leurs paramètres uniquement, à l'exception des opérateurs de conversion nommés `op_Implicit` et `op_Explicit`, qui peuvent également être surchargés selon leur type de retour. | 38
Surcharge | -- | Si deux ou plusieurs méthodes conformes CLS déclarées dans un type ont le même nom et, pour un jeu spécifique d’instanciations de types, ont le même paramètre et les mêmes types de retour, alors toutes ces méthodes sont sémantiquement équivalentes à ces instanciations de type. | 48
Propriétés | [Propriétés](#properties) | Les méthodes qui implémentent les méthodes getter et setter d’une propriété doivent être marquées `SpecialName` dans les métadonnées. | 24
Propriétés | [Propriétés](#properties) | Les accesseurs d’une propriété doivent tous être statiques, virtuels ou être des instances. | 26
Propriétés | [Propriétés](#properties) | Le type d’une propriété devra correspondre au type de retour de la méthode getter et au type du dernier argument de la méthode setter. Les types des paramètres de la propriété devront correspondre aux types des paramètres de la méthode getter et aux types de tous les paramètres de la méthode setter, sauf le dernier. Tous ces types devront être conformes à CLS et ne pas être des pointeurs managés (à savoir, ils ne doivent pas être passés par référence). | 27
Propriétés | [Propriétés](#properties) | Les propriétés adhéreront à un modèle d’attribution de nom spécifique. L'attribut `SpecialName` dont il est question dans la règle 24 de la spécification CLS sera ignoré dans les comparaisons de noms appropriées et respectera les règles d'identificateur. Une propriété aura une méthode getter, une méthode setter ou les deux. | 28
Conversion de type | [Conversion de type](#type-conversion) | Si op_Implicit ou op_Explicit est fourni, un autre moyen est utilisé pour fournir la contrainte. | 39
Types | [Types et signatures de membres de types](#types-and-type-member-signatures) | Les types de valeurs encadrés ne sont pas conformes à CLS. | 3
Types | [Types et signatures de membres de types](#types-and-type-member-signatures) | Tous les types apparaissant dans une signature devront être conformes à CLS. Tous les types composant un type générique instancié devront être conformes à CLS. | 11
Types | [Types et signatures de membres de types](#types-and-type-member-signatures) | Les références typées ne sont pas conformes CLS. | 14
Types | [Types et signatures de membres de types](#types-and-type-member-signatures) | Les types de pointeurs non managés ne sont pas conformes à CLS. | 17
Types | [Types et signatures de membres de types](#types-and-type-member-signatures) | Les classes, les types de valeurs et les interfaces conformes CLS ne doivent pas nécessiter l’implémentation de membres non conformes CLS | 20
Types | [Types et signatures de membres de types](#types-and-type-member-signatures) | [System.Object](xref:System.Object) est conforme CLS. Toute autre classe conforme à CLS héritera d'une classe conforme à CLS. | 23

Index des sous-sections :

* [Types et signatures de membres de types](#types-and-type-member-signatures)
* [Conventions d’affectation de noms](#naming-conventions)
* [Conversion de type](#type-conversion)
* [Tableaux](#arrays)
* [Interfaces](#interfaces)
* [Énumérations](#enumerations)
* [Membres de types en général](#type-members-in-general)
* [Accessibilité des membres](#member-accessibility)
* [Types et membres génériques](#generic-types-and-members)
* [Constructeurs](#constructors)
* [Propriétés](#properties)
* [Événements](#events)
* [Surcharges](#overloads)
* [Exceptions](#exceptions)
* [Attributs](#attributes)

### <a name="types-and-type-member-signatures"></a>Types et signatures de membres de types

Le type [System.Object](xref:System.Object) est conforme CLS et correspond au type de base de tous les types d’objets du système de types .Net Framework. Dans le .NET Framework, l’héritage est implicite (par exemple, la classe [String](xref:System.String) hérite implicitement de la classe `Object`) ou explicite (par exemple, la classe [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) hérite explicitement de la classe [ArgumentException](xref:System.ArgumentException), qui hérite explicitement de la classe [Exception](xref:System.Exception). Pour qu'un type dérivé soit conforme à CLS, son type de base doit également être conforme à CLS.

L'exemple suivant montre un type dérivé dont le type de base n'est pas conforme à CLS. Il définit une classe `Counter` de base qui utilise un entier 32 bits non signé en tant que compteur. La classe fournissant une fonctionnalité de compteur en encapsulant un entier non signé, elle est marquée comme non conforme à CLS. Par conséquent, une classe dérivée, `NonZeroCounter`, n'est pas non plus conforme à CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

Tous les types qui apparaissent dans les signatures de membres, notamment le type de retour d’une méthode ou un type de propriété, doivent être conformes à CLS. En outre, pour les types génériques :

* Tous les types qui composent un type générique instancié doivent être conformes à CLS.

* Tous les types utilisés comme contraintes sur des paramètres génériques doivent eux-mêmes être conformes à CLS.

Le [système de type commun](common-type-system.md) .NET inclut un certain nombre de types intégrés pris en charge directement par le Common Langage Runtime et qui sont spécialement encodés dans les métadonnées d’un assembly. Parmi les types intrinsèques, les types répertoriés dans le tableau suivant sont conformes à CLS.

Type conforme à CLS | Description
------------------ | -----------
[Poids](xref:System.Byte) | Entier 8 bits non signé
[Int16](xref:System.Int16) | Entier 16 bits signé
[Int32](xref:System.Int32) | Entier 32 bits signé
[Int64](xref:System.Int64) | Entier 64 bits signé
[Unique](xref:System.Single) | Valeur à virgule flottante simple précision
[Double](xref:System.Double) | Valeur à virgule flottante double précision
[Booléen](xref:System.Boolean) | Type de valeur true ou false
[Char](xref:System.Char) | Unité de code encodée en UTF-16
[Décimal](xref:System.Decimal) | Nombre décimal à virgule fixe
[IntPtr](xref:System.IntPtr) | Pointeur ou handle d'une taille définie par la plateforme
[Chaîne](xref:System.String) | Collection de zéro, un ou plusieurs objets Char

Les types intrinsèques répertoriés dans le tableau suivant ne sont pas conformes à CLS.

Type non conforme | Description | Alternative à la conformité CLS
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | Type de données entier signé 8 bits | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | Entier 16 bits non signé | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | Entier non signé 32 bits | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | Entier non signé 64 bits | [Int64](xref:System.Int64) (peut déborder), [BigInteger](xref:System.Numerics.BigInteger) ou [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | Pointeur ou handle non signé | [IntPtr](xref:System.IntPtr)

La bibliothèque de classes du .NET Framework ou toute autre bibliothèque de classes peut inclure d'autres types non conformes à CLS. Par exemple :

* Types de valeurs encadrés. L'exemple C# suivant crée une classe qui a une propriété publique de type `int*` nommée `Value`. Comme `int*` est un type de valeur encadré, le compilateur le signale comme non conforme à CLS.

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* Références typées, qui sont des constructions spéciales qui contiennent une référence à un objet et une référence à un type.

Si un type n’est pas conforme CLS, vous devez lui appliquer l’attribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) avec un paramètre *isCompliant* dont la valeur est `false`. Pour plus d’informations, consultez la section [Attribut CLSCompliantAttribute](#the-clscompliantattribute-attribute).

L'exemple suivant illustre le problème de conformité CLS dans une signature de méthode et dans une instanciation de type générique. Il définit une classe `InvoiceItem` avec une propriété de type [UInt32](xref:System.UInt32), une propriété de type [Nullable(Of UInt32)](xref:System.Nullable%601) et un constructeur avec des paramètres de type `UInt32` et `Nullable(Of UInt32)`. Vous obtenez quatre avertissements du compilateur lorsque vous essayez de compiler cet exemple.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

Pour supprimer les avertissements du compilateur, remplacez les types non conforme à CLS de l'interface publique `InvoiceItem` par des types conformes :

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

Outre les types spécifiques répertoriés, certaines catégories de types ne sont pas conformes à CLS. Celles-ci incluent les types de pointeurs non managés et les types de pointeurs de fonctions. L'exemple suivant génère un avertissement du compilateur, car il utilise un pointeur vers un entier pour créer un tableau d'entiers.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

Pour les classes abstraites conformes CLS (autrement dit, les classes marquées comme `abstract` en C#), tous les membres de la classe doivent également être conformes CLS.

### <a name="naming-conventions"></a>Conventions d’affectation de noms

Étant donné que certains langages de programmation ne respectent pas la casse, les identificateurs (tels que les noms d'espaces de noms, de types et de membres) doivent se différencier par autre chose que la casse. Deux identificateurs sont considérés comme équivalents si leurs mappages en minuscules sont identiques. L'exemple C# suivant définit deux classes publiques : `Person` et `person`. Étant donné qu'elles ne diffèrent que par leur casse, le compilateur C# les signale comme étant non conformes à CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

Les identificateurs de langage de programmation, tels que les noms d’espaces de noms, de types et de membres, doivent être conformes à la [norme Unicode](https://unicode.org/reports/tr15/). Cela signifie que :

* Le premier caractère d'un identificateur peut être une lettre majuscule, une lettre minuscule, une initiale majuscule, une lettre de modificateur, une autre lettre ou un nombre sous forme de lettre, Unicode. Pour plus d’informations sur les catégories de caractères Unicode, consultez l’énumération [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory).

* Les caractères suivants peuvent provenir de n’importe quelle catégorie comme premier caractère, et peuvent également inclure des marques de non-espacement, des marques de l’espacement, des nombres décimaux, des signes de ponctuation de connecteur et des codes de mise en forme.

Avant de comparer les identificateurs, vous devez éliminer par filtrage les codes de mise en forme et convertir les identificateurs au formulaire de normalisation Unicode C, car un caractère unique peut être représenté par plusieurs unités de code encodées en UTF-16. Les séquences de caractères qui produisent les mêmes unités de code dans un formulaire de normalisation Unicode C ne sont pas conformes à CLS. L'exemple suivant définit une propriété nommée `Å`, qui est constituée du caractère SYMBOLE ANGSTRÖM (U+212B), et une deuxième propriété nommée `Å`, qui est constituée du caractère LETTRE MAJUSCULE LATINE A AVEC DIACRITIQUE ROND EN CHEF (U+00C5). Le compilateur C# signale le code source comme non conforme CLS.

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

Les noms de membres dans une portée donnée (tels que les espaces de noms dans un assembly, les types dans un espace de noms ou les membres dans un type) doivent être uniques, à l'exception des noms résolus par la surcharge. Cette spécification est plus stricte que celle du système de type commun, qui autorise plusieurs membres d'une portée à avoir des noms identiques tant qu'il s'agit de types de membres différents (par exemple, l'un est une méthode et l'autre est un champ). En particulier, pour les membres de types :

* Les champs et les types imbriqués se distinguent par le nom uniquement.

* Les méthodes, les propriétés et les événements qui portent le même nom doivent différer par autre chose que le type de retour.

L'exemple suivant illustre la spécification selon laquelle les noms de membres doivent être uniques dans leur portée. Il définit une classe nommée `Converter` qui inclut quatre membres nommés `Conversion`. Trois sont des méthodes, le dernier est une propriété. La méthode qui inclut un paramètre `Int64` est nommée de manière unique, contrairement aux deux méthodes contenant un paramètre `Int32`, car la valeur de retour n'est pas considérée comme faisant partie de la signature d'un membre. La propriété `Conversion` enfreint également cette spécification, car les propriétés ne peuvent pas avoir le même nom que les méthodes surchargées.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

Les langages individuels incluent des mots clés uniques de sorte que les langages qui ciblent le Common Langage Runtime doivent également fournir un mécanisme de référencement des identificateurs (tels que les noms de types) qui coïncident avec les mots clés. Par exemple, `case` est un mot clé en C# et Visual Basic. Toutefois, l'exemple Visual Basic suivant peut supprimer l'ambiguïté entre une classe nommée `case` et le mot clé `case` en utilisant des accolades ouvrantes et fermantes. Sans cela, l'exemple générerait le message d'erreur : « Mot clé non valide en tant qu'identificateur » et échouerait lors de la compilation.

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

L’exemple C# suivant peut instancier la classe `case` en utilisant le symbole @ pour lever l’ambiguïté de l’identificateur par rapport au mot clé de langage. Sans cela, le compilateur C# afficherait deux messages d'erreur : « Type attendu » et « Terme d'expression non valide 'case' ».

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a>Conversion de type

La spécification CLS (Common Language Specification) définit deux opérateurs de conversion :

* `op_Implicit`, qui est utilisé pour les conversions étendues qui n'entraînent pas la perte de données ou de précision. Par exemple, la structure [Decimal](xref:System.Decimal) inclut un opérateur `op_Implicit` surchargé pour convertir les valeurs de types intégraux et les valeurs [Char](xref:System.Char) en valeurs `Decimal`.

* `op_Explicit`, qui est utilisé pour les conversions restrictives qui peuvent entraîner la perte d'amplitude (une valeur est convertie en une valeur qui entraîne une plus petite plage) ou de précision. Par exemple, la structure `Decimal` inclut un opérateur `op_Explicit` surchargé pour convertir les valeurs [Double](xref:System.Double) et [Single](xref:System.Single) en `Decimal`, et convertir les valeurs `Decimal` en valeurs intégrales, `Double`, `Single` et `Char`.

Toutefois, tous les langages ne prennent pas en charge la surcharge d'opérateur ou la définition d'opérateurs personnalisés. Si vous décidez d'implémenter ces opérateurs de conversion, vous devez également fournir une autre façon d'effectuer la conversion. Nous vous recommandons de fournir les méthodes `From`Xxx et `To`Xxx.

L'exemple suivant définit les conversions implicites et explicites conformes à CLS. Il crée une `UDouble` classe qui représente un nombre à virgule flottante double précision signé. Il s'applique aux conversions implicites de `UDouble` à `Double` et aux conversions explicites de `UDouble` à `Single`, de `Double` à `UDouble` et de `Single` à `UDouble`. Il définit également une méthode `ToDouble` comme une alternative à l'opérateur de conversion implicite et les méthodes `ToSingle`, `FromDouble` et `FromSingle` comme alternatives aux opérateurs de conversion explicite.

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a>Tableaux

Les tableaux conformes à CLS respectent les règles suivantes :

* Toutes les dimensions d'un tableau doivent avoir une limite inférieure égale à zéro. L'exemple suivant crée un tableau non conforme à CLS avec une limite inférieure égale à un. En dépit de la présence de l’attribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) , le compilateur ne détecte pas que le tableau retourné par la `Numbers.GetTenPrimes` méthode n’est pas conforme CLS.

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* Tous les éléments du tableau doivent se composer de types conformes à CLS. L'exemple suivant définit deux méthodes qui retournent des tableaux non conformes à CLS. La première retourne un tableau de valeurs [UInt32](xref:System.UInt32). La deuxième retourne un tableau [Object](xref:System.Object) qui inclut les valeurs [Int32](xref:System.Int32) et `UInt32`. Bien que le compilateur identifie le premier tableau comme non conforme en raison de son type `UInt32`, il ne parvient pas à reconnaître que le second tableau inclut des éléments non conformes à CLS.

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* La résolution de surcharge pour les méthodes qui ont des paramètres de tableau repose sur le fait qu’il s’agit de tableaux et sur leur type d’élément. C'est pourquoi la définition suivante d'une méthode `GetSquares` surchargée est conforme à CLS.

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a>Interfaces

Les interfaces conformes à CLS peuvent définir des propriétés, des événements et des méthodes virtuelles (méthodes sans implémentation). Une interface conforme à CLS ne peut avoir aucune des caractéristiques suivantes :

* Méthodes statiques ou champs statiques. Le compilateur C# génère des erreurs de compilation si un membre statique est défini dans une interface.

* Champs. Le compilateur C# génère des erreurs de compilation si un champ est défini dans une interface.

* Méthodes qui ne sont pas conformes à CLS. Par exemple, la définition d'interface suivante inclut une méthode, `INumber.GetUnsigned`, qui est marquée comme non conforme à CLS. Cet exemple génère un avertissement du compilateur.

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  En raison de cette règle, pour implémenter des membres non conformes à CLS, il n'est pas nécessaire d'utiliser des types conformes à CLS. Si une infrastructure conforme à CLS expose une classe qui implémente une interface non conforme à CLS, elle doit également fournir des implémentations concrètes de tous les membres non conformes.

Les compilateurs de langages conformes à CLS doivent également permettre à une classe de fournir des implémentations séparées des membres qui ont les mêmes nom et signature dans plusieurs interfaces. C# prend en charge des implémentations d’interface explicites pour fournir des implémentations différentes de méthodes portant le même nom. L'exemple suivant illustre ce scénario en définissant une classe `Temperature` qui implémente les interfaces `ICelsius` et `IFahrenheit` en tant qu'implémentations d'interface explicites.

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a>Énumérations

Les énumérations conformes à CLS doivent suivre ces règles :

* Le type sous-jacent de l’énumération doit être un entier conforme CLS intrinsèque ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32) ou [Int64](xref:System.Int64)). Par exemple, le code suivant tente de définir une énumération dont le type sous-jacent est [UInt32](xref:System.UInt32) et génère un avertissement du compilateur.

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* Un type d'énumération doit avoir un champ d'instance unique nommé `Value__` qui est marqué avec l'attribut `FieldAttributes.RTSpecialName`. Cela vous permet de référencer implicitement la valeur du champ.

* Une énumération inclut les champs statiques littéraux du même type que l'énumération elle-même. Par exemple, si vous définissez une énumération `State` avec les valeurs `State.On` et `State.Off`, `State.On` et `State.Off` sont les deux champs statiques littéraux dont le type est `State`.

* Il existe deux types d'énumérations :

  * Une énumération qui représente un jeu de valeurs entières nommées qui s'excluent mutuellement. Ce type d’énumération est indiqué par l’absence de l’attribut personnalisé [System.FlagsAttribute](xref:System.FlagsAttribute).

  * Une énumération qui représente un jeu d'indicateurs binaires qui peuvent être combinés pour générer une valeur sans nom. Ce type d’énumération est indiqué par la présence de l’attribut personnalisé [System.FlagsAttribute](xref:System.FlagsAttribute).

Pour plus d’informations, consultez la documentation de la structure [Enum](xref:System.Enum).

* La valeur d'une énumération ne se limite pas à la plage de ses valeurs spécifiées. En d'autres termes, la plage de valeurs d'une énumération est la plage de sa valeur sous-jacente. Vous pouvez utiliser la méthode `Enum.IsDefined` pour déterminer si une valeur spécifiée est membre d'une énumération.

### <a name="type-members-in-general"></a>Membres de types en général

La spécification CLS (Common Language Specification) nécessite que tous les champs et toutes les méthodes soient accessibles en tant que membres d'une classe particulière. Par conséquent, les méthodes et les champs statiques globaux (autrement dit, les méthodes ou les champs statiques définis en dehors d'un type) ne sont pas conformes à CLS. Si vous essayez d’inclure un champ global ou une méthode globale dans votre code source, le compilateur C# génère une erreur de compilateur.

La spécification CLS (Common Language Specification) prend uniquement en charge la convention d'appel managée standard. Elle ne prend pas en charge les conventions d'appel non managées ni les méthodes avec des listes d'arguments variables marquées avec le mot clé `varargs`. Pour les listes d’arguments variables compatibles avec la convention d’appel managée standard, utilisez l’attribut [ParamArrayAttribute](xref:System.ParamArrayAttribute) ou l’implémentation de chaque langage, comme le mot clé `params` en C# et le mot clé `ParamArray` en Visual Basic.

### <a name="member-accessibility"></a>Accessibilité des membres

Le remplacement d'un membre hérité ne peut pas modifier l'accessibilité de ce membre. Par exemple, une méthode publique dans une classe de base ne peut pas être remplacée par une méthode privée dans une classe dérivée. Il existe une exception : un membre `protected internal` (en C#) ou `Protected Friend` (en Visual Basic) dans un assembly qui est remplacé par un type dans un autre assembly.  Dans ce cas, l'accessibilité du remplacement est `Protected`.

L’exemple suivant illustre l’erreur générée quand l’attribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) a la valeur `true`, et que `Person`, qui est une classe dérivée de `Animal`, tente de remplacer l’accessibilité publique de la propriété `Species` par une accessibilité privée. L'exemple se compile correctement si son accessibilité devient publique.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

Les types de la signature d'un membre doivent être accessibles chaque fois que ce membre est accessible. Par exemple, cela signifie qu’un membre public ne peut pas inclure un paramètre dont le type est privé, protégé ou interne. L'exemple suivant illustre l'erreur de compilateur obtenue lorsqu'un constructeur de classe `StringWrapper` expose une valeur d'énumération `StringOperationType` interne qui détermine comment une valeur de chaîne doit être encapsulée.

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a>Types et membres génériques

Les types imbriqués ont toujours au moins autant de paramètres génériques que leur type englobant. Ceux-ci correspondent par position aux paramètres génériques du type englobant. Le type générique peut également inclure de nouveaux paramètres génériques.

La relation entre les paramètres de type générique d'un type conteneur et ses types imbriqués peut être masquée par la syntaxe des différents langages. Dans l'exemple suivant, un type générique `Outer<T>` contient deux classes imbriquées, `Inner1A` et `Inner1B<U>`. Les appels à la méthode `ToString`, dont chaque classe hérite de `Object.ToString`, indiquent que chaque classe imbriquée inclut les paramètres de type de sa classe conteneur.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

Les noms des types génériques sont encodés sous la forme *nom*'*n*, où *nom* est le nom du type, *`* est un caractère littéral et *n* est le nombre de paramètres déclarés sur le type ou, pour les types génériques imbriqués, le nombre de paramètres de type récemment introduits. Cet encodage de noms de types génériques intéresse principalement les développeurs qui utilisent la réflexion pour accéder aux types génériques conformes à CLS dans une bibliothèque.

Si les contraintes sont appliquées à un type générique, tous les types utilisés en tant que contraintes doivent également être conformes à CLS. L'exemple suivant définit une classe nommée `BaseClass` qui n'est pas conforme à CLS et une classe générique nommée `BaseCollection` dont le paramètre de type doit dériver de `BaseClass`. Toutefois, comme `BaseClass` n'est pas conforme à CLS, le compilateur émet un avertissement.

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

Si un type générique est dérivé d'un type de base générique, il doit redéclarer toutes les contraintes pour s'assurer que les contraintes du type de base sont également satisfaites. L'exemple suivant définit un `Number<T>` qui peut représenter un type numérique. Il définit également une classe `FloatingPoint<T>` qui représente une valeur à virgule flottante. Toutefois, le code source ne se compile pas, car il n'applique pas la contrainte `Number<T>` (ce T doit être un type de valeur) à `FloatingPoint<T>`.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

L'exemple se compile correctement si la contrainte est ajoutée à la classe `FloatingPoint<T>`.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

La spécification CLS (Common Language Specification) impose un modèle conservateur par instanciation pour les types imbriqués et les membres protégés. Les types génériques ouverts ne peuvent pas exposer de champs ou de membres avec des signatures qui contiennent une instanciation spécifique d'un type générique imbriqué et protégé. Les types non génériques qui étendent une instanciation spécifique d'une classe de base ou une interface générique ne peuvent pas exposer de champs ou de membres avec des signatures qui contiennent une instanciation différente d'un type générique imbriqué et protégé.

L’exemple suivant définit un type générique, `C1<T>`, et une classe protégée, `C1<T>.N`. `C1<T>` a deux méthodes : `M1` et `M2`. Toutefois, la méthode `M1` n’est pas conforme CLS, car elle essaie de retourner un objet `C1<int>.N` de `C1<T>`. Une deuxième classe, `C2`, est dérivée de `C1<long>`. Elle a deux méthodes, `M3` et `M4`. `M3`’est pas conforme CLS, car elle essaie de retourner un objet `C1<int>.N` d’une sous-classe de `C1<long>`. Les compilateurs de langage peuvent être encore plus restrictifs. Dans cet exemple, Visual Basic affiche une erreur lorsqu'il tente de compiler `M4`.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a>Constructeurs

Les constructeurs des classes et structures conformes à CLS doivent suivre ces règles :

* Un constructeur d'une classe dérivée doit appeler le constructeur d'instance de sa classe de base avant d'accéder aux données d'instance héritées. Cette spécification est due au fait que les constructeurs de classes de base ne sont pas hérités par leurs classes dérivées. Cette règle ne s'applique pas aux structures, qui ne prennent pas en charge l'héritage direct.

  En général, les compilateurs appliquent cette règle indépendamment de la conformité CLS, comme indiqué dans l'exemple suivant. Il crée une classe `Doctor` dérivée d'une classe `Person`, mais la classe `Doctor` ne parvient pas à appeler le constructeur de classe `Person` pour initialiser les champs d'instance hérités.

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* Un constructeur d'objet ne peut être appelé que pour créer un objet. En outre, un objet ne peut pas être initialisé deux fois. Par exemple, cela signifie que `Object.MemberwiseClone` ne doit pas appeler de constructeurs.

### <a name="properties"></a>Propriétés

Les propriétés dans les types conformes à CLS doivent suivre ces règles :

* Une propriété doit posséder une méthode setter, getter ou les deux. Dans un assembly, celles-ci sont implémentées comme des méthodes spéciales, ce qui signifie qu’elles apparaîtront comme des méthodes distinctes (l’accesseur Get est nommé `get` \_ *NomPropriété* et l’accesseur Set est `set` \_ *PropertyName*) marqué comme `SpecialName` dans les métadonnées de l’assembly. Le compilateur C# applique automatiquement cette règle sans qu’il soit nécessaire d’appliquer l’attribut <xref:System.CLSCompliantAttribute>.

* Le type d’une propriété correspond au type de retour de la méthode getter de la propriété et du dernier argument de la méthode setter. Ces types doivent être conformes à CLS et les arguments ne peuvent pas être assignés à la propriété par référence (autrement dit, ils ne peuvent pas être des pointeurs managés).

* Si une propriété possède une méthode getter et une méthode setter, elles doivent être toutes les deux virtuelles, statiques ou être toutes les deux des instances. Le compilateur C# applique automatiquement cette règle par le biais de la syntaxe de définition de propriété.

### <a name="events"></a>Événements

Un événement est défini par son nom et son type. Le type d'événement est un délégué utilisé pour indiquer l'événement. Par exemple, l'événement `DbConnection.StateChange` est de type `StateChangeEventHandler`. Outre l'événement lui-même, trois méthodes avec des noms basés sur le nom de l'événement fournissent une implémentation de l'événement et sont marquées comme `SpecialName` dans les métadonnées de l'assembly :

* Une méthode pour ajouter un gestionnaire d’événements, appelée `add`_*EventName*. Par exemple, la méthode d'abonnement aux événements pour l'événement `DbConnection.StateChange` est nommée `add_StateChange`.

* Une méthode pour supprimer un gestionnaire d’événements, appelée `remove`_*EventName*. Par exemple, la méthode de suppression pour l'événement `DbConnection.StateChange` est nommée `remove_StateChange`.

* Une méthode pour indiquer que l’événement s’est produit, nommée `raise`\_*NomÉvénement*.

> [!NOTE]
> La plupart des règles de la spécification CLS concernant les événements sont implémentées par les compilateurs de langage et sont transparentes aux développeurs de composants.

L'accessibilité des méthodes permettant d'ajouter, de supprimer et de déclencher un événement doit être identique. Les méthodes doivent également toutes être statiques, instanciées ou virtuelles. Les méthodes d'ajout et de suppression d'un événement ont un paramètre dont le type est le type du délégué d'événement. Les méthodes d'ajout et de suppression doivent être toutes les deux présentes ou absentes.

L'exemple suivant définit une classe conforme à CLS nommée `Temperature` qui déclenche un événement `TemperatureChanged` si le changement de température entre deux lectures est égal ou supérieur à une valeur seuil. La classe `Temperature` définit explicitement une méthode `raise_TemperatureChanged` afin de pouvoir exécuter de manière sélective les gestionnaires d'événements.

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a>Surcharges

La spécification CLS impose les conditions suivantes aux membres surchargés :

* Les membres peuvent être surchargés selon le nombre de paramètres et le type d'un paramètre. La convention d’appel, le type de retour, les modificateurs personnalisés appliqués à la méthode ou à son paramètre et le fait que les paramètres soient transmis par valeur ou par référence ne sont pas pris en considération lors de la différenciation des surcharges. Pour obtenir un exemple, consultez le code de l’exigence indiquant que les noms doivent être uniques dans une portée, dans la section [Conventions d’affectation de noms](#naming-conventions).

* Seules les propriétés et les méthodes peuvent être surchargées. Les champs et les événements ne peuvent pas être surchargés.

* Les méthodes génériques peuvent être surchargées selon le nombre de leurs paramètres génériques.

> [!NOTE]
> Les opérateurs `op_Explicit` et `op_Implicit` sont des exceptions à la règle indiquant que la valeur de retour n'est pas considérée comme faisant partie d'une signature de méthode pour la résolution de la surcharge. Ces deux opérateurs peuvent être surchargés selon leurs paramètres et leur valeur de retour.

### <a name="exceptions"></a>Exceptions

Les objets d’exception doivent dériver de [System.Exception](xref:System.Exception) ou d’un autre type dérivé de `System.Exception`. L'exemple suivant illustre l'erreur de compilateur obtenue lorsqu'une classe personnalisée nommée `ErrorClass` est utilisée pour la gestion des exceptions.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

Pour corriger cette erreur, la classe `ErrorClass` doit hériter de `System.Exception`. Par ailleurs, la propriété Message doit être remplacée. L'exemple suivant corrige ces erreurs pour définir une classe `ErrorClass` conforme à CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a>Attributs

Dans les assemblys .NET Framework, les attributs personnalisés fournissent un mécanisme extensible pour stocker des attributs personnalisés et récupérer les métadonnées concernant la programmation des objets, tels que les assemblys, les types, les membres et les paramètres de méthode. Les attributs personnalisés doivent dériver de [System.Attribute](xref:System.Attribute) ou d’un type dérivé de `System.Attribute`.

L'exemple suivant enfreint cette règle. Il définit une classe `NumericAttribute` qui ne dérive pas de `System.Attribute`. Une erreur du compilateur se produit uniquement lorsque l’attribut non conforme CLS est appliqué, et non lorsque la classe est définie.

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

Le constructeur ou les propriétés d'un attribut conforme à CLS peuvent exposer uniquement les types suivants :

* [Booléen](xref:System.Boolean)

* [Poids](xref:System.Byte)

* [Char](xref:System.Char)

* [Double](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Unique](xref:System.Single)

* [Chaîne](xref:System.String)

* [Type](xref:System.Type)

* Tout type d'énumération dont le type sous-jacent est `Byte`, `Int16`, `Int32` ou `Int64`.

L’exemple suivant définit une classe `DescriptionAttribute` qui dérive de [Attribute](xref:System.Attribute). Le constructeur de classe a un paramètre de type `Descriptor`, la classe n'est donc pas conforme à CLS. Le compilateur C# émet un avertissement mais se compile correctement.

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a>Attribut CLSCompliantAttribute

L’attribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) permet d’indiquer si un élément de programme est conforme à la spécification CLS (Common Language Specification). Le constructeur `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` inclut un seul paramètre obligatoire, *isCompliant*, qui indique si l’élément de programme est conforme CLS.

Au moment de la compilation, le compilateur détecte les éléments non conformes qui sont présumés conformes à CLS et émet alors un avertissement. Le compilateur n'émet pas d'avertissements pour les types ou les membres qui sont explicitement déclarés comme étant non conformes.

Les développeurs de composants peuvent utiliser l'attribut `CLSCompliantAttribute` de deux façons :

* Pour définir les parties de l'interface publique exposées par un composant qui sont conformes à CLS et celles qui ne sont pas conformes à CLS. Lorsque l'attribut est utilisé pour marquer des éléments de programme particuliers comme étant conformes à CLS, son utilisation garantit que ces éléments sont accessibles à partir de tous les langages et outils qui ciblent le .NET Framework.

* Pour vérifier que l'interface publique de la bibliothèque de composants expose uniquement les éléments de programme conformes à CLS. Si les éléments ne sont pas conformes à CLS, les compilateurs publieront généralement un avertissement.

> [!WARNING]
> Dans certains cas, les compilateurs de langages imposent les règles conformes à CLS que l'attribut `CLSCompliantAttribute` soit utilisé ou non. Par exemple, la définition d’un membre `*static` dans une interface est une infraction à une règle CLS. Toutefois, si vous définissez un membre `*static` dans une interface, le compilateur C# affiche un message d’erreur et ne compile pas l’application.

L’attribut `CLSCompliantAttribute` est marqué avec un attribut [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) qui a la valeur `AttributeTargets.All`. Cette valeur permet d'appliquer l'attribut `CLSCompliantAttribute` à un élément de programme, notamment aux assemblys, modules, types (classes, structures, énumérations, interfaces et délégués), membres de types (constructeurs, méthodes, propriétés, champs et événements), paramètres, paramètres génériques et valeurs de retour. Toutefois, dans la pratique, vous devez appliquer l'attribut uniquement aux assemblys, aux types et aux membres de types. Sinon, les compilateurs ignorent l'attribut et continuent à générer des avertissements de compilateur lorsqu'ils rencontrent un paramètre non conforme, un paramètre générique ou une valeur de retour dans l'interface publique de votre bibliothèque.

La valeur de l'attribut `CLSCompliantAttribute` est héritée par les éléments de programme contenus. Par exemple, si un assembly est marqué comme étant conforme à CLS, ses types sont également conformes à CLS. Si un type est marqué comme étant conforme à CLS, ses membres et types imbriqués seront également conformes à CLS.

Vous pouvez remplacer explicitement la conformité héritée en appliquant l'attribut `CLSCompliantAttribute` à un élément de programme contenu. Par exemple, vous pouvez utiliser l’attribut `CLSCompliantAttribute` avec une valeur *isCompliant* égale à `false` pour définir un type non conforme dans un assembly conforme, et avec une valeur *isCompliant* égale à `true` pour définir un type conforme dans un assembly non conforme. Vous pouvez également définir des membres non conformes dans un type conforme. Toutefois, un type non conforme ne peut pas avoir de membres conformes, vous ne pouvez donc pas utiliser l’attribut avec une valeur *isCompliant* égale à `true` pour remplacer l’héritage d’un type non conforme.

Lorsque vous développez des composants, vous devez toujours utiliser l'attribut `CLSCompliantAttribute` pour indiquer si votre assembly, ses types et ses membres sont conformes à CLS.

Pour créer des composants conformes à CLS :

1. Utilisez `CLSCompliantAttribute` pour marquer votre assembly comme étant conforme à CLS.

2. Marquez les types exposés publiquement de l'assembly qui ne sont pas conformes à CLS comme non conformes.

3. Marquez tous les membres exposés publiquement dans des types conformes à CLS comme non conformes.

4. Fournissez une alternative conforme à CLS pour les membres non conformes.

Si vous avez correctement marqué tous vos types et membres non conformes, le compilateur ne doit émettre aucun avertissement de non-conformité. Toutefois, vous devez indiquer quels membres ne sont pas conformes à CLS et répertorier leurs alternatives conformes à CLS dans votre documentation produit.

L'exemple suivant utilise l'attribut `CLSCompliantAttribute` pour définir un assembly conforme à CLS et un type, `CharacterUtilities`, qui a deux membres non conformes à CLS. Les deux membres étant référencés avec l'attribut `CLSCompliant(false)`, le compilateur ne génère aucun avertissement. La classe fournit également une alternative conforme à CLS pour les deux méthodes. Normalement, nous ajouterions seulement deux surcharges à la méthode `ToUTF16` pour fournir des alternatives conformes à CLS. Toutefois, les méthodes ne pouvant pas être surchargées selon la valeur de retour, les noms des méthodes conformes à CLS sont différents des noms des méthodes non conformes.

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

Si vous développez une application plutôt qu'une bibliothèque (autrement dit, si vous n'exposez pas des types ou des membres qui peuvent être utilisés par d'autres développeurs d'applications), la conformité CLS des éléments de programme que votre application consomme n'a d'intérêt que si votre langage ne les prend pas en charge. Dans ce cas, votre compilateur de langage générera une erreur lorsque vous essaierez d'utiliser un élément non conforme à CLS.

## <a name="cross-language-interoperability"></a>Interopérabilité interlangage

L'indépendance du langage a plusieurs significations possibles. Une des significations implique la consommation de façon transparente des types écrits dans un langage à partir d’une application écrite dans un autre langage. Une deuxième signification, qui est le sujet de cet article, consiste à combiner du code écrit dans plusieurs langages dans un même assembly .NET Framework.

L'exemple suivant illustre l'interopérabilité interlangage en créant une bibliothèque de classes nommée Utilities.dll qui comprend deux classes, `NumericLib` et `StringLib`. La classe `NumericLib` est écrite en C# et la classe `StringLib` est écrite en Visual Basic. Voici le code source de `StringUtil.vb`, qui comprend un seul membre, `ToTitleCase`, dans sa classe `StringLib`.

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

Voici le code source de NumberUtil.cs, qui définit une classe `NumericLib` qui a deux membres, `IsEven` et `NearZero`.

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

Pour placer les deux classes dans un même assembly, vous devez les compiler dans des modules. Pour compiler le fichier de code source Visual Basic dans un module, utilisez cette commande :

```console
vbc /t:module StringUtil.vb
```

Pour compiler le fichier de code source C# dans un module, utilisez cette commande :

```console
csc /t:module NumberUtil.cs
```

Vous utilisez ensuite l’outil de liaison (Link.exe) pour compiler les deux modules en un assembly :

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

L'exemple suivant appelle ensuite les méthodes `NumericLib.NearZero` et `StringLib.ToTitleCase`. Le code Visual Basic et le code C# peuvent accéder aux méthodes des deux classes.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

Pour compiler le code Visual Basic, utilisez cette commande :

```console
vbc example.vb /r:UtilityLib.dll
```

Pour compiler avec C#, changez le nom du compilateur vbc en csc et changez l’extension de fichier .vb en .cs :

```console
csc example.cs /r:UtilityLib.dll
```
