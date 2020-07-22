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
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="6d966-103">Spécification des noms de types complets</span><span class="sxs-lookup"><span data-stu-id="6d966-103">Specifying fully qualified type names</span></span>

<span data-ttu-id="6d966-104">Vous devez spécifier des noms de types pour pouvoir valider l’entrée servant aux diverses opérations de réflexion.</span><span class="sxs-lookup"><span data-stu-id="6d966-104">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="6d966-105">Un nom de type complet se compose d’une spécification de nom d’assembly, d’une spécification d’espace de noms et d’un nom de type.</span><span class="sxs-lookup"><span data-stu-id="6d966-105">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="6d966-106">Les spécifications de noms de types sont utilisées par les méthodes telles que <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> et <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d966-106">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="6d966-107">Grammaire pour les noms de types</span><span class="sxs-lookup"><span data-stu-id="6d966-107">Grammar for type names</span></span>

 <span data-ttu-id="6d966-108">La grammaire définit la syntaxe des langages formels.</span><span class="sxs-lookup"><span data-stu-id="6d966-108">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="6d966-109">Le tableau suivant décrit les règles lexicales permettant de reconnaître une entrée valide.</span><span class="sxs-lookup"><span data-stu-id="6d966-109">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="6d966-110">Les éléments terminaux (qui ne peuvent pas être réduits davantage) sont affichés en majuscules.</span><span class="sxs-lookup"><span data-stu-id="6d966-110">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="6d966-111">Les éléments non terminaux (qui peuvent être réduits davantage) sont affichés dans une casse mixte ou entre des guillemets simples ; toutefois, le guillemet simple (') ne fait pas partie de la syntaxe proprement dite.</span><span class="sxs-lookup"><span data-stu-id="6d966-111">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="6d966-112">La barre verticale (&#124;) signale des règles qui ont des sous-règles.</span><span class="sxs-lookup"><span data-stu-id="6d966-112">The pipe character (&#124;) denotes rules that have subrules.</span></span>

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

## <a name="specifying-special-characters"></a><span data-ttu-id="6d966-113">Spécification de caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="6d966-113">Specifying special characters</span></span>

<span data-ttu-id="6d966-114">Dans un nom de type, IDENTIFIER correspond à n’importe quel nom valide déterminé par les règles d’un langage.</span><span class="sxs-lookup"><span data-stu-id="6d966-114">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="6d966-115">Utilisez la barre oblique inverse (\\) comme caractère d’échappement pour séparer les jetons suivants quand ils sont utilisés avec IDENTIFIER.</span><span class="sxs-lookup"><span data-stu-id="6d966-115">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="6d966-116">par jeton</span><span class="sxs-lookup"><span data-stu-id="6d966-116">Token</span></span>|<span data-ttu-id="6d966-117">Signification</span><span class="sxs-lookup"><span data-stu-id="6d966-117">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="6d966-118">\\,</span><span class="sxs-lookup"><span data-stu-id="6d966-118">\\,</span></span>|<span data-ttu-id="6d966-119">Séparateur d’assembly.</span><span class="sxs-lookup"><span data-stu-id="6d966-119">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="6d966-120">Séparateur de type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="6d966-120">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="6d966-121">Type référence.</span><span class="sxs-lookup"><span data-stu-id="6d966-121">Reference type.</span></span>|
|\\*|<span data-ttu-id="6d966-122">Type pointeur.</span><span class="sxs-lookup"><span data-stu-id="6d966-122">Pointer type.</span></span>|
|<span data-ttu-id="6d966-123">\\[</span><span class="sxs-lookup"><span data-stu-id="6d966-123">\\[</span></span>|<span data-ttu-id="6d966-124">Délimiteur de dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="6d966-124">Array dimension delimiter.</span></span>|
|<span data-ttu-id="6d966-125">\\]</span><span class="sxs-lookup"><span data-stu-id="6d966-125">\\]</span></span>|<span data-ttu-id="6d966-126">Délimiteur de dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="6d966-126">Array dimension delimiter.</span></span>|
|<span data-ttu-id="6d966-127">\\.</span><span class="sxs-lookup"><span data-stu-id="6d966-127">\\.</span></span>|<span data-ttu-id="6d966-128">Utilisez la barre oblique inverse avant un point uniquement si celui-ci est utilisé dans une spécification de tableau.</span><span class="sxs-lookup"><span data-stu-id="6d966-128">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="6d966-129">Les points de NamespaceSpec ne sont pas précédés d’une barre oblique inverse.</span><span class="sxs-lookup"><span data-stu-id="6d966-129">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="6d966-130">\\\|Barre oblique inverse nécessaire comme littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="6d966-130">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="6d966-131">Notez que des espaces peuvent être utilisés dans tous les composants TypeSpec, sauf AssemblyNameSpec.</span><span class="sxs-lookup"><span data-stu-id="6d966-131">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="6d966-132">Dans AssemblyNameSpec, les espaces précédant le séparateur « , » peuvent être utilisés, mais ceux situés après le séparateur « , » sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="6d966-132">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="6d966-133">Les classes Reflection, telles que <xref:System.Type.FullName%2A?displayProperty=nameWithType>, retournent le nom tronqué, lequel peut être utilisé dans un appel à <xref:System.Type.GetType%2A>, comme dans `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="6d966-133">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="6d966-134">Par exemple, le nom complet d’un type peut être `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="6d966-134">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="6d966-135">Si l’espace de noms est `Ozzy.Out+Back`, le signe plus (+) doit être précédé d’une barre oblique inverse.</span><span class="sxs-lookup"><span data-stu-id="6d966-135">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="6d966-136">Sinon, l’analyseur l’interprète comme un séparateur d’imbrication.</span><span class="sxs-lookup"><span data-stu-id="6d966-136">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="6d966-137">La réflexion génère cette chaîne comme suit : `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="6d966-137">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="6d966-138">Spécification des noms d’assemblys</span><span class="sxs-lookup"><span data-stu-id="6d966-138">Specifying assembly names</span></span>

<span data-ttu-id="6d966-139">Au minimum, vous devez fournir le nom textuel (IDENTIFIER) de l’assembly comme spécification du nom d’assembly.</span><span class="sxs-lookup"><span data-stu-id="6d966-139">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="6d966-140">Vous pouvez faire suivre IDENTIFIER d’une liste de paires de propriétés/valeurs avec la virgule comme séparateur, comme l’illustre le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="6d966-140">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="6d966-141">L’affectation d’un nom à IDENTIFIER doit se conformer aux règles d’attribution de noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="6d966-141">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="6d966-142">IDENTIFIER ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="6d966-142">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="6d966-143">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="6d966-143">Property name</span></span>|<span data-ttu-id="6d966-144">Description</span><span class="sxs-lookup"><span data-stu-id="6d966-144">Description</span></span>|<span data-ttu-id="6d966-145">Valeurs autorisées</span><span class="sxs-lookup"><span data-stu-id="6d966-145">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="6d966-146">**Version**</span><span class="sxs-lookup"><span data-stu-id="6d966-146">**Version**</span></span>|<span data-ttu-id="6d966-147">Numéro de version de l’assembly</span><span class="sxs-lookup"><span data-stu-id="6d966-147">Assembly version number</span></span>|<span data-ttu-id="6d966-148">*version_majeure.version_mineure_build.révision*, où *version_majeure*, *version_mineure*, *build* et *révision* sont des entiers compris entre 0 et 65535 inclus.</span><span class="sxs-lookup"><span data-stu-id="6d966-148">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="6d966-149">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="6d966-149">**PublicKey**</span></span>|<span data-ttu-id="6d966-150">Clé publique complète</span><span class="sxs-lookup"><span data-stu-id="6d966-150">Full public key</span></span>|<span data-ttu-id="6d966-151">Valeur de chaîne de la clé publique complète au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="6d966-151">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="6d966-152">Spécifiez une référence Null (**Nothing** en Visual Basic) pour indiquer explicitement un assembly privé.</span><span class="sxs-lookup"><span data-stu-id="6d966-152">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="6d966-153">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="6d966-153">**PublicKeyToken**</span></span>|<span data-ttu-id="6d966-154">Jeton de clé publique (hachage de 8 octets de la clé publique complète)</span><span class="sxs-lookup"><span data-stu-id="6d966-154">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="6d966-155">Valeur de chaîne du jeton de clé publique au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="6d966-155">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="6d966-156">Spécifiez une référence Null (**Nothing** en Visual Basic) pour indiquer explicitement un assembly privé.</span><span class="sxs-lookup"><span data-stu-id="6d966-156">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="6d966-157">**Culturel**</span><span class="sxs-lookup"><span data-stu-id="6d966-157">**Culture**</span></span>|<span data-ttu-id="6d966-158">Culture de l’assembly</span><span class="sxs-lookup"><span data-stu-id="6d966-158">Assembly culture</span></span>|<span data-ttu-id="6d966-159">Culture de l’assembly au format RFC-1766 ou « neutre » pour les assemblys indépendants du langage (non-satellites).</span><span class="sxs-lookup"><span data-stu-id="6d966-159">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="6d966-160">**Personnalisée**</span><span class="sxs-lookup"><span data-stu-id="6d966-160">**Custom**</span></span>|<span data-ttu-id="6d966-161">Objet binaire volumineux (BLOB) personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6d966-161">Custom binary large object (BLOB).</span></span> <span data-ttu-id="6d966-162">Utilisé uniquement dans les assemblys générés par le [générateur d’images natives (Ngen)](../tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="6d966-162">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="6d966-163">Chaîne personnalisée utilisée par le générateur d’images natives (Ngen) pour informer le cache d’assembly que l’assembly installé est une image native, et qu’il doit donc être installé dans le cache des images natives.</span><span class="sxs-lookup"><span data-stu-id="6d966-163">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="6d966-164">Également appelée chaîne zap.</span><span class="sxs-lookup"><span data-stu-id="6d966-164">Also called a zap string.</span></span>|

<span data-ttu-id="6d966-165">L’exemple suivant illustre un **AssemblyName** pour un assembly nommé simplement avec une culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="6d966-165">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="6d966-166">L’exemple suivant illustre une référence complète pour un assembly utilisant un nom fort et la culture « en ».</span><span class="sxs-lookup"><span data-stu-id="6d966-166">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="6d966-167">Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui peut correspondre à un assembly portant un nom fort ou nommé simplement.</span><span class="sxs-lookup"><span data-stu-id="6d966-167">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="6d966-168">Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui doit correspondre à un assembly nommé simplement.</span><span class="sxs-lookup"><span data-stu-id="6d966-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="6d966-169">Les exemples suivants montrent chacun un **AssemblyName** partiellement spécifié, qui doit correspondre à un assembly portant un nom fort.</span><span class="sxs-lookup"><span data-stu-id="6d966-169">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="6d966-170">Spécification de types génériques</span><span class="sxs-lookup"><span data-stu-id="6d966-170">Specifying generic types</span></span>

<span data-ttu-id="6d966-171">SimpleTypeSpec\`NUMBER représente un type générique ouvert avec entre 1 et *n* paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="6d966-171">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="6d966-172">Par exemple, pour obtenir une référence à la liste de types génériques ouverte \<T> ou à la liste de types génériques fermée \<String> , utilisez ``Type.GetType("System.Collections.Generic.List`1")`` pour obtenir une référence au dictionnaire de types génériques \<TKey,TValue> , utilisez ``Type.GetType("System.Collections.Generic.Dictionary`2")`` .</span><span class="sxs-lookup"><span data-stu-id="6d966-172">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="6d966-173">Spécification des pointeurs</span><span class="sxs-lookup"><span data-stu-id="6d966-173">Specifying pointers</span></span>

<span data-ttu-id="6d966-174">SimpleTypeSpec\* représente un pointeur non managé.</span><span class="sxs-lookup"><span data-stu-id="6d966-174">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="6d966-175">Par exemple, pour obtenir un pointeur vers le type MyType, utilisez `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="6d966-175">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="6d966-176">Pour obtenir un pointeur vers un autre pointeur vers le type MyType, utilisez `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="6d966-176">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="6d966-177">Spécification des références</span><span class="sxs-lookup"><span data-stu-id="6d966-177">Specifying references</span></span>

<span data-ttu-id="6d966-178">SimpleTypeSpec & représente un pointeur ou une référence managé.</span><span class="sxs-lookup"><span data-stu-id="6d966-178">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="6d966-179">Par exemple, pour obtenir une référence au type MyType, utilisez `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="6d966-179">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="6d966-180">Notez que contrairement aux pointeurs, les références sont limitées à un niveau.</span><span class="sxs-lookup"><span data-stu-id="6d966-180">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="6d966-181">Spécification des tableaux</span><span class="sxs-lookup"><span data-stu-id="6d966-181">Specifying arrays</span></span>

<span data-ttu-id="6d966-182">Dans la syntaxe BNF, ReflectionEmitDimension ne s’applique qu’aux définitions de types incomplètes récupérées à l’aide de <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d966-182">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d966-183">Les définitions de types incomplètes sont des objets <xref:System.Reflection.Emit.TypeBuilder> construits à l’aide de <xref:System.Reflection.Emit?displayProperty=nameWithType>, mais sur lesquels <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> n’a pas été appelé.</span><span class="sxs-lookup"><span data-stu-id="6d966-183">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="6d966-184">ReflectionDimension peut être utilisé pour récupérer une définition de type achevée, c’est-à-dire un type qui a été chargé.</span><span class="sxs-lookup"><span data-stu-id="6d966-184">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="6d966-185">Les tableaux sont accessibles dans la réflexion en spécifiant le rang du tableau :</span><span class="sxs-lookup"><span data-stu-id="6d966-185">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="6d966-186">`Type.GetType("MyArray[]")` obtient un tableau unidimensionnel dont la limite inférieure est égale à 0.</span><span class="sxs-lookup"><span data-stu-id="6d966-186">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="6d966-187">`Type.GetType("MyArray[*]")` obtient un tableau unidimensionnel dont la limite inférieure est inconnue.</span><span class="sxs-lookup"><span data-stu-id="6d966-187">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="6d966-188">`Type.GetType("MyArray[][]")` obtient un tableau contenant un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="6d966-188">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="6d966-189">`Type.GetType("MyArray[*,*]")` et`Type.GetType("MyArray[,]")` obtiennent un tableau rectangulaire à deux dimensions dont les limites inférieures sont inconnues.</span><span class="sxs-lookup"><span data-stu-id="6d966-189">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="6d966-190">Notez que du point de vue du runtime, `MyArray[] != MyArray[*]`, mais pour les tableaux multidimensionnels, les deux notations sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="6d966-190">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="6d966-191">En d’autres termes, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` prend la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="6d966-191">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="6d966-192">Pour **ModuleBuilder. GetType**, `MyArray[0..5]` indique un tableau à une seule dimension avec la taille 6, la limite inférieure 0.</span><span class="sxs-lookup"><span data-stu-id="6d966-192">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="6d966-193">`MyArray[4…]` indique un tableau unidimensionnel dont la taille est inconnue et dont la limite inférieure est égale à 4.</span><span class="sxs-lookup"><span data-stu-id="6d966-193">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d966-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d966-194">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6d966-195">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="6d966-195">Viewing Type Information</span></span>](viewing-type-information.md)
