---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 337cb794ef9a405a178f1998cbe27b5da7709382
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397439"
---
# <a name="-optimize"></a><span data-ttu-id="df229-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="df229-102">-optimize</span></span>
<span data-ttu-id="df229-103">Active ou désactive les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="df229-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df229-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df229-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="df229-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="df229-105">Arguments</span></span>  
  
|<span data-ttu-id="df229-106">Terme</span><span class="sxs-lookup"><span data-stu-id="df229-106">Term</span></span>|<span data-ttu-id="df229-107">Définition</span><span class="sxs-lookup"><span data-stu-id="df229-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="df229-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="df229-108">`+` &#124; `-`</span></span>|<span data-ttu-id="df229-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="df229-109">Optional.</span></span> <span data-ttu-id="df229-110">L' `-optimize-` option désactive les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="df229-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="df229-111">L' `-optimize+` option active les optimisations.</span><span class="sxs-lookup"><span data-stu-id="df229-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="df229-112">Par défaut, les optimisations sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="df229-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df229-113">Notes</span><span class="sxs-lookup"><span data-stu-id="df229-113">Remarks</span></span>  
 <span data-ttu-id="df229-114">Les optimisations du compilateur diminuent la taille du fichier de sortie, le rendent plus rapide et plus efficace.</span><span class="sxs-lookup"><span data-stu-id="df229-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="df229-115">Toutefois, étant donné que les optimisations entraînent une réorganisation du code dans le fichier de sortie, `-optimize+` peut compliquer le débogage.</span><span class="sxs-lookup"><span data-stu-id="df229-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="df229-116">Tous les modules générés avec `-target:module` pour un assembly doivent utiliser les mêmes `-optimize` paramètres que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="df229-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="df229-117">Pour plus d’informations, consultez [-target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="df229-117">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="df229-118">Vous pouvez combiner les `-optimize` `-debug` options et.</span><span class="sxs-lookup"><span data-stu-id="df229-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="df229-119">Pour définir-Optimize dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df229-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="df229-120">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="df229-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="df229-121">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="df229-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="df229-122">2. cliquez sur l’onglet **compiler** .</span><span class="sxs-lookup"><span data-stu-id="df229-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="df229-123">3. cliquez sur le bouton **avancé** .</span><span class="sxs-lookup"><span data-stu-id="df229-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="df229-124">4. modifiez la case à cocher **activer les optimisations** .</span><span class="sxs-lookup"><span data-stu-id="df229-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="df229-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="df229-125">Example</span></span>  
 <span data-ttu-id="df229-126">Le code suivant compile `T2.vb` et active les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="df229-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="df229-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df229-127">See also</span></span>

- [<span data-ttu-id="df229-128">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="df229-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="df229-129">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df229-129">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="df229-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="df229-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="df229-131">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df229-131">-target (Visual Basic)</span></span>](target.md)
