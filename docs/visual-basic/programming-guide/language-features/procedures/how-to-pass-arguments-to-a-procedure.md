---
title: 'Comment : passer des arguments à une procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 903e05facccd1f2afdf4bb51b200531feb64aa79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387775"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="7ba34-102">Comment : passer des arguments à une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ba34-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="7ba34-103">Lorsque vous appelez une procédure, vous devez suivre le nom de la procédure avec une liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7ba34-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="7ba34-104">Vous fournissez un argument correspondant à chaque paramètre requis que la procédure définit et vous pouvez éventuellement fournir des arguments aux `Optional` paramètres.</span><span class="sxs-lookup"><span data-stu-id="7ba34-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="7ba34-105">Si vous ne fournissez pas `Optional` de paramètre dans l’appel, vous devez inclure une virgule pour marquer son emplacement dans la liste d’arguments si vous fournissez des arguments suivants.</span><span class="sxs-lookup"><span data-stu-id="7ba34-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="7ba34-106">Si vous envisagez de passer un argument d’un type de données différent de celui de son paramètre correspondant, par exemple `Byte` à `String` , vous pouvez définir le commutateur de vérification de type ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) sur `Off` .</span><span class="sxs-lookup"><span data-stu-id="7ba34-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="7ba34-107">Si `Option Strict` est `On` , vous devez utiliser des conversions étendues ou des mots clés de conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="7ba34-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="7ba34-108">Pour plus d’informations, consultez [conversions étendues et restrictives](../data-types/widening-and-narrowing-conversions.md) et [fonctions de conversion de type](../../../language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="7ba34-108">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="7ba34-109">Pour plus d’informations, consultez [paramètres et arguments](./procedure-parameters-and-arguments.md)d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="7ba34-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="7ba34-110">Pour passer un ou plusieurs arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="7ba34-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="7ba34-111">Dans l’instruction appelante, suivez le nom de la procédure avec des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7ba34-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="7ba34-112">À l’intérieur des parenthèses, placez une liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="7ba34-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="7ba34-113">Incluez un argument pour chaque paramètre requis que la procédure définit et séparez les arguments par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7ba34-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="7ba34-114">Vérifiez que chaque argument est une expression valide qui prend la valeur d’un type de données convertible en type défini par la procédure pour le paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="7ba34-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="7ba34-115">Si un paramètre est défini comme [facultatif](../../../language-reference/modifiers/optional.md), vous pouvez l’inclure dans la liste d’arguments ou l’omettre.</span><span class="sxs-lookup"><span data-stu-id="7ba34-115">If a parameter is defined as [Optional](../../../language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="7ba34-116">Si vous l’omettez, la procédure utilise la valeur par défaut définie pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="7ba34-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="7ba34-117">Si vous omettez un argument pour un `Optional` paramètre et qu’il existe un autre paramètre après celui-ci dans la liste de paramètres, vous pouvez marquer la place de l’argument omis par une virgule supplémentaire dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="7ba34-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="7ba34-118">L’exemple suivant appelle la <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> fonction Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7ba34-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="7ba34-119">L’exemple précédent fournit le premier argument requis, qui est la chaîne de message à afficher.</span><span class="sxs-lookup"><span data-stu-id="7ba34-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="7ba34-120">Il omet un argument pour le deuxième paramètre facultatif, qui spécifie les boutons à afficher dans la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="7ba34-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="7ba34-121">Étant donné que l’appel ne fournit pas de valeur, `MsgBox` utilise la valeur par défaut, `MsgBoxStyle.OKOnly` , qui affiche uniquement un bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="7ba34-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="7ba34-122">La deuxième virgule de la liste d’arguments marque l’emplacement du deuxième argument omis et la dernière chaîne est passée au troisième paramètre facultatif de `MsgBox` , qui est le texte à afficher dans la barre de titre.</span><span class="sxs-lookup"><span data-stu-id="7ba34-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba34-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ba34-123">See also</span></span>

- [<span data-ttu-id="7ba34-124">Sub, procédures</span><span class="sxs-lookup"><span data-stu-id="7ba34-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="7ba34-125">Function, procédures</span><span class="sxs-lookup"><span data-stu-id="7ba34-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="7ba34-126">Procédures Property</span><span class="sxs-lookup"><span data-stu-id="7ba34-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="7ba34-127">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="7ba34-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="7ba34-128">Comment : définir un paramètre pour une procédure</span><span class="sxs-lookup"><span data-stu-id="7ba34-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="7ba34-129">Passage des arguments par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="7ba34-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="7ba34-130">Procédures récursives</span><span class="sxs-lookup"><span data-stu-id="7ba34-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="7ba34-131">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="7ba34-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="7ba34-132">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="7ba34-132">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="7ba34-133">Programmation orientée objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ba34-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
