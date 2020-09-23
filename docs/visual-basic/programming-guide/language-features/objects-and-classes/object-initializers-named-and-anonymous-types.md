---
title: "Initialiseurs d'objets : types nommés et anonymes"
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 724407fed5bf90ed6e3e470cbabc9e42856cb99a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087477"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="81f3d-102">Initialiseurs d'objets : types nommés et anonymes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81f3d-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>

<span data-ttu-id="81f3d-103">Les initialiseurs d’objets vous permettent de spécifier des propriétés pour un objet complexe à l’aide d’une expression unique.</span><span class="sxs-lookup"><span data-stu-id="81f3d-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="81f3d-104">Elles peuvent être utilisées pour créer des instances de types nommés et de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="81f3d-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="81f3d-105">Déclarations</span><span class="sxs-lookup"><span data-stu-id="81f3d-105">Declarations</span></span>  

 <span data-ttu-id="81f3d-106">Les déclarations d’instances de types nommés et anonymes peuvent paraître presque identiques, mais leurs effets ne sont pas les mêmes.</span><span class="sxs-lookup"><span data-stu-id="81f3d-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="81f3d-107">Chaque catégorie possède des capacités et des restrictions propres.</span><span class="sxs-lookup"><span data-stu-id="81f3d-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="81f3d-108">L’exemple suivant montre un moyen pratique de déclarer et d’initialiser une instance d’une classe nommée, `Customer` , à l’aide d’une liste d’initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="81f3d-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="81f3d-109">Notez que le nom de la classe est spécifié après le mot clé `New` .</span><span class="sxs-lookup"><span data-stu-id="81f3d-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="81f3d-110">Un type anonyme n’a pas de nom utilisable.</span><span class="sxs-lookup"><span data-stu-id="81f3d-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="81f3d-111">Par conséquent, une instanciation d’un type anonyme ne peut pas inclure un nom de classe.</span><span class="sxs-lookup"><span data-stu-id="81f3d-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="81f3d-112">Les exigences et les résultats des deux déclarations ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="81f3d-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="81f3d-113">Pour `namedCust` , une `Customer` classe qui a une `Name` propriété doit déjà exister, et la déclaration crée une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="81f3d-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="81f3d-114">Pour `anonymousCust` , le compilateur définit une nouvelle classe qui a une propriété, une chaîne appelée `Name` et crée une nouvelle instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="81f3d-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="81f3d-115">Types nommés</span><span class="sxs-lookup"><span data-stu-id="81f3d-115">Named Types</span></span>  

 <span data-ttu-id="81f3d-116">Les initialiseurs d’objets fournissent un moyen simple d’appeler le constructeur d’un type, puis de définir les valeurs de certaines ou de toutes les propriétés dans une même instruction.</span><span class="sxs-lookup"><span data-stu-id="81f3d-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="81f3d-117">Le compilateur appelle le constructeur approprié pour l’instruction : le constructeur sans paramètre si aucun argument n’est présenté, ou un constructeur paramétrable si un ou plusieurs arguments sont envoyés.</span><span class="sxs-lookup"><span data-stu-id="81f3d-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="81f3d-118">Après cela, les propriétés spécifiées sont initialisées dans l’ordre dans lequel elles sont présentées dans la liste d’initialiseurs.</span><span class="sxs-lookup"><span data-stu-id="81f3d-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="81f3d-119">Chaque initialisation dans la liste d’initialiseurs se compose de l’assignation d’une valeur initiale à un membre de la classe.</span><span class="sxs-lookup"><span data-stu-id="81f3d-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="81f3d-120">Les noms et types de données des membres sont déterminés lorsque la classe est définie.</span><span class="sxs-lookup"><span data-stu-id="81f3d-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="81f3d-121">Dans les exemples suivants, la `Customer` classe doit exister et doit avoir des membres nommés `Name` et `City` qui peuvent accepter des valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="81f3d-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="81f3d-122">Vous pouvez également obtenir le même résultat à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="81f3d-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="81f3d-123">Chacune de ces déclarations est équivalente à l’exemple suivant, qui crée un `Customer` objet à l’aide du constructeur sans paramètre, puis spécifie les valeurs initiales des `Name` Propriétés et à `City` l’aide d’une `With` instruction.</span><span class="sxs-lookup"><span data-stu-id="81f3d-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="81f3d-124">Si la `Customer` classe contient un constructeur paramétrable qui vous permet d’envoyer une valeur pour `Name` , par exemple, vous pouvez également déclarer et initialiser un `Customer` objet des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="81f3d-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="81f3d-125">Vous n’avez pas besoin d’initialiser toutes les propriétés, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="81f3d-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="81f3d-126">Toutefois, la liste d’initialisation ne peut pas être vide.</span><span class="sxs-lookup"><span data-stu-id="81f3d-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="81f3d-127">Les propriétés non initialisées conservent leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="81f3d-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="81f3d-128">Inférence de type avec des types nommés</span><span class="sxs-lookup"><span data-stu-id="81f3d-128">Type Inference with Named Types</span></span>  

 <span data-ttu-id="81f3d-129">Vous pouvez raccourcir le code pour la déclaration de `cust1` en combinant des initialiseurs d’objets et l’inférence de type local.</span><span class="sxs-lookup"><span data-stu-id="81f3d-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="81f3d-130">Cela vous permet d’omettre la `As` clause dans la déclaration de la variable.</span><span class="sxs-lookup"><span data-stu-id="81f3d-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="81f3d-131">Le type de données de la variable est déduit du type de l’objet créé par l’assignation.</span><span class="sxs-lookup"><span data-stu-id="81f3d-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="81f3d-132">Dans l’exemple suivant, le type de `cust6` est `Customer` .</span><span class="sxs-lookup"><span data-stu-id="81f3d-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="81f3d-133">Remarques sur les types nommés</span><span class="sxs-lookup"><span data-stu-id="81f3d-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="81f3d-134">Un membre de classe ne peut pas être initialisé plus d’une fois dans la liste d’initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="81f3d-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="81f3d-135">La déclaration de `cust7` provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="81f3d-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="81f3d-136">Un membre peut être utilisé pour s’initialiser lui-même ou un autre champ.</span><span class="sxs-lookup"><span data-stu-id="81f3d-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="81f3d-137">Si vous accédez à un membre avant qu’il n’ait été initialisé, comme dans la déclaration suivante pour `cust8` , la valeur par défaut sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="81f3d-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="81f3d-138">N’oubliez pas que lorsqu’une déclaration qui utilise un initialiseur d’objet est traitée, la première chose qui se produit est que le constructeur approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="81f3d-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="81f3d-139">Après cela, les champs individuels de la liste d’initialiseurs sont initialisés.</span><span class="sxs-lookup"><span data-stu-id="81f3d-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="81f3d-140">Dans les exemples suivants, la valeur par défaut de `Name` est assignée pour `cust8` , et une valeur initialisée est assignée dans `cust9` .</span><span class="sxs-lookup"><span data-stu-id="81f3d-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="81f3d-141">L’exemple suivant utilise le constructeur paramétrable de `cust3` et `cust4` pour déclarer et initialiser `cust10` et `cust11` .</span><span class="sxs-lookup"><span data-stu-id="81f3d-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="81f3d-142">Les initialiseurs d’objets peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="81f3d-142">Object initializers can be nested.</span></span> <span data-ttu-id="81f3d-143">Dans l’exemple suivant, `AddressClass` est une classe qui a deux propriétés, `City` et `State` , et la `Customer` classe a une `Address` propriété qui est une instance de `AddressClass` .</span><span class="sxs-lookup"><span data-stu-id="81f3d-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="81f3d-144">La liste d’initialisation ne peut pas être vide.</span><span class="sxs-lookup"><span data-stu-id="81f3d-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="81f3d-145">L’instance en cours d’initialisation ne peut pas être de type Object.</span><span class="sxs-lookup"><span data-stu-id="81f3d-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="81f3d-146">Les membres de classe en cours d’initialisation ne peuvent pas être des membres partagés, des membres en lecture seule, des constantes ou des appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="81f3d-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="81f3d-147">Les membres de classe en cours d’initialisation ne peuvent pas être indexés ou qualifiés.</span><span class="sxs-lookup"><span data-stu-id="81f3d-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="81f3d-148">Les exemples suivants génèrent des erreurs du compilateur :</span><span class="sxs-lookup"><span data-stu-id="81f3d-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="81f3d-149">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="81f3d-149">Anonymous Types</span></span>  

 <span data-ttu-id="81f3d-150">Les types anonymes utilisent des initialiseurs d’objets pour créer des instances de nouveaux types que vous ne définissez pas explicitement et que vous nommez.</span><span class="sxs-lookup"><span data-stu-id="81f3d-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="81f3d-151">Au lieu de cela, le compilateur génère un type en fonction des propriétés que vous désignez dans la liste d’initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="81f3d-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="81f3d-152">Étant donné que le nom du type n’est pas spécifié, il est appelé *type anonyme*.</span><span class="sxs-lookup"><span data-stu-id="81f3d-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="81f3d-153">Par exemple, comparez la déclaration suivante à la précédente pour `cust6` .</span><span class="sxs-lookup"><span data-stu-id="81f3d-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="81f3d-154">La seule différence est qu’aucun nom n’est spécifié après `New` pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="81f3d-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="81f3d-155">Toutefois, ce qui se passe est assez différent.</span><span class="sxs-lookup"><span data-stu-id="81f3d-155">However, what happens is quite different.</span></span> <span data-ttu-id="81f3d-156">Le compilateur définit un nouveau type anonyme qui a deux propriétés, `Name` et `City` , et en crée une instance avec les valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="81f3d-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="81f3d-157">L’inférence de type détermine les types de `Name` et `City` dans l’exemple comme des chaînes.</span><span class="sxs-lookup"><span data-stu-id="81f3d-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="81f3d-158">Le nom du type anonyme est généré par le compilateur et peut varier de la compilation à la compilation.</span><span class="sxs-lookup"><span data-stu-id="81f3d-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="81f3d-159">Votre code ne doit pas utiliser ou s’appuyer sur le nom d’un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="81f3d-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="81f3d-160">Étant donné que le nom du type n’est pas disponible, vous ne pouvez pas utiliser une `As` clause pour déclarer `cust13` .</span><span class="sxs-lookup"><span data-stu-id="81f3d-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="81f3d-161">Son type doit être déduit.</span><span class="sxs-lookup"><span data-stu-id="81f3d-161">Its type must be inferred.</span></span> <span data-ttu-id="81f3d-162">Sans utiliser la liaison tardive, cela limite l’utilisation des types anonymes aux variables locales.</span><span class="sxs-lookup"><span data-stu-id="81f3d-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="81f3d-163">Les types anonymes fournissent une prise en charge critique pour les requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="81f3d-163">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="81f3d-164">Pour plus d’informations sur l’utilisation de types anonymes dans les requêtes, consultez [types anonymes](anonymous-types.md) et [Introduction à LINQ dans Visual Basic](../linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="81f3d-164">For more information about the use of anonymous types in queries, see [Anonymous Types](anonymous-types.md) and [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="81f3d-165">Remarques sur les types anonymes</span><span class="sxs-lookup"><span data-stu-id="81f3d-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="81f3d-166">En règle générale, la totalité ou la plupart des propriétés d’une déclaration de type anonyme sont des propriétés de clé, qui sont indiquées en tapant le mot clé `Key` devant le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="81f3d-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="81f3d-167">Pour plus d’informations sur les propriétés de clé, consultez [Key](../../../language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="81f3d-167">For more information about key properties, see [Key](../../../language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="81f3d-168">Comme les types nommés, les listes d’initialiseurs pour les définitions de types anonymes doivent déclarer au moins une propriété.</span><span class="sxs-lookup"><span data-stu-id="81f3d-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="81f3d-169">Quand une instance d’un type anonyme est déclarée, le compilateur génère une définition de type anonyme correspondante.</span><span class="sxs-lookup"><span data-stu-id="81f3d-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="81f3d-170">Les noms et les types de données des propriétés sont extraits de la déclaration d’instance et sont inclus par le compilateur dans la définition.</span><span class="sxs-lookup"><span data-stu-id="81f3d-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="81f3d-171">Les propriétés ne sont pas nommées et définies à l’avance, comme c’est le cas pour un type nommé.</span><span class="sxs-lookup"><span data-stu-id="81f3d-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="81f3d-172">Leurs types sont déduits.</span><span class="sxs-lookup"><span data-stu-id="81f3d-172">Their types are inferred.</span></span> <span data-ttu-id="81f3d-173">Vous ne pouvez pas spécifier les types de données des propriétés à l’aide d’une `As` clause.</span><span class="sxs-lookup"><span data-stu-id="81f3d-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="81f3d-174">Les types anonymes peuvent également établir les noms et les valeurs de leurs propriétés de plusieurs autres façons.</span><span class="sxs-lookup"><span data-stu-id="81f3d-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="81f3d-175">Par exemple, une propriété de type anonyme peut accepter à la fois le nom et la valeur d’une variable, ou le nom et la valeur d’une propriété d’un autre objet.</span><span class="sxs-lookup"><span data-stu-id="81f3d-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="81f3d-176">Pour plus d’informations sur les options permettant de définir des propriétés dans des types anonymes, consultez [Comment : déduire les types et les noms de propriétés dans des déclarations de type anonyme](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="81f3d-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f3d-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81f3d-177">See also</span></span>

- [<span data-ttu-id="81f3d-178">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="81f3d-178">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="81f3d-179">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="81f3d-179">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="81f3d-180">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81f3d-180">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="81f3d-181">Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes</span><span class="sxs-lookup"><span data-stu-id="81f3d-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="81f3d-182">Clé</span><span class="sxs-lookup"><span data-stu-id="81f3d-182">Key</span></span>](../../../language-reference/modifiers/key.md)
- [<span data-ttu-id="81f3d-183">Comment : déclarer un objet à l'aide d'un initialiseur d'objet</span><span class="sxs-lookup"><span data-stu-id="81f3d-183">How to: Declare an Object by Using an Object Initializer</span></span>](how-to-declare-an-object-by-using-an-object-initializer.md)
