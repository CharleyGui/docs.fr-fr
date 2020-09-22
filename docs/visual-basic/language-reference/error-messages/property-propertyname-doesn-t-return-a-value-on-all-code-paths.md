---
title: La propriété '<propertyname>' ne retourne pas une valeur pour tous les chemins de code
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 6a80a8275a7b9c5e3cbfa410ee219e0d16ce5918
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870949"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="a259d-102">La propriété '\<propertyname>' ne retourne pas une valeur pour tous les chemins de code</span><span class="sxs-lookup"><span data-stu-id="a259d-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="a259d-103">La propriété' \<propertyname> 'ne retourne pas de valeur pour tous les chemins de code.</span><span class="sxs-lookup"><span data-stu-id="a259d-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="a259d-104">Une exception de référence null peut se produire au moment de l'exécution lorsque le résultat est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a259d-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="a259d-105">Une procédure de propriété `Get` possède au moins un chemin d’accès possible via son code qui ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="a259d-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="a259d-106">Vous pouvez retourner une valeur à partir d’une procédure de propriété `Get` de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="a259d-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="a259d-107">Assignez la valeur au nom de la propriété, puis exécutez une `Exit Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="a259d-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
- <span data-ttu-id="a259d-108">Assignez la valeur au nom de la propriété, puis exécutez l' `End Get` instruction.</span><span class="sxs-lookup"><span data-stu-id="a259d-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
- <span data-ttu-id="a259d-109">Incluez la valeur dans une [instruction return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a259d-109">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="a259d-110">Si le contrôle est transmis à `Exit Property` ou `End Get` et que vous n’avez affecté aucune valeur au nom de la propriété, la `Get` procédure retourne la valeur par défaut du type de données de la propriété.</span><span class="sxs-lookup"><span data-stu-id="a259d-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="a259d-111">Pour plus d’informations, consultez « Behavior » dans l' [instruction de fonction](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a259d-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="a259d-112">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="a259d-112">By default, this message is a warning.</span></span> <span data-ttu-id="a259d-113">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a259d-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a259d-114">**ID d’erreur :** BC42107</span><span class="sxs-lookup"><span data-stu-id="a259d-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a259d-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a259d-115">To correct this error</span></span>  
  
- <span data-ttu-id="a259d-116">Vérifiez votre logique de workflow de contrôle et assurez-vous que vous attribuez une valeur avant chaque instruction qui provoque un retour.</span><span class="sxs-lookup"><span data-stu-id="a259d-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="a259d-117">Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours l' `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="a259d-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="a259d-118">Dans ce cas, la dernière instruction avant `End Get` doit être une `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="a259d-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a259d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a259d-119">See also</span></span>

- [<span data-ttu-id="a259d-120">Procédures Property</span><span class="sxs-lookup"><span data-stu-id="a259d-120">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="a259d-121">Property Statement</span><span class="sxs-lookup"><span data-stu-id="a259d-121">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="a259d-122">Get, instruction</span><span class="sxs-lookup"><span data-stu-id="a259d-122">Get Statement</span></span>](../statements/get-statement.md)
