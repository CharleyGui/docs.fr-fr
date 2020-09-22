---
title: "'<membername>' ne peut pas exposer le type '<typename>' en dehors du projet via <containertype> '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 31d44c93d62163df4d81cb8503b633f0eb317372
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873808"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="8be3c-102">'\<membername>' ne peut pas exposer le type '\<typename>' en dehors du projet via \<containertype> '\<containertypename>'</span><span class="sxs-lookup"><span data-stu-id="8be3c-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>

<span data-ttu-id="8be3c-103">Une variable, un paramètre de procédure ou un retour de fonction est exposé en dehors de son conteneur, mais il est déclaré en tant que type qui ne doit pas être exposé à l’extérieur du conteneur.</span><span class="sxs-lookup"><span data-stu-id="8be3c-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="8be3c-104">Le code squelette suivant illustre une situation qui génère cette erreur.</span><span class="sxs-lookup"><span data-stu-id="8be3c-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="8be3c-105">Un type qui est déclaré `Protected` , `Friend` , `Protected Friend` ou `Private` est destiné à avoir un accès limité en dehors de son contexte de déclaration.</span><span class="sxs-lookup"><span data-stu-id="8be3c-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="8be3c-106">Son utilisation en tant que type de données d’une variable avec un accès moins limité serait à l’encontre de cet objectif.</span><span class="sxs-lookup"><span data-stu-id="8be3c-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="8be3c-107">Dans le code squelette précédent, `exposedVar` est `Public` et expose `privateClass` au code qui ne doit pas y avoir accès.</span><span class="sxs-lookup"><span data-stu-id="8be3c-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="8be3c-108">**ID d’erreur :** BC30909</span><span class="sxs-lookup"><span data-stu-id="8be3c-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8be3c-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="8be3c-109">To correct this error</span></span>  
  
- <span data-ttu-id="8be3c-110">Modifiez le niveau d’accès de la variable, du paramètre de procédure ou du retour de fonction pour qu’il soit au moins aussi restrictif que le niveau d’accès de son type de données.</span><span class="sxs-lookup"><span data-stu-id="8be3c-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be3c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8be3c-111">See also</span></span>

- [<span data-ttu-id="8be3c-112">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8be3c-112">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
