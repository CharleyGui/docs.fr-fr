---
title: 'Tutorial: Créer un fournisseur de type'
description: Apprenez à créer vos propres fournisseurs de type F 3.0 en examinant plusieurs fournisseurs de type simple pour illustrer les concepts de base.
ms.date: 11/04/2019
ms.openlocfilehash: 3b8145d4c2d8bf96b6dcf66de02e9f2d83927d74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186121"
---
# <a name="tutorial-create-a-type-provider"></a>Tutorial: Créer un fournisseur de type

Le mécanisme de fournisseur de type dans le cadre de la FMD est une partie importante de son soutien à la programmation riche en informations. Ce tutoriel explique comment créer vos propres fournisseurs de type en vous promenant à travers le développement de plusieurs fournisseurs de type simple pour illustrer les concepts de base. Pour plus d’informations sur le mécanisme de fournisseur de type dans F, voir [Fournisseurs de type](index.md).

L’écosystème FMD contient une gamme de fournisseurs de type pour les services de données Internet et d’entreprise couramment utilisés. Par exemple :

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) inclut les fournisseurs de type pour les formats de documents JSON, XML, CSV et HTML.

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) offre un accès fortement typé aux bases de données SQL par le biais d’une cartographie d’objets et de requêtes F-LINQ contre ces sources de données.

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) dispose d’un ensemble de fournisseurs de type pour l’intégration vérifiée en temps de compilation de T-SQL en F.

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) est un ancien ensemble de fournisseurs de type à utiliser uniquement avec la programmation cadre .NET pour accéder aux services de données SQL, Entity Framework, OData et WSDL.

Si nécessaire, vous pouvez créer des fournisseurs de type personnalisé, ou vous pouvez référencer les fournisseurs de type que d’autres ont créés. Par exemple, votre organisation pourrait avoir un service de données qui fournit un nombre important et croissant d’ensembles de données nommés, chacun avec son propre schéma de données stables. Vous pouvez créer un fournisseur de type qui lit les schémas et présente les ensembles de données actuels au programmeur d’une manière fortement tapée.

## <a name="before-you-start"></a>Avant de commencer

Le mécanisme de fournisseur de type est principalement conçu pour injecter des espaces stables de données et d’information de service dans l’expérience de programmation de F.

Ce mécanisme n’est pas conçu pour injecter des espaces d’information dont le schéma change pendant l’exécution du programme d’une manière pertinente à la logique du programme. En outre, le mécanisme n’est pas conçu pour la méta-programmation intra-langage, même si ce domaine contient quelques utilisations valides. Vous ne devez utiliser ce mécanisme que si nécessaire et lorsque le développement d’un fournisseur de type donne une très grande valeur.

Vous devriez éviter d’écrire un fournisseur de type où un schéma n’est pas disponible. De même, vous devriez éviter d’écrire un fournisseur de type où une bibliothèque ordinaire (ou même existante) .NET suffirait.

Avant de commencer, vous pourriez poser les questions suivantes :

- Avez-vous un schéma pour votre source d’information? Dans l’affirmative, quelle est la cartographie dans le système de type F et NET ?

- Pouvez-vous utiliser une API existante (dactylographié dynamiquement) comme point de départ pour votre mise en œuvre ?

- Aurez-vous et votre organisation ont suffisamment d’utilisations du fournisseur de type pour le rendre utile à l’écriture? Est-ce qu’une bibliothèque .NET normale répondrait à vos besoins?

- Combien votre schéma va-t-il changer ?

- Va-t-il changer pendant le codage?

- Changera-t-il entre les sessions de codage ?

- Cela changera-t-il pendant l’exécution du programme?

Les fournisseurs de type sont les mieux adaptés aux situations où le schéma est stable au moment de l’exécution et pendant la durée de vie du code compilé.

## <a name="a-simple-type-provider"></a>Un fournisseur de type simple

