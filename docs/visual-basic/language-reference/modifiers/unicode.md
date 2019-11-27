---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344221"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="7ee8e-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ee8e-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="7ee8e-103">Spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs Unicode, quel que soit le nom de la procédure externe qui est déclarée.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="7ee8e-104">Quand vous appelez une procédure définie à l’extérieur de votre projet, le compilateur Visual Basic n’a pas accès aux informations qu’il doit avoir pour pouvoir appeler la procédure correctement.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="7ee8e-105">Ces informations incluent l’emplacement de la procédure, son identification, sa séquence d’appel et son type de retour, ainsi que le jeu de caractères de chaîne qu’elle utilise.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="7ee8e-106">L' [instruction DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="7ee8e-107">La partie `charsetmodifier` dans l’instruction `Declare` fournit les informations du jeu de caractères pour marshaler les chaînes pendant un appel à la procédure externe.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="7ee8e-108">Cela affecte également la manière dont Visual Basic recherche le nom de la procédure externe dans le fichier externe.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="7ee8e-109">Le modificateur `Unicode` spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs Unicode et doit rechercher la procédure sans modifier son nom au cours de la recherche.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="7ee8e-110">Si aucun modificateur de jeu de caractères n’est spécifié, `Ansi` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ee8e-111">Notes</span><span class="sxs-lookup"><span data-stu-id="7ee8e-111">Remarks</span></span>  
 <span data-ttu-id="7ee8e-112">Le modificateur `Unicode` peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="7ee8e-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="7ee8e-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="7ee8e-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="7ee8e-114">Notes de développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="7ee8e-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="7ee8e-115">Ce mot clé n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7ee8e-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee8e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ee8e-116">See also</span></span>

- [<span data-ttu-id="7ee8e-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="7ee8e-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="7ee8e-118">Auto</span><span class="sxs-lookup"><span data-stu-id="7ee8e-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="7ee8e-119">Mots clés</span><span class="sxs-lookup"><span data-stu-id="7ee8e-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
