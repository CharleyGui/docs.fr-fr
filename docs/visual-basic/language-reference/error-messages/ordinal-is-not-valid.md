---
title: Nombre non valide
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7b9bd8435b56dd5e33d14eb35d76aacc7d60c8b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413051"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="231a5-102">Nombre non valide</span><span class="sxs-lookup"><span data-stu-id="231a5-102">Ordinal is not valid</span></span>
<span data-ttu-id="231a5-103">Votre appel à une bibliothèque de liens dynamiques (DLL) indiquait d’utiliser un nombre au lieu d’un nom de procédure, à l’aide de la `#num` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="231a5-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="231a5-104">Cette erreur a les causes possibles suivantes :</span><span class="sxs-lookup"><span data-stu-id="231a5-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="231a5-105">Une tentative de conversion `#num` de l’expression en ordinal a échoué.</span><span class="sxs-lookup"><span data-stu-id="231a5-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="231a5-106">Le `#num` spécifié ne spécifie pas de fonction dans la dll.</span><span class="sxs-lookup"><span data-stu-id="231a5-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="231a5-107">Une bibliothèque de types a une déclaration non valide, ce qui entraîne l’utilisation interne d’un nombre ordinal non valide.</span><span class="sxs-lookup"><span data-stu-id="231a5-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="231a5-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="231a5-108">To correct this error</span></span>  
  
1. <span data-ttu-id="231a5-109">Assurez-vous que l’expression représente un nombre valide ou appelez la procédure par nom.</span><span class="sxs-lookup"><span data-stu-id="231a5-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="231a5-110">Assurez-vous que `#num` identifie une fonction valide dans la dll.</span><span class="sxs-lookup"><span data-stu-id="231a5-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="231a5-111">Isolez l’appel de procédure à l’origine du problème en commentant le code.</span><span class="sxs-lookup"><span data-stu-id="231a5-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="231a5-112">Écrivez une `Declare` instruction pour la procédure et signalez le problème au fournisseur de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="231a5-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="231a5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="231a5-113">See also</span></span>

- [<span data-ttu-id="231a5-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="231a5-114">Declare Statement</span></span>](../statements/declare-statement.md)
