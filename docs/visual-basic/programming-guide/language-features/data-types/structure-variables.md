---
title: Variables de structure (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: a86a60def9ac1b8140194ecb6f5e784c62a0e101
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630971"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="0b280-102">Variables de structure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b280-102">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="0b280-103">Une fois que vous avez créé une structure, vous pouvez déclarer des variables au niveau de la procédure et au niveau du module comme ce type.</span><span class="sxs-lookup"><span data-stu-id="0b280-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="0b280-104">Par exemple, vous pouvez créer une structure qui enregistre des informations sur un système informatique.</span><span class="sxs-lookup"><span data-stu-id="0b280-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="0b280-105">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0b280-105">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="0b280-106">Vous pouvez maintenant déclarer des variables de ce type.</span><span class="sxs-lookup"><span data-stu-id="0b280-106">You can now declare variables of that type.</span></span> <span data-ttu-id="0b280-107">La déclaration suivante illustre cela.</span><span class="sxs-lookup"><span data-stu-id="0b280-107">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="0b280-108">Dans les classes et les modules, les structures déclarées à l’aide de l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) utilisent par défaut l’accès public.</span><span class="sxs-lookup"><span data-stu-id="0b280-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="0b280-109">Si vous envisagez de disposer d’une structure privée, assurez-vous de la déclarer à l’aide du mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md) .</span><span class="sxs-lookup"><span data-stu-id="0b280-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="0b280-110">Accès aux valeurs de structure</span><span class="sxs-lookup"><span data-stu-id="0b280-110">Access to Structure Values</span></span>

<span data-ttu-id="0b280-111">Pour assigner et récupérer des valeurs à partir des éléments d’une variable de structure, vous utilisez la même syntaxe que celle utilisée pour définir et obtenir des propriétés sur un objet.</span><span class="sxs-lookup"><span data-stu-id="0b280-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="0b280-112">Vous placez l’opérateur d’accès aux`.`membres () entre le nom de la variable de structure et le nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0b280-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="0b280-113">L’exemple suivant accède aux éléments des variables précédemment déclarées en tant `systemInfo`que type.</span><span class="sxs-lookup"><span data-stu-id="0b280-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="0b280-114">Affectation de variables de structure</span><span class="sxs-lookup"><span data-stu-id="0b280-114">Assigning Structure Variables</span></span>

<span data-ttu-id="0b280-115">Vous pouvez également assigner une variable à une autre si les deux sont du même type de structure.</span><span class="sxs-lookup"><span data-stu-id="0b280-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="0b280-116">Cela permet de copier tous les éléments d’une structure dans les éléments correspondants de l’autre.</span><span class="sxs-lookup"><span data-stu-id="0b280-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="0b280-117">La déclaration suivante illustre cela.</span><span class="sxs-lookup"><span data-stu-id="0b280-117">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="0b280-118">Si un élément de structure est un type référence, tel qu' `String`un `Object`tableau, ou, le pointeur vers les données est copié.</span><span class="sxs-lookup"><span data-stu-id="0b280-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="0b280-119">Dans l’exemple précédent, si `systemInfo` avait inclus une variable objet, l’exemple précédent aurait copié le pointeur de `mySystem` vers `yourSystem`, et une modification apportée aux données de l’objet par le biais d’une structure serait appliquée lors de l’accès par le biais de l’autre structure.</span><span class="sxs-lookup"><span data-stu-id="0b280-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b280-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b280-120">See also</span></span>

- [<span data-ttu-id="0b280-121">Types de données</span><span class="sxs-lookup"><span data-stu-id="0b280-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="0b280-122">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="0b280-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="0b280-123">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="0b280-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="0b280-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="0b280-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="0b280-125">Structures</span><span class="sxs-lookup"><span data-stu-id="0b280-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0b280-126">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="0b280-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="0b280-127">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="0b280-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="0b280-128">Structures et autres éléments de programmation</span><span class="sxs-lookup"><span data-stu-id="0b280-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="0b280-129">Structures et classes</span><span class="sxs-lookup"><span data-stu-id="0b280-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="0b280-130">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="0b280-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
