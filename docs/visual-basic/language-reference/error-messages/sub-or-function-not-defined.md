---
title: Sub ou Function non défini (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 3a56d5596c79900bb5818a6ed7f8736859b5ea15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593198"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="00efa-102">Sub ou Function non défini (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00efa-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="00efa-103">Un `Sub` ou `Function` doit être défini pour pouvoir être appelés.</span><span class="sxs-lookup"><span data-stu-id="00efa-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="00efa-104">Cette erreur peut avoir plusieurs causes :</span><span class="sxs-lookup"><span data-stu-id="00efa-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="00efa-105">Faute d’orthographe dans le nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="00efa-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="00efa-106">Essayez d’appeler une procédure à partir d’un autre projet sans ajouter explicitement une référence à ce projet dans le **références** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="00efa-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="00efa-107">Spécification d’une procédure qui n’est pas visible à la procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="00efa-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="00efa-108">Déclaration d’une routine de bibliothèque de liens dynamiques (DLL) de Windows ou d’une routine de ressource de code Macintosh qui n’est pas dans la ressource de bibliothèque ou de code spécifiée.</span><span class="sxs-lookup"><span data-stu-id="00efa-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00efa-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="00efa-109">To correct this error</span></span>  
  
1. <span data-ttu-id="00efa-110">Assurez-vous que le nom de la procédure est correctement orthographié.</span><span class="sxs-lookup"><span data-stu-id="00efa-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="00efa-111">Rechercher le nom du projet contenant la procédure que vous souhaitez appeler le **références** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="00efa-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="00efa-112">Si elle n’apparaît pas, cliquez sur le **Parcourir** bouton pour le rechercher.</span><span class="sxs-lookup"><span data-stu-id="00efa-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="00efa-113">Cochez la case située à gauche du nom du projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="00efa-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="00efa-114">Vérifiez le nom de la routine.</span><span class="sxs-lookup"><span data-stu-id="00efa-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00efa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00efa-115">See also</span></span>

- [<span data-ttu-id="00efa-116">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="00efa-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="00efa-117">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="00efa-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="00efa-118">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="00efa-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="00efa-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="00efa-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
