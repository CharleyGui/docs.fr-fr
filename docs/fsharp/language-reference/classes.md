---
title: Classes
description: 'Découvrez comment les classes F # sont des types qui représentent des objets qui peuvent avoir des propriétés, des méthodes et des événements.'
ms.date: 05/16/2016
ms.openlocfilehash: fd6638e0f1c08cf667a73582e19b2bb5bba46e20
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970165"
---
# <a name="classes"></a>Classes

Les *classes* sont des types qui représentent des objets qui peuvent avoir des propriétés, des méthodes et des événements.

## <a name="syntax"></a>Syntaxe

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a>Notes

Les classes représentent la Description fondamentale des types d’objets .NET ; la classe est le concept de type principal qui prend en charge la programmation orientée objet en F #.

Dans la syntaxe précédente, `type-name` est un identificateur valide. Le `type-params` décrit des paramètres de type générique facultatifs. Il se compose de noms de paramètre de type et de contraintes placés entre crochets pointus ( `<` et `>` ). Pour plus d’informations, consultez [génériques](./generics/index.md) et [contraintes](./generics/constraints.md). `parameter-list`Décrit les paramètres du constructeur. Le premier modificateur d’accès concerne le type ; le deuxième appartient au constructeur principal. Dans les deux cas, la valeur par défaut est `public` .

Vous spécifiez la classe de base pour une classe à l’aide du `inherit` mot clé. Vous devez fournir des arguments entre parenthèses pour le constructeur de classe de base.

Vous déclarez des champs ou des valeurs de fonction qui sont locaux à la classe en utilisant des `let` liaisons, et vous devez suivre les règles générales pour les `let` liaisons. La `do-bindings` section comprend le code à exécuter lors de la construction de l’objet.

Le `member-list` se compose de constructeurs supplémentaires, de déclarations de méthode statiques et d’instance, de déclarations d’interface, de liaisons abstraites et de déclarations de propriété et d’événement. Celles-ci sont décrites dans [membres](./members/index.md).

Le `identifier` utilisé avec le `as` mot clé facultatif donne un nom à la variable d’instance, ou à un auto-identificateur, qui peut être utilisé dans la définition de type pour faire référence à l’instance du type. Pour plus d’informations, consultez la section auto Identifiers plus loin dans cette rubrique.

Les mots clés `class` et `end` qui marquent le début et la fin de la définition sont facultatifs.

Les types mutuellement récursifs, qui sont des types qui se référencent mutuellement, sont joints au `and` mot clé, tout comme les fonctions mutuellement récursives. Pour obtenir un exemple, consultez la section types mutuellement récursifs.

## <a name="constructors"></a>Constructeurs

Le constructeur est du code qui crée une instance du type de classe. Les constructeurs pour les classes fonctionnent un peu différemment en F # et dans d’autres langages .NET. Dans une classe F #, il y a toujours un constructeur principal dont les arguments sont décrits dans le `parameter-list` qui suit le nom de type, et dont le corps se compose des `let` liaisons (et `let rec` ) au début de la déclaration de classe et des `do` liaisons qui suivent. Les arguments du constructeur principal sont dans la portée tout au long de la déclaration de classe.

Vous pouvez ajouter des constructeurs supplémentaires en utilisant le `new` mot clé pour ajouter un membre, comme suit :

`new`(`argument-list`) = `constructor-body`

Le corps du nouveau constructeur doit appeler le constructeur principal qui est spécifié en haut de la déclaration de classe.

L’exemple suivant illustre ce concept. Dans le code suivant, `MyClass` a deux constructeurs, un constructeur principal qui prend deux arguments et un autre constructeur qui ne prend pas d’arguments.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>Liaisons Let et do

Les `let` `do` liaisons et dans une définition de classe forment le corps du constructeur de classe primaire, et par conséquent, elles s’exécutent chaque fois qu’une instance de classe est créée. Si une `let` liaison est une fonction, elle est compilée dans un membre. Si la `let` liaison est une valeur qui n’est pas utilisée dans une fonction ou un membre, elle est compilée dans une variable locale pour le constructeur. Dans le cas contraire, elle est compilée dans un champ de la classe. Les `do` expressions qui suivent sont compilées dans le constructeur principal et exécutent le code d’initialisation pour chaque instance. Étant donné que tous les constructeurs supplémentaires appellent toujours le constructeur principal, les `let` liaisons et les `do` liaisons s’exécutent toujours quel que soit le constructeur appelé.

Les champs créés par des `let` liaisons sont accessibles dans l’ensemble des méthodes et des propriétés de la classe ; Toutefois, ils ne sont pas accessibles à partir de méthodes statiques, même si les méthodes statiques prennent une variable d’instance comme paramètre. Ils ne sont pas accessibles à l’aide de l’auto-identificateur, s’il en existe un.

## <a name="self-identifiers"></a>Identificateurs automatiques

Un *auto-identificateur* est un nom qui représente l’instance actuelle. Les auto-identificateurs ressemblent au `this` mot clé en C# ou C++ ou `Me` dans Visual Basic. Vous pouvez définir un auto-identificateur de deux manières différentes, selon que vous souhaitez que l’auto-identificateur soit dans la portée de la définition de classe entière ou uniquement pour une méthode individuelle.

Pour définir un auto-identificateur pour l’ensemble de la classe, utilisez le `as` mot clé après les parenthèses fermantes de la liste de paramètres du constructeur et spécifiez le nom de l’identificateur.

Pour définir un auto-identificateur pour une seule méthode, fournissez l’auto-identificateur dans la déclaration de membre, juste avant le nom de la méthode et un point (.) comme séparateur.

