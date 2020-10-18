---
title: Option Strict On interdit le passage du type '<typename1>' au type '<typename2>' lors de la recopie de la valeur du paramètre 'ByRef' '<parametername>' dans l'argument correspondant.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: a95a4b792742efcc165f7c7a9592582d34618f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162802"
---
# <a name="bc41999-implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="e6d84-102">BC41999 : conversion implicite de' \<typename1> 'en' \<typename2> 'lors de la recopie de la valeur du paramètre’ByRef' ' \<parametername> 'dans l’argument correspondant.</span><span class="sxs-lookup"><span data-stu-id="e6d84-102">BC41999: Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>

<span data-ttu-id="e6d84-103">Une procédure est appelée avec un argument [ByRef](../modifiers/byref.md) d’un type différent de celui de son paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="e6d84-103">A procedure is called with a [ByRef](../modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>

 <span data-ttu-id="e6d84-104">Si vous passez un argument `ByRef` , Visual Basic copie parfois la valeur de l’argument dans une variable locale de la procédure au lieu de passer une référence.</span><span class="sxs-lookup"><span data-stu-id="e6d84-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="e6d84-105">Dans ce cas, quand la procédure est retournée, Visual Basic doit ensuite copier la valeur de la variable locale dans l’argument du code appelant.</span><span class="sxs-lookup"><span data-stu-id="e6d84-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>

 <span data-ttu-id="e6d84-106">Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e6d84-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="e6d84-107">Toutefois, si les types sont différents, Visual Basic doit effectuer une conversion dans les deux directions.</span><span class="sxs-lookup"><span data-stu-id="e6d84-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="e6d84-108">Étant donné que vous ne pouvez pas utiliser `CType` ou l’un des autres mots clés de conversion sur un argument ou un paramètre de procédure, une telle conversion est toujours implicite.</span><span class="sxs-lookup"><span data-stu-id="e6d84-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>

 <span data-ttu-id="e6d84-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="e6d84-109">By default, this message is a warning.</span></span> <span data-ttu-id="e6d84-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e6d84-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="e6d84-111">**ID d’erreur :** BC41999</span><span class="sxs-lookup"><span data-stu-id="e6d84-111">**Error ID:** BC41999</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e6d84-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e6d84-112">To correct this error</span></span>

- <span data-ttu-id="e6d84-113">Si possible, utilisez un argument d’appel du même type que le paramètre de procédure, afin Visual Basic n’a pas besoin d’effectuer de conversion.</span><span class="sxs-lookup"><span data-stu-id="e6d84-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>

- <span data-ttu-id="e6d84-114">Si vous devez appeler la procédure avec un type d’argument différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, définissez le paramètre sur [ByVal](../modifiers/byval.md) au lieu de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="e6d84-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6d84-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6d84-115">See also</span></span>

- [<span data-ttu-id="e6d84-116">Procédures</span><span class="sxs-lookup"><span data-stu-id="e6d84-116">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="e6d84-117">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="e6d84-117">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e6d84-118">Passage des arguments par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="e6d84-118">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="e6d84-119">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="e6d84-119">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
