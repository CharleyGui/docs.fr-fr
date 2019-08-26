---
title: -filealign (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603013"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="f6aae-102">-filealign (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f6aae-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="f6aae-103">L’option **-filealign** permet de spécifier la taille des sections de votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f6aae-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6aae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6aae-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6aae-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f6aae-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="f6aae-106">Valeur qui spécifie la taille des sections dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f6aae-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="f6aae-107">Les valeurs valides sont 512, 1024, 2048, 4096 et 8192.</span><span class="sxs-lookup"><span data-stu-id="f6aae-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="f6aae-108">Ces valeurs sont exprimées en octets.</span><span class="sxs-lookup"><span data-stu-id="f6aae-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6aae-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6aae-109">Remarks</span></span>  
 <span data-ttu-id="f6aae-110">Chaque section est alignée sur une limite qui est un multiple de la valeur **-filealign**.</span><span class="sxs-lookup"><span data-stu-id="f6aae-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="f6aae-111">Il n’existe aucune valeur fixe par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6aae-111">There is no fixed default.</span></span> <span data-ttu-id="f6aae-112">Si la valeur **-filealign** n’est pas spécifiée, le Common Language Runtime choisit une valeur par défaut au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f6aae-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="f6aae-113">En spécifiant la taille de la section, vous affectez la taille du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f6aae-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="f6aae-114">Il peut être utile de modifier la taille de la section pour les programmes qui sont exécutés sur des appareils de petite taille.</span><span class="sxs-lookup"><span data-stu-id="f6aae-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="f6aae-115">Utilisez [DUMPBIN](/cpp/build/reference/dumpbin-options) pour afficher des informations sur les sections de votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f6aae-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f6aae-116">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6aae-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f6aae-117">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="f6aae-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="f6aae-118">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f6aae-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="f6aae-119">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="f6aae-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="f6aae-120">Modifiez la propriété **Alignement des fichiers**.</span><span class="sxs-lookup"><span data-stu-id="f6aae-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="f6aae-121">Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6aae-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6aae-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6aae-122">See also</span></span>

- [<span data-ttu-id="f6aae-123">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="f6aae-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f6aae-124">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="f6aae-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
