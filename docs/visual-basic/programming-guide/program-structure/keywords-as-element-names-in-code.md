---
title: Mots clés comme noms d’éléments dans le code
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: a98f0b027700717b414d58e1284ddec655eb25f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403224"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="6b2b5-102">Utilisation des mots clés comme noms d'éléments dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b2b5-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="6b2b5-103">Tout élément de programme (par exemple, une variable, une classe ou un membre) peut avoir le même nom qu’un mot clé restreint.</span><span class="sxs-lookup"><span data-stu-id="6b2b5-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="6b2b5-104">Par exemple, vous pouvez créer une variable nommée `Loop` .</span><span class="sxs-lookup"><span data-stu-id="6b2b5-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="6b2b5-105">Toutefois, pour faire référence à votre version de, qui porte le même nom que le `Loop` mot clé Restricted, vous devez le faire précéder d’une chaîne de qualification complète ou la placer entre crochets ( `[ ]` ), comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6b2b5-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="6b2b5-106">Si vous n’effectuez pas l’une de ces opérations, Visual Basic suppose l’utilisation du `Loop` mot clé Intrinsic et génère une erreur, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6b2b5-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="6b2b5-107">Vous pouvez utiliser des crochets lorsque vous faites référence à des formulaires et des contrôles, et lorsque vous déclarez une variable ou que vous définissez une procédure portant le même nom qu’un mot clé restreint.</span><span class="sxs-lookup"><span data-stu-id="6b2b5-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="6b2b5-108">Il peut être facile d’oublier de qualifier des noms ou d’inclure des crochets, et donc d’introduire des erreurs dans votre code et de le rendre plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="6b2b5-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="6b2b5-109">Pour cette raison, nous vous recommandons de ne pas utiliser de mots clés restreints comme noms d’éléments de programme.</span><span class="sxs-lookup"><span data-stu-id="6b2b5-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="6b2b5-110">Toutefois, si une version ultérieure de Visual Basic définit un nouveau mot clé qui est en conflit avec un nom de formulaire ou de contrôle existant, vous pouvez utiliser cette technique lors de la mise à jour de votre code pour utiliser la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="6b2b5-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b2b5-111">Votre programme peut également inclure des noms d’éléments fournis par d’autres assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="6b2b5-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="6b2b5-112">Si ces noms sont en conflit avec des mots clés restreints, si vous placez des crochets autour, les Visual Basic les interprètent comme des éléments définis.</span><span class="sxs-lookup"><span data-stu-id="6b2b5-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2b5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b2b5-113">See also</span></span>

- [<span data-ttu-id="6b2b5-114">Conventions d'affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b2b5-114">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="6b2b5-115">Structure de programme et conventions de code</span><span class="sxs-lookup"><span data-stu-id="6b2b5-115">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="6b2b5-116">Mots clés</span><span class="sxs-lookup"><span data-stu-id="6b2b5-116">Keywords</span></span>](../../language-reference/keywords/index.md)
