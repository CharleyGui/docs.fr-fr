---
title: Impossible de faire référence à un membre instance d'une classe à partir d'une méthode partagée ou d'un initialiseur de membre partagé sans une instance explicite de la classe
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: a2a5ab99ff68e6dce783a2fd986ee6e8c15ae858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701176"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="97a26-102">Impossible de faire référence à un membre instance d'une classe à partir d'une méthode partagée ou d'un initialiseur de membre partagé sans une instance explicite de la classe</span><span class="sxs-lookup"><span data-stu-id="97a26-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="97a26-103">Vous avez tenté de faire référence à un membre non partagé d’une classe à partir d’une procédure partagée.</span><span class="sxs-lookup"><span data-stu-id="97a26-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="97a26-104">L’exemple suivant illustre une telle situation.</span><span class="sxs-lookup"><span data-stu-id="97a26-104">The following example demonstrates such a situation.</span></span>  
  
```vb  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="97a26-105">Dans l’exemple précédent, l’instruction d’assignation `x = 10` génère ce message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="97a26-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="97a26-106">Cela est dû au fait qu’une procédure partagée tente d’accéder à une variable d’instance.</span><span class="sxs-lookup"><span data-stu-id="97a26-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="97a26-107">La variable `x` est un membre d’instance parce qu’elle n’est pas déclarée comme [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="97a26-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="97a26-108">Chaque instance de la classe `sample` contient sa propre variable individuelle `x`.</span><span class="sxs-lookup"><span data-stu-id="97a26-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="97a26-109">Lorsqu’une instance définit ou modifie la valeur de `x`, elle n’affecte pas la valeur de `x` dans une autre instance.</span><span class="sxs-lookup"><span data-stu-id="97a26-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="97a26-110">Toutefois, la procédure `setX` est `Shared` parmi toutes les instances de la classe `sample`.</span><span class="sxs-lookup"><span data-stu-id="97a26-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="97a26-111">Cela signifie qu’elle n’est pas associée à une instance de la classe, mais qu’elle fonctionne indépendamment des instances individuelles.</span><span class="sxs-lookup"><span data-stu-id="97a26-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="97a26-112">Étant donné qu’elle n’a pas de connexion avec une instance particulière, `setX` ne peut pas accéder à une variable d’instance.</span><span class="sxs-lookup"><span data-stu-id="97a26-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="97a26-113">Il doit fonctionner uniquement sur les variables `Shared`.</span><span class="sxs-lookup"><span data-stu-id="97a26-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="97a26-114">Lorsque `setX` définit ou modifie la valeur d’une variable partagée, cette nouvelle valeur est disponible pour toutes les instances de la classe.</span><span class="sxs-lookup"><span data-stu-id="97a26-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="97a26-115">**ID d’erreur :** BC30369</span><span class="sxs-lookup"><span data-stu-id="97a26-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97a26-116">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="97a26-116">To correct this error</span></span>  
  
1. <span data-ttu-id="97a26-117">Décidez si vous souhaitez que le membre soit partagé entre toutes les instances de la classe, ou qu’il reste individuel pour chaque instance.</span><span class="sxs-lookup"><span data-stu-id="97a26-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2. <span data-ttu-id="97a26-118">Si vous souhaitez qu’une seule copie du membre soit partagée entre toutes les instances, ajoutez le mot clé `Shared` à la déclaration de membre.</span><span class="sxs-lookup"><span data-stu-id="97a26-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="97a26-119">Conservez le mot clé `Shared` dans la déclaration de procédure.</span><span class="sxs-lookup"><span data-stu-id="97a26-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3. <span data-ttu-id="97a26-120">Si vous souhaitez que chaque instance ait sa propre copie individuelle du membre, ne spécifiez pas `Shared` pour la déclaration de membre.</span><span class="sxs-lookup"><span data-stu-id="97a26-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="97a26-121">Supprimez le mot clé `Shared` de la déclaration de procédure.</span><span class="sxs-lookup"><span data-stu-id="97a26-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a26-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97a26-122">See also</span></span>

- [<span data-ttu-id="97a26-123">Shared</span><span class="sxs-lookup"><span data-stu-id="97a26-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
