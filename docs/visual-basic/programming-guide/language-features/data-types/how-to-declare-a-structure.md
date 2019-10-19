---
title: 'Comment : déclarer une structure (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: c3090b5b8e53e5a5a990ae11c91464797bde9803
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582303"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="6b465-102">Comment : déclarer une structure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b465-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="6b465-103">Vous commencez une déclaration de structure par l' [instruction structure](../../../../visual-basic/language-reference/statements/structure-statement.md)et vous la terminez par l’instruction `End Structure`.</span><span class="sxs-lookup"><span data-stu-id="6b465-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="6b465-104">Entre ces deux instructions, vous devez déclarer au moins un *élément*.</span><span class="sxs-lookup"><span data-stu-id="6b465-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="6b465-105">Les éléments peuvent être de n’importe quel type de données, mais au moins un doit être une variable non partagée ou un événement non personnalisé non partagé.</span><span class="sxs-lookup"><span data-stu-id="6b465-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="6b465-106">Vous ne pouvez pas initialiser l’un des éléments de structure dans la déclaration de structure.</span><span class="sxs-lookup"><span data-stu-id="6b465-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="6b465-107">Quand vous déclarez une variable comme étant d’un type structure, vous assignez des valeurs aux éléments en y accédant via la variable.</span><span class="sxs-lookup"><span data-stu-id="6b465-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="6b465-108">Pour plus d’informations sur les différences entre les structures et les classes, consultez [structures et classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="6b465-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="6b465-109">À des fins de démonstration, envisagez une situation dans laquelle vous souhaitez effectuer le suivi du nom, de l’extension téléphonique et du salaire d’un employé.</span><span class="sxs-lookup"><span data-stu-id="6b465-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="6b465-110">Une structure vous permet d’effectuer cette opération dans une variable unique.</span><span class="sxs-lookup"><span data-stu-id="6b465-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="6b465-111">Pour déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="6b465-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="6b465-112">Créez les instructions de début et de fin pour la structure.</span><span class="sxs-lookup"><span data-stu-id="6b465-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="6b465-113">Vous pouvez spécifier le niveau d’accès d’une structure à l’aide du mot clé [public](../../../../visual-basic/language-reference/modifiers/public.md), [protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)ou [Private](../../../../visual-basic/language-reference/modifiers/private.md) , ou vous pouvez laisser la valeur par défaut `Public`.</span><span class="sxs-lookup"><span data-stu-id="6b465-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="6b465-114">Ajoutez des éléments au corps de la structure.</span><span class="sxs-lookup"><span data-stu-id="6b465-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="6b465-115">Une structure doit avoir au moins un élément.</span><span class="sxs-lookup"><span data-stu-id="6b465-115">A structure must have at least one element.</span></span> <span data-ttu-id="6b465-116">Vous devez déclarer chaque élément et spécifier un niveau d’accès pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="6b465-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="6b465-117">Si vous utilisez l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sans mot clé, l’accessibilité a pour valeur par défaut `Public`.</span><span class="sxs-lookup"><span data-stu-id="6b465-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="6b465-118">Le champ `salary` dans l’exemple précédent est `Private`, ce qui signifie qu’il est inaccessible en dehors de la structure, même à partir de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="6b465-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="6b465-119">Toutefois, la procédure `giveRaise` est `Public` et peut donc être appelée à partir de l’extérieur de la structure.</span><span class="sxs-lookup"><span data-stu-id="6b465-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="6b465-120">De même, vous pouvez déclencher l’événement `salaryReviewTime` à partir de l’extérieur de la structure.</span><span class="sxs-lookup"><span data-stu-id="6b465-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="6b465-121">En plus des variables, des procédures `Sub` et des événements, vous pouvez également définir des constantes, des procédures `Function` et des propriétés dans une structure.</span><span class="sxs-lookup"><span data-stu-id="6b465-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="6b465-122">Vous pouvez désigner au plus une propriété comme *propriété par défaut*, à condition qu’elle prenne au moins un argument.</span><span class="sxs-lookup"><span data-stu-id="6b465-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="6b465-123">Vous pouvez gérer un événement à l’aide d’une procédure de `Sub` [partagée](../../../../visual-basic/language-reference/modifiers/shared.md) .</span><span class="sxs-lookup"><span data-stu-id="6b465-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="6b465-124">Pour plus d’informations, consultez [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="6b465-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b465-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b465-125">See also</span></span>

- [<span data-ttu-id="6b465-126">Types de données</span><span class="sxs-lookup"><span data-stu-id="6b465-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="6b465-127">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="6b465-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="6b465-128">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="6b465-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="6b465-129">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="6b465-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="6b465-130">Structures</span><span class="sxs-lookup"><span data-stu-id="6b465-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6b465-131">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="6b465-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="6b465-132">Variables de structure</span><span class="sxs-lookup"><span data-stu-id="6b465-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="6b465-133">Structures et autres éléments de programmation</span><span class="sxs-lookup"><span data-stu-id="6b465-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="6b465-134">Structures et classes</span><span class="sxs-lookup"><span data-stu-id="6b465-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="6b465-135">Type de données défini par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="6b465-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
