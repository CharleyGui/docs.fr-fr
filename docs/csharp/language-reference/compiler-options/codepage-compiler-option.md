---
title: -codepage (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: c85cd8935bcefd1353707624052b62ee982f7b07
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603051"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="c689a-102">-codepage (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="c689a-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="c689a-103">Cette option spécifie la page de codes à utiliser pendant la compilation si la page exigée n’est pas la page de codes par défaut actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="c689a-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c689a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c689a-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="c689a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c689a-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="c689a-106">Identificateur de la page de codes à utiliser pour tous les fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c689a-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c689a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="c689a-107">Remarks</span></span>  
 <span data-ttu-id="c689a-108">Le compilateur tente tout d’abord d’interpréter tous les fichiers sources comme des fichiers UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c689a-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="c689a-109">Si vos fichiers de code source sont encodés dans un format autre que UTF-8 et s’ils utilisent des caractères autres que des caractères ASCII 7 bits, utilisez l’option **-codepage** pour spécifier la page de codes à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c689a-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="c689a-110">**-codepage** s’applique à tous les fichiers de code source inclus dans votre compilation.</span><span class="sxs-lookup"><span data-stu-id="c689a-110">**-codepage** applies to all source code files in your compilation.</span></span>  
    
 <span data-ttu-id="c689a-111">Pour plus d’informations sur la façon de savoir quelles pages de codes sont prises en charge sur votre système, consultez [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo).</span><span class="sxs-lookup"><span data-stu-id="c689a-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="c689a-112">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="c689a-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c689a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c689a-113">See also</span></span>

- [<span data-ttu-id="c689a-114">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="c689a-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c689a-115">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="c689a-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
