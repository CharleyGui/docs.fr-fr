---
title: "Comment : définir plusieurs versions d'une procédure"
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 870a18dbf3a7e28b7d7b612e853beeec6908cf6f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387931"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="07580-102">Comment : définir plusieurs versions d'une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07580-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="07580-103">Vous pouvez définir une procédure dans plusieurs versions en la *surchargeant* , à l’aide du même nom mais d’une liste de paramètres différente pour chaque version.</span><span class="sxs-lookup"><span data-stu-id="07580-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="07580-104">L’objectif de la surcharge est de définir plusieurs versions étroitement liées d’une procédure sans avoir à les différencier par nom.</span><span class="sxs-lookup"><span data-stu-id="07580-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="07580-105">Pour plus d'informations, consultez [Procedure Overloading](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="07580-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="07580-106">Pour définir plusieurs versions d’une procédure</span><span class="sxs-lookup"><span data-stu-id="07580-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="07580-107">Écrivez une `Sub` `Function` instruction de déclaration ou pour chaque version de la procédure que vous souhaitez définir.</span><span class="sxs-lookup"><span data-stu-id="07580-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="07580-108">Utilisez le même nom de procédure dans chaque déclaration.</span><span class="sxs-lookup"><span data-stu-id="07580-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="07580-109">Faites précéder le `Sub` `Function` mot clé ou dans chaque déclaration du mot clé [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="07580-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="07580-110">Vous pouvez éventuellement omettre `Overloads` dans les déclarations, mais si vous l’incluez dans une des déclarations, vous devez l’inclure dans chaque déclaration.</span><span class="sxs-lookup"><span data-stu-id="07580-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="07580-111">Après chaque instruction de déclaration, écrivez le code de procédure pour gérer le cas spécifique où le code appelant fournit des arguments correspondant à la liste de paramètres de cette version.</span><span class="sxs-lookup"><span data-stu-id="07580-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="07580-112">Vous n’avez pas besoin de tester les paramètres fournis par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="07580-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="07580-113">Visual Basic passe le contrôle à la version correspondante de votre procédure.</span><span class="sxs-lookup"><span data-stu-id="07580-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="07580-114">Mettez fin à chaque version de la procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="07580-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07580-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="07580-115">Example</span></span>  
 <span data-ttu-id="07580-116">L’exemple suivant définit une `Sub` procédure pour la publication d’une transaction sur le solde d’un client.</span><span class="sxs-lookup"><span data-stu-id="07580-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="07580-117">Elle utilise le `Overloads` mot clé pour définir deux versions de la procédure, une qui accepte le client par nom et l’autre par numéro de compte.</span><span class="sxs-lookup"><span data-stu-id="07580-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="07580-118">Le code appelant peut obtenir l’identification du client en tant que `String` ou `Integer` , puis utiliser la même instruction appelante dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="07580-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="07580-119">Pour plus d’informations sur l’appel de ces versions de la `post` procédure, consultez [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="07580-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="07580-120">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="07580-120">Compile the code</span></span>  
 <span data-ttu-id="07580-121">Vérifiez que chaque version surchargée a le même nom de procédure, mais une autre liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="07580-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07580-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07580-122">See also</span></span>

- [<span data-ttu-id="07580-123">Procédures</span><span class="sxs-lookup"><span data-stu-id="07580-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="07580-124">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="07580-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="07580-125">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="07580-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="07580-126">Comment : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="07580-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="07580-127">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres</span><span class="sxs-lookup"><span data-stu-id="07580-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="07580-128">Considérations sur les surcharges de procédures</span><span class="sxs-lookup"><span data-stu-id="07580-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="07580-129">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="07580-129">Overload Resolution</span></span>](./overload-resolution.md)
