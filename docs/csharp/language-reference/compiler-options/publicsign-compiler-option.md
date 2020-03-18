---
title: -publicsign (Options du compilateur C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61662528"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="e7a83-102">-publicsign (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="e7a83-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="e7a83-103">Cette option force le compilateur à appliquer une clé publique sans signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e7a83-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="e7a83-104">L’option **-publicsign** définit également un bit dans l’assembly qui indique au runtime que le fichier est signé.</span><span class="sxs-lookup"><span data-stu-id="e7a83-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7a83-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7a83-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="e7a83-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e7a83-106">Arguments</span></span>

<span data-ttu-id="e7a83-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e7a83-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7a83-108">Notes </span><span class="sxs-lookup"><span data-stu-id="e7a83-108">Remarks</span></span>

<span data-ttu-id="e7a83-109">L’option **-publicsign** nécessite l’utilisation de l’option [-keyfile](keyfile-compiler-option.md) ou [-keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e7a83-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="e7a83-110">Les options **keyfile** ou **keycontainer** spécifient la clé publique.</span><span class="sxs-lookup"><span data-stu-id="e7a83-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="e7a83-111">Les options **-publicsign** et **-delaysign** s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="e7a83-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="e7a83-112">Parfois appelée « fausse signature » ou « signature OSS », la signature publique inclut la clé publique dans un assembly de sortie et définit l’indicateur « signé ». Toutefois, elle ne signe pas l’assembly avec une clé privée.</span><span class="sxs-lookup"><span data-stu-id="e7a83-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="e7a83-113">Cette approche est utile dans le cadre de projets open source. Vous pouvez en effet générer des assemblys compatibles avec les assemblys publiés « totalement signés », même si vous n’avez pas accès à la clé privée utilisée pour les signer.</span><span class="sxs-lookup"><span data-stu-id="e7a83-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="e7a83-114">Puisque pratiquement aucun consommateur ne doit vérifier si l’assembly est totalement signé, ces assemblys générés publiquement peuvent être utilisés dans la quasi-totalité des scénarios employant des assemblys totalement signés.</span><span class="sxs-lookup"><span data-stu-id="e7a83-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e7a83-115">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e7a83-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="e7a83-116">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="e7a83-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="e7a83-117">Modifiez la propriété **Différer la signature uniquement**.</span><span class="sxs-lookup"><span data-stu-id="e7a83-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7a83-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7a83-118">See also</span></span>

- [<span data-ttu-id="e7a83-119">Option -delaysign du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e7a83-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="e7a83-120">Option -keyfile du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e7a83-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="e7a83-121">Option -keycontainer du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e7a83-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="e7a83-122">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="e7a83-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="e7a83-123">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="e7a83-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