L’exemple de code suivant illustre les deux façons de créer un auto-identificateur. Dans la première ligne, le `as` mot clé est utilisé pour définir l’auto-identificateur. Dans la cinquième ligne, l’identificateur `this` est utilisé pour définir un auto-identificateur dont la portée est limitée à la méthode `PrintMessage` .

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Contrairement à d’autres langages .NET, vous pouvez nommer l’auto-identificateur comme vous le souhaitez. vous n’êtes pas limité à des noms tels que `self` , `Me` ou `this` .

L’auto-identificateur qui est déclaré avec le `as` mot clé n’est pas initialisé avant le constructeur de base. Par conséquent, lorsqu’il est utilisé avant ou à l’intérieur du constructeur de base, `System.InvalidOperationException: The initialization of an object or value resulted in an object or value being accessed recursively before it was fully initialized.` est déclenché pendant l’exécution. Vous pouvez utiliser l’auto-identificateur librement après le constructeur de base, par exemple dans les `let` liaisons ou `do` liaisons.

## <a name="generic-type-parameters"></a>Paramètres de type générique

Les paramètres de type générique sont spécifiés entre crochets pointus ( `<` et `>` ), sous la forme d’un guillemet simple suivi d’un identificateur. Plusieurs paramètres de type générique sont séparés par des virgules. Le paramètre de type générique est dans la portée tout au long de la déclaration. L’exemple de code suivant montre comment spécifier des paramètres de type générique.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Les arguments de type sont déduits lorsque le type est utilisé. Dans le code suivant, le type inféré est une séquence de tuples.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Spécification de l’héritage

La `inherit` clause identifie la classe de base directe, le cas échéant. En F #, une seule classe de base directe est autorisée. Les interfaces qu’une classe implémente ne sont pas considérées comme des classes de base. Les interfaces sont présentées dans la rubrique [interfaces](Interfaces.md) .

Vous pouvez accéder aux méthodes et aux propriétés de la classe de base à partir de la classe dérivée en utilisant le mot clé Language `base` comme identificateur, suivi d’un point (.) et du nom du membre.

Pour plus d’informations, consultez [Héritage](inheritance.md).

## <a name="members-section"></a>Section membres

Vous pouvez définir des méthodes statiques ou d’instance, des propriétés, des implémentations d’interface, des membres abstraits, des déclarations d’événements et des constructeurs supplémentaires dans cette section. Les liaisons Let et do ne peuvent pas apparaître dans cette section. Étant donné que les membres peuvent être ajoutés à divers types F # en plus des classes, ils sont décrits dans une rubrique distincte, [membres](./members/index.md).

## <a name="mutually-recursive-types"></a>Types mutuellement récursifs

Quand vous définissez des types qui font référence les uns aux autres de manière circulaire, vous associez les définitions de type à l’aide du `and` mot clé. Le `and` mot clé remplace le `type` mot clé sur tous les autres définitions, à l’exception de la première définition, comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

La sortie est une liste de tous les fichiers dans le répertoire actif.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Quand utiliser des classes, des unions, des enregistrements et des structures

Étant donné la variété des types à choisir, vous devez avoir une bonne compréhension de ce à quoi chaque type est conçu pour sélectionner le type approprié pour une situation particulière. Les classes sont conçues pour une utilisation dans des contextes de programmation orientés objet. La programmation orientée objet est le paradigme dominant utilisé dans les applications écrites pour le .NET Framework. Si votre code F # doit fonctionner étroitement avec la .NET Framework ou une autre bibliothèque orientée objet, et en particulier si vous devez étendre à partir d’un système de type orienté objet tel qu’une bibliothèque d’interface utilisateur, les classes sont probablement appropriées.

Si vous n’interopèrez pas étroitement avec le code orienté objet, ou si vous écrivez du code autonome qui, par conséquent, est protégé contre les interactions fréquentes avec le code orienté objet, vous devez envisager d’utiliser des enregistrements et des unions discriminées. Une union discriminée unique et bien pensée, associée au code de correspondance de modèle approprié, peut souvent être utilisée comme une alternative plus simple à une hiérarchie d’objets. Pour plus d’informations sur les unions discriminées, consultez [unions discriminées](discriminated-unions.md).

Les enregistrements présentent l’avantage d’être plus simples que les classes, mais les enregistrements ne sont pas appropriés lorsque les demandes d’un type dépassent ce qui peut être accompli avec leur simplicité. Les enregistrements sont fondamentalement des agrégats simples de valeurs, sans constructeurs distincts qui peuvent exécuter des actions personnalisées, sans champs masqués, et sans implémentations d’héritage ou d’interface. Bien que les membres tels que les propriétés et les méthodes puissent être ajoutés aux enregistrements pour rendre leur comportement plus complexe, les champs stockés dans un enregistrement sont toujours un simple agrégat de valeurs. Pour plus d’informations sur les enregistrements, consultez [enregistrements](records.md).

Les structures sont également utiles pour les petits agrégats de données, mais elles diffèrent des classes et des enregistrements dans le cas où il s’agit de types valeur .NET. Les classes et les enregistrements sont des types référence .NET. La sémantique des types valeur et des types référence est différente dans le fait que les types valeur sont passés par valeur. Cela signifie qu’ils sont copiés bit par bit lorsqu’ils sont passés en tant que paramètres ou retournés par une fonction. Ils sont également stockés sur la pile ou, s’ils sont utilisés en tant que champ, incorporés à l’intérieur de l’objet parent au lieu d’être stockés dans leur propre emplacement distinct sur le tas. Par conséquent, les structures sont appropriées pour les données fréquemment sollicitées lorsque la surcharge liée à l’accès au segment de mémoire est un problème. Pour plus d’informations sur les structures, consultez [structures](structures.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Members](./members/index.md) (Membres)
- [Héritage](inheritance.md)
- [Interfaces](interfaces.md)
