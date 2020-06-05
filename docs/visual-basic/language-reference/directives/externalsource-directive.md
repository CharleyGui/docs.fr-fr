---
title: '#ExternalSource, directive'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: e4c7704c32c3a6c73e069d0b7129d5386696b438
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402990"
---
# <a name="externalsource-directive"></a><span data-ttu-id="9002f-102">#ExternalSource, directive</span><span class="sxs-lookup"><span data-stu-id="9002f-102">#ExternalSource Directive</span></span>

<span data-ttu-id="9002f-103">Indique un mappage entre des lignes spécifiques de code source et du texte externe à la source.</span><span class="sxs-lookup"><span data-stu-id="9002f-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9002f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9002f-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="9002f-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="9002f-105">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="9002f-106">Chemin d’accès à la source externe.</span><span class="sxs-lookup"><span data-stu-id="9002f-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="9002f-107">Numéro de ligne de la première ligne de la source externe.</span><span class="sxs-lookup"><span data-stu-id="9002f-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="9002f-108">Ligne où l’erreur se produit dans la source externe.</span><span class="sxs-lookup"><span data-stu-id="9002f-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="9002f-109">Met fin au bloc `#ExternalSource`.</span><span class="sxs-lookup"><span data-stu-id="9002f-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9002f-110">Notes</span><span class="sxs-lookup"><span data-stu-id="9002f-110">Remarks</span></span>  

 <span data-ttu-id="9002f-111">Cette directive est utilisée uniquement par le compilateur et le débogueur.</span><span class="sxs-lookup"><span data-stu-id="9002f-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="9002f-112">Un fichier source peut inclure des directives de source externe, qui indiquent un mappage entre des lignes de code spécifiques dans le fichier source et du texte externe à la source, tel qu’un fichier. aspx.</span><span class="sxs-lookup"><span data-stu-id="9002f-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="9002f-113">Si des erreurs sont rencontrées dans le code source désigné pendant la compilation, elles sont identifiées comme provenant de la source externe.</span><span class="sxs-lookup"><span data-stu-id="9002f-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="9002f-114">Les directives de source externe n’ont aucun effet sur la compilation et ne peuvent pas être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="9002f-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="9002f-115">Ils sont destinés à un usage interne par l’application uniquement.</span><span class="sxs-lookup"><span data-stu-id="9002f-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9002f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9002f-116">See also</span></span>

- [<span data-ttu-id="9002f-117">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="9002f-117">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
