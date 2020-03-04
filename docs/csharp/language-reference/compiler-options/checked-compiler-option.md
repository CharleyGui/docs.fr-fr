---
title: -checked (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 44dc0fc8f50e5248ce2fca17c36f7309a6aca8d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239690"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="10e49-102">-checked (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="10e49-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="10e49-103">L’option **-checked** spécifie si une instruction arithmétique entière qui produit une valeur en dehors de la plage du type de données, et qui n’est pas dans la portée d’un mot clé [checked](../keywords/checked.md) ou [unchecked](../keywords/unchecked.md), doit provoquer une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="10e49-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10e49-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="10e49-105">Notes</span><span class="sxs-lookup"><span data-stu-id="10e49-105">Remarks</span></span>  
 <span data-ttu-id="10e49-106">Une instruction arithmétique entière qui est dans la portée d’un mot clé `checked` ou `unchecked` n’est pas soumise à l’effet de l’option **-checked**.</span><span class="sxs-lookup"><span data-stu-id="10e49-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="10e49-107">Si une instruction arithmétique entière qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked` produit une valeur en dehors de la plage du type de données, et que **-checked+** (ou **-checked**) est utilisé dans la compilation, cette instruction provoque une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="10e49-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="10e49-108">Si **-checked-** est utilisé dans la compilation, cette instruction ne provoque pas d’exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="10e49-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="10e49-109">La valeur par défaut de cette option est **-checked-**. La vérification du dépassement de capacité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="10e49-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="10e49-110">Certains outils automatisés qui sont utilisés pour générer des applications volumineuses définissent l’option -checked sur +.</span><span class="sxs-lookup"><span data-stu-id="10e49-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="10e49-111">Un scénario d’usage de l’option -checked- est de substituer l’option globale par défaut de l’outil en spécifiant -checked-.</span><span class="sxs-lookup"><span data-stu-id="10e49-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="10e49-112">Pour définir cette option du compilateur dans l’environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10e49-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="10e49-113">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="10e49-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="10e49-114">Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="10e49-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="10e49-115">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="10e49-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="10e49-116">Cliquez sur le bouton **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="10e49-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="10e49-117">Modifiez la propriété **Vérifier la débordement arithmétique** .</span><span class="sxs-lookup"><span data-stu-id="10e49-117">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="10e49-118">Pour accéder à cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="10e49-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10e49-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="10e49-119">Example</span></span>  
 <span data-ttu-id="10e49-120">La commande suivante compile `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="10e49-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="10e49-121">L’utilisation de `-checked` dans la commande spécifie que toute instruction arithmétique entière dans le fichier qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked`, et qui produit une valeur en dehors de la plage du type de données, provoque une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="10e49-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="10e49-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10e49-122">See also</span></span>

- [<span data-ttu-id="10e49-123">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="10e49-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="10e49-124">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="10e49-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
