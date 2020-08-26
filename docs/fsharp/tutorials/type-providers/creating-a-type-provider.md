---
title: 'Didacticiel : créer un fournisseur de type'
description: 'Découvrez comment créer vos propres fournisseurs de type F # dans F # 3,0 en examinant plusieurs fournisseurs de types simples pour illustrer les concepts de base.'
ms.date: 11/04/2019
ms.openlocfilehash: 71225614ed983a76d35c214faa87bbad0fbb7d24
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810870"
---
# <a name="tutorial-create-a-type-provider"></a>Didacticiel : créer un fournisseur de type

Le mécanisme du fournisseur de type en F # est une partie importante de la prise en charge de la programmation riche en informations. Ce didacticiel explique comment créer vos propres fournisseurs de type en vous guidant tout au long du développement de plusieurs fournisseurs de types simples pour illustrer les concepts de base. Pour plus d’informations sur le mécanisme du fournisseur de type en F #, consultez [fournisseurs de type](index.md).

L’écosystème F # contient une plage de fournisseurs de type pour les services de données Internet et d’entreprise couramment utilisés. Par exemple :

- [FSharp. Data](https://fsharp.github.io/FSharp.Data/) comprend des fournisseurs de type pour les formats de documents JSON, XML, CSV et html.

- [SqlProvider](https://fsprojects.github.io/SQLProvider/) fournit un accès fortement typé aux bases de données SQL via un mappage d’objets et des requêtes LINQ F # sur ces sources de données.

- [FSharp. Data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) possède un ensemble de fournisseurs de type pour l’incorporation activée de T-SQL au moment de la compilation en F #.

- [FSharp. Data. TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) est un ancien ensemble de fournisseurs de type à utiliser uniquement avec .NET Framework programmation pour l’accès aux services de données SQL, Entity Framework, ODATA et WSDL.

Le cas échéant, vous pouvez créer des fournisseurs de type personnalisé, ou référencer des fournisseurs de type que d’autres ont créés. Par exemple, votre organisation peut avoir un service de données qui fournit un nombre important et croissant de jeux de données nommés, chacun avec son propre schéma de données stable. Vous pouvez créer un fournisseur de type qui lit les schémas et présente les jeux de données actuels au programmeur de manière fortement typée.

## <a name="before-you-start"></a>Avant de commencer

Le mécanisme du fournisseur de type est principalement conçu pour injecter des données stables et des espaces d’informations de service dans l’expérience de programmation F #.

Ce mécanisme n’est pas conçu pour injecter des espaces d’information dont le schéma est modifié pendant l’exécution du programme, en ce qui concerne la logique du programme. En outre, le mécanisme n’est pas conçu pour la méta-programmation intra-langage, même si ce domaine contient des utilisations valides. Vous devez utiliser ce mécanisme uniquement lorsque cela est nécessaire et lorsque le développement d’un fournisseur de type produit une valeur très élevée.

Évitez d’écrire un fournisseur de type dans lequel un schéma n’est pas disponible. De même, vous devez éviter d’écrire un fournisseur de type dans lequel une bibliothèque .NET ordinaire (ou même une bibliothèque existante) suffirait.

Avant de commencer, vous pouvez poser les questions suivantes :

- Disposez-vous d’un schéma pour votre source d’informations ? Dans ce cas, qu’est-ce que le mappage dans le système de type F # et .NET ?

- Pouvez-vous utiliser une API existante (de type dynamique) comme point de départ pour votre implémentation ?

- Votre organisation et vous-même avez-vous des utilisations suffisantes du fournisseur de type pour que l’écriture soit utile ? Une bibliothèque .NET normale répond-elle à vos besoins ?

- Combien votre schéma sera-t-il modifié ?

- Va-t-il changer au cours du codage ?

- Sera-t-il modifié entre les sessions de codage ?

- Va-t-il changer au cours de l’exécution du programme ?

Les fournisseurs de type sont mieux adaptés aux situations où le schéma est stable au moment de l’exécution et Pendant la durée de vie du code compilé.

## <a name="a-simple-type-provider"></a>Un fournisseur de type simple

Cet exemple est Samples. HelloWorldTypeProvider, de la même façon que les exemples du `examples` répertoire du [Kit de développement logiciel (SDK) du fournisseur de type F #](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). Le fournisseur met à disposition un « espace de type » qui contient 100 types effacés, comme le montre le code suivant en utilisant la syntaxe de signature F # et en omettant les détails pour tous les sauf `Type1` . Pour plus d’informations sur les types effacés, consultez [Détails sur les types fournis effacés](#details-about-erased-provided-types) plus loin dans cette rubrique.

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

Notez que le jeu de types et de membres fourni est statiquement connu. Cet exemple ne tire pas parti de la capacité des fournisseurs à fournir des types qui dépendent d’un schéma. L’implémentation du fournisseur de type est présentée dans le code suivant, et les détails sont traités dans les sections ultérieures de cette rubrique.

> [!WARNING]
> Il peut y avoir des différences entre ce code et les exemples en ligne.

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

Pour utiliser ce fournisseur, ouvrez une instance distincte de Visual Studio, créez un script F #, puis ajoutez une référence au fournisseur à partir de votre script à l’aide de #r comme le montre le code suivant :

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

Recherchez ensuite les types sous l' `Samples.HelloWorldTypeProvider` espace de noms généré par le fournisseur de type.

Avant de recompiler le fournisseur, assurez-vous que vous avez fermé toutes les instances de Visual Studio et F# Interactive qui utilisent la DLL du fournisseur. Sinon, une erreur de génération se produit, car la DLL de sortie est verrouillée.

Pour déboguer ce fournisseur à l’aide d’instructions print, créez un script qui expose un problème au fournisseur, puis utilisez le code suivant :

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Pour déboguer ce fournisseur à l’aide de Visual Studio, ouvrez le Invite de commandes développeur pour Visual Studio avec les informations d’identification d’administration, puis exécutez la commande suivante :

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Au lieu de cela, ouvrez Visual Studio, ouvrez le menu Déboguer, choisissez `Debug/Attach to process…` , puis attachez à un autre `devenv` processus dans lequel vous modifiez votre script. À l’aide de cette méthode, vous pouvez cibler plus facilement une logique particulière dans le fournisseur de type en tapant de manière interactive des expressions dans la deuxième instance (avec IntelliSense complet et d’autres fonctionnalités).

Vous pouvez désactiver le débogage Uniquement mon code pour mieux identifier les erreurs dans le code généré. Pour plus d’informations sur l’activation ou la désactivation de cette fonctionnalité, consultez [navigation dans le code avec le débogueur](/visualstudio/debugger/navigating-through-code-with-the-debugger). En outre, vous pouvez également définir l’interception des exceptions de première chance en ouvrant le `Debug` menu, puis `Exceptions` en choisissant ou en appuyant sur les touches Ctrl + Alt + E pour ouvrir la `Exceptions` boîte de dialogue. Dans cette boîte de dialogue, sous `Common Language Runtime Exceptions` , activez la `Thrown` case à cocher.

### <a name="implementation-of-the-type-provider"></a>Implémentation du fournisseur de type

Cette section vous guide à travers les principales sections de l’implémentation du fournisseur de type. Tout d’abord, vous définissez le type du fournisseur de type personnalisé lui-même :

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Ce type doit être public, et vous devez le marquer avec l’attribut [TypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderattribute.html) afin que le compilateur reconnaisse le fournisseur de type lorsqu’un projet F # distinct référence l’assembly qui contient le type. Le paramètre de *configuration* est facultatif et, le cas échéant, contient des informations de configuration contextuelle pour l’instance de fournisseur de type créée par le compilateur F #.

Ensuite, implémentez l’interface [ITypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-itypeprovider.html) . Dans ce cas, vous utilisez le `TypeProviderForNamespaces` type de l' `ProvidedTypes` API comme type de base. Ce type d’assistance peut fournir une collection finie d’espaces de noms fournis de façon dynamique, chacun d’entre eux contenant directement un nombre fini de types fixes et fournis de façon dynamique. Dans ce contexte, le fournisseur génère des types de manière *dynamique* , même s’ils ne sont pas nécessaires ou utilisés.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Ensuite, définissez les valeurs privées locales qui spécifient l’espace de noms pour les types fournis et recherchez l’assembly du fournisseur de type lui-même. Cet assembly est utilisé ultérieurement comme type de parent logique des types effacés fournis.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Ensuite, créez une fonction pour fournir chacun des types Type1... Type100. Cette fonction est expliquée plus en détail plus loin dans cette rubrique.

```fsharp
let makeOneProvidedType (n:int) = …
```

Ensuite, générez les types fournis par 100 :

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Ensuite, ajoutez les types en tant qu’espace de noms fourni :

```fsharp
do this.AddNamespace(namespaceName, types)
```

Enfin, ajoutez un attribut d’assembly qui indique que vous créez une DLL de fournisseur de type :

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Fournir un type et ses membres

La `makeOneProvidedType` fonction effectue le véritable travail de fourniture de l’un des types.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Cette étape explique l’implémentation de cette fonction. Tout d’abord, créez le type fourni (par exemple, type1, lorsque n = 1 ou Type57, quand n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Notez les points suivants :

- Ce type fourni est effacé.  Étant donné que vous indiquez que le type `obj` de base est, les instances s’affichent en tant que valeurs de type [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) dans le code compilé.

- Lorsque vous spécifiez un type non imbriqué, vous devez spécifier l’assembly et l’espace de noms. Pour les types effacés, l’assembly doit être l’assembly du fournisseur de type lui-même.

Ensuite, ajoutez la documentation XML au type. Cette documentation est retardée, c’est-à-dire calculée à la demande si le compilateur hôte en a besoin.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Ensuite, vous ajoutez une propriété statique fournie au type :

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

L’obtention de cette propriété correspond toujours à la chaîne « Hello ! ». Le `GetterCode` de la propriété utilise un quotation F #, qui représente le code généré par le compilateur hôte pour obtenir la propriété. Pour plus d’informations sur les guillemets, consultez [Quotations de code (F #)](../../language-reference/code-quotations.md).

Ajoutez la documentation XML à la propriété.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Attachez à présent la propriété fournie au type fourni. Vous devez attacher un membre fourni à un seul et unique type. Dans le cas contraire, le membre ne sera jamais accessible.

```fsharp
t.AddMember staticProp
```

Créez maintenant un constructeur fourni qui ne prend aucun paramètre.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode`Pour le constructeur retourne un quotation F #, qui représente le code que le compilateur hôte génère lorsque le constructeur est appelé. Par exemple, vous pouvez utiliser le constructeur suivant :

```fsharp
new Type10()
```

Une instance du type fourni sera créée avec les données sous-jacentes « données de l’objet ». Le code entre guillemets comprend une conversion en [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) , car ce type est l’effacement de ce type fourni (comme vous l’avez spécifié quand vous avez déclaré le type fourni).

Ajoutez la documentation XML au constructeur et ajoutez le constructeur fourni au type fourni :

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Créez un deuxième constructeur fourni qui accepte un paramètre :

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

Le du `InvokeCode` constructeur retourne à nouveau un quotation F #, qui représente le code généré par le compilateur hôte pour un appel à la méthode. Par exemple, vous pouvez utiliser le constructeur suivant :

```fsharp
new Type10("ten")
```

Une instance du type fourni est créée avec les données sous-jacentes « dix ». Vous avez peut-être déjà remarqué que la `InvokeCode` fonction retourne une quotation. L’entrée de cette fonction est une liste d’expressions, une par paramètre de constructeur. Dans ce cas, une expression qui représente la valeur d’un paramètre unique est disponible dans `args.[0]` . Le code d’un appel au constructeur convertit la valeur de retour en type effacé `obj` . Après avoir ajouté le deuxième constructeur fourni au type, vous créez une propriété d’instance fournie :

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

L’obtention de cette propriété retourne la longueur de la chaîne, qui est l’objet de représentation. La `GetterCode` propriété retourne un quotation F # qui spécifie le code que le compilateur hôte génère pour recevoir la propriété. Comme `InvokeCode` , la `GetterCode` fonction retourne une quotation. Le compilateur hôte appelle cette fonction avec une liste d’arguments. Dans ce cas, les arguments incluent uniquement l’expression unique qui représente l’instance sur laquelle l’accesseur Get est appelé, auquel vous pouvez accéder à l’aide de `args.[0]` . L’implémentation de `GetterCode` , puis les épissures dans le devis de résultat au type effacé `obj` , et un cast est utilisé pour satisfaire le mécanisme du compilateur pour vérifier les types que l’objet est une chaîne. La partie suivante de `makeOneProvidedType` fournit une méthode d’instance avec un paramètre.

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

Enfin, créez un type imbriqué qui contient 100 propriétés imbriquées. La création de ce type imbriqué et de ses propriétés est différée, c’est-à-dire calculée à la demande.

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

L’exemple de cette section fournit uniquement des *types fournis effacés*, qui sont particulièrement utiles dans les situations suivantes :

- Lorsque vous écrivez un fournisseur pour un espace d’informations qui contient uniquement des données et des méthodes.

- Lorsque vous écrivez un fournisseur dans lequel la sémantique de type Runtime exacte n’est pas essentielle pour une utilisation pratique de l’espace d’information.

- Lorsque vous écrivez un fournisseur pour un espace d’informations tellement grand et interconnecté, il n’est techniquement pas possible de générer des types .NET réels pour l’espace d’information.

Dans cet exemple, chaque type fourni est effacé en type `obj` , et toutes les utilisations du type s’affichent en tant que type `obj` dans le code compilé. En fait, les objets sous-jacents dans ces exemples sont des chaînes, mais le type apparaît comme `System.Object` dans le code compilé .net. Comme pour toutes les utilisations de l’effacement de type, vous pouvez utiliser le boxing, l’unboxing et le cast explicites pour corrompre les types effacés. Dans ce cas, une exception de cast non valide peut se produire lorsque l’objet est utilisé. Un Runtime du fournisseur peut définir son propre type de représentation privée pour aider à se protéger contre les fausses représentations. Vous ne pouvez pas définir de types effacés en F # lui-même. Seuls les types fournis peuvent être effacés. Vous devez comprendre les ramifications, à la fois pratiques et sémantiques, de l’utilisation de types effacés pour votre fournisseur de type ou d’un fournisseur qui fournit des types effacés. Un type effacé n’a pas de type .NET réel. Par conséquent, vous ne pouvez pas faire de réflexion exacte sur le type et vous risquez de compromettre les types effacés si vous utilisez des casts de Runtime et d’autres techniques qui reposent sur la sémantique de type Runtime exacte. La sous-version des types effacés aboutit souvent à des exceptions de conversion de type au moment de l’exécution.

### <a name="choosing-representations-for-erased-provided-types"></a>Choix des représentations pour les types fournis effacés

Pour certaines utilisations de types fournis effacés, aucune représentation n’est requise. Par exemple, le type fourni effacé peut contenir uniquement des propriétés et des membres statiques et aucun constructeur, et aucune méthode ou propriété ne retournerait une instance du type. Si vous pouvez atteindre les instances d’un type fourni effacé, vous devez prendre en compte les questions suivantes :

**Qu’est-ce que l’effacement d’un type fourni ?**

- L’effacement d’un type fourni est le mode d’affichage du type dans le code .NET compilé.

- L’effacement d’un type de classe effacé fourni est toujours le premier type de base non effacé dans la chaîne d’héritage du type.

- L’effacement d’un type d’interface effacé fourni est toujours `System.Object` .

**Quelles sont les représentations d’un type fourni ?**

- L’ensemble d’objets possibles pour un type fourni effacé est appelé ses représentations. Dans l’exemple de ce document, les représentations de tous les types fournis par l’effacement `Type1..Type100` sont toujours des objets String.

Toutes les représentations d’un type fourni doivent être compatibles avec l’effacement du type fourni. (Sinon, soit le compilateur F # génère une erreur pour une utilisation du fournisseur de type, soit le code .NET non vérifiable non valide sera généré. Un fournisseur de type n’est pas valide s’il retourne du code qui donne une représentation qui n’est pas valide.)

Vous pouvez choisir une représentation pour les objets fournis à l’aide de l’une des approches suivantes, qui sont très courantes :

- Si vous fournissez simplement un wrapper fortement typé sur un type .NET existant, il est souvent judicieux que votre type efface ce type, utilise des instances de ce type comme représentations, ou les deux à la fois. Cette approche est appropriée lorsque la plupart des méthodes existantes sur ce type ont toujours un sens quand vous utilisez la version fortement typée.

- Si vous souhaitez créer une API qui diffère considérablement de toute API .NET existante, il est logique de créer des types au moment de l’exécution qui seront l’effacement de type et les représentations pour les types fournis.

L’exemple de ce document utilise des chaînes comme représentations des objets fournis. Souvent, il peut être approprié d’utiliser d’autres objets pour les représentations. Par exemple, vous pouvez utiliser un dictionnaire comme conteneur de propriétés :

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Vous pouvez également définir un type dans votre fournisseur de type qui sera utilisé lors de l’exécution pour former la représentation, ainsi qu’une ou plusieurs opérations d’exécution :

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Les membres fournis peuvent alors construire des instances de ce type d’objet :

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

Dans ce cas, vous pouvez (si vous le souhaitez) utiliser ce type comme effacement de type en spécifiant ce type comme lors de la `baseType` construction de `ProvidedTypeDefinition` :

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Leçons clés

La section précédente a expliqué comment créer un fournisseur de type d’effacement simple qui fournit une plage de types, de propriétés et de méthodes. Cette section a également expliqué le concept d’effacement de type, y compris certains avantages et inconvénients liés à la fourniture de types effacés à partir d’un fournisseur de type, et les représentations des types effacés.

## <a name="a-type-provider-that-uses-static-parameters"></a>Fournisseur de type qui utilise des paramètres statiques

La possibilité de paramétrer des fournisseurs de type par données statiques permet de nombreux scénarios intéressants, même si le fournisseur n’a pas besoin d’accéder à des données locales ou distantes. Dans cette section, vous allez découvrir quelques techniques de base pour regrouper un tel fournisseur.

### <a name="type-checked-regex-provider"></a>Fournisseur d’expressions régulières vérifiées de type

Imaginez que vous souhaitiez implémenter un fournisseur de type pour les expressions régulières qui encapsule les <xref:System.Text.RegularExpressions.Regex> bibliothèques .net dans une interface qui fournit les garanties au moment de la compilation suivantes :

- Vérification de la validité d’une expression régulière.

- Fournir des propriétés nommées sur les correspondances basées sur tout nom de groupe dans l’expression régulière.

Cette section vous montre comment utiliser des fournisseurs de type pour créer un `RegexTyped` type que le modèle d’expression régulière paramètrete pour offrir ces avantages. Le compilateur signale une erreur si le modèle fourni n’est pas valide et que le fournisseur de type peut extraire les groupes du modèle afin que vous puissiez y accéder à l’aide des propriétés nommées sur les correspondances. Quand vous concevez un fournisseur de type, vous devez prendre en compte la façon dont son API exposée doit s’afficher pour les utilisateurs finaux et comment cette conception sera traduite en code .NET. L’exemple suivant montre comment utiliser une telle API pour récupérer les composants de l’indicatif de zone :

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

L’exemple suivant montre comment le fournisseur de type traduit ces appels :

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Notez les points suivants :

- Le type Regex standard représente le type paramétré `RegexTyped` .

- Le `RegexTyped` constructeur entraîne un appel au constructeur Regex, en passant l’argument de type statique pour le modèle.

- Les résultats de la `Match` méthode sont représentés par le <xref:System.Text.RegularExpressions.Match> type standard.

- Chaque groupe nommé produit une propriété fournie et l’accès à la propriété entraîne l’utilisation d’un indexeur sur la collection d’une correspondance `Groups` .

Le code suivant est le cœur de la logique permettant d’implémenter un tel fournisseur, et cet exemple omet l’ajout de tous les membres au type fourni. Pour plus d’informations sur chaque membre ajouté, consultez la section appropriée plus loin dans cette rubrique. Pour obtenir le code complet, téléchargez l’exemple à partir du [Pack d’exemples F # 3,0](https://archive.codeplex.com/?p=fsharp3sample) sur le site Web CodePlex.

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

- Le fournisseur de type accepte deux paramètres statiques : `pattern` , qui est obligatoire, et `options` , qui sont facultatifs (car une valeur par défaut est fournie).

- Une fois les arguments statiques fournis, vous créez une instance de l’expression régulière. Cette instance lèvera une exception si l’expression régulière est incorrecte, et cette erreur sera signalée aux utilisateurs.

- Dans le `DefineStaticParameters` rappel, vous définissez le type qui sera retourné une fois les arguments fournis.

- Ce code affecte `HideObjectMethods` la valeur true pour que l’expérience IntelliSense reste rationalisée. Cet attribut entraîne la `Equals` `GetHashCode` suppression des membres,, `Finalize` et `GetType` des listes IntelliSense pour un objet fourni.

- Vous utilisez `obj` comme type de base de la méthode, mais vous utiliserez un `Regex` objet comme représentation d’exécution de ce type, comme le montre l’exemple suivant.

- L’appel au `Regex` constructeur lève une <xref:System.ArgumentException> lorsqu’une expression régulière n’est pas valide. Le compilateur intercepte cette exception et signale un message d’erreur à l’utilisateur au moment de la compilation ou dans l’éditeur Visual Studio. Cette exception permet de valider des expressions régulières sans exécuter une application.

Le type défini ci-dessus n’est pas encore utile, car il ne contient aucune méthode ou propriété significative. Tout d’abord, ajoutez une `IsMatch` méthode statique :

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

Le code précédent définit une méthode `IsMatch` , qui prend une chaîne comme entrée et retourne un `bool` . La seule difficulté est l’utilisation de l' `args` argument dans la `InvokeCode` définition. Dans cet exemple, `args` est une liste de devis qui représente les arguments de cette méthode. Si la méthode est une méthode d’instance, le premier argument représente l' `this` argument. Toutefois, pour une méthode statique, les arguments sont tous uniquement les arguments explicites de la méthode. Notez que le type de la valeur entre guillemets doit correspondre au type de retour spécifié (dans ce cas, `bool` ). Notez également que ce code utilise la `AddXmlDoc` méthode pour s’assurer que la méthode fournie possède également une documentation utile, que vous pouvez fournir via IntelliSense.

Ensuite, ajoutez une méthode de correspondance d’instance. Toutefois, cette méthode doit retourner une valeur d’un `Match` type fourni afin que les groupes soient accessibles de manière fortement typée. Par conséquent, vous devez d’abord déclarer le `Match` type. Étant donné que ce type dépend du modèle qui a été fourni en tant qu’argument statique, ce type doit être imbriqué dans la définition de type paramétrable :

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Vous ajoutez ensuite une propriété au type de correspondance pour chaque groupe. Au moment de l’exécution, une correspondance est représentée comme une <xref:System.Text.RegularExpressions.Match> valeur ; par conséquent, le devis qui définit la propriété doit utiliser la <xref:System.Text.RegularExpressions.Match.Groups> propriété indexée pour obtenir le groupe approprié.

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

Là encore, Notez que vous ajoutez la documentation XML à la propriété fournie. Notez également qu’une propriété peut être lue si une `GetterCode` fonction est fournie et que la propriété peut être écrite si une `SetterCode` fonction est fournie, donc la propriété résultante est en lecture seule.

Vous pouvez maintenant créer une méthode d’instance qui retourne une valeur de ce `Match` type :

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

Étant donné que vous créez une méthode d’instance, `args.[0]` représente l' `RegexTyped` instance sur laquelle la méthode est appelée, et `args.[1]` est l’argument d’entrée.

Enfin, fournissez un constructeur afin que les instances du type fourni puissent être créées.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Le constructeur efface simplement la création d’une instance Regex .NET standard, qui est à nouveau boxed en objet, car `obj` est l’effacement du type fourni. Avec cette modification, l’exemple d’utilisation d’API spécifié précédemment dans la rubrique fonctionne comme prévu. Le code suivant est complet et final :

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

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Fournisseur de type qui est stocké par les données locales

Souvent, vous pouvez souhaiter que les fournisseurs de type présentent des API basées sur des paramètres statiques non seulement, mais également des informations sur des systèmes locaux ou distants. Cette section traite des fournisseurs de type basés sur les données locales, tels que les fichiers de données locaux.

### <a name="simple-csv-file-provider"></a>Fournisseur de fichiers CSV simple

En guise d’exemple simple, imaginez un fournisseur de type pour l’accès aux données scientifiques au format CSV (valeurs séparées par des virgules). Cette section part du principe que les fichiers CSV contiennent une ligne d’en-tête suivie de données à virgule flottante, comme le montre le tableau suivant :

|Distance (compteur)|Heure (seconde)|
|----------------|-------------|
|50,0|3.7|
|100.0|5.2|
|150.0|6.4|

Cette section montre comment fournir un type que vous pouvez utiliser pour obtenir des lignes avec une `Distance` propriété de type `float<meter>` et une `Time` propriété de type `float<second>` . Pour plus de simplicité, les hypothèses suivantes sont prises :

- Les noms d’en-tête sont inférieurs à l’unité ou se présentent sous la forme « nom (unité) » et ne contiennent pas de virgules.

- Les unités sont toutes des unités système (SI), car le module [FSharp. Data. UnitSystems. si. UnitNames module (F #)](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitnames.html) définit.

- Les unités sont toutes simples (par exemple, les compteurs) au lieu de composent (par exemple, compteur/seconde).

- Toutes les colonnes contiennent des données à virgule flottante.

Un fournisseur plus complet délibérera ces restrictions.

Là encore, la première étape consiste à réfléchir à l’aspect de l’API. À partir d’un `info.csv` fichier avec le contenu de la table précédente (au format séparé par des virgules), les utilisateurs du fournisseur doivent être en mesure d’écrire du code qui ressemble à l’exemple suivant :

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Dans ce cas, le compilateur doit convertir ces appels en un nom similaire à l’exemple suivant :

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

La traduction optimale exige que le fournisseur de type définisse un `CsvFile` type réel dans l’assembly du fournisseur de type. Les fournisseurs de type s’appuient souvent sur quelques types et méthodes d’assistance pour encapsuler la logique importante. Étant donné que les mesures sont effacées au moment de l’exécution, vous pouvez utiliser `float[]` comme type effacé pour une ligne. Le compilateur traitera différentes colonnes comme ayant différents types de mesures. Par exemple, la première colonne de notre exemple est de type `float<meter>` , et la seconde a `float<second>` . Toutefois, la représentation effacée peut rester assez simple.

Le code suivant illustre le cœur de l’implémentation.

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

Notez les points suivants à propos de l’implémentation :

- Les constructeurs surchargés autorisent le fichier d’origine ou celui qui a un schéma identique à lire. Ce modèle est courant lorsque vous écrivez un fournisseur de type pour des sources de données locales ou distantes, et ce modèle permet d’utiliser un fichier local comme modèle pour les données distantes.

- Vous pouvez utiliser la valeur [TypeProviderConfig](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderconfig.html) qui est passée au constructeur du fournisseur de type pour résoudre les noms de fichiers relatifs.

- Vous pouvez utiliser la `AddDefinitionLocation` méthode pour définir l’emplacement des propriétés fournies. Par conséquent, si vous utilisez `Go To Definition` sur une propriété fournie, le fichier CSV s’ouvre dans Visual Studio.

- Vous pouvez utiliser le `ProvidedMeasureBuilder` type pour rechercher les unités si et pour générer les types appropriés `float<_>` .

### <a name="key-lessons"></a>Leçons clés

Cette section a expliqué comment créer un fournisseur de type pour une source de données locale avec un schéma simple contenu dans la source de données elle-même.

## <a name="going-further"></a>Aller plus loin

Les sections suivantes incluent des suggestions pour une étude plus approfondie.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Examen du code compilé pour les types effacés

Pour vous donner une idée de la façon dont l’utilisation du fournisseur de type correspond au code émis, examinez la fonction suivante à l’aide du `HelloWorldTypeProvider` qui est utilisé précédemment dans cette rubrique.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Voici une image du code obtenu décompilé à l’aide de ildasm.exe :

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

Comme le montre l’exemple, toutes les mentions du type `Type1` et de la `InstanceProperty` propriété ont été effacées, ce qui laisse uniquement les opérations sur les types de Runtime impliqués.

### <a name="design-and-naming-conventions-for-type-providers"></a>Conventions de conception et de nommage pour les fournisseurs de type

Respectez les conventions suivantes lors de la création de fournisseurs de type.

**Fournisseurs pour les protocoles de connectivité** En général, les noms de la plupart des dll de fournisseur pour les protocoles de connectivité de données et de services, tels que OData ou les connexions SQL, doivent se terminer par `TypeProvider` ou `TypeProviders` . Par exemple, utilisez un nom de DLL qui ressemble à la chaîne suivante :

`Fabrikam.Management.BasicTypeProviders.dll`

Assurez-vous que les types fournis sont membres de l’espace de noms correspondant et indiquez le protocole de connectivité que vous avez implémenté :

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Fournisseurs d’utilitaires pour le codage général**.  Pour un fournisseur de type utilitaire comme celui des expressions régulières, le fournisseur de type peut faire partie d’une bibliothèque de base, comme le montre l’exemple suivant :

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

Dans ce cas, le type fourni apparaîtrait à un point approprié selon les conventions de conception .NET normales :

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Sources de données Singleton**. Certains fournisseurs de type se connectent à une source de données dédiée unique et fournissent uniquement des données. Dans ce cas, vous devez supprimer le `TypeProvider` suffixe et utiliser des conventions normales pour l’affectation de noms .net :

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Pour plus d’informations, consultez la `GetConnection` Convention de conception décrite plus loin dans cette rubrique.

### <a name="design-patterns-for-type-providers"></a>Modèles de conception pour les fournisseurs de type

Les sections suivantes décrivent les modèles de conception que vous pouvez utiliser lors de la création de fournisseurs de type.

#### <a name="the-getconnection-design-pattern"></a>Modèle de conception GetConnection

La plupart des fournisseurs de type doivent être écrits pour utiliser le `GetConnection` modèle utilisé par les fournisseurs de type dans FSharp.Data.TypeProviders.dll, comme le montre l’exemple suivant :

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Fournisseurs de type avec des données et services distants

Avant de créer un fournisseur de type qui est associé à des données et des services distants, vous devez tenir compte d’une série de problèmes inhérents à la programmation connectée. Ces problèmes incluent les considérations suivantes :

- mappage de schéma

- activité et invalidation en présence d’une modification de schéma

- mise en cache de schéma

- implémentations asynchrones d’opérations d’accès aux données

- prise en charge des requêtes, y compris les requêtes LINQ

- informations d’identification et authentification

Cette rubrique n’explore pas ces problèmes plus en détail.

### <a name="additional-authoring-techniques"></a>Techniques de création supplémentaires

Quand vous écrivez vos propres fournisseurs de type, vous souhaiterez peut-être utiliser les techniques supplémentaires suivantes.

### <a name="creating-types-and-members-on-demand"></a>Création de types et de membres à la demande

L’API ProvidedType a des versions retardées de AddMember.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Ces versions sont utilisées pour créer des espaces à la demande de types.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Fourniture de types de tableau et d’instanciations de types génériques

Vous faites des membres fournis (dont les signatures incluent des types tableau, des types ByRef et des instanciations de types génériques) à l’aide de la normale `MakeArrayType` , `MakePointerType` et `MakeGenericType` sur n’importe quelle instance de <xref:System.Type> , y compris `ProvidedTypeDefinitions` .

> [!NOTE]
> Dans certains cas, vous devrez peut-être utiliser le programme d’assistance dans `ProvidedTypeBuilder.MakeGenericType` .  Pour plus d’informations, consultez la [documentation du kit de développement logiciel du fournisseur de type](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) .

### <a name="providing-unit-of-measure-annotations"></a>Fournir des annotations d’unité de mesure

L’API ProvidedTypes fournit des assistances pour fournir des annotations de mesure. Par exemple, pour fournir le type `float<kg>` , utilisez le code suivant :

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Pour fournir le type `Nullable<decimal<kg/m^2>>` , utilisez le code suivant :

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Accès aux ressources de projet local ou de script local

Chaque instance d’un fournisseur de type peut recevoir une `TypeProviderConfig` valeur pendant la construction. Cette valeur contient le « dossier de résolution » pour le fournisseur (autrement dit, le dossier du projet pour la compilation ou le répertoire qui contient un script), la liste des assemblys référencés et d’autres informations.

### <a name="invalidation"></a>Invalidation

Les fournisseurs peuvent déclencher des signaux d’invalidation pour notifier le service de langage F # que les hypothèses de schéma peuvent avoir changé. Lorsque l’invalidation se produit, un typecheck est restauré si le fournisseur est hébergé dans Visual Studio. Ce signal sera ignoré lorsque le fournisseur est hébergé dans F# Interactive ou par le compilateur F # (fsc.exe).

### <a name="caching-schema-information"></a>Mise en cache des informations de schéma

Les fournisseurs doivent souvent mettre en cache l’accès aux informations de schéma. Les données mises en cache doivent être stockées à l’aide d’un nom de fichier donné en tant que paramètre statique ou en tant que données utilisateur. Un exemple de mise en cache de schéma est le `LocalSchemaFile` paramètre dans les fournisseurs de type dans l' `FSharp.Data.TypeProviders` assembly. Dans l’implémentation de ces fournisseurs, ce paramètre statique indique au fournisseur de type d’utiliser les informations de schéma dans le fichier local spécifié au lieu d’accéder à la source de données sur le réseau. Pour utiliser les informations de schéma mises en cache, vous devez également définir le paramètre static `ForceUpdate` sur `false` . Vous pouvez utiliser une technique similaire pour activer l’accès aux données en ligne et hors connexion.

### <a name="backing-assembly"></a>Assembly de stockage

Quand vous compilez un `.dll` `.exe` fichier ou, le fichier. dll de stockage des types générés est lié de manière statique à l’assembly résultant. Ce lien est créé en copiant les définitions de type de langage intermédiaire (IL) et toutes les ressources managées à partir de l’assembly de stockage dans l’assembly final. Lorsque vous utilisez F# Interactive, le fichier. dll de sauvegarde n’est pas copié et est chargé directement dans le processus de F# Interactive.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Exceptions et diagnostics des fournisseurs de type

Toutes les utilisations de tous les membres des types fournis peuvent lever des exceptions. Dans tous les cas, si un fournisseur de type lève une exception, le compilateur hôte attribut l’erreur à un fournisseur de type spécifique.

- Les exceptions de fournisseur de type ne doivent jamais entraîner des erreurs internes du compilateur.

- Les fournisseurs de type ne peuvent pas signaler d’avertissements.

- Lorsqu’un fournisseur de type est hébergé dans le compilateur F #, un environnement de développement F #, ou F# Interactive, toutes les exceptions de ce fournisseur sont interceptées. La propriété message est toujours le texte d’erreur et aucune trace de la pile ne s’affiche. Si vous envisagez de lever une exception, vous pouvez lever les exemples suivants : `System.NotSupportedException` , `System.IO.IOException` , `System.Exception` .

#### <a name="providing-generated-types"></a>Fourniture de types générés

Jusqu’à présent, ce document a expliqué comment fournir des types effacés. Vous pouvez également utiliser le mécanisme du fournisseur de type en F # pour fournir des types générés, qui sont ajoutés en tant que définitions de type .NET réelles dans le programme des utilisateurs. Vous devez faire référence aux types fournis générés à l’aide d’une définition de type.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

Le code d’assistance ProvidedTypes-0,2 qui fait partie de la version F # 3,0 n’a qu’une prise en charge limitée pour la fourniture de types générés. Les instructions suivantes doivent être vraies pour une définition de type générée :

- `isErased` doit être défini sur `false`.

- Le type généré doit être ajouté à un nouveau construit `ProvidedAssembly()` , qui représente un conteneur pour les fragments de code générés.

- Le fournisseur doit avoir un assembly qui possède un fichier. dll .NET de sauvegarde réel avec un fichier. dll correspondant sur le disque.

## <a name="rules-and-limitations"></a>Règles et limitations

Lorsque vous écrivez des fournisseurs de type, gardez à l’esprit les règles et limitations suivantes.

### <a name="provided-types-must-be-reachable"></a>Les types fournis doivent être accessibles

Tous les types fournis doivent être accessibles à partir des types non imbriqués. Les types non imbriqués sont fournis dans l’appel au `TypeProviderForNamespaces` constructeur ou à un appel à `AddNamespace` . Par exemple, si le fournisseur fournit un type `StaticClass.P : T` , vous devez vous assurer que T est un type non imbriqué ou imbriqué sous un.

Par exemple, certains fournisseurs ont une classe statique telle que `DataTypes` qui contient ces `T1, T2, T3, ...` types. Dans le cas contraire, l’erreur indique qu’une référence au type T dans l’assembly A a été trouvée, mais que le type est introuvable dans cet assembly. Si cette erreur s’affiche, vérifiez que tous vos sous-types sont accessibles à partir des types de fournisseurs. Remarque : ces `T1, T2, T3...` types sont appelés types *à la volée* . N’oubliez pas de les placer dans un espace de noms accessible ou un type parent.

### <a name="limitations-of-the-type-provider-mechanism"></a>Limitations du mécanisme du fournisseur de type

Le mécanisme du fournisseur de type en F # présente les limitations suivantes :

- L’infrastructure sous-jacente pour les fournisseurs de type en F # ne prend pas en charge les types génériques fournis ou les méthodes génériques fournies.

- Le mécanisme ne prend pas en charge les types imbriqués avec des paramètres statiques.

## <a name="development-tips"></a>Conseils de développement

Les conseils suivants peuvent être utiles pendant le processus de développement :

### <a name="run-two-instances-of-visual-studio"></a>Exécuter deux instances de Visual Studio

Vous pouvez développer le fournisseur de type dans une instance et tester le fournisseur dans l’autre, car l’IDE de test prend un verrou sur le fichier. dll qui empêche le fournisseur de type d’être régénéré. Par conséquent, vous devez fermer la deuxième instance de Visual Studio pendant que le fournisseur est créé dans la première instance, puis vous devez rouvrir la deuxième instance après la génération du fournisseur.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Déboguer des fournisseurs de type à l’aide d’appels de fsc.exe

Vous pouvez appeler des fournisseurs de type à l’aide des outils suivants :

- fsc.exe (compilateur de ligne de commande F #)

- fsi.exe (compilateur F# Interactive)

- devenv.exe (Visual Studio)

Il est souvent plus facile de déboguer les fournisseurs de type à l’aide de fsc.exe sur un fichier de script de test (par exemple, script. FSX). Vous pouvez lancer un débogueur à partir d’une invite de commandes.

```console
devenv /debugexe fsc.exe script.fsx
```

  Vous pouvez utiliser la journalisation de l’impression vers stdout.

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de type](index.md)
- [Kit de développement logiciel du fournisseur de type](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
