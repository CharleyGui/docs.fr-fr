---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 286dd8bd9949b584cec38642f44ba9ac5e924732
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557175"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="22431-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22431-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="22431-103">Fait en sorte que le compilateur accepte uniquement la syntaxe qui est incluse dans la version de Visual Basic Language spécifiée.</span><span class="sxs-lookup"><span data-stu-id="22431-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22431-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22431-104">Syntax</span></span>  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="22431-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="22431-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="22431-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="22431-106">Required.</span></span> <span data-ttu-id="22431-107">Version du langage à utiliser pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="22431-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="22431-108">Les valeurs acceptées sont `9` ,,,, `10` `11` `12` `14` , `15` , `15.3` , `15.5` `default` et `latest` .</span><span class="sxs-lookup"><span data-stu-id="22431-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.</span></span>

 <span data-ttu-id="22431-109">L’un des nombres entiers peut également être spécifié à l’aide de `.0` comme version mineure, par exemple `11.0` .</span><span class="sxs-lookup"><span data-stu-id="22431-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="22431-110">Vous pouvez voir la liste de toutes les valeurs possibles en spécifiant `-langversion:?` sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="22431-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22431-111">Notes</span><span class="sxs-lookup"><span data-stu-id="22431-111">Remarks</span></span>  
 <span data-ttu-id="22431-112">L' `-langversion` option spécifie la syntaxe que le compilateur accepte.</span><span class="sxs-lookup"><span data-stu-id="22431-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="22431-113">Par exemple, si vous spécifiez que la version du langage est 9,0, le compilateur génère des erreurs pour la syntaxe qui est valide uniquement dans la version 10,0 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="22431-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="22431-114">Vous pouvez utiliser cette option lorsque vous développez des applications qui ciblent différentes versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22431-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="22431-115">Par exemple, si vous ciblez .NET Framework 3,5, vous pouvez utiliser cette option pour vous assurer que vous n’utilisez pas la syntaxe de la version de langue 10,0.</span><span class="sxs-lookup"><span data-stu-id="22431-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="22431-116">Vous ne pouvez définir `-langversion` directement qu’à l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="22431-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="22431-117">Pour plus d’informations, consultez [Ciblage d’une version spécifique du .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).</span><span class="sxs-lookup"><span data-stu-id="22431-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/visual-studio-multi-targeting-overview).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22431-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="22431-118">Example</span></span>  
 <span data-ttu-id="22431-119">Le code suivant compile `sample.vb` pour Visual Basic 9,0.</span><span class="sxs-lookup"><span data-stu-id="22431-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="22431-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22431-120">See also</span></span>

- [<span data-ttu-id="22431-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="22431-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="22431-122">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="22431-122">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
