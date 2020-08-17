---
title: -publicsign (Options du compilateur C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 2655e0216a412053e052ab2ec2fcc8c68ea4f968
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268047"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="5f906-102">-publicsign (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="5f906-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="5f906-103">Cette option force le compilateur à appliquer une clé publique sans signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5f906-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="5f906-104">L’option **-publicsign** définit également un bit dans l’assembly qui indique au runtime que le fichier est signé.</span><span class="sxs-lookup"><span data-stu-id="5f906-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f906-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f906-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="5f906-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="5f906-106">Arguments</span></span>

<span data-ttu-id="5f906-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5f906-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f906-108">Notes</span><span class="sxs-lookup"><span data-stu-id="5f906-108">Remarks</span></span>

<span data-ttu-id="5f906-109">L’option **-publicsign** nécessite l’utilisation de l’option [-keyfile](keyfile-compiler-option.md) ou [-keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5f906-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="5f906-110">Les options **keyfile** ou **keycontainer** spécifient la clé publique.</span><span class="sxs-lookup"><span data-stu-id="5f906-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="5f906-111">Les options **-publicsign** et **-delaysign** s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="5f906-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="5f906-112">Parfois appelée « fausse signature » ou « signature OSS », la signature publique inclut la clé publique dans un assembly de sortie et définit l’indicateur « signé ». Toutefois, elle ne signe pas l’assembly avec une clé privée.</span><span class="sxs-lookup"><span data-stu-id="5f906-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="5f906-113">Cette approche est utile dans le cadre de projets open source. Vous pouvez en effet générer des assemblys compatibles avec les assemblys publiés « totalement signés », même si vous n’avez pas accès à la clé privée utilisée pour les signer.</span><span class="sxs-lookup"><span data-stu-id="5f906-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="5f906-114">Puisque pratiquement aucun consommateur ne doit vérifier si l’assembly est totalement signé, ces assemblys générés publiquement peuvent être utilisés dans la quasi-totalité des scénarios employant des assemblys totalement signés.</span><span class="sxs-lookup"><span data-stu-id="5f906-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a><span data-ttu-id="5f906-115">Pour définir cette option du compilateur dans un fichier csproj</span><span class="sxs-lookup"><span data-stu-id="5f906-115">To set this compiler option in a csproj file</span></span>

<span data-ttu-id="5f906-116">Ouvrez le fichier. csproj pour un projet, puis ajoutez l’élément suivant :</span><span class="sxs-lookup"><span data-stu-id="5f906-116">Open the .csproj file for a project, and add the following element:</span></span>

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a><span data-ttu-id="5f906-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f906-117">See also</span></span>

- [<span data-ttu-id="5f906-118">Option -delaysign du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="5f906-118">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="5f906-119">Option -keyfile du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="5f906-119">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="5f906-120">Option -keycontainer du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="5f906-120">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="5f906-121">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="5f906-121">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="5f906-122">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="5f906-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
