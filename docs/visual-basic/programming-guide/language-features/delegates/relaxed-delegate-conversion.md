---
title: Conversion simplifiée des délégués
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: b914d0479f160199744a8f9923c0bebc87321329
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086073"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="d679c-102">Conversion simplifiée des délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d679c-102">Relaxed Delegate Conversion (Visual Basic)</span></span>

<span data-ttu-id="d679c-103">La conversion souple des délégués vous permet d’assigner des fonctions et des fonctions aux délégués ou aux gestionnaires même lorsque leurs signatures ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="d679c-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="d679c-104">Par conséquent, la liaison aux délégués devient cohérente avec la liaison déjà autorisée pour les appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="d679c-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="d679c-105">Paramètres et type de retour</span><span class="sxs-lookup"><span data-stu-id="d679c-105">Parameters and Return Type</span></span>  

 <span data-ttu-id="d679c-106">Au lieu de la correspondance exacte de signature, la conversion souple exige que les conditions suivantes soient remplies lorsque `Option Strict` a la valeur `On` :</span><span class="sxs-lookup"><span data-stu-id="d679c-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="d679c-107">Une conversion étendue doit exister à partir du type de données de chaque paramètre délégué vers le type de données du paramètre correspondant de la fonction affectée ou de `Sub` .</span><span class="sxs-lookup"><span data-stu-id="d679c-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="d679c-108">Dans l’exemple suivant, le délégué `Del1` a un paramètre, un `Integer` .</span><span class="sxs-lookup"><span data-stu-id="d679c-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="d679c-109">`m`Le paramètre dans les expressions lambda affectées doit avoir un type de données pour lequel il existe une conversion étendue à partir de `Integer` , tel que `Long` ou `Double` .</span><span class="sxs-lookup"><span data-stu-id="d679c-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="d679c-110">Les conversions restrictives sont autorisées uniquement lorsque `Option Strict` a la valeur `Off` .</span><span class="sxs-lookup"><span data-stu-id="d679c-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="d679c-111">Une conversion étendue doit exister dans la direction opposée du type de retour de la fonction affectée ou `Sub` au type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="d679c-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="d679c-112">Dans les exemples suivants, le corps de chaque expression lambda assignée doit correspondre à un type de données qui s’étend à `Integer` parce que le type de retour de `del1` est `Integer` .</span><span class="sxs-lookup"><span data-stu-id="d679c-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="d679c-113">Si `Option Strict` a la valeur `Off` , la restriction étendue est supprimée dans les deux directions.</span><span class="sxs-lookup"><span data-stu-id="d679c-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="d679c-114">Omission de spécifications de paramètres</span><span class="sxs-lookup"><span data-stu-id="d679c-114">Omitting Parameter Specifications</span></span>  

 <span data-ttu-id="d679c-115">Les délégués souples vous permettent également d’omettre complètement les spécifications de paramètres dans la méthode assignée :</span><span class="sxs-lookup"><span data-stu-id="d679c-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="d679c-116">Notez que vous ne pouvez pas spécifier certains paramètres et omettre d’autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="d679c-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="d679c-117">La possibilité d’omettre des paramètres est utile dans une situation telle que la définition d’un gestionnaire d’événements, où plusieurs paramètres complexes sont impliqués.</span><span class="sxs-lookup"><span data-stu-id="d679c-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="d679c-118">Les arguments de certains gestionnaires d’événements ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="d679c-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="d679c-119">Au lieu de cela, le gestionnaire accède directement à l’état du contrôle sur lequel l’événement est inscrit et ignore les arguments.</span><span class="sxs-lookup"><span data-stu-id="d679c-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="d679c-120">Les délégués souples vous permettent d’omettre les arguments dans ces déclarations quand aucune ambiguïté ne résulte.</span><span class="sxs-lookup"><span data-stu-id="d679c-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="d679c-121">Dans l’exemple suivant, la méthode entièrement spécifiée `OnClick` peut être réécrite sous la forme `RelaxedOnClick` .</span><span class="sxs-lookup"><span data-stu-id="d679c-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="d679c-122">Exemples AddressOf</span><span class="sxs-lookup"><span data-stu-id="d679c-122">AddressOf Examples</span></span>  

 <span data-ttu-id="d679c-123">Les expressions lambda sont utilisées dans les exemples précédents pour faciliter la consultation des relations de type.</span><span class="sxs-lookup"><span data-stu-id="d679c-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="d679c-124">Toutefois, les mêmes assouplissements sont autorisées pour les assignations de délégué qui utilisent `AddressOf` , `Handles` ou `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="d679c-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="d679c-125">Dans l’exemple suivant, `f1` les fonctions,, `f2` `f3` et `f4` peuvent toutes être assignées à `Del1` .</span><span class="sxs-lookup"><span data-stu-id="d679c-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="d679c-126">L’exemple suivant est valide uniquement lorsque `Option Strict` a la valeur `Off` .</span><span class="sxs-lookup"><span data-stu-id="d679c-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="d679c-127">Suppression des retours de fonction</span><span class="sxs-lookup"><span data-stu-id="d679c-127">Dropping Function Returns</span></span>  

 <span data-ttu-id="d679c-128">La conversion souple des délégués vous permet d’assigner une fonction à un `Sub` délégué, en ignorant la valeur de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d679c-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="d679c-129">Toutefois, vous ne pouvez pas assigner un `Sub` à un délégué de fonction.</span><span class="sxs-lookup"><span data-stu-id="d679c-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="d679c-130">Dans l’exemple suivant, l’adresse de la fonction `doubler` est assignée au `Sub` délégué `Del3` .</span><span class="sxs-lookup"><span data-stu-id="d679c-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="d679c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d679c-131">See also</span></span>

- [<span data-ttu-id="d679c-132">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="d679c-132">Lambda Expressions</span></span>](../procedures/lambda-expressions.md)
- [<span data-ttu-id="d679c-133">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="d679c-133">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="d679c-134">Délégués</span><span class="sxs-lookup"><span data-stu-id="d679c-134">Delegates</span></span>](index.md)
- [<span data-ttu-id="d679c-135">Comment : passer des procédures à une autre procédure en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d679c-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="d679c-136">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="d679c-136">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="d679c-137">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="d679c-137">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
