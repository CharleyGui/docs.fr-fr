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
ms.openlocfilehash: 4e07698e7abdad00983b61412fa2a57e651d4d46
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606986"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="f6c34-102">-checked (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f6c34-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="f6c34-103">L’option **-checked** spécifie si une instruction arithmétique entière qui produit une valeur en dehors de la plage du type de données, et qui n’est pas dans la portée d’un mot clé [checked](../keywords/checked.md) ou [unchecked](../keywords/unchecked.md), doit provoquer une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6c34-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6c34-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f6c34-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6c34-105">Remarks</span></span>  
 <span data-ttu-id="f6c34-106">Une instruction arithmétique entière qui est dans la portée d’un mot clé `checked` ou `unchecked` n’est pas soumise à l’effet de l’option **-checked**.</span><span class="sxs-lookup"><span data-stu-id="f6c34-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="f6c34-107">Si une instruction arithmétique entière qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked` produit une valeur en dehors de la plage du type de données, et que **-checked+** (ou **-checked**) est utilisé dans la compilation, cette instruction provoque une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6c34-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="f6c34-108">Si **-checked-** est utilisé dans la compilation, cette instruction ne provoque pas d’exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6c34-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="f6c34-109">La valeur par défaut de cette option est **-checked-** . La vérification du dépassement de capacité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="f6c34-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="f6c34-110">Certains outils automatisés qui sont utilisés pour générer des applications volumineuses définissent l’option -checked sur +.</span><span class="sxs-lookup"><span data-stu-id="f6c34-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="f6c34-111">Un scénario d’usage de l’option -checked- est de substituer l’option globale par défaut de l’outil en spécifiant -checked-.</span><span class="sxs-lookup"><span data-stu-id="f6c34-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f6c34-112">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6c34-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f6c34-113">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="f6c34-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="f6c34-114">Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="f6c34-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="f6c34-115">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f6c34-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="f6c34-116">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="f6c34-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="f6c34-117">Modifiez la propriété **Vérifier les dépassements de capacité arithmétiques positifs et négatifs**.</span><span class="sxs-lookup"><span data-stu-id="f6c34-117">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="f6c34-118">Pour accéder à cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6c34-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6c34-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="f6c34-119">Example</span></span>  
 <span data-ttu-id="f6c34-120">La commande suivante compile `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="f6c34-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="f6c34-121">L’utilisation de `-checked` dans la commande spécifie que toute instruction arithmétique entière dans le fichier qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked`, et qui produit une valeur en dehors de la plage du type de données, provoque une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6c34-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6c34-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6c34-122">See also</span></span>

- [<span data-ttu-id="f6c34-123">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="f6c34-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f6c34-124">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="f6c34-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