Cet échantillon est Samples.HelloWorldTypeProvider, similaire `examples` aux échantillons dans le répertoire du fournisseur de [type F SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). Le fournisseur met à disposition un «espace de type» qui contient 100 types effacés, comme le montre `Type1`le code suivant en utilisant la syntaxe signature F et en omettant les détails pour tous sauf . Pour plus d’informations sur les types effacés, voir [Détails sur les types fournis effacés](#details-about-erased-provided-types) plus tard dans ce sujet.

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType =
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

Notez que l’ensemble des types et des membres fournis est connu de façon statique. Cet exemple ne tire pas parti de la capacité des fournisseurs de fournir des types qui dépendent d’un schéma. La mise en œuvre du fournisseur de type est décrite dans le code suivant, et les détails sont couverts dans les sections ultérieures de ce sujet.

> [!WARNING]
> Il peut y avoir des différences entre ce code et les échantillons en ligne.

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =

  // Inheriting from this type provides implementations of ITypeProvider
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) =
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>]
do()
```

Pour utiliser ce fournisseur, ouvrez une instance distincte de Visual Studio, créez un script F, puis ajoutez une référence au fournisseur de votre script en utilisant #r comme le code suivant l’indique :

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

Ensuite, recherchez les `Samples.HelloWorldTypeProvider` types sous l’espace nom que le fournisseur de type généré.

Avant de recomposer le fournisseur, assurez-vous d’avoir fermé toutes les instances de Visual Studio et de F Interactive qui utilisent le fournisseur DLL. Dans le cas contraire, une erreur de construction se produira parce que la sortie DLL sera verrouillée.

Pour déboiffer ce fournisseur en utilisant des instructions imprimées, faire un script qui expose un problème avec le fournisseur, puis utiliser le code suivant:

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Pour déboguer ce fournisseur en utilisant Visual Studio, ouvrez le Developer Command Prompt pour Visual Studio avec des informations administratives, et exécutez la commande suivante :

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Comme alternative, ouvrez Visual Studio, ouvrez `Debug/Attach to process…`le menu Debug, choisissez et attachez-vous à un autre `devenv` processus où vous modifiez votre script. En utilisant cette méthode, vous pouvez plus facilement cibler une logique particulière dans le fournisseur de type en tapant interactivement des expressions dans la deuxième instance (avec IntelliSense complet et d’autres fonctionnalités).

Vous pouvez désactiver Just My Code débogage pour mieux identifier les erreurs dans le code généré. Pour plus d’informations sur la façon d’activer ou désactiver cette fonctionnalité, voir [Naviguer à travers code avec le Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger). En outre, vous pouvez également définir la `Debug` capture d’exception de première chance en ouvrant le menu, puis en choisissant `Exceptions` ou en choisissant les clés Ctrl-Alt-E pour ouvrir la boîte de `Exceptions` dialogue. Dans cette boîte de `Common Language Runtime Exceptions`dialogue, `Thrown` sous , sélectionnez la case à cocher.

### <a name="implementation-of-the-type-provider"></a>Mise en œuvre du fournisseur de type

Cette section vous guide à travers les principales sections de la mise en œuvre du fournisseur de type. Tout d’abord, vous définissez le type pour le fournisseur de type personnalisé lui-même:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Ce type doit être public, et vous devez le marquer avec l’attribut [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) de sorte que le compilateur reconnaîtra le fournisseur de type lorsqu’un projet F distinct fait référence à l’assemblage qui contient le type. Le paramètre *config* est facultatif et, s’il est présent, contient des informations de configuration contextuelle pour l’instance type fournisseur que le compilateur F crée.

Ensuite, vous implémentez l’interface [ITypeProvider.](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) Dans ce cas, `TypeProviderForNamespaces` vous utilisez `ProvidedTypes` le type de l’API comme type de base. Ce type d’aide peut fournir une collection limitée d’espaces de nom avidement fournis, dont chacun contient directement un nombre fini de types fixes, avidement fournis. Dans ce contexte, le fournisseur génère *avec empressement* des types même s’ils ne sont pas nécessaires ou utilisés.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Ensuite, définissez les valeurs privées locales qui spécifient l’espace de nom pour les types fournis, et trouvez l’assemblage du fournisseur de type lui-même. Cet assemblage est utilisé plus tard comme le type parent logique des types effacés qui sont fournis.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Ensuite, créez une fonction pour fournir chacun des types Type1... Type100. Cette fonction est expliquée plus en détail plus tard dans ce sujet.

```fsharp
let makeOneProvidedType (n:int) = …
```

Ensuite, générer les 100 types fournis:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Ensuite, ajoutez les types comme un espace de nom fourni:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Enfin, ajoutez un attribut d’assemblage qui indique que vous créez un fournisseur de type DLL :

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Fournir un type et ses membres

La `makeOneProvidedType` fonction fait le vrai travail de fournir l’un des types.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Cette étape explique la mise en œuvre de cette fonction. Tout d’abord, créez le type fourni (par exemple, Type1, quand n 1, ou Type57, quand n 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Vous devez noter les points suivants :

- Ce type fourni est effacé.  Parce que vous indiquez `obj`que le type de base est , les instances apparaîtront comme des valeurs de type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) dans le code compilé.

- Lorsque vous spécifiez un type non imbriqué, vous devez spécifier l’espace de l’assemblage et du nom. Pour les types effacés, l’assemblage doit être le type d’assemblage fournisseur lui-même.

Ensuite, ajoutez la documentation XML au type. Cette documentation est retardée, c’est-à-dire calculée à la demande si le compilateur hôte en a besoin.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Ensuite, vous ajoutez une propriété statique fournie au type:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Obtenir cette propriété sera toujours évaluer à la chaîne "Bonjour!". Le `GetterCode` pour la propriété utilise une citation F, qui représente le code que le compilateur hôte génère pour obtenir la propriété. Pour plus d’informations sur les citations, voir [Citations de code (F)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Ajoutez de la documentation XML à la propriété.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Attachez maintenant la propriété fournie au type fourni. Vous devez joindre un membre fourni à un seul et unique type. Sinon, le membre ne sera jamais accessible.

```fsharp
t.AddMember staticProp
```

Maintenant, créez un constructeur fourni qui ne prend aucun paramètre.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

Le `InvokeCode` constructeur renvoie une citation F, qui représente le code que le compilateur hôte génère lorsque le constructeur est appelé. Par exemple, vous pouvez utiliser le constructeur suivant :

```fsharp
new Type10()
```

Une instance du type fourni sera créée avec des données sous-jacentes "Les données de l’objet". Le code cité comprend une conversion en [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) parce que ce type est l’effacement de ce type fourni (comme vous l’avez précisé lorsque vous avez déclaré le type fourni).

Ajouter la documentation XML au constructeur et ajouter le constructeur fourni au type fourni :

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Créez un deuxième constructeur fourni qui prend un paramètre :

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

Le `InvokeCode` pour le constructeur retourne à nouveau une citation F, qui représente le code que le compilateur hôte généré pour un appel à la méthode. Par exemple, vous pouvez utiliser le constructeur suivant :

```fsharp
new Type10("ten")
```

Une instance du type fourni est créée avec des données sous-jacentes "dix". Vous avez peut-être `InvokeCode` déjà remarqué que la fonction renvoie une citation. L’entrée à cette fonction est une liste d’expressions, une par paramètre constructeur. Dans ce cas, une expression qui représente `args.[0]`la valeur de paramètre unique est disponible en . Le code d’appel au constructeur contraigne la valeur `obj`de retour au type effacé . Après avoir ajouté le deuxième constructeur fourni au type, vous créez une propriété d’instance fournie :

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Obtenir cette propriété retournera la longueur de la chaîne, qui est l’objet de représentation. La `GetterCode` propriété renvoie une citation de F qui spécifie le code que le compilateur hôte génère pour obtenir la propriété. Comme, `InvokeCode` `GetterCode` la fonction renvoie une citation. Le compilateur hôte appelle cette fonction avec une liste d’arguments. Dans ce cas, les arguments comprennent juste l’expression unique qui représente l’instance sur `args.[0]`laquelle l’getter est appelé, que vous pouvez accéder en utilisant . La mise `GetterCode` en œuvre des épissages dans `obj`la citation de résultat au type effacé, et un plâtre est utilisé pour satisfaire le mécanisme du compilateur pour vérifier les types que l’objet est une chaîne. La partie `makeOneProvidedType` suivante fournit une méthode d’instance avec un paramètre.

```fsharp
let instanceMeth =
    ProvidedMethod(methodName = "InstanceMethod",
                   parameters = [ProvidedParameter("x",typeof<int>)],
                   returnType = typeof<char>,
                   invokeCode = (fun args ->
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

Enfin, créez un type imbriqué qui contient 100 propriétés imbriquées. La création de ce type imbriqué et de ses propriétés est retardée, c’est-à-dire calculée à la demande.

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  sprintf "This is StaticProperty%d on NestedType" i)

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a>Détails sur les types fournis effacés

L’exemple de cette section ne fournit que des *types effacés fournis,* qui sont particulièrement utiles dans les situations suivantes :

- Lorsque vous écrivez un fournisseur pour un espace d’information qui ne contient que des données et des méthodes.

- Lorsque vous écrivez un fournisseur où la sémantique précise de type runtime n’est pas essentielle pour une utilisation pratique de l’espace d’information.

- Lorsque vous écrivez un fournisseur pour un espace d’information qui est si grand et interconnecté qu’il n’est pas techniquement possible de générer de vrais types .NET pour l’espace d’information.

Dans cet exemple, chaque type fourni `obj`est effacé au type, et `obj` toutes les utilisations du type apparaîtront comme type dans le code compilé. En fait, les objets sous-jacents dans ces exemples sont des chaînes, mais le type apparaîtra comme `System.Object` dans le code compilé .NET. Comme avec toutes les utilisations de l’effacement de type, vous pouvez utiliser la boxe explicite, le déballage, et le moulage pour subvertir les types effacés. Dans ce cas, une exception de casting qui n’est pas valide peut en résulter lorsque l’objet est utilisé. Un runtime fournisseur peut définir son propre type de représentation privée pour aider à se protéger contre les fausses représentations. Vous ne pouvez pas définir les types effacés en F lui-même. Seuls les types fournis peuvent être effacés. Vous devez comprendre les ramifications, pratiques et sémantiques, d’utiliser soit des types effacés pour votre fournisseur de type ou un fournisseur qui fournit des types effacés. Un type effacé n’a pas de type .NET réel. Par conséquent, vous ne pouvez pas faire une réflexion précise sur le type, et vous pourriez subvertir les types effacés si vous utilisez des moulages de temps d’exécution et d’autres techniques qui s’appuient sur la sémantique exacte de type runtime. La subversion des types effacés entraîne souvent des exceptions de type de fonte au moment de l’exécution.

### <a name="choosing-representations-for-erased-provided-types"></a>Choisir des représentations pour les types fournis effacés

Pour certaines utilisations de types fournis effacés, aucune représentation n’est requise. Par exemple, le type effacé fourni ne peut contenir que des propriétés statiques et des membres et aucun constructeur, et aucune méthode ou propriété ne retournerait une instance du type. Si vous pouvez joindre des instances d’un type fourni effacé, vous devez tenir compte des questions suivantes :

**Quelle est l’effacement d’un type fourni?**

- L’effacement d’un type fourni est la façon dont le type apparaît dans le code .NET compilé.

- L’effacement d’un type de classe effacé fourni est toujours le premier type de base non effacé dans la chaîne d’héritage du type.

- L’effacement d’un type d’interface effacé fourni est toujours `System.Object`.

**Quelles sont les représentations d’un type fourni?**

- L’ensemble d’objets possibles pour un type à condition effacé est appelé ses représentations. Dans l’exemple de ce document, les représentations `Type1..Type100` de tous les types effacés fournis sont toujours des objets en chaîne.

Toutes les représentations d’un type fourni doivent être compatibles avec l’effacement du type fourni. (Sinon, soit le compilateur F donnera une erreur pour une utilisation du fournisseur de type, ou un code .NET invérifiable qui n’est pas valide sera généré. Un fournisseur de type n’est pas valide s’il renvoie du code qui donne une représentation qui n’est pas valide.)

Vous pouvez choisir une représentation pour les objets fournis en utilisant l’une ou l’autre des approches suivantes, qui sont toutes deux très courantes :

- Si vous fournissez simplement un emballage fortement tapé sur un type .NET existant, il est souvent logique pour votre type d’effacer à ce type, utiliser des instances de ce type comme représentations, ou les deux. Cette approche est appropriée lorsque la plupart des méthodes existantes sur ce type ont encore du sens lors de l’utilisation de la version fortement tapée.

- Si vous voulez créer une API qui diffère considérablement de tout API .NET existant, il est logique de créer des types de temps d’exécution qui seront l’effacement de type et les représentations pour les types fournis.

L’exemple dans ce document utilise les chaînes comme représentations d’objets fournis. Fréquemment, il peut être approprié d’utiliser d’autres objets pour des représentations. Par exemple, vous pouvez utiliser un dictionnaire comme sac de propriété :

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Comme alternative, vous pouvez définir un type dans votre fournisseur de type qui sera utilisé à l’heure d’exécution pour former la représentation, ainsi qu’une ou plusieurs opérations de temps d’exécution :

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Les membres à condition de construire des instances de ce type d’objet :

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

Dans ce cas, vous pouvez (optionnellement) utiliser ce type comme effacement de type en spécifiant ce type comme lors de la `baseType` construction de la `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Leçons clés

La section précédente expliquait comment créer un simple fournisseur de type effacement qui fournit une gamme de types, de propriétés et de méthodes. Cette section a également expliqué le concept d’effacement de type, y compris certains des avantages et des inconvénients de fournir des types effacés d’un fournisseur de type, et a discuté des représentations des types effacés.

## <a name="a-type-provider-that-uses-static-parameters"></a>Un fournisseur de type qui utilise des paramètres statiques

La possibilité de paramétriser les fournisseurs de type par des données statiques permet de nombreux scénarios intéressants, même dans les cas où le fournisseur n’a pas besoin d’accéder à des données locales ou distantes. Dans cette section, vous apprendrez quelques techniques de base pour mettre sur pied un tel fournisseur.

### <a name="type-checked-regex-provider"></a>Type Vérifié Regex Fournisseur

Imaginez que vous souhaitez implémenter un fournisseur <xref:System.Text.RegularExpressions.Regex> de type pour les expressions régulières qui enveloppe les bibliothèques .NET dans une interface qui fournit les garanties suivantes de temps de compilation :

- Vérifier si une expression régulière est valide.

- Fournir des propriétés nommées sur les correspondances qui sont basées sur les noms de groupe dans l’expression régulière.

Cette section vous montre comment utiliser `RegexTyped` des fournisseurs de type pour créer un type que le modèle d’expression régulière paramélise pour fournir ces avantages. Le compilateur signalera une erreur si le modèle fourni n’est pas valide, et le fournisseur de type peut extraire les groupes du modèle afin que vous puissiez y accéder en utilisant des propriétés nommées sur les allumettes. Lorsque vous concevez un fournisseur de type, vous devez considérer comment son API exposé devrait regarder aux utilisateurs finaux et comment cette conception se traduira par le code .NET. L’exemple suivant montre comment utiliser une telle API pour obtenir les composants du code régional :

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

L’exemple suivant montre comment le fournisseur de type traduit ces appels :

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Notez les points suivants :

- Le type Regex standard `RegexTyped` représente le type paramétré.

- Le `RegexTyped` constructeur donne lieu à un appel au constructeur Regex, en passant dans l’argument de type statique pour le modèle.

- Les résultats `Match` de la méthode sont <xref:System.Text.RegularExpressions.Match> représentés par le type standard.

- Chaque groupe désigné se traduit par une propriété fournie, et l’accès à `Groups` la propriété entraîne l’utilisation d’un indexer sur la collection d’un match.

Le code suivant est au cœur de la logique pour implémenter un tel fournisseur, et cet exemple omet l’ajout de tous les membres au type fourni. Pour obtenir de l’information sur chaque membre ajouté, consultez la section appropriée plus tard dans ce sujet. Pour le code complet, téléchargez l’échantillon à partir du [pack d’échantillons F 3.0](https://archive.codeplex.com/?p=fsharp3sample) sur le site Web de CodePlex.

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with
          | [| :? string as pattern|] ->

            // Create an instance of the regular expression.
            //
            // This will fail with System.ArgumentException if the regular expression is not valid.
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty =
              ProvidedTypeDefinition(
                thisAssembly,
                rootNamespace,
                typeName,
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

Notez les points suivants :

- Le fournisseur de type prend `pattern`deux paramètres statiques: `options`le , qui est obligatoire, et le , qui sont facultatifs (parce qu’une valeur par défaut est fournie).

- Une fois les arguments statiques fournis, vous créez un exemple de l’expression régulière. Cette instance jettera une exception si le Regex est mal formé, et cette erreur sera signalée aux utilisateurs.

- Dans `DefineStaticParameters` le rappel, vous définissez le type qui sera retourné après que les arguments sont fournis.

- Ce code `HideObjectMethods` s’établit à vrai afin que l’expérience IntelliSense reste rationalisée. Cet attribut `Equals`provoque `GetHashCode` `Finalize`le `GetType` , , et les membres d’être supprimés à partir de listes IntelliSense pour un objet fourni.

- Vous `obj` utilisez comme type de base de la `Regex` méthode, mais vous allez utiliser un objet comme la représentation en temps d’exécution de ce type, comme le montre l’exemple suivant.

- L’appel `Regex` au constructeur lance <xref:System.ArgumentException> un quand une expression régulière n’est pas valide. Le compilateur saisit cette exception et signale un message d’erreur à l’utilisateur à l’heure de compilation ou dans l’éditeur Visual Studio. Cette exception permet de valider les expressions régulières sans exécuter d’application.

Le type défini ci-dessus n’est pas encore utile parce qu’il ne contient pas de méthodes ou de propriétés significatives. Tout d’abord, ajouter une méthode statique: `IsMatch`

```fsharp
let isMatch =
    ProvidedMethod(
        methodName = "IsMatch",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = typeof<bool>,
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string."
ty.AddMember isMatch
```

Le code précédent définit `IsMatch`une méthode , qui prend `bool`une chaîne comme entrée et renvoie un . La seule partie délicate est `args` l’utilisation `InvokeCode` de l’argument dans la définition. Dans cet `args` exemple, est une liste de citations qui représente les arguments à cette méthode. Si la méthode est une méthode d’instance, le premier argument représente l’argument. `this` Cependant, pour une méthode statique, les arguments ne sont que les arguments explicites de la méthode. Notez que le type de valeur citée doit correspondre au `bool`type de retour spécifié (dans ce cas, ). Notez également que `AddXmlDoc` ce code utilise la méthode pour s’assurer que la méthode fournie dispose également d’une documentation utile, que vous pouvez fournir par IntelliSense.

Ensuite, ajoutez une méthode de match d’instance. Toutefois, cette méthode devrait retourner `Match` une valeur de type fourni afin que les groupes puissent être consultés d’une manière fortement tapée. Ainsi, vous déclarez d’abord le `Match` type. Étant donné que ce type dépend du modèle qui a été fourni comme argument statique, ce type doit être imbriqué dans la définition de type paramétré :

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Vous ajoutez ensuite une propriété au type Match pour chaque groupe. Au moment de l’exécution, <xref:System.Text.RegularExpressions.Match> une correspondance est représentée comme une valeur, <xref:System.Text.RegularExpressions.Match.Groups> de sorte que la citation qui définit la propriété doit utiliser la propriété indexée pour obtenir le groupe concerné.

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
    matchTy.AddMember prop
```

Encore une fois, notez que vous ajoutez la documentation XML à la propriété fournie. Notez également qu’une propriété `GetterCode` peut être lue si une `SetterCode` fonction est fournie, et la propriété peut être écrite si une fonction est fournie, de sorte que la propriété résultante est lue seulement.

Maintenant, vous pouvez créer une méthode `Match` d’instance qui renvoie une valeur de ce type:

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

Parce que vous créez `args.[0]` une `RegexTyped` méthode d’instance, représente l’instance sur laquelle la méthode est appelée, et `args.[1]` est l’argument de l’entrée.

Enfin, fournir un constructeur afin que des instances du type fourni puissent être créées.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Le constructeur efface simplement à la création d’une instance standard .NET Regex, qui est à nouveau en boîte à un objet parce que `obj` c’est l’effacement du type fourni. Avec ce changement, l’utilisation de l’API échantillon qui spécifié plus tôt dans le sujet fonctionne comme prévu. Le code suivant est complet et définitif :

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with
            | [| :? string as pattern|] ->

                // Create an instance of the regular expression.

                let r = System.Text.RegularExpressions.Regex(pattern)

                // Declare the typed regex provided type.

                let ty =
                    ProvidedTypeDefinition(
                        thisAssembly,
                        rootNamespace,
                        typeName,
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch =
                    ProvidedMethod(
                        methodName = "IsMatch",
                        parameters = [ProvidedParameter("input", typeof<string>)],
                        returnType = typeof<bool>,
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy =
                    ProvidedTypeDefinition(
                        "MatchType",
                        baseType = Some baseTy,
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop =
                          ProvidedProperty(
                            propertyName = group,
                            propertyType = typeof<Group>,
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth =
                  ProvidedMethod(
                    methodName = "Match",
                    parameters = [ProvidedParameter("input", typeof<string>)],
                    returnType = matchTy,
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor =
                  ProvidedConstructor(
                    parameters = [],
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a>Leçons clés

Cette section a expliqué comment créer un fournisseur de type qui fonctionne sur ses paramètres statiques. Le fournisseur vérifie le paramètre statique et fournit des opérations en fonction de sa valeur.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Un fournisseur de type qui est soutenu par des données locales

Fréquemment, vous pouvez vouloir des fournisseurs de type pour présenter des API basées non seulement sur des paramètres statiques, mais aussi des informations provenant de systèmes locaux ou distants. Cette section traite des fournisseurs de type qui sont basés sur des données locales, telles que les fichiers de données locaux.

### <a name="simple-csv-file-provider"></a>Fournisseur de fichiers CSV simple

À titre d’exemple, considérez un fournisseur de type pour accéder aux données scientifiques dans le format Comma Separated Value (CSV). Cette section suppose que les fichiers CSV contiennent une rangée d’en-têtes suivie de données de points flottants, comme l’illustre le tableau suivant :

|Distance (mètre)|Temps (deuxième)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

Cette section montre comment fournir un type que vous `Distance` pouvez utiliser `float<meter>` pour `Time` obtenir `float<second>`des rangées avec une propriété de type et une propriété de type . Par souci de simplicité, les hypothèses suivantes sont faites :

- Les noms d’en-tête sont soit unitaires ou ont le formulaire "Nom (unité)" et ne contiennent pas de virgules.

- Les unités sont toutes des unités System International (SI) comme le définit le module [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) .

- Les unités sont toutes simples (par exemple, compteur) plutôt que composé (par exemple, compteur /seconde).

- Toutes les colonnes contiennent des données de points flottants.

Un fournisseur plus complet assouplirait ces restrictions.

Encore une fois, la première étape consiste à examiner à quoi devrait ressembler l’API. Compte `info.csv` tenu d’un fichier avec le contenu du tableau précédent (en format virgule séparé), les utilisateurs du fournisseur doivent être en mesure d’écrire du code qui ressemble à l’exemple suivant:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Dans ce cas, le compilateur devrait convertir ces appels en quelque chose comme l’exemple suivant:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

La traduction optimale exigera du fournisseur `CsvFile` de type qu’il définisse un type réel dans l’assemblage du fournisseur de type. Les fournisseurs de type comptent souvent sur quelques types et méthodes d’aide pour envelopper la logique importante. Parce que les mesures sont effacées `float[]` au moment de la course, vous pouvez utiliser un type effacé pour une rangée. Le compilateur traitera différentes colonnes comme ayant différents types de mesure. Par exemple, la première colonne `float<meter>`dans notre exemple `float<second>`a le type , et le second a . Cependant, la représentation effacée peut rester assez simple.

Le code suivant montre le cœur de l’implémentation.

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop =
                ProvidedProperty(fieldName, fieldTy,
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop)

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 =
            ProvidedConstructor([],
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)],
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop =
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy),
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

Notez les points suivants sur la mise en œuvre :

- Les constructeurs surchargés permettent soit à l’ancien fichier, soit à un schéma identique d’être lu. Ce modèle est courant lorsque vous écrivez un fournisseur de type pour les sources de données locales ou distantes, et ce modèle permet à un fichier local d’être utilisé comme modèle pour les données à distance.

- Vous pouvez utiliser la valeur [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) qui est transmise au constructeur fournisseur de type pour résoudre les noms de fichiers relatifs.

- Vous pouvez `AddDefinitionLocation` utiliser la méthode pour définir l’emplacement des propriétés fournies. Par conséquent, `Go To Definition` si vous utilisez sur une propriété fournie, le fichier CSV s’ouvrira dans Visual Studio.

- Vous pouvez `ProvidedMeasureBuilder` utiliser le type pour rechercher les `float<_>` unités SI et pour générer les types pertinents.

### <a name="key-lessons"></a>Leçons clés

Cette section a expliqué comment créer un fournisseur de type pour une source de données locale avec un schéma simple qui est contenu dans la source de données elle-même.

## <a name="going-further"></a>Aller plus loin

Les sections suivantes contiennent des suggestions pour une étude plus approfondie.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Un regard sur le code compilé pour les types effacés

Pour vous donner une idée de la façon dont l’utilisation du fournisseur de type correspond `HelloWorldTypeProvider` au code émis, regardez la fonction suivante en utilisant le qui est utilisé plus tôt dans ce sujet.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Voici une image du code résultant décomposé en utilisant ildasm.exe:

```il
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

Comme l’exemple le montre, `Type1` toutes `InstanceProperty` les mentions du type et de la propriété ont été effacées, ne laissant que des opérations sur les types de temps d’exécution impliqués.

### <a name="design-and-naming-conventions-for-type-providers"></a>Conventions de conception et de nomination pour les fournisseurs de type

Observez les conventions suivantes lors de la rédaction de fournisseurs de type.

**Fournisseurs de protocoles de connectivité** En général, les noms de la plupart des DLS fournisseurs pour les protocoles de `TypeProvider` connectivité `TypeProviders`des données et des services, tels que les connexions OData ou SQL, devraient se terminer ou . Par exemple, utilisez un nom DLL qui ressemble à la chaîne suivante :

`Fabrikam.Management.BasicTypeProviders.dll`

Assurez-vous que vos types fournis sont membres de l’espace nom correspondant et indiquez le protocole de connectivité que vous avez mis en œuvre :

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Fournisseurs de services publics pour le codage général**.  Pour un fournisseur de type utilitaire comme celui pour les expressions régulières, le fournisseur de type peut faire partie d’une bibliothèque de base, comme le montre l’exemple suivant :

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

Dans ce cas, le type fourni apparaîtrait à un point approprié selon les conventions normales de conception .NET :

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Sources de données Singleton**. Certains fournisseurs de type se connectent à une seule source de données dédiées et ne fournissent que des données. Dans ce cas, vous `TypeProvider` devez laisser tomber le suffixe et utiliser des conventions normales pour .NET nommant:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Pour plus d’informations, voir la `GetConnection` convention de conception qui est décrite plus tard dans ce sujet.

### <a name="design-patterns-for-type-providers"></a>Modèles de conception pour les fournisseurs de type

Les sections suivantes décrivent les modèles de conception que vous pouvez utiliser lors de la rédaction de fournisseurs de type.

#### <a name="the-getconnection-design-pattern"></a>Le modèle de conception GetConnection

La plupart des fournisseurs de `GetConnection` type doivent être écrits pour utiliser le modèle utilisé par les fournisseurs de type dans FSharp.Data.TypeProviders.dll, comme le montre l’exemple suivant:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Fournisseurs de types soutenus par des données et des services à distance

Avant de créer un fournisseur de type qui est soutenu par des données et des services distants, vous devez tenir compte d’une gamme de questions inhérentes à la programmation connectée. Ces questions comprennent les considérations suivantes :

- cartographie du schéma

- la vivacité et l’invalidation en présence de changement de schéma

- mise en cache de schémas

- mises en œuvre asynchrone des opérations d’accès aux données

- demandes à l’appui, y compris les requêtes LINQ

- informations d’identification et authentification

Ce sujet n’explore pas ces questions plus loin.

### <a name="additional-authoring-techniques"></a>Techniques d’auteur supplémentaires

Lorsque vous écrivez vos propres fournisseurs de type, vous pouvez utiliser les techniques supplémentaires suivantes.

### <a name="creating-types-and-members-on-demand"></a>Création de types et de membres à la demande

L’API ProvidedType a retardé les versions d’AddMember.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Ces versions sont utilisées pour créer des espaces à la demande de types.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Fournir des types de tableaux et des instantanéisissements de type génériques

Vous faites des membres fournis (dont les signatures comprennent les types de tableau, les `MakeArrayType` `MakePointerType`types `MakeGenericType` byref, <xref:System.Type>et `ProvidedTypeDefinitions`les instantanéiations des types génériques) en utilisant la normale , , et sur n’importe quel cas de , y compris .

> [!NOTE]
> Dans certains cas, vous devrez peut-être utiliser l’aide dans `ProvidedTypeBuilder.MakeGenericType`.  Consultez la [documentation SDK de Type Provider](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) pour plus de détails.

### <a name="providing-unit-of-measure-annotations"></a>Fournir une unité d’annotations de mesure

L’API ProvidedTypes fournit des aides pour fournir des annotations de mesure. Par exemple, pour `float<kg>`fournir le type, utilisez le code suivant :

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Pour fournir `Nullable<decimal<kg/m^2>>`le type, utilisez le code suivant :

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Accès aux ressources project-local ou script-local

Chaque instance d’un fournisseur `TypeProviderConfig` de type peut être donnée une valeur pendant la construction. Cette valeur contient le « dossier de résolution » pour le fournisseur (c’est-à-dire le dossier de projet pour la compilation ou l’annuaire qui contient un script), la liste des assemblages référencés et d’autres informations.

### <a name="invalidation"></a>Invalidation

Les fournisseurs peuvent soulever des signaux d’invalidation pour aviser le service linguistique FD que les hypothèses de schéma peuvent avoir changé. Lorsque l’invalidation se produit, un typecheck est refait si le fournisseur est hébergé dans Visual Studio. Ce signal sera ignoré lorsque le fournisseur est hébergé dans F Interactive ou par le compilateur F (fsc.exe).

### <a name="caching-schema-information"></a>Caching Schema Informations

Les fournisseurs doivent souvent cacher l’accès à l’information sur les schémas. Les données mises en cache doivent être stockées à l’aide d’un nom de fichier qui est donné sous forme de paramètre statique ou de données utilisateur. Un exemple de mise en `LocalSchemaFile` cache de schéma `FSharp.Data.TypeProviders` est le paramètre dans les fournisseurs de type dans l’assemblage. Dans la mise en œuvre de ces fournisseurs, ce paramètre statique ordonne au fournisseur de type d’utiliser les informations schématiques dans le fichier local spécifié au lieu d’accéder à la source de données sur le réseau. Pour utiliser des informations de schéma mise en `ForceUpdate` `false`cache, vous devez également définir le paramètre statique à . Vous pouvez utiliser une technique similaire pour activer l’accès aux données en ligne et hors ligne.

### <a name="backing-assembly"></a>Assemblée de soutien

Lorsque vous compilez `.exe` un ou un `.dll` fichier, le fichier support .dll pour les types générés est statiquement lié à l’assemblage résultant. Ce lien est créé en copiant les définitions de type Langue intermédiaire (IL) et toutes les ressources gérées de l’assemblage de soutien à l’assemblage final. Lorsque vous utilisez F Interactive, le fichier support .dll n’est pas copié et est plutôt chargé directement dans le processus interactif F.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Exceptions et diagnostics de la part des fournisseurs de types

Toutes les utilisations de tous les membres des types fournis peuvent jeter des exceptions. Dans tous les cas, si un fournisseur de type lance une exception, le compilateur hôte attribue l’erreur à un fournisseur de type spécifique.

- Les exceptions des fournisseurs de type ne devraient jamais entraîner d’erreurs internes de compilateur.

- Les fournisseurs de type ne peuvent pas signaler les avertissements.

- Lorsqu’un fournisseur de type est hébergé dans le compilateur F, un environnement de développement FMD ou F Interactive, toutes les exceptions de ce fournisseur sont prises. La propriété Message est toujours le texte d’erreur, et aucune trace de pile n’apparaît. Si vous allez jeter une exception, vous pouvez `System.NotSupportedException`jeter `System.IO.IOException` `System.Exception`les exemples suivants: , .

#### <a name="providing-generated-types"></a>Fournir des types générés

Jusqu’à présent, ce document a expliqué comment fournir des types effacés. Vous pouvez également utiliser le mécanisme de fournisseur de type dans F pour fournir les types générés, qui sont ajoutés comme définitions réelles de type .NET dans le programme des utilisateurs. Vous devez vous référer aux types produits en utilisant une définition de type.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

Le code d’assistance ProvidedTypes-0.2 qui fait partie de la version F 3.0 n’a qu’un soutien limité pour fournir des types générés. Les énoncés suivants doivent être valables pour une définition de type générée :

- `isErased` doit être défini sur `false`.

- Le type généré doit être `ProvidedAssembly()`ajouté à un nouveau bâtiment, qui représente un conteneur pour les fragments de code générés.

- Le fournisseur doit avoir un assemblage qui a un fichier support .NET .dll réel avec un fichier correspondant .dll sur le disque.

## <a name="rules-and-limitations"></a>Règles et limites

Lorsque vous écrivez des fournisseurs de type, gardez à l’esprit les règles et les limitations suivantes.

### <a name="provided-types-must-be-reachable"></a>À condition que les types soient accessibles

Tous les types fournis doivent être accessibles à partir des types non imbriqués. Les types non imbriqués sont `TypeProviderForNamespaces` donnés dans l’appel au constructeur ou un appel à `AddNamespace`. Par exemple, si le `StaticClass.P : T`fournisseur fournit un type, vous devez vous assurer que T est soit un type non imbriqué ou imbriqué sous un seul.

Par exemple, certains fournisseurs ont `DataTypes` une classe `T1, T2, T3, ...` statique comme celle qui contient ces types. Sinon, l’erreur dit qu’une référence au type T dans l’assemblage A a été trouvée, mais le type n’a pas pu être trouvé dans cet assemblage. Si cette erreur apparaît, vérifiez que tous vos sous-types peuvent être atteints à partir des types de fournisseur. Remarque : `T1, T2, T3...` Ces types sont appelés les types à *la volée.* N’oubliez pas de les mettre dans un espace nom accessible ou un type de parent.

### <a name="limitations-of-the-type-provider-mechanism"></a>Limitations du mécanisme de fournisseur de type

Le mécanisme de fournisseur de type dans le FMD a les limites suivantes :

- L’infrastructure sous-jacente pour les fournisseurs de type dans F N’appuie pas les types génériques fournis ou fourni des méthodes génériques.

- Le mécanisme ne prend pas en charge les types imbriqués avec des paramètres statiques.

## <a name="development-tips"></a>Conseils de développement

Vous trouverez peut-être les conseils suivants utiles pendant le processus de développement :

### <a name="run-two-instances-of-visual-studio"></a>Exécuter deux instances de Visual Studio

Vous pouvez développer le fournisseur de type dans un cas et tester le fournisseur dans l’autre parce que le test IDE prendra un verrou sur le fichier .dll qui empêche le fournisseur de type d’être reconstruit. Ainsi, vous devez fermer la deuxième instance de Visual Studio pendant que le fournisseur est construit dans le premier cas, puis vous devez rouvrir la deuxième instance après la construction du fournisseur.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Fournisseurs de type Debug en utilisant des invocations de fsc.exe

Vous pouvez invoquer des fournisseurs de type en utilisant les outils suivants :

- fsc.exe (Compilateur de ligne de commande F)

- fsi.exe (Compilateur interactif de F)

- devenv.exe (Studio visuel)

Vous pouvez souvent déboquer les fournisseurs de type le plus facilement en utilisant fsc.exe sur un fichier de script de test (par exemple, script.fsx). Vous pouvez lancer un débbugger à partir d’une invite de commande.

```console
devenv /debugexe fsc.exe script.fsx
```

  Vous pouvez utiliser l’enregistrement d’impression à stdout.

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de type](index.md)
- [Le fournisseur de type SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
