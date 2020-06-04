---
title: La copie de la valeur du paramètre 'ByRef' '<parametername>' dans l'argument correspondant passe du type '<typename1>' au type '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: bac5f9a88df719bc64a8b0541f65e5912275866e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409749"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a><span data-ttu-id="5aa81-102">La copie de la valeur du paramètre 'ByRef' '\<parametername>' dans l'argument correspondant passe du type '\<typename1>' au type '\<typename2>'</span><span class="sxs-lookup"><span data-stu-id="5aa81-102">Copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument narrows from type '\<typename1>' to type '\<typename2>'</span></span>
<span data-ttu-id="5aa81-103">Une procédure est appelée avec un argument qui s’étend au type de paramètre correspondant, et la conversion du paramètre en argument est restrictive.</span><span class="sxs-lookup"><span data-stu-id="5aa81-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="5aa81-104">Quand vous définissez une classe ou une structure, vous pouvez définir un ou plusieurs opérateurs de conversion pour convertir le type de la classe ou de la structure en d’autres types.</span><span class="sxs-lookup"><span data-stu-id="5aa81-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="5aa81-105">Vous pouvez également définir des opérateurs de conversion inverse pour convertir ces autres types vers le type de votre classe ou de votre structure.</span><span class="sxs-lookup"><span data-stu-id="5aa81-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="5aa81-106">Quand vous utilisez votre type de classe ou de structure dans un appel de procédure, Visual Basic pouvez utiliser ces opérateurs de conversion pour convertir le type d’un argument vers le type de son paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="5aa81-106">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="5aa81-107">Si vous passez l’argument [ByRef](../modifiers/byref.md), Visual Basic copie parfois la valeur de l’argument dans une variable locale de la procédure au lieu de passer une référence.</span><span class="sxs-lookup"><span data-stu-id="5aa81-107">If you pass the argument [ByRef](../modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="5aa81-108">Dans ce cas, quand la procédure est retournée, Visual Basic doit ensuite copier la valeur de la variable locale dans l’argument du code appelant.</span><span class="sxs-lookup"><span data-stu-id="5aa81-108">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="5aa81-109">Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5aa81-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="5aa81-110">Toutefois, si les types sont différents, Visual Basic doit effectuer une conversion dans les deux directions.</span><span class="sxs-lookup"><span data-stu-id="5aa81-110">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="5aa81-111">Si l’un des types est votre type de classe ou de structure, Visual Basic devez le convertir vers et à partir de l’autre type.</span><span class="sxs-lookup"><span data-stu-id="5aa81-111">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="5aa81-112">Si l’une de ces conversions est étendue, la conversion inverse peut être restrictive.</span><span class="sxs-lookup"><span data-stu-id="5aa81-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="5aa81-113">**ID d’erreur :** BC32053</span><span class="sxs-lookup"><span data-stu-id="5aa81-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5aa81-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5aa81-114">To correct this error</span></span>  
  
- <span data-ttu-id="5aa81-115">Si possible, utilisez un argument d’appel du même type que le paramètre de procédure, afin Visual Basic n’a pas besoin d’effectuer de conversion.</span><span class="sxs-lookup"><span data-stu-id="5aa81-115">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="5aa81-116">Si vous devez appeler la procédure avec un type d’argument différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, définissez le paramètre sur [ByVal](../modifiers/byval.md) au lieu de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="5aa81-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>  
  
- <span data-ttu-id="5aa81-117">Si vous devez retourner une valeur dans l’argument d’appel, définissez l’opérateur de conversion inverse comme [Widening](../modifiers/widening.md), si possible.</span><span class="sxs-lookup"><span data-stu-id="5aa81-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa81-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5aa81-118">See also</span></span>

- [<span data-ttu-id="5aa81-119">Procédures</span><span class="sxs-lookup"><span data-stu-id="5aa81-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="5aa81-120">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="5aa81-120">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5aa81-121">Passage des arguments par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="5aa81-121">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="5aa81-122">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="5aa81-122">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="5aa81-123">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="5aa81-123">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="5aa81-124">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="5aa81-124">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="5aa81-125">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="5aa81-125">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="5aa81-126">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5aa81-126">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="5aa81-127">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="5aa81-127">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
