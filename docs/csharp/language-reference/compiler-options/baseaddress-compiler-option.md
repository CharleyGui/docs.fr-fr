---
description: -baseaddress (Options du compilateur C#)
title: -baseaddress (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 42b1891c29457745689542a4c9e0482ec5e918fa
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126006"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="dc0d2-103">-baseaddress (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="dc0d2-103">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="dc0d2-104">L’option **-baseaddress** vous permet de spécifier l’adresse de base préférée à laquelle doit être chargée une DLL.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-104">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="dc0d2-105">Pour plus d’informations sur le moment et la raison de l’utilisation de cette option, consultez [Larry Osterman’s WebLog](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="dc0d2-105">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc0d2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc0d2-106">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc0d2-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="dc0d2-107">Arguments</span></span>  
 `address`  
 <span data-ttu-id="dc0d2-108">Adresse de base de la DLL.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-108">The base address for the DLL.</span></span> <span data-ttu-id="dc0d2-109">Cette adresse peut être spécifiée sous forme d’un nombre décimal, hexadécimal ou octal.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-109">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc0d2-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="dc0d2-110">Remarks</span></span>  
 <span data-ttu-id="dc0d2-111">L’adresse de base par défaut d’une DLL est définie par le Common Language Runtime (CLR) .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-111">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="dc0d2-112">Sachez que le dernier chiffre de cette adresse sera arrondi.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-112">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="dc0d2-113">Par exemple, si vous spécifiez l’adresse 0x11110001, elle est arrondie à 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-113">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="dc0d2-114">Pour terminer le processus de signature d’une DLL, utilisez SN.EXE avec l’option -R.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-114">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="dc0d2-115">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc0d2-115">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="dc0d2-116">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-116">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="dc0d2-117">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-117">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="dc0d2-118">Cliquez sur le bouton **Avancé** .</span><span class="sxs-lookup"><span data-stu-id="dc0d2-118">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="dc0d2-119">Modifiez la propriété **Adresse de base de la DLL**.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-119">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="dc0d2-120">Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc0d2-120">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc0d2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc0d2-121">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dc0d2-122">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="dc0d2-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="dc0d2-123">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="dc0d2-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
