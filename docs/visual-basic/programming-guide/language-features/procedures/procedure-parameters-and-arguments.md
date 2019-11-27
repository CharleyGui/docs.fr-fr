---
title: Paramètres et arguments d’une procédure
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352579"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="d9213-102">Paramètres et arguments d’une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9213-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="d9213-103">Dans la plupart des cas, une procédure a besoin d’informations sur les circonstances dans lesquelles elle a été appelée.</span><span class="sxs-lookup"><span data-stu-id="d9213-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="d9213-104">Une procédure qui exécute des tâches répétitives ou partagées utilise des informations différentes pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="d9213-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="d9213-105">Ces informations se composent de variables, de constantes et d’expressions que vous transmettez à la procédure lorsque vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="d9213-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="d9213-106">Un *paramètre* représente une valeur que la procédure vous attend à fournir lorsque vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="d9213-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="d9213-107">La déclaration de la procédure définit ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="d9213-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="d9213-108">Vous pouvez définir une procédure sans paramètres, un paramètre ou plusieurs.</span><span class="sxs-lookup"><span data-stu-id="d9213-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="d9213-109">La partie de la définition de procédure qui spécifie les paramètres est appelée *liste de paramètres*.</span><span class="sxs-lookup"><span data-stu-id="d9213-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="d9213-110">Un *argument* représente la valeur que vous fournissez à un paramètre de procédure lorsque vous appelez la procédure.</span><span class="sxs-lookup"><span data-stu-id="d9213-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="d9213-111">Le code appelant fournit les arguments lorsqu’il appelle la procédure.</span><span class="sxs-lookup"><span data-stu-id="d9213-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="d9213-112">La partie de l’appel de procédure qui spécifie les arguments est appelée *liste d’arguments*.</span><span class="sxs-lookup"><span data-stu-id="d9213-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="d9213-113">L’illustration suivante montre le code appelant la procédure `safeSquareRoot` à partir de deux emplacements différents.</span><span class="sxs-lookup"><span data-stu-id="d9213-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="d9213-114">Le premier appel passe la valeur de la variable `x` (4,0) au paramètre `number`, et la valeur de retour dans `root` (2,0) est assignée à la variable `y`.</span><span class="sxs-lookup"><span data-stu-id="d9213-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="d9213-115">Le deuxième appel passe la valeur littérale 9,0 à `number`et affecte la valeur de retour (3,0) à la variable `z`.</span><span class="sxs-lookup"><span data-stu-id="d9213-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Diagramme qui illustre le passage d’un argument à un paramètre](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="d9213-117">Pour plus d’informations, consultez [différences entre les paramètres et les arguments](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d9213-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="d9213-118">Type de données du paramètre</span><span class="sxs-lookup"><span data-stu-id="d9213-118">Parameter Data Type</span></span>  
 <span data-ttu-id="d9213-119">Vous définissez un type de données pour un paramètre à l’aide de la clause `As` dans sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="d9213-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="d9213-120">Par exemple, la fonction suivante accepte une chaîne et un entier.</span><span class="sxs-lookup"><span data-stu-id="d9213-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="d9213-121">Si le commutateur de vérification de type ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `Off,` la clause `As` est facultative, mais si un paramètre l’utilise, tous les paramètres doivent l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="d9213-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="d9213-122">Si la vérification de type est `On`, la clause `As` est requise pour tous les paramètres de procédure.</span><span class="sxs-lookup"><span data-stu-id="d9213-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="d9213-123">Si le code appelant s’attend à fournir un argument avec un type de données différent de celui de son paramètre correspondant, par exemple `Byte` à un paramètre `String`, il doit effectuer l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d9213-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="d9213-124">Fournissez uniquement des arguments avec des types de données qui s’étendent au type de données du paramètre ;</span><span class="sxs-lookup"><span data-stu-id="d9213-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="d9213-125">Définissez `Option Strict Off` pour autoriser les conversions restrictives implicites ; ni</span><span class="sxs-lookup"><span data-stu-id="d9213-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="d9213-126">Utilisez un mot clé de conversion pour convertir explicitement le type de données.</span><span class="sxs-lookup"><span data-stu-id="d9213-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="d9213-127">Paramètres de type</span><span class="sxs-lookup"><span data-stu-id="d9213-127">Type Parameters</span></span>  
 <span data-ttu-id="d9213-128">Une *procédure générique* définit également un ou plusieurs *paramètres de type* en plus de ses paramètres normaux.</span><span class="sxs-lookup"><span data-stu-id="d9213-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="d9213-129">Une procédure générique permet au code appelant de passer différents types de données chaque fois qu’il appelle la procédure. il peut donc adapter les types de données aux exigences de chaque appel individuel.</span><span class="sxs-lookup"><span data-stu-id="d9213-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="d9213-130">Consultez [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d9213-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9213-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9213-131">See also</span></span>

- [<span data-ttu-id="d9213-132">Procédures</span><span class="sxs-lookup"><span data-stu-id="d9213-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d9213-133">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="d9213-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="d9213-134">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="d9213-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="d9213-135">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="d9213-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d9213-136">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="d9213-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d9213-137">Guide pratique : définir un paramètre pour une procédure</span><span class="sxs-lookup"><span data-stu-id="d9213-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="d9213-138">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="d9213-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="d9213-139">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="d9213-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d9213-140">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="d9213-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="d9213-141">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9213-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
