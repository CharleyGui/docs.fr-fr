---
title: -main (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602724"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="832d1-102">-main (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="832d1-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="832d1-103">Cette option spécifie la classe qui contient le point d’entrée du programme dans le cas où plusieurs classes contiennent une méthode **Main**.</span><span class="sxs-lookup"><span data-stu-id="832d1-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="832d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="832d1-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="832d1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="832d1-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="832d1-106">Type contenant la méthode **Main**.</span><span class="sxs-lookup"><span data-stu-id="832d1-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="832d1-107">Le nom de classe fourni doit être complet, c’est-à-dire qu’il doit inclure l’espace de noms complet contenant la classe, suivi du nom de classe.</span><span class="sxs-lookup"><span data-stu-id="832d1-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="832d1-108">Par exemple, si la méthode `Main` se trouve dans la classe `Program` dans l’espace de noms `MyApplication.Core`, l’option du compilateur doit être `-main:MyApplication.Core.Program`.</span><span class="sxs-lookup"><span data-stu-id="832d1-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="832d1-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="832d1-109">Remarks</span></span>  
 <span data-ttu-id="832d1-110">Si votre compilation comprend plusieurs types avec une méthode [Main](../../programming-guide/main-and-command-args/index.md), vous pouvez spécifier le type qui contient la méthode **Main** à utiliser comme point d’entrée dans le programme.</span><span class="sxs-lookup"><span data-stu-id="832d1-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="832d1-111">Cette option est à utiliser lors de la compilation d’un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="832d1-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="832d1-112">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="832d1-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="832d1-113">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="832d1-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="832d1-114">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="832d1-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="832d1-115">Modifiez la propriété **Objet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="832d1-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="832d1-116">Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="832d1-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="832d1-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="832d1-117">Example</span></span>  
 <span data-ttu-id="832d1-118">Compilez `t2.cs` et `t3.cs`, en spécifiant que la **Main** se trouve dans `Test2` :</span><span class="sxs-lookup"><span data-stu-id="832d1-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="832d1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="832d1-119">See also</span></span>

- [<span data-ttu-id="832d1-120">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="832d1-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="832d1-121">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="832d1-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
