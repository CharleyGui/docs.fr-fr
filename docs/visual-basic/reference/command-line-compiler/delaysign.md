---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 6d3c89d598714446e04ba40155951f771d474866
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971994"
---
# <a name="-delaysign"></a><span data-ttu-id="70090-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="70090-102">-delaysign</span></span>
<span data-ttu-id="70090-103">Spécifie si l'assembly sera complètement ou partiellement signé.</span><span class="sxs-lookup"><span data-stu-id="70090-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70090-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70090-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="70090-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="70090-105">Arguments</span></span>  
 <span data-ttu-id="70090-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="70090-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="70090-107">facultatif.</span><span class="sxs-lookup"><span data-stu-id="70090-107">Optional.</span></span> <span data-ttu-id="70090-108">Utilisez `-delaysign-` si vous souhaitez obtenir un assembly complètement signé.</span><span class="sxs-lookup"><span data-stu-id="70090-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="70090-109">Utilisez `-delaysign+` si vous souhaitez placer la clé publique dans l’assembly et réserver de l’espace pour le hachage signé.</span><span class="sxs-lookup"><span data-stu-id="70090-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="70090-110">Par défaut, il s’agit de `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="70090-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70090-111">Notes</span><span class="sxs-lookup"><span data-stu-id="70090-111">Remarks</span></span>  
 <span data-ttu-id="70090-112">L' `-delaysign` option n’a aucun effet, sauf si elle est utilisée avec [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="70090-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="70090-113">Quand vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="70090-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="70090-114">La signature numérique obtenue est stockée dans le fichier qui contient le manifeste.</span><span class="sxs-lookup"><span data-stu-id="70090-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="70090-115">Lorsqu’un assembly est signé différé, le compilateur ne calcule pas et ne stocke pas la signature, mais réserve de l’espace dans le fichier afin que la signature puisse être ajoutée ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="70090-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="70090-116">Par exemple, en utilisant `-delaysign+`, un développeur dans une organisation peut distribuer des versions de test non signées d’un assembly que les testeurs peuvent inscrire auprès du global assembly cache et utiliser.</span><span class="sxs-lookup"><span data-stu-id="70090-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="70090-117">Lorsque le travail sur l’assembly est terminé, la personne responsable de la clé privée de l’organisation peut signer complètement l’assembly.</span><span class="sxs-lookup"><span data-stu-id="70090-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="70090-118">Ce cloisonnement empêche la divulgation de la clé privée de l’organisation, tout en permettant à tous les développeurs de travailler sur les assemblys.</span><span class="sxs-lookup"><span data-stu-id="70090-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="70090-119">Pour plus d’informations sur la signature d’un assembly [, consultez Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="70090-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="70090-120">Pour définir-delaysign dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="70090-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="70090-121">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="70090-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="70090-122">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="70090-122">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="70090-123">Cliquez sur l’onglet **Signature**.</span><span class="sxs-lookup"><span data-stu-id="70090-123">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="70090-124">Définissez la valeur dans la zone **différer la signature uniquement** .</span><span class="sxs-lookup"><span data-stu-id="70090-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70090-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70090-125">See also</span></span>

- [<span data-ttu-id="70090-126">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70090-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="70090-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="70090-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="70090-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="70090-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="70090-129">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="70090-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
