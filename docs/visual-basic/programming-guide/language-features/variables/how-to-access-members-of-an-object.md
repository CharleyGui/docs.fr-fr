---
title: 'Procédure : Accéder aux membres d’un objet (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 882046b829ade2da7c10b3db4c0d6c9ca9f3d579
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630832"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="19dd6-102">Procédure : Accéder aux membres d’un objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19dd6-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="19dd6-103">Quand vous avez une variable objet qui fait référence à un objet, vous souhaitez souvent travailler avec les membres de cet objet, tels que ses méthodes, propriétés, champs et événements.</span><span class="sxs-lookup"><span data-stu-id="19dd6-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="19dd6-104">Par exemple, une fois que vous avez créé <xref:System.Windows.Forms.Form> un nouvel objet, vous pouvez définir sa <xref:System.Windows.Forms.Control.Text%2A> propriété ou appeler sa <xref:System.Windows.Forms.Control.Focus%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="19dd6-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="19dd6-105">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="19dd6-105">Accessing Members</span></span>

<span data-ttu-id="19dd6-106">Vous accédez aux membres d’un objet par le biais de la variable qui y fait référence.</span><span class="sxs-lookup"><span data-stu-id="19dd6-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="19dd6-107">Pour accéder aux membres d’un objet</span><span class="sxs-lookup"><span data-stu-id="19dd6-107">To access members of an object</span></span>

- <span data-ttu-id="19dd6-108">Utilisez l’opérateur d’accès aux membres`.`() entre le nom de la variable objet et le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="19dd6-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="19dd6-109">Si le membre est [partagé](../../../../visual-basic/language-reference/modifiers/shared.md), vous n’avez pas besoin d’une variable pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="19dd6-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="19dd6-110">Accès aux membres d’un objet de type connu</span><span class="sxs-lookup"><span data-stu-id="19dd6-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="19dd6-111">Si vous connaissez le type d’un objet au moment de la compilation, vous pouvez utiliser la *liaison précoce* pour une variable qui y fait référence.</span><span class="sxs-lookup"><span data-stu-id="19dd6-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="19dd6-112">Pour accéder aux membres d’un objet pour lequel vous connaissez le type au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="19dd6-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="19dd6-113">Déclarez la variable objet comme étant du type de l’objet que vous souhaitez assigner à la variable.</span><span class="sxs-lookup"><span data-stu-id="19dd6-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="19dd6-114">Avec `Option Strict On`, vous pouvez assigner uniquement <xref:System.Windows.Forms.Form> des objets (ou des objets d' <xref:System.Windows.Forms.Form>un type `extraForm`dérivé de) à.</span><span class="sxs-lookup"><span data-stu-id="19dd6-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="19dd6-115">Si vous avez défini une classe ou une structure avec une `CType` conversion étendue en <xref:System.Windows.Forms.Form>, vous pouvez également assigner cette classe ou structure à. `extraForm`</span><span class="sxs-lookup"><span data-stu-id="19dd6-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="19dd6-116">Utilisez l’opérateur d’accès aux membres`.`() entre le nom de la variable objet et le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="19dd6-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="19dd6-117">Vous pouvez accéder à toutes les méthodes et propriétés spécifiques à la <xref:System.Windows.Forms.Form> classe, quel que soit le `Option Strict` paramètre.</span><span class="sxs-lookup"><span data-stu-id="19dd6-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="19dd6-118">Accès aux membres d’un objet de type inconnu</span><span class="sxs-lookup"><span data-stu-id="19dd6-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="19dd6-119">Si vous ne connaissez pas le type d’un objet au moment de la compilation, vous devez utiliser la *liaison tardive* pour toute variable qui y fait référence.</span><span class="sxs-lookup"><span data-stu-id="19dd6-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="19dd6-120">Pour accéder aux membres d’un objet pour lequel vous ne connaissez pas le type au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="19dd6-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="19dd6-121">Déclarez la variable objet comme étant du [type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="19dd6-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="19dd6-122">(Déclarer une variable comme `Object` étant identique à la déclarer comme <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="19dd6-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="19dd6-123">Avec `Option Strict On`, vous pouvez accéder uniquement aux membres qui sont définis sur la <xref:System.Object> classe.</span><span class="sxs-lookup"><span data-stu-id="19dd6-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="19dd6-124">Utilisez l’opérateur d’accès aux membres`.`() entre le nom de la variable objet et le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="19dd6-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="19dd6-125">Pour pouvoir accéder aux membres de n’importe quel objet que vous affectez à la variable objet, vous `Option Strict Off`devez définir.</span><span class="sxs-lookup"><span data-stu-id="19dd6-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="19dd6-126">Dans ce cas, le compilateur ne peut pas garantir qu’un membre donné est exposé par l’objet que vous affectez à la variable.</span><span class="sxs-lookup"><span data-stu-id="19dd6-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="19dd6-127">Si l’objet n’expose pas un membre auquel vous essayez d’accéder <xref:System.MemberAccessException> , une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="19dd6-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="19dd6-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19dd6-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="19dd6-129">Variables objets</span><span class="sxs-lookup"><span data-stu-id="19dd6-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="19dd6-130">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="19dd6-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="19dd6-131">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="19dd6-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="19dd6-132">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="19dd6-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
