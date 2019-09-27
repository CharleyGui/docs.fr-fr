---
title: Property, instruction (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 2c3e417aad404171a43342dc92773615ec350ef5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332743"
---
# <a name="property-statement"></a><span data-ttu-id="c4839-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c4839-102">Property Statement</span></span>

<span data-ttu-id="c4839-103">Déclare le nom d’une propriété, ainsi que les procédures de propriété utilisées pour stocker et récupérer la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4839-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4839-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a><span data-ttu-id="c4839-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c4839-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="c4839-106">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-106">Optional.</span></span> <span data-ttu-id="c4839-107">Liste des attributs qui s’appliquent à cette propriété ou à la procédure `Get` ou `Set`.</span><span class="sxs-lookup"><span data-stu-id="c4839-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="c4839-108">Consultez la [liste des attributs](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="c4839-109">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-109">Optional.</span></span> <span data-ttu-id="c4839-110">Spécifie que cette propriété est la propriété par défaut pour la classe ou la structure sur laquelle elle est définie.</span><span class="sxs-lookup"><span data-stu-id="c4839-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="c4839-111">Les propriétés par défaut doivent accepter des paramètres et peuvent être définies et récupérées sans spécifier le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="c4839-112">Si vous déclarez la propriété comme `Default`, vous ne pouvez pas utiliser `Private` sur la propriété ou sur l’une de ses procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="c4839-113">Facultatif sur l’instruction `Property` et sur au plus une des instructions `Get` et `Set`.</span><span class="sxs-lookup"><span data-stu-id="c4839-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="c4839-114">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="c4839-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="c4839-115">Public</span><span class="sxs-lookup"><span data-stu-id="c4839-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="c4839-116">Protected</span><span class="sxs-lookup"><span data-stu-id="c4839-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="c4839-117">Friend</span><span class="sxs-lookup"><span data-stu-id="c4839-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="c4839-118">Private</span><span class="sxs-lookup"><span data-stu-id="c4839-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="c4839-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="c4839-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="c4839-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="c4839-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="c4839-121">Consultez [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="c4839-122">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-122">Optional.</span></span> <span data-ttu-id="c4839-123">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="c4839-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="c4839-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="c4839-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="c4839-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="c4839-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="c4839-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="c4839-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="c4839-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="c4839-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="c4839-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="c4839-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="c4839-129">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-129">Optional.</span></span> <span data-ttu-id="c4839-130">Consultez [partagé](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="c4839-131">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-131">Optional.</span></span> <span data-ttu-id="c4839-132">Consultez [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="c4839-133">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-133">Optional.</span></span> <span data-ttu-id="c4839-134">Consultez [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="c4839-135">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-135">Optional.</span></span> <span data-ttu-id="c4839-136">Consultez [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="c4839-137">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-137">Optional.</span></span> <span data-ttu-id="c4839-138">Consultez [iterator](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="c4839-139">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c4839-139">Required.</span></span> <span data-ttu-id="c4839-140">Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-140">Name of the property.</span></span> <span data-ttu-id="c4839-141">Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="c4839-142">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-142">Optional.</span></span> <span data-ttu-id="c4839-143">Liste des noms de variables locales qui représentent les paramètres de cette propriété, ainsi que des paramètres supplémentaires possibles de la procédure `Set`.</span><span class="sxs-lookup"><span data-stu-id="c4839-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="c4839-144">Consultez la [liste des paramètres](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="c4839-145">Obligatoire si `Option Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="c4839-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="c4839-146">Type de données de la valeur retournée par cette propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="c4839-147">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-147">Optional.</span></span> <span data-ttu-id="c4839-148">Indique que cette propriété implémente une ou plusieurs propriétés, chacune d’elles étant définie dans une interface implémentée par la classe ou la structure conteneur de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="c4839-149">Consultez [Implements, instruction](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="c4839-150">Obligatoire si `Implements` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c4839-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="c4839-151">Liste des propriétés en cours d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="c4839-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="c4839-152">Chaque `implementedproperty` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c4839-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="c4839-153">Élément</span><span class="sxs-lookup"><span data-stu-id="c4839-153">Part</span></span>|<span data-ttu-id="c4839-154">Description</span><span class="sxs-lookup"><span data-stu-id="c4839-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="c4839-155">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c4839-155">Required.</span></span> <span data-ttu-id="c4839-156">Nom d’une interface implémentée par la classe ou la structure conteneur de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="c4839-157">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c4839-157">Required.</span></span> <span data-ttu-id="c4839-158">Nom par lequel la propriété est définie dans `interface`.</span><span class="sxs-lookup"><span data-stu-id="c4839-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="c4839-159">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-159">Optional.</span></span> <span data-ttu-id="c4839-160">Obligatoire si la propriété est marquée `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="c4839-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="c4839-161">Démarre une procédure de propriété `Get` qui est utilisée pour retourner la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="c4839-162">L’instruction `Get` n’est pas utilisée avec les [Propriétés implémentées automatiquement](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="c4839-163">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-163">Optional.</span></span> <span data-ttu-id="c4839-164">Bloc d’instructions à exécuter dans la procédure `Get` ou `Set`.</span><span class="sxs-lookup"><span data-stu-id="c4839-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="c4839-165">Met fin à la procédure de propriété `Get`.</span><span class="sxs-lookup"><span data-stu-id="c4839-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="c4839-166">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4839-166">Optional.</span></span> <span data-ttu-id="c4839-167">Obligatoire si la propriété est marquée `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="c4839-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="c4839-168">Démarre une procédure de propriété `Set` qui est utilisée pour stocker la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="c4839-169">L’instruction `Set` n’est pas utilisée avec les [Propriétés implémentées automatiquement](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="c4839-170">Met fin à la procédure de propriété `Set`.</span><span class="sxs-lookup"><span data-stu-id="c4839-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="c4839-171">Met fin à la définition de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4839-172">Notes</span><span class="sxs-lookup"><span data-stu-id="c4839-172">Remarks</span></span>

<span data-ttu-id="c4839-173">L’instruction `Property` introduit la déclaration d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="c4839-174">Une propriété peut avoir une procédure `Get` (lecture seule), une procédure `Set` (écriture seule) ou les deux (lecture-écriture).</span><span class="sxs-lookup"><span data-stu-id="c4839-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="c4839-175">Vous pouvez omettre la procédure `Get` et `Set` lors de l’utilisation d’une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c4839-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="c4839-176">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="c4839-177">Vous pouvez utiliser `Property` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="c4839-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="c4839-178">Cela signifie que le *contexte de déclaration* pour une propriété doit être une classe, une structure, un module ou une interface, et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="c4839-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="c4839-179">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c4839-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="c4839-180">Par défaut, les propriétés utilisent un accès public.</span><span class="sxs-lookup"><span data-stu-id="c4839-180">By default, properties use public access.</span></span> <span data-ttu-id="c4839-181">Vous pouvez ajuster le niveau d’accès d’une propriété à l’aide d’un modificateur d’accès sur l’instruction `Property`, et vous pouvez éventuellement ajuster l’une de ses procédures de propriété à un niveau d’accès plus restrictif.</span><span class="sxs-lookup"><span data-stu-id="c4839-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="c4839-182">Visual Basic passe un paramètre à la procédure `Set` pendant les attributions de propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="c4839-183">Si vous ne fournissez pas de paramètre pour `Set`, l’environnement de développement intégré (IDE) utilise un paramètre implicite nommé `value`.</span><span class="sxs-lookup"><span data-stu-id="c4839-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="c4839-184">Ce paramètre contient la valeur à assigner à la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="c4839-185">En général, vous stockez cette valeur dans une variable locale privée et la Retournez chaque fois que la procédure `Get` est appelée.</span><span class="sxs-lookup"><span data-stu-id="c4839-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="c4839-186">Règles</span><span class="sxs-lookup"><span data-stu-id="c4839-186">Rules</span></span>

- <span data-ttu-id="c4839-187">**Niveaux d’accès mixtes.**</span><span class="sxs-lookup"><span data-stu-id="c4839-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="c4839-188">Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour la procédure `Get` ou `Set`, mais pas pour les deux.</span><span class="sxs-lookup"><span data-stu-id="c4839-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="c4839-189">Dans ce cas, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="c4839-190">Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer la procédure `Set` `Private`, mais pas `Public`.</span><span class="sxs-lookup"><span data-stu-id="c4839-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="c4839-191">Si vous définissez une propriété `ReadOnly` ou `WriteOnly`, la procédure de propriété unique (respectivement `Get` ou `Set`) représente l’ensemble de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="c4839-192">Vous ne pouvez pas déclarer un niveau d’accès différent pour une telle procédure, car cela aurait pour effet de définir deux niveaux d’accès pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="c4839-193">**Type de retour.**</span><span class="sxs-lookup"><span data-stu-id="c4839-193">**Return Type.**</span></span> <span data-ttu-id="c4839-194">L’instruction `Property` peut déclarer le type de données de la valeur qu’elle retourne.</span><span class="sxs-lookup"><span data-stu-id="c4839-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="c4839-195">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface.</span><span class="sxs-lookup"><span data-stu-id="c4839-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="c4839-196">Si vous ne spécifiez pas `returntype`, la propriété retourne `Object`.</span><span class="sxs-lookup"><span data-stu-id="c4839-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="c4839-197">**Déploiement.**</span><span class="sxs-lookup"><span data-stu-id="c4839-197">**Implementation.**</span></span> <span data-ttu-id="c4839-198">Si cette propriété utilise le mot clé `Implements`, la classe ou la structure conteneur doit avoir une instruction `Implements` immédiatement après son instruction `Class` ou `Structure`.</span><span class="sxs-lookup"><span data-stu-id="c4839-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="c4839-199">L’instruction `Implements` doit inclure chaque interface spécifiée dans `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="c4839-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="c4839-200">Toutefois, le nom par lequel une interface définit le `Property` (dans `definedname`) n’a pas besoin d’être identique au nom de cette propriété (dans `name`).</span><span class="sxs-lookup"><span data-stu-id="c4839-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="c4839-201">Comportement</span><span class="sxs-lookup"><span data-stu-id="c4839-201">Behavior</span></span>

- <span data-ttu-id="c4839-202">**Retour d’une procédure de propriété.**</span><span class="sxs-lookup"><span data-stu-id="c4839-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="c4839-203">Lorsque la procédure `Get` ou `Set` retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui l’a appelée.</span><span class="sxs-lookup"><span data-stu-id="c4839-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="c4839-204">Les instructions `Exit Property` et `Return` provoquent une sortie immédiate d’une procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="c4839-205">N’importe quel nombre d’instructions `Exit Property` et `Return` peut apparaître n’importe où dans la procédure, et vous pouvez mélanger des instructions `Exit Property` et `Return`.</span><span class="sxs-lookup"><span data-stu-id="c4839-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="c4839-206">**Valeur de retour.**</span><span class="sxs-lookup"><span data-stu-id="c4839-206">**Return Value.**</span></span> <span data-ttu-id="c4839-207">Pour retourner une valeur à partir d’une procédure `Get`, vous pouvez affecter la valeur au nom de la propriété ou l’inclure dans une instruction `Return`.</span><span class="sxs-lookup"><span data-stu-id="c4839-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="c4839-208">L’exemple suivant affecte la valeur de retour au nom de la propriété `quoteForTheDay`, puis utilise l’instruction `Exit Property` pour retourner.</span><span class="sxs-lookup"><span data-stu-id="c4839-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="c4839-209">Si vous utilisez `Exit Property` sans assigner de valeur à `name`, la procédure `Get` retourne la valeur par défaut pour le type de données de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c4839-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="c4839-210">En même temps, l’instruction `Return` affecte la valeur de retour de la procédure `Get` et quitte la procédure.</span><span class="sxs-lookup"><span data-stu-id="c4839-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="c4839-211">L’exemple suivant illustre cela.</span><span class="sxs-lookup"><span data-stu-id="c4839-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="c4839-212">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4839-212">Example</span></span>

<span data-ttu-id="c4839-213">L’exemple suivant déclare une propriété dans une classe.</span><span class="sxs-lookup"><span data-stu-id="c4839-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="c4839-214">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4839-214">See also</span></span>

- [<span data-ttu-id="c4839-215">Propriétés implémentées automatiquement</span><span class="sxs-lookup"><span data-stu-id="c4839-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="c4839-216">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="c4839-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="c4839-217">Get (instruction)</span><span class="sxs-lookup"><span data-stu-id="c4839-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="c4839-218">Set (instruction)</span><span class="sxs-lookup"><span data-stu-id="c4839-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="c4839-219">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="c4839-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="c4839-220">Default</span><span class="sxs-lookup"><span data-stu-id="c4839-220">Default</span></span>](../modifiers/default.md)
