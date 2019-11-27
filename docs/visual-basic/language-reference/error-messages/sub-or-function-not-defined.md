---
title: Sub ou Function non défini
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 8b81460eccb6be8baa2ea7bc68d0f80c9d16398e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349575"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="9ded9-102">Sub ou Function non défini (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ded9-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="9ded9-103">Un `Sub` ou `Function` doit être défini pour être appelé.</span><span class="sxs-lookup"><span data-stu-id="9ded9-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="9ded9-104">Cette erreur peut avoir plusieurs causes :</span><span class="sxs-lookup"><span data-stu-id="9ded9-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="9ded9-105">Orthographe du nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="9ded9-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="9ded9-106">Tentative d’appel d’une procédure à partir d’un autre projet sans ajouter explicitement une référence à ce projet dans la boîte de dialogue **références** .</span><span class="sxs-lookup"><span data-stu-id="9ded9-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="9ded9-107">Spécification d’une procédure qui n’est pas visible pour la procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="9ded9-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="9ded9-108">Déclaration d’une routine de bibliothèque de liens dynamiques (DLL) Windows ou d’une routine de ressource de code Macintosh qui ne se trouve pas dans la bibliothèque ou la ressource de code spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9ded9-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9ded9-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9ded9-109">To correct this error</span></span>  
  
1. <span data-ttu-id="9ded9-110">Assurez-vous que le nom de la procédure est correctement orthographié.</span><span class="sxs-lookup"><span data-stu-id="9ded9-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="9ded9-111">Recherchez le nom du projet contenant la procédure que vous souhaitez appeler dans la boîte de dialogue **références** .</span><span class="sxs-lookup"><span data-stu-id="9ded9-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="9ded9-112">S’il n’apparaît pas, cliquez sur le bouton **Parcourir** pour le Rechercher.</span><span class="sxs-lookup"><span data-stu-id="9ded9-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="9ded9-113">Activez la case à cocher située à gauche du nom du projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9ded9-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="9ded9-114">Vérifiez le nom de la routine.</span><span class="sxs-lookup"><span data-stu-id="9ded9-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ded9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ded9-115">See also</span></span>

- [<span data-ttu-id="9ded9-116">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="9ded9-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="9ded9-117">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="9ded9-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="9ded9-118">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="9ded9-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9ded9-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="9ded9-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
