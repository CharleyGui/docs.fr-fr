---
title: 'Procédure : Déclarer une structure'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a6b70d0973e92db90e35e61b7fed2279c5b0bac3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393972"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="5a9ee-102">Comment : déclarer une structure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a9ee-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="5a9ee-103">Vous commencez une déclaration de structure par l' [instruction structure](../../../language-reference/statements/structure-statement.md)et vous la terminez par l' `End Structure` instruction.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-103">You begin a structure declaration with the [Structure Statement](../../../language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="5a9ee-104">Entre ces deux instructions, vous devez déclarer au moins un *élément*.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="5a9ee-105">Les éléments peuvent être de n’importe quel type de données, mais au moins un doit être une variable non partagée ou un événement non personnalisé non partagé.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="5a9ee-106">Vous ne pouvez pas initialiser l’un des éléments de structure dans la déclaration de structure.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="5a9ee-107">Quand vous déclarez une variable comme étant d’un type structure, vous assignez des valeurs aux éléments en y accédant via la variable.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="5a9ee-108">Pour plus d’informations sur les différences entre les structures et les classes, consultez [structures et classes](structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5a9ee-108">For a discussion of the differences between structures and classes, see [Structures and Classes](structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="5a9ee-109">À des fins de démonstration, envisagez une situation dans laquelle vous souhaitez effectuer le suivi du nom, de l’extension téléphonique et du salaire d’un employé.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="5a9ee-110">Une structure vous permet d’effectuer cette opération dans une variable unique.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="5a9ee-111">Pour déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="5a9ee-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="5a9ee-112">Créez les instructions de début et de fin pour la structure.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="5a9ee-113">Vous pouvez spécifier le niveau d’accès d’une structure à l’aide du mot clé [public](../../../language-reference/modifiers/public.md), [protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)ou [Private](../../../language-reference/modifiers/private.md) , ou vous pouvez laisser la valeur par défaut `Public` .</span><span class="sxs-lookup"><span data-stu-id="5a9ee-113">You can specify the access level of a structure using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="5a9ee-114">Ajoutez des éléments au corps de la structure.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="5a9ee-115">Une structure doit avoir au moins un élément.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-115">A structure must have at least one element.</span></span> <span data-ttu-id="5a9ee-116">Vous devez déclarer chaque élément et spécifier un niveau d’accès pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="5a9ee-117">Si vous utilisez l' [instruction Dim](../../../language-reference/statements/dim-statement.md) sans mot clé, l’accessibilité est par défaut `Public` .</span><span class="sxs-lookup"><span data-stu-id="5a9ee-117">If you use the [Dim Statement](../../../language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
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
  
     <span data-ttu-id="5a9ee-118">Le `salary` champ dans l’exemple précédent est `Private` , ce qui signifie qu’il est inaccessible en dehors de la structure, même à partir de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="5a9ee-119">Toutefois, la `giveRaise` procédure est `Public` . elle peut donc être appelée à partir de l’extérieur de la structure.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="5a9ee-120">De même, vous pouvez déclencher l' `salaryReviewTime` événement à l’extérieur de la structure.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="5a9ee-121">Outre les variables, `Sub` les procédures et les événements, vous pouvez également définir des constantes, des `Function` procédures et des propriétés dans une structure.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="5a9ee-122">Vous pouvez désigner au plus une propriété comme *propriété par défaut*, à condition qu’elle prenne au moins un argument.</span><span class="sxs-lookup"><span data-stu-id="5a9ee-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="5a9ee-123">Vous pouvez gérer un événement avec une procédure [partagée](../../../language-reference/modifiers/shared.md) `Sub` .</span><span class="sxs-lookup"><span data-stu-id="5a9ee-123">You can handle an event with a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="5a9ee-124">Pour plus d’informations, consultez [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="5a9ee-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a9ee-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a9ee-125">See also</span></span>

- [<span data-ttu-id="5a9ee-126">Types de données</span><span class="sxs-lookup"><span data-stu-id="5a9ee-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="5a9ee-127">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="5a9ee-127">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="5a9ee-128">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="5a9ee-128">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="5a9ee-129">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="5a9ee-129">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="5a9ee-130">Structures</span><span class="sxs-lookup"><span data-stu-id="5a9ee-130">Structures</span></span>](structures.md)
- [<span data-ttu-id="5a9ee-131">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="5a9ee-131">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="5a9ee-132">Variables de structure</span><span class="sxs-lookup"><span data-stu-id="5a9ee-132">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="5a9ee-133">Structures et autres éléments de programmation</span><span class="sxs-lookup"><span data-stu-id="5a9ee-133">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="5a9ee-134">Structures et classes</span><span class="sxs-lookup"><span data-stu-id="5a9ee-134">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="5a9ee-135">Type de données défini par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5a9ee-135">User-Defined Data Type</span></span>](../../../language-reference/data-types/user-defined-data-type.md)
