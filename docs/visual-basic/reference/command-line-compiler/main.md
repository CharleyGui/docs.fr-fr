---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005507"
---
# <a name="-main"></a><span data-ttu-id="7a8b1-102">-main</span><span class="sxs-lookup"><span data-stu-id="7a8b1-102">-main</span></span>
<span data-ttu-id="7a8b1-103">Spécifie la classe ou le module qui contient la procédure `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a8b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a8b1-104">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="7a8b1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7a8b1-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="7a8b1-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-106">Required.</span></span> <span data-ttu-id="7a8b1-107">Nom de la classe ou du module qui contient le `Sub Main` procédure à appeler au démarrage du programme.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="7a8b1-108">Il peut s’agir de la forme **-main : module** ou **-main : namespace. module**.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a8b1-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="7a8b1-109">Remarks</span></span>  
 <span data-ttu-id="7a8b1-110">Utilisez cette option lorsque vous créez un fichier exécutable ou un programme exécutable Windows.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="7a8b1-111">Si l’option **-main** est omise, le compilateur recherche un `Sub Main` partagé valide dans toutes les classes et tous les modules publics.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="7a8b1-112">Pour plus d’informations sur les différentes formes de la procédure `Main`, consultez la [procédure principale dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) .</span><span class="sxs-lookup"><span data-stu-id="7a8b1-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="7a8b1-113">Lorsque `location` est une classe qui hérite de <xref:System.Windows.Forms.Form>, le compilateur fournit une procédure `Main` par défaut qui démarre l’application si la classe n’a pas de `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="7a8b1-114">Cela vous permet de compiler du code sur la ligne de commande qui a été créée dans l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="7a8b1-115">Pour définir-main dans l’environnement de développement intégré de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a8b1-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="7a8b1-116">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7a8b1-117">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="7a8b1-118">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="7a8b1-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="7a8b1-119">Vérifiez que la case à cocher **activer l’infrastructure** de l’application n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="7a8b1-120">Modifiez la valeur dans la zone **objet de démarrage** .</span><span class="sxs-lookup"><span data-stu-id="7a8b1-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a8b1-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a8b1-121">Example</span></span>  
 <span data-ttu-id="7a8b1-122">Le code suivant compile `T2.vb` et `T3.vb`, en spécifiant que la procédure `Sub Main` sera trouvée dans la classe `Test2`.</span><span class="sxs-lookup"><span data-stu-id="7a8b1-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a8b1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a8b1-123">See also</span></span>

- [<span data-ttu-id="7a8b1-124">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a8b1-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7a8b1-125">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a8b1-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="7a8b1-126">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="7a8b1-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="7a8b1-127">Procédure principale dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a8b1-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
