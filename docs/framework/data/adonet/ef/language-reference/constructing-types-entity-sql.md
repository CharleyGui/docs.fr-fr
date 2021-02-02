---
title: Construction de types (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 89b4c3bb8b9d69767aa30cee5331269537c084bd
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427025"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="5fb75-102">Construction de types (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5fb75-102">Constructing Types (Entity SQL)</span></span>

<!-- markdownlint-disable DOCSMD001 -->
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5fb75-103">fournit trois genres de constructeurs : des constructeurs de ligne, des constructeurs de type nommé et des constructeurs de collection.</span><span class="sxs-lookup"><span data-stu-id="5fb75-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>

## <a name="row-constructors"></a><span data-ttu-id="5fb75-104">Constructeurs de ligne</span><span class="sxs-lookup"><span data-stu-id="5fb75-104">Row Constructors</span></span>

<span data-ttu-id="5fb75-105">Les constructeurs de ligne s'avèrent utiles dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour construire des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="5fb75-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="5fb75-106">Le type de résultat d'un constructeur de ligne est un type de ligne dont les types de champs correspondent aux types des valeurs qui ont servi à construire la ligne.</span><span class="sxs-lookup"><span data-stu-id="5fb75-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="5fb75-107">Par exemple, l’expression suivante construit une valeur de type `Record(a int, b string, c int)` :</span><span class="sxs-lookup"><span data-stu-id="5fb75-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>

`ROW(1 AS a, "abc" AS b, a + 34 AS c)`

<span data-ttu-id="5fb75-108">Si vous ne fournissez pas d'alias pour une expression contenue dans un constructeur de ligne, Entity Framework essaie d'en générer un.</span><span class="sxs-lookup"><span data-stu-id="5fb75-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="5fb75-109">Pour plus d’informations, consultez la section « règles d’alias » dans [identificateurs](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5fb75-109">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>

<span data-ttu-id="5fb75-110">Les règles suivantes s'appliquent à l'utilisation d'alias dans les expressions d'un constructeur de ligne :</span><span class="sxs-lookup"><span data-stu-id="5fb75-110">The following rules apply to expression aliasing in a row constructor:</span></span>

- <span data-ttu-id="5fb75-111">les expressions contenues dans un constructeur de ligne ne peuvent pas faire référence aux autres alias du même constructeur ;</span><span class="sxs-lookup"><span data-stu-id="5fb75-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>
- <span data-ttu-id="5fb75-112">deux expressions contenues dans un même constructeur de ligne ne peuvent pas avoir le même alias.</span><span class="sxs-lookup"><span data-stu-id="5fb75-112">Two expressions in the same row constructor cannot have the same alias.</span></span>

<span data-ttu-id="5fb75-113">Pour plus d’informations sur les constructeurs de ligne, consultez [ligne](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5fb75-113">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>

## <a name="collection-constructors"></a><span data-ttu-id="5fb75-114">Constructeurs de collection</span><span class="sxs-lookup"><span data-stu-id="5fb75-114">Collection Constructors</span></span>

<span data-ttu-id="5fb75-115">Les constructeurs de collection dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permettent de créer une instance d’un multiensemble à partir d’une liste de valeurs.</span><span class="sxs-lookup"><span data-stu-id="5fb75-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="5fb75-116">Toutes les valeurs du constructeur doivent être de type `T` mutuellement compatible et le constructeur produit une collection de type `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="5fb75-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="5fb75-117">Par exemple, l'expression suivante crée une collection d'entiers :</span><span class="sxs-lookup"><span data-stu-id="5fb75-117">For example, the following expression creates a collection of integers:</span></span>

`Multiset(1, 2, 3)`

`{1, 2, 3}`

<span data-ttu-id="5fb75-118">Les constructeurs multiensembles vides ne sont pas autorisés, car le type des éléments ne peut pas être déterminé.</span><span class="sxs-lookup"><span data-stu-id="5fb75-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="5fb75-119">L'exemple suivant n'est pas valide :</span><span class="sxs-lookup"><span data-stu-id="5fb75-119">The following is not valid:</span></span>

`multiset() {}`

<span data-ttu-id="5fb75-120">Pour plus d’informations, [consultez](multiset-entity-sql.md)multiensemble.</span><span class="sxs-lookup"><span data-stu-id="5fb75-120">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>

## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="5fb75-121">Constructeurs de type nommé (initialiseurs NamedType)</span><span class="sxs-lookup"><span data-stu-id="5fb75-121">Named Type Constructors (NamedType Initializers)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5fb75-122">permet aux constructeurs de type (initialiseurs) de créer des instances de types complexes nommés et de types d'entités.</span><span class="sxs-lookup"><span data-stu-id="5fb75-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="5fb75-123">Par exemple, l'expression suivante crée une instance d'un type `Person`.</span><span class="sxs-lookup"><span data-stu-id="5fb75-123">For example, the following expression creates an instance of a `Person` type.</span></span>

`Person("abc", 12)`

<span data-ttu-id="5fb75-124">L'expression suivante crée une instance d'un type complexe.</span><span class="sxs-lookup"><span data-stu-id="5fb75-124">The following expression creates an instance of a complex type.</span></span>

`MyModel.ZipCode(‘98118’, ‘4567’)`

<span data-ttu-id="5fb75-125">L'expression suivante crée une instance d'un type complexe imbriqué.</span><span class="sxs-lookup"><span data-stu-id="5fb75-125">The following expression creates an instance of a nested complex type.</span></span>

`MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`

<span data-ttu-id="5fb75-126">L'expression suivante crée une instance d'une entité avec un type complexe imbriqué.</span><span class="sxs-lookup"><span data-stu-id="5fb75-126">The following expression creates an instance of an entity with a nested complex type.</span></span>

`MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`

<span data-ttu-id="5fb75-127">L'exemple suivant montre comment initialiser une propriété d'un type complexe en valeur Null.</span><span class="sxs-lookup"><span data-stu-id="5fb75-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`

<span data-ttu-id="5fb75-128">Les arguments passés au constructeur sont supposés se trouver dans le même ordre que dans la déclaration des attributs du type.</span><span class="sxs-lookup"><span data-stu-id="5fb75-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>

<span data-ttu-id="5fb75-129">Pour plus d’informations, consultez [constructeur de type nommé](named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5fb75-129">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fb75-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fb75-130">See also</span></span>

- [<span data-ttu-id="5fb75-131">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5fb75-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5fb75-132">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5fb75-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="5fb75-133">Système de types</span><span class="sxs-lookup"><span data-stu-id="5fb75-133">Type System</span></span>](type-system-entity-sql.md)
