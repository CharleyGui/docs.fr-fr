---
title: -delaysign (Options du compilateur C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970448"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="966bd-102">-delaysign (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="966bd-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="966bd-103">Cette option fait en sorte que le compilateur réserve de l’espace dans le fichier de sortie afin qu’une signature numérique puisse être ajoutée ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="966bd-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="966bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="966bd-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="966bd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="966bd-105">Arguments</span></span>

<span data-ttu-id="966bd-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="966bd-106">`+` &#124; `-`</span></span>

<span data-ttu-id="966bd-107">Utilisez **-delaysign-** si vous souhaitez obtenir un assembly complètement signé.</span><span class="sxs-lookup"><span data-stu-id="966bd-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="966bd-108">Utilisez **-delaysign+** si vous souhaitez uniquement placer la clé publique dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="966bd-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="966bd-109">**-delaysign-** est l’option par défaut.</span><span class="sxs-lookup"><span data-stu-id="966bd-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="966bd-110">Notes </span><span class="sxs-lookup"><span data-stu-id="966bd-110">Remarks</span></span>

<span data-ttu-id="966bd-111">**L’option -delaysign n’a** aucun effet à moins d’être utilisée avec [-keyfile](./keyfile-compiler-option.md) ou [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="966bd-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="966bd-112">Les options **-delaysign** et **-publicsign** s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="966bd-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="966bd-113">Quand vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="966bd-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="966bd-114">L’opération crée une signature numérique qui est stockée dans le fichier contenant le manifeste.</span><span class="sxs-lookup"><span data-stu-id="966bd-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="966bd-115">Pour un assembly avec signature différée, le compilateur ne calcule pas, ni ne stocke la signature, mais réserve de l'espace dans le fichier pour que la signature puisse être ajoutée par la suite.</span><span class="sxs-lookup"><span data-stu-id="966bd-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="966bd-116">Par exemple, l’utilisation de **-delaysign+** permet à un testeur de placer l’assembly dans le cache global.</span><span class="sxs-lookup"><span data-stu-id="966bd-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="966bd-117">Après un test, vous pouvez signer complètement l’assembly en plaçant la clé privée dans l’assembly à l’aide de l’utilitaire [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="966bd-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="966bd-118">Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md) et [Différer la signature d’un assembly](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="966bd-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="966bd-119">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="966bd-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="966bd-120">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="966bd-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="966bd-121">Modifiez la propriété **Différer la signature uniquement**.</span><span class="sxs-lookup"><span data-stu-id="966bd-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="966bd-122">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="966bd-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="966bd-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="966bd-123">See also</span></span>

- [<span data-ttu-id="966bd-124">Option -publicsign C#</span><span class="sxs-lookup"><span data-stu-id="966bd-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="966bd-125">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="966bd-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="966bd-126">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="966bd-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
