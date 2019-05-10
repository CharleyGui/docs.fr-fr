---
title: Construction de types (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: d43793b1d514b9dd81f524a30cd5bf1622aa5258
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64632219"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="02b17-102">Construction de types (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="02b17-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="02b17-103">propose trois types de constructeurs : constructeurs de ligne, constructeurs de type nommé et constructeurs de collection.</span><span class="sxs-lookup"><span data-stu-id="02b17-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="02b17-104">Constructeurs de ligne</span><span class="sxs-lookup"><span data-stu-id="02b17-104">Row Constructors</span></span>  
 <span data-ttu-id="02b17-105">Les constructeurs de ligne s'avèrent utiles dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour construire des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="02b17-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="02b17-106">Le type de résultat d'un constructeur de ligne est un type de ligne dont les types de champs correspondent aux types des valeurs qui ont servi à construire la ligne.</span><span class="sxs-lookup"><span data-stu-id="02b17-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="02b17-107">Par exemple, l’expression suivante construit une valeur de type `Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="02b17-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="02b17-108">Si vous ne fournissez pas d'alias pour une expression contenue dans un constructeur de ligne, Entity Framework essaie d'en générer un.</span><span class="sxs-lookup"><span data-stu-id="02b17-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="02b17-109">Pour plus d’informations, consultez la section « Règles d’alias » dans [identificateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="02b17-109">For more information, see the "Aliasing Rules" section in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="02b17-110">Les règles suivantes s'appliquent à l'utilisation d'alias dans les expressions d'un constructeur de ligne :</span><span class="sxs-lookup"><span data-stu-id="02b17-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="02b17-111">les expressions contenues dans un constructeur de ligne ne peuvent pas faire référence aux autres alias du même constructeur ;</span><span class="sxs-lookup"><span data-stu-id="02b17-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="02b17-112">deux expressions contenues dans un même constructeur de ligne ne peuvent pas avoir le même alias.</span><span class="sxs-lookup"><span data-stu-id="02b17-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="02b17-113">Pour plus d’informations sur les constructeurs de ligne, consultez [ligne](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="02b17-113">For more information about row constructors, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="02b17-114">Constructeurs de collection</span><span class="sxs-lookup"><span data-stu-id="02b17-114">Collection Constructors</span></span>  
 <span data-ttu-id="02b17-115">Les constructeurs de collection dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permettent de créer une instance d’un multiensemble à partir d’une liste de valeurs.</span><span class="sxs-lookup"><span data-stu-id="02b17-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="02b17-116">Toutes les valeurs du constructeur doivent être de type `T` mutuellement compatible et le constructeur produit une collection de type `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="02b17-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="02b17-117">Par exemple, l'expression suivante crée une collection d'entiers :</span><span class="sxs-lookup"><span data-stu-id="02b17-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="02b17-118">Les constructeurs multiensembles vides ne sont pas autorisés, car le type des éléments ne peut pas être déterminé.</span><span class="sxs-lookup"><span data-stu-id="02b17-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="02b17-119">L'exemple suivant n'est pas valide :</span><span class="sxs-lookup"><span data-stu-id="02b17-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="02b17-120">Pour plus d’informations, consultez [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="02b17-120">For more information, see [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="02b17-121">Constructeurs de type nommé (initialiseurs NamedType)</span><span class="sxs-lookup"><span data-stu-id="02b17-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="02b17-122">permet aux constructeurs de type (initialiseurs) de créer des instances de types complexes nommés et de types d'entités.</span><span class="sxs-lookup"><span data-stu-id="02b17-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="02b17-123">Par exemple, l'expression suivante crée une instance d'un type `Person`.</span><span class="sxs-lookup"><span data-stu-id="02b17-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="02b17-124">L'expression suivante crée une instance d'un type complexe.</span><span class="sxs-lookup"><span data-stu-id="02b17-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="02b17-125">L'expression suivante crée une instance d'un type complexe imbriqué.</span><span class="sxs-lookup"><span data-stu-id="02b17-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="02b17-126">L'expression suivante crée une instance d'une entité avec un type complexe imbriqué.</span><span class="sxs-lookup"><span data-stu-id="02b17-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="02b17-127">L'exemple suivant montre comment initialiser une propriété d'un type complexe en valeur Null.</span><span class="sxs-lookup"><span data-stu-id="02b17-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="02b17-128">Les arguments passés au constructeur sont supposés se trouver dans le même ordre que dans la déclaration des attributs du type.</span><span class="sxs-lookup"><span data-stu-id="02b17-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="02b17-129">Pour plus d’informations, consultez [constructeur de Type nommé](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="02b17-129">For more information, see [Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b17-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02b17-130">See also</span></span>

- [<span data-ttu-id="02b17-131">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="02b17-131">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="02b17-132">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="02b17-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="02b17-133">Système de type</span><span class="sxs-lookup"><span data-stu-id="02b17-133">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
