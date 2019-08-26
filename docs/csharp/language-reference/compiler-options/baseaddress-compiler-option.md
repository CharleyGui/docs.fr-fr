---
title: -baseaddress (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: e96ab3ece6edc36c913a8efc0097ff9c4a1e3c22
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69607032"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="9bf47-102">-baseaddress (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="9bf47-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="9bf47-103">L’option **-baseaddress** vous permet de spécifier l’adresse de base préférée à laquelle doit être chargée une DLL.</span><span class="sxs-lookup"><span data-stu-id="9bf47-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="9bf47-104">Pour plus d’informations sur le moment et la raison de l’utilisation de cette option, consultez [Larry Osterman’s WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span><span class="sxs-lookup"><span data-stu-id="9bf47-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf47-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bf47-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="9bf47-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="9bf47-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="9bf47-107">Adresse de base de la DLL.</span><span class="sxs-lookup"><span data-stu-id="9bf47-107">The base address for the DLL.</span></span> <span data-ttu-id="9bf47-108">Cette adresse peut être spécifiée sous forme d’un nombre décimal, hexadécimal ou octal.</span><span class="sxs-lookup"><span data-stu-id="9bf47-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bf47-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="9bf47-109">Remarks</span></span>  
 <span data-ttu-id="9bf47-110">L’adresse de base par défaut d’une DLL est définie par le Common Language Runtime (CLR) .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bf47-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="9bf47-111">Sachez que le dernier chiffre de cette adresse sera arrondi.</span><span class="sxs-lookup"><span data-stu-id="9bf47-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="9bf47-112">Par exemple, si vous spécifiez l’adresse 0x11110001, elle est arrondie à 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="9bf47-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="9bf47-113">Pour terminer le processus de signature d’une DLL, utilisez SN.EXE avec l’option -R.</span><span class="sxs-lookup"><span data-stu-id="9bf47-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9bf47-114">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9bf47-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="9bf47-115">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="9bf47-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="9bf47-116">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="9bf47-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="9bf47-117">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="9bf47-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="9bf47-118">Modifiez la propriété **Adresse de base de la DLL**.</span><span class="sxs-lookup"><span data-stu-id="9bf47-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="9bf47-119">Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bf47-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf47-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bf47-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9bf47-121">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="9bf47-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9bf47-122">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="9bf47-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
