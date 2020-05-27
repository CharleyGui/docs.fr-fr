---
title: Héritage dans C#
description: Apprenez à utiliser l’héritage dans les bibliothèques et applications C#.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 8e24ad3e93dcd11f39ae979a3acda4c4ada13dc5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007726"
---
# <a name="inheritance-in-c-and-net"></a>Héritage dans C# et .NET

Ce didacticiel vous présente l’héritage dans C#. L’héritage est une fonctionnalité des langages de programmation orientés objet qui vous permet de définir une classe de base qui fournit des fonctionnalités spécifiques (données et comportement) et de définir des classes dérivées qui héritent ou substituent cette fonctionnalité.

## <a name="prerequisites"></a>Prérequis

Ce didacticiel part du principe que vous avez installé le kit SDK .NET Core. Visitez la page des [téléchargements .net Core](https://dotnet.microsoft.com/download) pour le télécharger. Il vous faut également un éditeur de code. Ce didacticiel utilise [Visual Studio Code](https://code.visualstudio.com), mais vous pouvez utiliser l’éditeur de code de votre choix.

## <a name="running-the-examples"></a>Exécution des exemples

Pour créer et exécuter les exemples de ce didacticiel, vous utilisez l’utilitaire [dotnet](../../core/tools/dotnet.md) en ligne de commande. Pour chaque exemple, procédez comme suit :

1. Créez un répertoire pour stocker l’exemple.
1. Entrez la commande [dotnet new console](../../core/tools/dotnet-new.md) dans l’invite de commandes pour créer un projet .NET Core.
1. Copiez et collez le code de l’exemple dans votre éditeur de code.
1. Entrez la commande [dotnet restore](../../core/tools/dotnet-restore.md) à partir de la ligne de commande pour charger ou restaurer les dépendances du projet.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Entrez la commande [dotnet run](../../core/tools/dotnet-run.md) pour compiler et exécuter l’exemple.

## <a name="background-what-is-inheritance"></a>Présentation : Qu’est-ce que l’héritage ?

*L’héritage* est un des attributs fondamentaux de la programmation orientée objet. Il vous permet de définir une classe enfant qui réutilise (hérite), étend ou modifie le comportement d’une classe parente. La classe dont les membres sont hérités s’appelle la *classe de base*. La classe qui hérite des membres de la classe de base est appelée la *classe dérivée*.

C# et .NET prennent uniquement en charge *l’héritage simple*. C’est-à-dire qu’une classe ne peut hériter que d'une seule classe. Toutefois, l’héritage est transitif, ce qui permet de définir une hiérarchie d’héritage pour un ensemble de types. En d’autres termes, le type `D` peut hériter du type `C`, qui hérite du type `B`, qui hérite du type de classe de base `A`. Étant donné que l’héritage est transitif, les membres de type `A` sont disponibles pour le type `D`.

Tous les membres d’une classe de base ne sont pas hérités par les classes dérivées. Les membres suivants ne sont pas hérités :

- Les [constructeurs statiques](../programming-guide/classes-and-structs/static-constructors.md), qui initialisent les données statiques d’une classe.

- Les [Constructeurs d’instance](../programming-guide/classes-and-structs/constructors.md), que vous appelez pour créer une nouvelle instance de la classe. Chaque classe doit définir ses propres constructeurs.

- Les [finaliseurs](../programming-guide/classes-and-structs/destructors.md), qui sont appelés par le récupérateur de mémoire du runtime pour détruire les instances d’une classe.

Bien que tous les autres membres de classe de base sont hérités par les classes dérivées, leur visibilité dépend de leur accessibilité. L’accessibilité d’un membre affecte sa visibilité pour les classes dérivées de la manière suivante :

- Les membres [Privés](../language-reference/keywords/private.md) sont visibles uniquement dans les classes dérivées qui sont imbriquées dans leur classe de base. Sinon, ils ne sont pas visibles dans les classes dérivées. Dans l’exemple suivant, `A.B` est une classe imbriquée qui dérive de `A`, et `C` dérive de `A`. Le champ privé `A.value` est visible dans A.B. Toutefois, si vous supprimez les commentaires de la méthode `C.GetValue` et essayez de compiler l’exemple, il génère l’erreur de compilateur CS0122 : « 'A.value est inaccessible en raison de son niveau de protection ».

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- Les membres [protégés](../language-reference/keywords/protected.md) sont visibles uniquement dans les classes dérivées.

- Les membres [internes](../language-reference/keywords/internal.md) sont visibles uniquement dans les classes dérivées qui sont trouvent dans le même assembly que la classe de base. Ils ne sont pas visibles dans les classes dérivées situées dans un autre assembly à partir de la classe de base.

- Les membres [publics](../language-reference/keywords/public.md) sont visibles dans les classes dérivées et font partie de l’interface publique de la classe dérivée. Les membres publics hérités peuvent être appelés comme s’ils étaient définis dans la classe dérivée. Dans l’exemple suivant, la classe `A` définit une méthode nommée `Method1`, et la classe `B` hérite de la classe `A`. L’exemple appelle ensuite `Method1` comme s’il s’agissait d’une méthode d’instance sur `B`.

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Les classes dérivées peuvent également *substituer* les membres hérités en fournissant une implémentation alternative. Pour être en mesure de substituer un membre, le membre de la classe de base doit être marqué avec le mot-clé [virtual](../language-reference/keywords/virtual.md). Par défaut, les membres de classe de base ne sont pas marqués comme `virtual` et ne peut pas être substitués. Une tentative de substituer un membre non virtuel, comme dans l’exemple suivant, génère l’erreur de compilateur CS0506 : « \<member> : impossible de substituer le membre hérité \<member>, car il n’est pas marqué comme virtual, abstract ou override.

```csharp
public class A
{
    public void Method1()
    {
        // Do something.
    }
}

public class B : A
{
    public override void Method1() // Generates CS0506.
    {
        // Do something else.
    }
}
```

Dans certains cas, une classe dérivée *doit* remplacer l’implémentation de la classe de base. Les membres de classe de base marqués avec le mot-clé [abstract](../language-reference/keywords/abstract.md) requièrent que les classes dérivées les remplacent. Compiler l’exemple suivant génère l’erreur de compilateur CS0534, « &lt;class&gt; does not implement inherited abstract member &lt;member&gt; », car la classe `B` ne fournit aucune implémentation de `A.Method1`.

```csharp
public abstract class A
{
    public abstract void Method1();
}

public class B : A // Generates CS0534.
{
    public void Method3()
    {
        // Do something.
    }
}
```

L’héritage s’applique uniquement aux classes et interfaces. Les autres catégories de type (structures, délégués et énumérations) ne permettent pas l’héritage. En raison de ces règles, la tentative de compilation de code comme l’exemple suivant génère l’erreur de compilateur CS0527 : « Le type 'ValueType' dans la liste des interfaces n’est pas une interface ». Le message d’erreur indique que, même si vous pouvez définir les interfaces qu’implémente un struct, l’héritage n'est pas pris en charge.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Héritage implicite

Outre les types qui peuvent hériter via l’héritage simple, tous les types dans le système de types de .NET héritent implicitement de <xref:System.Object> ou d’un type dérivé. Les fonctionnalités communes de <xref:System.Object> sont disponibles pour n’importe quel type.

Pour comprendre ce que l’héritage implicite signifie, nous allons définir une nouvelle classe, `SimpleClass`, qui est simplement une définition de classe vide :

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Vous pouvez ensuite utiliser la réflexion (qui permet d’inspecter les métadonnées d’un type pour obtenir des informations sur ce type) pour obtenir la liste des membres qui appartiennent au type `SimpleClass`. Même si vous n’avez pas défini de membres dans votre classe `SimpleClass`, la sortie de l’exemple indique qu’il a en fait neuf membres. Un de ces membres est un constructeur sans paramètre (ou par défaut) qui est fourni automatiquement pour le type `SimpleClass` par le compilateur C#. Les huit restants sont membres de <xref:System.Object>, le type à partir duquel toutes les classes et interfaces du système de type .NET héritent implicitement.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

L’héritage implicite à partir de la classe <xref:System.Object> rend ces méthodes disponibles pour la classe `SimpleClass` :

- La méthode public `ToString`, qui convertit un objet `SimpleClass` en sa représentation de chaîne, retourne le nom de type complet. Dans ce cas, la méthode `ToString` retourne la chaîne « SimpleClass ».

- Voici trois méthodes de test d’égalité de deux objets : la méthode public instance `Equals(Object)`, la méthode public static `Equals(Object, Object)` et la méthode public static `ReferenceEquals(Object, Object)`. Par défaut, ces méthodes testent l’égalité des références. Autrement dit, pour être égales, deux variables d’objet doivent faire référence au même objet.

- La méthode public `GetHashCode`, qui calcule une valeur qui permet à une instance du type d’être utilisée dans des collections hachées.

- La méthode `GetType` publique qui retourne un objet <xref:System.Type> qui représente le type `SimpleClass`.

- La méthode protected <xref:System.Object.Finalize%2A>, qui est conçue pour libérer les ressources non gérées avant que la mémoire d’un objet soit récupérée par le récupérateur de mémoire.

- La méthode protected <xref:System.Object.MemberwiseClone%2A>, qui crée un clone partiel de l’objet actuel.

En raison de l’héritage implicite, vous pouvez appeler n’importe quel membre hérité d’un objet `SimpleClass` exactement comme s’il était en fait un membre défini dans la classe `SimpleClass`. Par exemple, l’exemple suivant appelle la méthode `SimpleClass.ToString`, dont `SimpleClass` hérite de <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Le tableau suivant répertorie les catégories de types que vous pouvez créer en C# et les types à partir desquels ils héritent implicitement. Chaque type de base apporte un autre ensemble de membres disponibles via l’héritage aux types dérivés implicitement.

| Catégorie de type | Hérite implicitement de                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| class         | <xref:System.Object>                                                          |
| struct        | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| délégué      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>L’héritage et une relation « est un »

En règle générale, l’héritage est utilisé pour exprimer une relation « est un » entre une classe de base et une ou plusieurs classes dérivées, où les classes dérivées sont des versions spécialisées de la classe de base ; la classe dérivée est un type de la classe de base. Par exemple, la classe `Publication` représente une publication de tout type et les classes `Book` et `Magazine` représentent les classes des types spécifiques de publications.

> [!NOTE]
> Les classes et structures peuvent implémenter une ou plusieurs interfaces. Bien que l’implémentation d’interface est souvent présentée comme une solution de contournement pour l’héritage unique ou comme une façon d’utiliser l’héritage avec les structures, elle est conçue pour exprimer une autre relation (« peut faire ») entre une interface et son type d’implémentation que l’héritage. Une interface définit un sous-ensemble de fonctionnalités (comme la capacité à tester l’égalité, comparer ou trier des objets, ou pour prendre en charge la mise en forme et l’analyse dépendant de la culture) que l’interface met à disposition pour ses types d’implémentation.

Notez que « est un » exprime également la relation entre un type et une instanciation spécifique de ce type. Dans l’exemple suivant, `Automobile` est une classe qui possède trois propriétés en lecture seule uniques : `Make`, le fabricant de l’automobile ; `Model`, le type de voiture et `Year`, son année de fabrication. Votre classe `Automobile` comporte également un constructeur dont les arguments sont assignés aux valeurs de propriété, et elle remplace la méthode <xref:System.Object.ToString%2A?displayProperty=nameWithType> pour générer une chaîne qui identifie de façon unique l’instance `Automobile` plutôt que la classe `Automobile`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

Dans ce cas, vous ne devriez pas vous reposer sur l’héritage pour représenter les modèles et constructeurs spécifiques. Par exemple, il est inutile de définir un type `Packard` pour représenter les véhicules automobiles fabriqués par la société Packard Motor Car. Au lieu de cela, vous pouvez les représenter en créant un objet `Automobile` avec les valeurs appropriées passées à son constructeur de classe, comme dans l’exemple suivant.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Une relation « est un » basée sur l’héritage est préférablement appliquée à une classe de base et aux classes dérivées qui ajoutent des membres supplémentaires à la classe de base ou qui nécessitent des fonctionnalités supplémentaires non présentes dans la classe de base.

## <a name="designing-the-base-class-and-derived-classes"></a>Conception de la classe de base et des classes dérivées

Examinons le processus de conception d’une classe de base et de ses classes dérivées. Dans cette section, vous allez définir une classe de base, `Publication` , qui représente une publication de tout type, comme un livre, un magazine, un journal, un journal, un article, etc. Vous définirez également une `Book` classe qui dérive de `Publication` . Vous pourriez facilement étendre l’exemple pour définir d’autres classes dérivées, comme `Magazine`, `Journal`, `Newspaper` et `Article`.

### <a name="the-base-publication-class"></a>Classe Publication de base

Lors de la conception de votre classe `Publication`, vous devez prendre plusieurs décisions de conception :

- Les membres à inclure dans votre classe de base `Publication` et si les membres `Publication` fournissent des implémentations de méthode, ou si `Publication` est une classe de base abstraite qui sert de modèle pour ses classes dérivées.

  Dans ce cas, la classe `Publication` fournit des implémentations de méthode. La section [Conception de classes de base abstraites et leurs classes dérivées](#abstract) contient un exemple qui utilise une classe de base abstraite pour définir les méthodes que les classes dérivées doivent substituer. Les classes dérivées sont libres de fournir une implémentation qui convient pour le type dérivé.

  La possibilité de réutiliser le code (autrement dit, plusieurs classes dérivées partagent la déclaration et l’implémentation de méthodes de classe de base et n’ont pas besoin de les substituer) constitue un avantage des classes de base non abstraites. Par conséquent, vous devez ajouter des membres à `Publication` si leur code est susceptible d’être partagé par certains ou la majorité des types `Publication` spécialisés. Si vous ne fournissez pas efficacement les implémentations de classe de base, vous devrez fournir des implémentations de membres en grande partie identiques dans les classes dérivées au lieu d’une implémentation unique dans la classe de base. La nécessité de maintenir le code dupliqué à plusieurs emplacements est une source potentielle de bogues.

  Pour optimiser la réutilisation du code et créer une hiérarchie d’héritage logique et intuitive, vous voulez vous assurer d’ajouter à la classe `Publication` uniquement les données et fonctionnalités communes à toutes les publications ou la plupart d’entre elles. Les classes dérivées implémentent ensuite les membres qui sont uniques pour les types particuliers de publications qu’ils représentent.

- La mesure dans laquelle étendre votre hiérarchie de classes. Souhaitez-vous développer une hiérarchie de trois classes ou plus, plutôt que simplement une classe de base et une ou plusieurs classes dérivées ? Par exemple, `Publication` peut être une classe de base de `Periodical`, qui est elle-même une classe de base de `Magazine`, `Journal` et `Newspaper`.

  Dans votre exemple, vous allez utiliser la hiérarchie simple d’une classe `Publication` et d’une classe dérivée unique, `Book`. Vous pouvez facilement étendre l’exemple pour créer un certain nombre de classes supplémentaires qui dérivent de `Publication` , telles que `Magazine` et `Article` .

- S’il est judicieux d’instancier la classe de base. Si ce n’est pas le cas, vous devez appliquer le mot-clé [abstract](../language-reference/keywords/abstract.md) à la classe. Dans le cas contraire, votre classe `Publication` peut être instanciée en appelant son constructeur de classe. Si une tentative est faite pour instancier une classe marquée avec le mot-clé `abstract` par un appel direct à son constructeur de classe, le compilateur C# génère l’erreur CS0144, « Impossible de créer une instance de la classe ou interface abstraite ». Si une tentative est faite pour instancier la classe à l’aide de la réflexion, la méthode de la réflexion lève une exception <xref:System.MemberAccessException>.

  Par défaut, une classe de base peut être instanciée en appelant son constructeur de classe. Vous n’avez pas à définir explicitement un constructeur de classe. S’il n’y en a aucun présent dans le code source de la classe de base, le compilateur C# fournit automatiquement un constructeur par défaut (sans paramètre).

  Dans votre exemple, vous marquez la classe `Publication` comme [abstract](../language-reference/keywords/abstract.md) afin qu’elle ne puisse pas être instanciée.  Une classe `abstract` sans méthode `abstract` indique que cette classe représente un concept abstrait qui est partagé entre plusieurs classes concrètes (comme `Book`, `Journal`).

- Si les classes dérivées doivent hériter de l’implémentation de classe de base de membres particuliers, si elles ont l’option de substituer l’implémentation de la classe de base ou si elles doivent fournir une implémentation. Vous utilisez le mot clé [abstract](../language-reference/keywords/abstract.md) pour forcer les classes dérivées à fournir une implémentation. Vous devez utiliser le mot clé [virtual](../language-reference/keywords/virtual.md) pour permettre aux classes dérivées de substituer une méthode de classe de base. Par défaut, les méthodes définies dans la classe de base ne sont *pas* substituables.

  La classe `Publication` n’a aucune méthode `abstract`, mais la classe elle-même est `abstract`.

- Si une classe dérivée représente la classe finale dans la hiérarchie d’héritage et ne peut pas elle-même être utilisée comme classe de base pour les classes dérivées supplémentaires. Par défaut, toute classe peut servir de classe de base. Vous pouvez appliquer le mot clé [sealed](../language-reference/keywords/sealed.md) pour indiquer qu’une classe ne peut pas servir de classe de base pour des classes supplémentaires. La tentative de dériver à partir d’une classe sealed a généré l’erreur de compilateur CS0509, « impossible de dériver à partir du type sealed \<typeName> ».

  Dans votre exemple, vous allez marquer votre classe dérivée en tant que `sealed`.

L’exemple suivant montre le code source pour la classe `Publication` ainsi qu’une énumération `PublicationType` retournée par la propriété `Publication.PublicationType`. Outre les membres qu’elle hérite de <xref:System.Object>, la classe `Publication` définit les membres uniques et substitutions de membres suivants :

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Un constructeur

  Étant donné que la classe `Publication` est `abstract`, elle ne peut pas être instanciée directement à partir du code comme dans l’exemple suivant :

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Toutefois, son constructeur d’instance peut être appelé directement à partir des constructeurs de classes dérivées, comme le code source pour la classe `Book` le montre.

- Deux propriétés liées à la publication

  `Title` est une propriété <xref:System.String> en lecture seule dont la valeur est fournie en appelant le constructeur `Publication`.

  `Pages` est une propriété <xref:System.Int32> en lecture seule qui indique le nombre total de pages de la publication. La valeur est stockée dans un champ privé nommé `totalPages`. Elle doit être positive, sans quoi une exception <xref:System.ArgumentOutOfRangeException> est levée.

- Membres liés à l’éditeur

  Deux propriétés en lecture seule, `Publisher` et `Type`. Les valeurs sont à l’origine fournies par l’appel au constructeur de la classe `Publication`.

- Membres liés à la publication

  Deux méthodes, `Publish` et `GetPublicationDate` définissent et retournent la date de publication. La méthode `Publish` définit l’indicateur privé `published` sur `true` lorsqu’elle est appelée et affecte la date passée comme argument au champ privé `datePublished`. La méthode `GetPublicationDate` retourne la chaîne « NYP » si l’indicateur `published` est `false`, et la valeur du champ `datePublished` si l’indicateur est `true`.

- Membres liés aux droits d’auteur

  La méthode `Copyright` prend comme arguments le nom du titulaire des droits d’auteur et l’année des droits d’auteur et les attribue aux propriétés `CopyrightName` et `CopyrightDate`.

- Une substitution de la méthode `ToString`

  Si un type ne remplace pas la méthode <xref:System.Object.ToString%2A?displayProperty=nameWithType>, il retourne le nom qualifié complet du type, ce qui n’aide pas vraiment à faire la différence entre une instance et une autre. La classe `Publication` substitue <xref:System.Object.ToString%2A?displayProperty=nameWithType> pour retourner la valeur de la propriété `Title`.

Le schéma suivant illustre la relation entre votre classe `Publication` de base et sa classe <xref:System.Object> implicitement héritée.

![Les classes Object et Publication](media/publication-class.jpg)

### <a name="the-book-class"></a>La classe `Book`

La classe `Book` représente un livre sous la forme d’un type spécialisé de publication. L’exemple suivant montre le code source pour la classe `Book`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Outre les membres qu’elle hérite de `Publication`, la classe `Book` définit les membres uniques et substitutions de membres suivants :

- Deux constructeurs

  Les deux constructeurs `Book` partagent trois paramètres communs. Deux d’entre eux, *title* et *publisher*, correspondent aux paramètres du constructeur `Publication`. Le troisième est *author*, qui est stocké dans une propriété `Author` non modifiable publique. Un constructeur inclut un paramètre *isbn*, qui est stocké dans l’auto-propriété `ISBN`.

  Le premier constructeur utilise le mot-clé [this](../language-reference/keywords/this.md) pour appeler l’autre constructeur. Le chaînage de constructeurs est un modèle courant pour la définition de constructeurs. Les constructeurs avec le moins de paramètres fournissent les valeurs par défaut au moment de l’appel du constructeur avec le plus grand nombre de paramètres.

  Le deuxième constructeur utilise le mot-clé [base](../language-reference/keywords/base.md) pour transmettre le titre et le nom de l’éditeur au constructeur de classe de base. Si vous n’effectuez pas un appel explicite à un constructeur de classe de base dans votre code source, le compilateur C# fournit automatiquement un appel au constructeur par défaut ou sans paramètres de la classe de base.

- Une propriété `ISBN` en lecture seule qui retourne le numéro ISBN de l’objet `Book`, un numéro unique à 10 ou 13 chiffres. Le numéro ISBN est fourni en tant qu’argument à un des constructeurs `Book`. Le numéro ISBN est stocké dans un champ de stockage privé qui est généré automatiquement par le compilateur.

- Une propriété `Author` en lecture seule. Le nom de l’auteur est fourni en tant qu’argument aux deux constructeurs `Book` et est stocké dans la propriété.

- Deux propriétés en lecture seule relatives au prix, `Price` et `Currency`. Leurs valeurs sont fournies comme arguments dans un appel de méthode `SetPrice`. La propriété `Currency` est le symbole de devise ISO à trois caractères (par exemple, USD pour le dollar américain). Les symboles de devise ISO peuvent être récupérés à partir de la propriété <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A>. Ces deux propriétés sont en lecture seule en externe, mais peuvent être définies par du code dans la classe `Book`.

- Une méthode `SetPrice` qui définit les valeurs des propriétés `Price` et `Currency`. Ces valeurs sont retournées par ces mêmes propriétés.

- Se substitue à la méthode `ToString` (héritée de `Publication`) et aux méthodes <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> et <xref:System.Object.GetHashCode%2A> (héritées de <xref:System.Object>).

  Sauf si elle est substituée, la méthode <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> teste l’égalité des références. Autrement dit, deux variables d’objet sont considérées comme égales si elles font référence au même objet. Dans la classe `Book`, en revanche, deux objets `Book` doivent être égaux s’ils ont le même ISBN.

  Lorsque vous substituez la méthode <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>, vous devez également substituer la méthode <xref:System.Object.GetHashCode%2A> qui retourne une valeur que le runtime utilise pour stocker les éléments dans les collections hachées pour une récupération efficace. Le code de hachage doit retourner une valeur qui est cohérente avec le test d’égalité. Étant donné que vous avez substitué <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> pour retourner `true` si les propriétés ISBN de deux objets `Book` sont égales, vous retournez le code de hachage calculé en appelant la méthode <xref:System.String.GetHashCode%2A> de la chaîne retournée par la propriété `ISBN`.

Le schéma suivant illustre la relation entre la base la classe `Book` et `Publication`, sa classe de base.

![Les classes Publication et Book](media/book-class.jpg)

Vous pouvez maintenant instancier un objet `Book`, appeler ses membres uniques et hérités le passer en tant qu’argument pour une méthode qui attend un paramètre de type `Publication` ou de type `Book`, comme illustré dans l’exemple suivant.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Conception de classes de base abstraites et de leurs classes dérivées
<a name="abstract"></a>

Dans l’exemple précédent, vous avez défini une classe de base qui a fourni une implémentation d’un certain nombre de méthodes pour permettre aux classes dérivées de partager du code. Dans de nombreux cas, toutefois, la classe de base n'est pas censée fournir une implémentation. Au lieu de cela, la classe de base est une *classe abstraite* qui déclare des *méthodes abstraites* ; elle sert de modèle qui définit les membres que chaque classe dérivée doit implémenter. En général, dans une classe de base abstraite, l’implémentation de chaque type dérivé est unique pour ce type. Vous avez marqué la classe avec le mot clé abstract, car il n’était pas judicieux d’instancier un objet `Publication`, même si la classe fournissait des implémentations de fonctionnalités communes aux publications.

Par exemple, chaque forme géométrique bidimensionnelle fermée inclut deux propriétés : l’aire, l’étendue interne de la forme, et le périmètre, ou la distance le long des bords de la forme. La façon de laquelle ces propriétés sont calculées, cependant, dépend entièrement de la forme spécifique. La formule pour calculer le périmètre (ou la circonférence) d’un cercle, par exemple, est différente de celle d’un triangle. La classe `Shape` est une classe `abstract` avec des méthodes `abstract`. Ceci indique que les classes dérivées partagent les mêmes fonctionnalités, mais ces classes dérivées implémentent ces fonctionnalités différemment.

L’exemple suivant définit une classe de base abstraite nommée `Shape` qui définit deux propriétés : `Area` et `Perimeter`. En plus de marquer la classe avec le mot clé [abstract](../language-reference/keywords/abstract.md), chaque membre de l’instance est également marqué avec le mot clé [abstract](../language-reference/keywords/abstract.md). Dans ce cas, `Shape` substitue également la méthode <xref:System.Object.ToString%2A?displayProperty=nameWithType> pour renvoyer le nom du type, plutôt que son nom qualifié complet. Elle définit aussi deux membres statiques, `GetArea` et `GetPerimeter`, qui permettent aux appelants de récupérer facilement l’aire et le périmètre d’une instance de toute classe dérivée. Lorsque vous passez une instance d’une classe dérivée à l’une de ces méthodes, le runtime appelle la substitution de la méthode de la classe dérivée.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Vous pouvez ensuite dériver des classes qui représentent des formes spécifiques à partir de `Shape`. L’exemple suivant définit trois classes : `Triangle`, `Rectangle` et `Circle`. Chaque forme utilise une formule unique pour calculer l’aire et périmètre. Certaines des classes dérivées définissent également des propriétés, telles que `Rectangle.Diagonal` et `Circle.Diameter`, qui sont propres à la forme qu’ils représentent.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

L'exemple suivant utilise les objets dérivés de `Shape`. Elle instancie un tableau d’objets dérivés de `Shape` et appelle les méthodes statiques de la classe `Shape` qui encapsule les valeurs de propriété de retour de `Shape`. Le runtime récupère les valeurs de propriétés substituées des types dérivés. L’exemple convertit également chaque objet `Shape` dans le tableau en son type dérivé et, si la conversion réussit, récupère les propriétés de cette sous-classe particulière de `Shape`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Voir aussi

- [Classes et objets](../tour-of-csharp/classes-and-objects.md)
- [Héritage (Guide de programmation C#)](../programming-guide/classes-and-structs/inheritance.md)
