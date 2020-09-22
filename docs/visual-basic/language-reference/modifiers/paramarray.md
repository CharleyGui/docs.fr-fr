---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: baf9303101eea9eed27e8a4eee9e04d255c798e9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867822"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="ce5cb-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce5cb-102">ParamArray (Visual Basic)</span></span>

<span data-ttu-id="ce5cb-103">Spécifie qu’un paramètre de procédure accepte un tableau facultatif d’éléments du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="ce5cb-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="ce5cb-104">`ParamArray` peut être utilisé uniquement sur le dernier paramètre d’une liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="ce5cb-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce5cb-105">Notes</span><span class="sxs-lookup"><span data-stu-id="ce5cb-105">Remarks</span></span>  

 <span data-ttu-id="ce5cb-106">`ParamArray` vous permet de passer un nombre arbitraire d’arguments à la procédure.</span><span class="sxs-lookup"><span data-stu-id="ce5cb-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="ce5cb-107">Un `ParamArray` paramètre est toujours déclaré à l’aide de [ByVal](byval.md).</span><span class="sxs-lookup"><span data-stu-id="ce5cb-107">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="ce5cb-108">Vous pouvez fournir un ou plusieurs arguments à un `ParamArray` paramètre en passant un tableau du type de données approprié, une liste de valeurs séparées par des virgules, ou rien du tout.</span><span class="sxs-lookup"><span data-stu-id="ce5cb-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="ce5cb-109">Pour plus d’informations, consultez « appel d’un ParamArray » dans les [tableaux de paramètres](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="ce5cb-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ce5cb-110">Chaque fois que vous traitez un tableau qui peut être indéfiniment volumineux, il existe un risque de surexécution de la capacité interne de votre application.</span><span class="sxs-lookup"><span data-stu-id="ce5cb-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="ce5cb-111">Si vous acceptez un tableau de paramètres du code appelant, vous devez tester sa longueur et prendre les mesures appropriées s’il est trop grand pour votre application.</span><span class="sxs-lookup"><span data-stu-id="ce5cb-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="ce5cb-112">Le modificateur `ParamArray` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="ce5cb-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ce5cb-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="ce5cb-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="ce5cb-114">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="ce5cb-114">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="ce5cb-115">Property Statement</span><span class="sxs-lookup"><span data-stu-id="ce5cb-115">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="ce5cb-116">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="ce5cb-116">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ce5cb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce5cb-117">See also</span></span>

- [<span data-ttu-id="ce5cb-118">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ce5cb-118">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="ce5cb-119">Tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="ce5cb-119">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
