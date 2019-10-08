---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005373"
---
# <a name="-optimize"></a><span data-ttu-id="a5cfe-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="a5cfe-102">-optimize</span></span>
<span data-ttu-id="a5cfe-103">Active ou désactive les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5cfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5cfe-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5cfe-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a5cfe-105">Arguments</span></span>  
  
|<span data-ttu-id="a5cfe-106">Terme</span><span class="sxs-lookup"><span data-stu-id="a5cfe-106">Term</span></span>|<span data-ttu-id="a5cfe-107">Définition</span><span class="sxs-lookup"><span data-stu-id="a5cfe-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="a5cfe-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a5cfe-108">`+` &#124; `-`</span></span>|<span data-ttu-id="a5cfe-109">facultatif.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-109">Optional.</span></span> <span data-ttu-id="a5cfe-110">L’option `-optimize-` désactive les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="a5cfe-111">L’option `-optimize+` active les optimisations.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="a5cfe-112">Par défaut, les optimisations sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5cfe-113">Notes</span><span class="sxs-lookup"><span data-stu-id="a5cfe-113">Remarks</span></span>  
 <span data-ttu-id="a5cfe-114">Les optimisations du compilateur diminuent la taille du fichier de sortie, le rendent plus rapide et plus efficace.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="a5cfe-115">Toutefois, étant donné que les optimisations entraînent une réorganisation du code dans le fichier de sortie, `-optimize+` peut compliquer le débogage.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="a5cfe-116">Tous les modules générés avec `-target:module` pour un assembly doivent utiliser les mêmes paramètres `-optimize` que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="a5cfe-117">Pour plus d’informations, consultez [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="a5cfe-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="a5cfe-118">Vous pouvez combiner les options `-optimize` et `-debug`.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="a5cfe-119">Pour définir-Optimize dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a5cfe-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="a5cfe-120">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a5cfe-121">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="a5cfe-122">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="a5cfe-123">3.  Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="a5cfe-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="a5cfe-124">4.  Modifiez la case à cocher **activer les optimisations** .</span><span class="sxs-lookup"><span data-stu-id="a5cfe-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a5cfe-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5cfe-125">Example</span></span>  
 <span data-ttu-id="a5cfe-126">Le code suivant compile `T2.vb` et active les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a5cfe-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5cfe-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5cfe-127">See also</span></span>

- [<span data-ttu-id="a5cfe-128">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5cfe-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a5cfe-129">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5cfe-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="a5cfe-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="a5cfe-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="a5cfe-131">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5cfe-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
