---
title: Spécification des noms de types qualifiés complets
description: Pour une entrée valide pour les opérations de réflexion, utilisez des noms de types qualifiés complets, qui ont des spécifications de nom d’assembly, des spécifications d’espace de noms et des noms de types.
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
ms.openlocfilehash: ff33b6abd31a82c6b80aa794564c5c48648cde63
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865227"
---
# <a name="specifying-fully-qualified-type-names"></a>Spécification des noms de types complets

Vous devez spécifier des noms de types pour pouvoir valider l’entrée servant aux diverses opérations de réflexion. Un nom de type complet se compose d’une spécification de nom d’assembly, d’une spécification d’espace de noms et d’un nom de type. Les spécifications de noms de types sont utilisées par les méthodes telles que <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> et <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.

## <a name="grammar-for-type-names"></a>Grammaire pour les noms de types

 La grammaire définit la syntaxe des langages formels. Le tableau suivant décrit les règles lexicales permettant de reconnaître une entrée valide. Les éléments terminaux (qui ne peuvent pas être réduits davantage) sont affichés en majuscules. Les éléments non terminaux (qui peuvent être réduits davantage) sont affichés dans une casse mixte ou entre des guillemets simples ; toutefois, le guillemet simple (') ne fait pas partie de la syntaxe proprement dite. La barre verticale (&#124;) signale des règles qui ont des sous-règles.

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a>Spécification de caractères spéciaux

Dans un nom de type, IDENTIFIER correspond à n’importe quel nom valide déterminé par les règles d’un langage.

Utilisez la barre oblique inverse (\\) comme caractère d’échappement pour séparer les jetons suivants quand ils sont utilisés avec IDENTIFIER.

|par jeton|Signification|
|-----------|-------------|
|\\,|Séparateur d’assembly.|
|\\+|Séparateur de type imbriqué.|
|\\&|Type référence.|
|\\*|Type pointeur.|
|\\[|Délimiteur de dimension du tableau.|
|\\]|Délimiteur de dimension du tableau.|
|\\.|Utilisez la barre oblique inverse avant un point uniquement si celui-ci est utilisé dans une spécification de tableau. Les points de NamespaceSpec ne sont pas précédés d’une barre oblique inverse.|
|\\\|Barre oblique inverse nécessaire comme littéral de chaîne.|

Notez que des espaces peuvent être utilisés dans tous les composants TypeSpec, sauf AssemblyNameSpec. Dans AssemblyNameSpec, les espaces précédant le séparateur « , » peuvent être utilisés, mais ceux situés après le séparateur « , » sont ignorés.

Les classes Reflection, telles que <xref:System.Type.FullName%2A?displayProperty=nameWithType>, retournent le nom tronqué, lequel peut être utilisé dans un appel à <xref:System.Type.GetType%2A>, comme dans `MyType.GetType(myType.FullName)`.

Par exemple, le nom complet d’un type peut être `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.

Si l’espace de noms est `Ozzy.Out+Back`, le signe plus (+) doit être précédé d’une barre oblique inverse. Sinon, l’analyseur l’interprète comme un séparateur d’imbrication. La réflexion génère cette chaîne comme suit : `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.

## <a name="specifying-assembly-names"></a>Spécification des noms d’assemblys

Au minimum, vous devez fournir le nom textuel (IDENTIFIER) de l’assembly comme spécification du nom d’assembly. Vous pouvez faire suivre IDENTIFIER d’une liste de paires de propriétés/valeurs avec la virgule comme séparateur, comme l’illustre le tableau suivant. L’affectation d’un nom à IDENTIFIER doit se conformer aux règles d’attribution de noms de fichiers. IDENTIFIER ne respecte pas la casse.

|Nom de la propriété|Description|Valeurs autorisées|
|-------------------|-----------------|----------------------|
|**Version**|Numéro de version de l’assembly|*version_majeure.version_mineure_build.révision*, où *version_majeure*, *version_mineure*, *build* et *révision* sont des entiers compris entre 0 et 65535 inclus.|
|**PublicKey**|Clé publique complète|Valeur de chaîne de la clé publique complète au format hexadécimal. Spécifiez une référence Null (**Nothing** en Visual Basic) pour indiquer explicitement un assembly privé.|
|**PublicKeyToken**|Jeton de clé publique (hachage de 8 octets de la clé publique complète)|Valeur de chaîne du jeton de clé publique au format hexadécimal. Spécifiez une référence Null (**Nothing** en Visual Basic) pour indiquer explicitement un assembly privé.|
|**Culturel**|Culture de l’assembly|Culture de l’assembly au format RFC-1766 ou « neutre » pour les assemblys indépendants du langage (non-satellites).|
|**Personnalisée**|Objet binaire volumineux (BLOB) personnalisé. Utilisé uniquement dans les assemblys générés par le [générateur d’images natives (Ngen)](../tools/ngen-exe-native-image-generator.md).|Chaîne personnalisée utilisée par le générateur d’images natives (Ngen) pour informer le cache d’assembly que l’assembly installé est une image native, et qu’il doit donc être installé dans le cache des images natives. Également appelée chaîne zap.|

L’exemple suivant illustre un **AssemblyName** pour un assembly nommé simplement avec une culture par défaut.

```csharp
com.microsoft.crypto, Culture=""
```

L’exemple suivant illustre une référence complète pour un assembly utilisant un nom fort et la culture « en ».

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui peut correspondre à un assembly portant un nom fort ou nommé simplement.

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui doit correspondre à un assembly nommé simplement.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui doit correspondre à un assembly portant un nom fort.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a>Spécification de types génériques

SimpleTypeSpec\`NUMBER représente un type générique ouvert avec entre 1 et *n* paramètres de type générique. Par exemple, pour obtenir une référence à la liste de types génériques ouverte \<T> ou à la liste de types génériques fermée \<String> , utilisez ``Type.GetType("System.Collections.Generic.List`1")`` pour obtenir une référence au dictionnaire de types génériques \<TKey,TValue> , utilisez ``Type.GetType("System.Collections.Generic.Dictionary`2")`` .

## <a name="specifying-pointers"></a>Spécification des pointeurs

SimpleTypeSpec* représente un pointeur non managé. Par exemple, pour obtenir un pointeur vers le type MyType, utilisez `Type.GetType("MyType*")`. Pour obtenir un pointeur vers un autre pointeur vers le type MyType, utilisez `Type.GetType("MyType**")`.

## <a name="specifying-references"></a>Spécification des références

SimpleTypeSpec & représente un pointeur ou une référence managé. Par exemple, pour obtenir une référence au type MyType, utilisez `Type.GetType("MyType &")`. Notez que contrairement aux pointeurs, les références sont limitées à un niveau.

## <a name="specifying-arrays"></a>Spécification des tableaux

Dans la syntaxe BNF, ReflectionEmitDimension ne s’applique qu’aux définitions de types incomplètes récupérées à l’aide de <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>. Les définitions de types incomplètes sont des objets <xref:System.Reflection.Emit.TypeBuilder> construits à l’aide de <xref:System.Reflection.Emit?displayProperty=nameWithType>, mais sur lesquels <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> n’a pas été appelé. ReflectionDimension peut être utilisé pour récupérer une définition de type achevée, c’est-à-dire un type qui a été chargé.

Les tableaux sont accessibles dans la réflexion en spécifiant le rang du tableau :

- `Type.GetType("MyArray[]")` obtient un tableau unidimensionnel dont la limite inférieure est égale à 0.

- `Type.GetType("MyArray[*]")` obtient un tableau unidimensionnel dont la limite inférieure est inconnue.
- `Type.GetType("MyArray[][]")` obtient un tableau contenant un tableau à deux dimensions.

- `Type.GetType("MyArray[*,*]")` et`Type.GetType("MyArray[,]")` obtiennent un tableau rectangulaire à deux dimensions dont les limites inférieures sont inconnues.

Notez que du point de vue du runtime, `MyArray[] != MyArray[*]`, mais pour les tableaux multidimensionnels, les deux notations sont équivalentes. En d’autres termes, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` prend la valeur **true**.

Pour **ModuleBuilder. GetType**, `MyArray[0..5]` indique un tableau à une seule dimension avec la taille 6, la limite inférieure 0. `MyArray[4…]` indique un tableau unidimensionnel dont la taille est inconnue et dont la limite inférieure est égale à 4.

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [Affichage des informations de type](viewing-type-information.md)
