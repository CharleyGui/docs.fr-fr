---
title: -CodePage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: e4cdc27ab021fe055f157b78946538f2b76870e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002359"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="23ab0-102">-CodePage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23ab0-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="23ab0-103">Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="23ab0-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ab0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23ab0-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="23ab0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="23ab0-105">Arguments</span></span>  
  
|<span data-ttu-id="23ab0-106">Terme</span><span class="sxs-lookup"><span data-stu-id="23ab0-106">Term</span></span>|<span data-ttu-id="23ab0-107">Définition</span><span class="sxs-lookup"><span data-stu-id="23ab0-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="23ab0-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="23ab0-108">Required.</span></span> <span data-ttu-id="23ab0-109">Le compilateur utilise la page de codes spécifiée par `id` pour interpréter l’encodage des fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="23ab0-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23ab0-110">Notes</span><span class="sxs-lookup"><span data-stu-id="23ab0-110">Remarks</span></span>  
 <span data-ttu-id="23ab0-111">Pour compiler le code source enregistré avec un encodage spécifique, vous pouvez utiliser `-codepage` pour spécifier la page de codes à utiliser.</span><span class="sxs-lookup"><span data-stu-id="23ab0-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="23ab0-112">L’option `-codepage` s’applique à tous les fichiers de code source de votre compilation.</span><span class="sxs-lookup"><span data-stu-id="23ab0-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="23ab0-113">Pour plus d’informations, consultez [encodage de caractères dans le .NET Framework](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="23ab0-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="23ab0-114">L’option `-codepage` n’est pas nécessaire si les fichiers de code source ont été enregistrés à l’aide de la page de codes ANSI, Unicode ou UTF-8 actuelle avec une signature.</span><span class="sxs-lookup"><span data-stu-id="23ab0-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="23ab0-115">Visual Studio enregistre par défaut tous les fichiers de code source avec la page de codes ANSI actuelle, à moins que l’utilisateur spécifie un autre encodage dans la boîte de dialogue **encodage** .</span><span class="sxs-lookup"><span data-stu-id="23ab0-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="23ab0-116">Visual Studio utilise la boîte de dialogue **encodage** pour ouvrir des fichiers de code source enregistrés avec une page de codes différente.</span><span class="sxs-lookup"><span data-stu-id="23ab0-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23ab0-117">L’option `-codepage` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="23ab0-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ab0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23ab0-118">See also</span></span>

- [<span data-ttu-id="23ab0-119">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23ab0-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
