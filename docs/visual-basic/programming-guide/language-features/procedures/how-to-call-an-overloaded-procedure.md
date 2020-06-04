---
title: 'Comment : appeler une procédure surchargée'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: de101309fa1edaaddc3defc5759d9293fbef684c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388541"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="ab9eb-102">Comment : appeler une procédure surchargée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab9eb-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="ab9eb-103">L’avantage de la surcharge d’une procédure est de la flexibilité de l’appel.</span><span class="sxs-lookup"><span data-stu-id="ab9eb-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="ab9eb-104">Le code appelant peut obtenir les informations qu’il doit passer à la procédure, puis appeler un nom de procédure unique, quels que soient les arguments transmis.</span><span class="sxs-lookup"><span data-stu-id="ab9eb-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="ab9eb-105">Pour appeler une procédure qui a plusieurs versions définies</span><span class="sxs-lookup"><span data-stu-id="ab9eb-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="ab9eb-106">Dans le code appelant, déterminez les données à passer à la procédure.</span><span class="sxs-lookup"><span data-stu-id="ab9eb-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="ab9eb-107">Écrivez l’appel de procédure de manière normale, en présentant les données dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="ab9eb-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="ab9eb-108">Veillez à ce que les arguments correspondent à la liste de paramètres dans l’une des versions définies pour la procédure.</span><span class="sxs-lookup"><span data-stu-id="ab9eb-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="ab9eb-109">Vous n’avez pas besoin de déterminer la version de la procédure à appeler.</span><span class="sxs-lookup"><span data-stu-id="ab9eb-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="ab9eb-110">Visual Basic passe le contrôle à la version correspondant à votre liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="ab9eb-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="ab9eb-111">L’exemple suivant appelle la `post` procédure déclarée dans [Comment : définir plusieurs versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="ab9eb-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="ab9eb-112">Il obtient l’identification du client, détermine s’il s’agit d’un `String` ou d’un `Integer` , puis, dans les deux cas, appelle la même procédure.</span><span class="sxs-lookup"><span data-stu-id="ab9eb-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="ab9eb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab9eb-113">See also</span></span>

- [<span data-ttu-id="ab9eb-114">Procédures</span><span class="sxs-lookup"><span data-stu-id="ab9eb-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ab9eb-115">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="ab9eb-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ab9eb-116">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="ab9eb-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="ab9eb-117">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="ab9eb-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="ab9eb-118">Comment : définir plusieurs versions d'une procédure</span><span class="sxs-lookup"><span data-stu-id="ab9eb-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="ab9eb-119">Comment : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="ab9eb-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="ab9eb-120">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres</span><span class="sxs-lookup"><span data-stu-id="ab9eb-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="ab9eb-121">Considérations sur les surcharges de procédures</span><span class="sxs-lookup"><span data-stu-id="ab9eb-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="ab9eb-122">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="ab9eb-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="ab9eb-123">Surcharges</span><span class="sxs-lookup"><span data-stu-id="ab9eb-123">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
