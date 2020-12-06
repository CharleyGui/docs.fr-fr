---
title: Propriétés
description: 'En savoir plus sur les propriétés F #, qui sont des membres qui représentent des valeurs associées à un objet.'
ms.date: 05/16/2016
ms.openlocfilehash: a2a4fbfc88831dcb5cad7a2da701969b2e98b2e3
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740196"
---
# <a name="properties"></a><span data-ttu-id="1c8de-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1c8de-103">Properties</span></span>

<span data-ttu-id="1c8de-104">Les *Propriétés* sont des membres qui représentent des valeurs associées à un objet.</span><span class="sxs-lookup"><span data-stu-id="1c8de-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c8de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c8de-105">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="1c8de-106">Notes</span><span class="sxs-lookup"><span data-stu-id="1c8de-106">Remarks</span></span>

<span data-ttu-id="1c8de-107">Les propriétés représentent la relation « has a » dans la programmation orientée objet, représentant les données associées aux instances d’objet ou, pour les propriétés statiques, avec le type.</span><span class="sxs-lookup"><span data-stu-id="1c8de-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="1c8de-108">Vous pouvez déclarer des propriétés de deux façons, selon que vous souhaitez spécifier explicitement la valeur sous-jacente (également appelée magasin de stockage) pour la propriété, ou si vous souhaitez autoriser le compilateur à générer automatiquement le magasin de stockage pour vous.</span><span class="sxs-lookup"><span data-stu-id="1c8de-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="1c8de-109">En général, vous devez utiliser la méthode la plus explicite si la propriété a une implémentation non triviale et la façon automatique lorsque la propriété est simplement un wrapper simple pour une valeur ou une variable.</span><span class="sxs-lookup"><span data-stu-id="1c8de-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="1c8de-110">Pour déclarer explicitement une propriété, utilisez le `member` mot clé.</span><span class="sxs-lookup"><span data-stu-id="1c8de-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="1c8de-111">Cette syntaxe déclarative est suivie par la syntaxe qui spécifie les `get` `set` méthodes et, également appelées *accesseurs*.</span><span class="sxs-lookup"><span data-stu-id="1c8de-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="1c8de-112">Les différentes formes de syntaxe explicite indiquées dans la section syntaxe sont utilisées pour les propriétés en lecture/écriture, en lecture seule et en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="1c8de-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="1c8de-113">Pour les propriétés en lecture seule, vous définissez uniquement une `get` méthode ; pour les propriétés en écriture seule, définissez uniquement une `set` méthode.</span><span class="sxs-lookup"><span data-stu-id="1c8de-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="1c8de-114">Notez que lorsqu’une propriété possède des `get` `set` accesseurs et, l’autre syntaxe vous permet de spécifier des attributs et des modificateurs d’accessibilité qui sont différents pour chaque accesseur, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1c8de-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="1c8de-115">Pour les propriétés en lecture/écriture, qui ont à la fois une `get` `set` méthode et, l’ordre de `get` et `set` peut être inversé.</span><span class="sxs-lookup"><span data-stu-id="1c8de-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="1c8de-116">Vous pouvez également fournir la syntaxe indiquée pour `get` uniquement et la syntaxe indiquée pour `set` uniquement au lieu d’utiliser la syntaxe combinée.</span><span class="sxs-lookup"><span data-stu-id="1c8de-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="1c8de-117">Cela simplifie la procédure de commentaire de la personne `get` ou de la `set` méthode, si c’est une opération que vous devrez peut-être faire.</span><span class="sxs-lookup"><span data-stu-id="1c8de-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="1c8de-118">Cette alternative à l’utilisation de la syntaxe combinée est illustrée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1c8de-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="1c8de-119">Les valeurs privées qui contiennent les données pour les propriétés sont appelées *magasins* de stockage.</span><span class="sxs-lookup"><span data-stu-id="1c8de-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="1c8de-120">Pour que le compilateur crée automatiquement le magasin de stockage, utilisez les mots clés `member val` , omettez l’auto-identificateur, puis fournissez une expression pour initialiser la propriété.</span><span class="sxs-lookup"><span data-stu-id="1c8de-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="1c8de-121">Si la propriété doit être mutable, incluez `with get, set` .</span><span class="sxs-lookup"><span data-stu-id="1c8de-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="1c8de-122">Par exemple, le type de classe suivant comprend deux propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="1c8de-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="1c8de-123">`Property1` est en lecture seule et est initialisé à l’argument fourni au constructeur principal, et `Property2` est une propriété définissable initialisée à une chaîne vide :</span><span class="sxs-lookup"><span data-stu-id="1c8de-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="1c8de-124">Les propriétés implémentées automatiquement font partie de l’initialisation d’un type. elles doivent donc être incluses avant toute autre définition de membre, tout comme les `let` liaisons et les `do` liaisons dans une définition de type.</span><span class="sxs-lookup"><span data-stu-id="1c8de-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="1c8de-125">Notez que l’expression qui initialise une propriété implémentée automatiquement n’est évaluée qu’au moment de l’initialisation, et non à chaque accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="1c8de-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="1c8de-126">Ce comportement diffère du comportement d’une propriété implémentée explicitement.</span><span class="sxs-lookup"><span data-stu-id="1c8de-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="1c8de-127">Cela signifie que le code permettant d’initialiser ces propriétés est ajouté au constructeur d’une classe.</span><span class="sxs-lookup"><span data-stu-id="1c8de-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="1c8de-128">Prenons le code suivant qui illustre cette différence :</span><span class="sxs-lookup"><span data-stu-id="1c8de-128">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn $"class1.AutoProperty = %d{class1.AutoProperty}"
printfn $"class1.ExplicitProperty = %d{class1.ExplicitProperty}"
```

<span data-ttu-id="1c8de-129">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="1c8de-129">**Output**</span></span>

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="1c8de-130">La sortie du code précédent indique que la valeur de la propriété autoproperty est inchangée quand elle est appelée à plusieurs reprises, tandis que le ExplicitProperty change chaque fois qu’elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="1c8de-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="1c8de-131">Cela démontre que l’expression pour une propriété implémentée automatiquement n’est pas évaluée à chaque fois, comme c’est le cas de la méthode Getter pour la propriété Explicit.</span><span class="sxs-lookup"><span data-stu-id="1c8de-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
><span data-ttu-id="1c8de-132">Certaines bibliothèques, telles que le Entity Framework (), `System.Data.Entity` effectuent des opérations personnalisées dans les constructeurs de classe de base qui ne fonctionnent pas correctement avec l’initialisation des propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="1c8de-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="1c8de-133">Dans ce cas, essayez d’utiliser des propriétés explicites.</span><span class="sxs-lookup"><span data-stu-id="1c8de-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="1c8de-134">Les propriétés peuvent être des membres de classes, de structures, d’unions discriminées, d’enregistrements, d’interfaces et d’extensions de type. elles peuvent également être définies dans des expressions d’objet.</span><span class="sxs-lookup"><span data-stu-id="1c8de-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="1c8de-135">Les attributs peuvent être appliqués aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="1c8de-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="1c8de-136">Pour appliquer un attribut à une propriété, écrivez l’attribut sur une ligne distincte avant la propriété.</span><span class="sxs-lookup"><span data-stu-id="1c8de-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="1c8de-137">Pour plus d’informations, consultez [Attributs](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1c8de-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="1c8de-138">Par défaut, les propriétés sont publiques.</span><span class="sxs-lookup"><span data-stu-id="1c8de-138">By default, properties are public.</span></span> <span data-ttu-id="1c8de-139">Les modificateurs d’accessibilité peuvent également être appliqués aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="1c8de-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="1c8de-140">Pour appliquer un modificateur d’accessibilité, ajoutez-le immédiatement avant le nom de la propriété s’il est destiné à s’appliquer aux deux `get` méthodes et. `set` Ajoutez-le avant les `get` `set` Mots clés et si une accessibilité différente est requise pour chaque accesseur.</span><span class="sxs-lookup"><span data-stu-id="1c8de-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="1c8de-141">Le *modificateur Accessibility* peut être l’un des suivants : `public` , `private` , `internal` .</span><span class="sxs-lookup"><span data-stu-id="1c8de-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="1c8de-142">Pour obtenir plus d'informations, voir [Contrôle d'accès](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="1c8de-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="1c8de-143">Les implémentations de propriétés sont exécutées chaque fois qu’un utilisateur accède à une propriété.</span><span class="sxs-lookup"><span data-stu-id="1c8de-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="1c8de-144">Propriétés statiques et d’instance</span><span class="sxs-lookup"><span data-stu-id="1c8de-144">Static and Instance Properties</span></span>

<span data-ttu-id="1c8de-145">Les propriétés peuvent être des propriétés statiques ou d’instance.</span><span class="sxs-lookup"><span data-stu-id="1c8de-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="1c8de-146">Les propriétés statiques peuvent être appelées sans instance et sont utilisées pour les valeurs associées au type, et non avec des objets individuels.</span><span class="sxs-lookup"><span data-stu-id="1c8de-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="1c8de-147">Pour les propriétés statiques, omettez l’auto-identificateur.</span><span class="sxs-lookup"><span data-stu-id="1c8de-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="1c8de-148">L’auto-identificateur est requis pour les propriétés d’instance.</span><span class="sxs-lookup"><span data-stu-id="1c8de-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="1c8de-149">La définition de propriété statique suivante est basée sur un scénario dans lequel vous avez un champ statique `myStaticValue` qui est le magasin de stockage pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="1c8de-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="1c8de-150">Les propriétés peuvent également être de type tableau, auquel cas elles sont appelées *propriétés indexées*.</span><span class="sxs-lookup"><span data-stu-id="1c8de-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="1c8de-151">Pour plus d’informations, consultez [propriétés indexées](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1c8de-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="1c8de-152">Annotation de type pour les propriétés</span><span class="sxs-lookup"><span data-stu-id="1c8de-152">Type Annotation for Properties</span></span>

<span data-ttu-id="1c8de-153">Dans de nombreux cas, le compilateur dispose de suffisamment d’informations pour déduire le type d’une propriété à partir du type du magasin de stockage, mais vous pouvez définir le type explicitement en ajoutant une annotation de type.</span><span class="sxs-lookup"><span data-stu-id="1c8de-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="1c8de-154">Utilisation d’accesseurs set de propriété</span><span class="sxs-lookup"><span data-stu-id="1c8de-154">Using Property set Accessors</span></span>

<span data-ttu-id="1c8de-155">Vous pouvez définir des propriétés qui fournissent `set` des accesseurs à l’aide de l' `<-` opérateur.</span><span class="sxs-lookup"><span data-stu-id="1c8de-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="1c8de-156">La sortie est **20**.</span><span class="sxs-lookup"><span data-stu-id="1c8de-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="1c8de-157">Propriétés abstraites</span><span class="sxs-lookup"><span data-stu-id="1c8de-157">Abstract Properties</span></span>

<span data-ttu-id="1c8de-158">Les propriétés peuvent être abstraites.</span><span class="sxs-lookup"><span data-stu-id="1c8de-158">Properties can be abstract.</span></span> <span data-ttu-id="1c8de-159">Comme pour les méthodes, `abstract` signifie simplement qu’il existe une répartition virtuelle associée à la propriété.</span><span class="sxs-lookup"><span data-stu-id="1c8de-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="1c8de-160">Les propriétés abstraites peuvent être véritablement abstraites, autrement dit, sans définition dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="1c8de-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="1c8de-161">La classe qui contient une telle propriété est par conséquent une classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="1c8de-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="1c8de-162">Abstraite peut simplement signifier qu’une propriété est virtuelle, et dans ce cas, une définition doit être présente dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="1c8de-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="1c8de-163">Notez que les propriétés abstraites ne doivent pas être privées et, si un accesseur est abstrait, l’autre doit également être abstraite.</span><span class="sxs-lookup"><span data-stu-id="1c8de-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="1c8de-164">Pour plus d’informations sur les classes abstraites, consultez [classes abstraites](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="1c8de-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="1c8de-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c8de-165">See also</span></span>

- <span data-ttu-id="1c8de-166">[Members](index.md) (Membres)</span><span class="sxs-lookup"><span data-stu-id="1c8de-166">[Members](index.md)</span></span>
- [<span data-ttu-id="1c8de-167">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1c8de-167">Methods</span></span>](methods.md)
