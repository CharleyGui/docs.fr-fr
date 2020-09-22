---
title: Espace de pile insuffisant
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: afb6a42372bdbd2e49ac15fbbf2b9e254f8db431
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871306"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="a30a1-102">Espace de pile insuffisant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a30a1-102">Out of stack space (Visual Basic)</span></span>

<span data-ttu-id="a30a1-103">La pile est une zone de travail de la mémoire qui augmente et diminue de manière dynamique avec les demandes de votre programme en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a30a1-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="a30a1-104">Ses limites ont été dépassées.</span><span class="sxs-lookup"><span data-stu-id="a30a1-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a30a1-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a30a1-105">To correct this error</span></span>  
  
1. <span data-ttu-id="a30a1-106">Vérifiez que les procédures ne sont pas imbriquées trop profondément.</span><span class="sxs-lookup"><span data-stu-id="a30a1-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="a30a1-107">Vérifiez que les procédures récursives se terminent correctement.</span><span class="sxs-lookup"><span data-stu-id="a30a1-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="a30a1-108">Si les variables locales requièrent plus d’espace de variable locale que le nombre disponible, essayez de déclarer des variables au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="a30a1-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="a30a1-109">Vous pouvez également déclarer toutes les variables de la procédure statique en faisant précéder le `Property` `Sub` `Function` mot clé, ou par `Static` .</span><span class="sxs-lookup"><span data-stu-id="a30a1-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="a30a1-110">Vous pouvez utiliser l' `Static` instruction pour déclarer des variables statiques individuelles dans des procédures.</span><span class="sxs-lookup"><span data-stu-id="a30a1-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="a30a1-111">Redéfinissez certaines chaînes de longueur fixe en tant que chaînes de longueur variable, car les chaînes de longueur fixe utilisent plus d’espace de pile que les chaînes de longueur variable.</span><span class="sxs-lookup"><span data-stu-id="a30a1-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="a30a1-112">Vous pouvez également définir la chaîne au niveau du module, où elle ne requiert aucun espace de pile.</span><span class="sxs-lookup"><span data-stu-id="a30a1-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="a30a1-113">Vérifiez le nombre d’appels de `DoEvents` fonction imbriqués, en utilisant la `Calls` boîte de dialogue pour afficher les procédures actives sur la pile.</span><span class="sxs-lookup"><span data-stu-id="a30a1-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="a30a1-114">Assurez-vous que vous n’avez pas provoqué une « cascade d’événements » en déclenchant un événement qui appelle une procédure d’événement déjà sur la pile.</span><span class="sxs-lookup"><span data-stu-id="a30a1-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="a30a1-115">Une cascade d’événements est similaire à un appel de procédure récursive inachevé, mais elle est moins évidente, puisque l’appel est effectué par Visual Basic plutôt qu’un appel explicite dans le code.</span><span class="sxs-lookup"><span data-stu-id="a30a1-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="a30a1-116">Utilisez la `Calls` boîte de dialogue pour afficher les procédures actives sur la pile.</span><span class="sxs-lookup"><span data-stu-id="a30a1-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30a1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a30a1-117">See also</span></span>

- [<span data-ttu-id="a30a1-118">Fenêtres Mémoire</span><span class="sxs-lookup"><span data-stu-id="a30a1-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
