---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 5530da4c784346df4a1088998b8d2027feee08e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403159"
---
# <a name="-main"></a><span data-ttu-id="ca571-102">-main</span><span class="sxs-lookup"><span data-stu-id="ca571-102">-main</span></span>
<span data-ttu-id="ca571-103">Spécifie la classe ou le module qui contient la procédure `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="ca571-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca571-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca571-104">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="ca571-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ca571-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="ca571-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ca571-106">Required.</span></span> <span data-ttu-id="ca571-107">Nom de la classe ou du module qui contient la `Sub Main` procédure à appeler au démarrage du programme.</span><span class="sxs-lookup"><span data-stu-id="ca571-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="ca571-108">Il peut s’agir de la forme **-main : module** ou **-main : namespace. module**.</span><span class="sxs-lookup"><span data-stu-id="ca571-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca571-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ca571-109">Remarks</span></span>  
 <span data-ttu-id="ca571-110">Utilisez cette option lorsque vous créez un fichier exécutable ou un programme exécutable Windows.</span><span class="sxs-lookup"><span data-stu-id="ca571-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="ca571-111">Si l’option **-main** est omise, le compilateur recherche un partagé valide `Sub Main` dans toutes les classes et tous les modules publics.</span><span class="sxs-lookup"><span data-stu-id="ca571-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="ca571-112">Pour plus d’informations sur les différentes formes de la procédure, consultez la [procédure principale dans Visual Basic](../../programming-guide/program-structure/main-procedure.md) `Main` .</span><span class="sxs-lookup"><span data-stu-id="ca571-112">See [Main Procedure in Visual Basic](../../programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="ca571-113">Quand `location` est une classe qui hérite de <xref:System.Windows.Forms.Form> , le compilateur fournit une procédure par défaut `Main` qui démarre l’application si la classe n’a pas de `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="ca571-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="ca571-114">Cela vous permet de compiler du code sur la ligne de commande qui a été créée dans l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="ca571-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="ca571-115">Pour définir-main dans l’environnement de développement intégré de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca571-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="ca571-116">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="ca571-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ca571-117">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ca571-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="ca571-118">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="ca571-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="ca571-119">Vérifiez que la case à cocher **activer l’infrastructure** de l’application n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="ca571-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="ca571-120">Modifiez la valeur dans la zone **objet de démarrage** .</span><span class="sxs-lookup"><span data-stu-id="ca571-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca571-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="ca571-121">Example</span></span>  
 <span data-ttu-id="ca571-122">Le code suivant compile `T2.vb` et `T3.vb` , en spécifiant que la `Sub Main` procédure sera trouvée dans la `Test2` classe.</span><span class="sxs-lookup"><span data-stu-id="ca571-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca571-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca571-123">See also</span></span>

- [<span data-ttu-id="ca571-124">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca571-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ca571-125">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca571-125">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="ca571-126">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="ca571-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="ca571-127">Procédure Main dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca571-127">Main Procedure in Visual Basic</span></span>](../../programming-guide/program-structure/main-procedure.md)
