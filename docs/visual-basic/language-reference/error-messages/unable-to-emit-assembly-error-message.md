---
title: "Impossible de créer l'assembly : <error message>"
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: c088f273c100b1a7eefcf74047865093f378e970
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161658"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="d8de3-102">BC30145 : impossible d’émettre l’assembly : \<error message></span><span class="sxs-lookup"><span data-stu-id="d8de3-102">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="d8de3-103">Le compilateur Visual Basic appelle Assembly Linker (*Al.exe*, également appelé ALink) pour générer un assembly avec un manifeste, et l’éditeur de liens signale une erreur lors de la phase d’émission de création de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d8de3-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="d8de3-104">**ID d’erreur :** BC30145</span><span class="sxs-lookup"><span data-stu-id="d8de3-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d8de3-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d8de3-105">To correct this error</span></span>

1. <span data-ttu-id="d8de3-106">Examinez le message d’erreur cité et consultez la rubrique [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) pour obtenir plus d’explications et de conseils.</span><span class="sxs-lookup"><span data-stu-id="d8de3-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="d8de3-107">Essayez de signer l’assembly manuellement à l’aide de l' [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ou de l' [Sn.exe (outil Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d8de3-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="d8de3-108">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d8de3-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="d8de3-109">Pour signer manuellement l'assembly</span><span class="sxs-lookup"><span data-stu-id="d8de3-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="d8de3-110">Utilisez l' [Sn.exe (outil Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) pour créer un fichier de paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="d8de3-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="d8de3-111">Ce fichier a une extension *. snk* .</span><span class="sxs-lookup"><span data-stu-id="d8de3-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="d8de3-112">Supprimez la référence COM qui génère l'erreur de votre projet.</span><span class="sxs-lookup"><span data-stu-id="d8de3-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="d8de3-113">Ouvrez le [invite de commandes développeur pour Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d8de3-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="d8de3-114">Dans Windows 10, entrez l' **invite de commandes développeur** dans la zone de recherche de la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="d8de3-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="d8de3-115">Ensuite, sélectionnez **invite de commandes développeur pour VS 2017** dans la liste des résultats.</span><span class="sxs-lookup"><span data-stu-id="d8de3-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="d8de3-116">Remplacez le répertoire par le répertoire dans lequel vous souhaitez placer votre wrapper d’assembly.</span><span class="sxs-lookup"><span data-stu-id="d8de3-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="d8de3-117">Entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d8de3-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="d8de3-118">Voici un exemple de la commande réelle que vous pouvez entrer :</span><span class="sxs-lookup"><span data-stu-id="d8de3-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="d8de3-119">Utilisez des guillemets doubles si un chemin d’accès ou un fichier contient des espaces.</span><span class="sxs-lookup"><span data-stu-id="d8de3-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="d8de3-120">Dans Visual Studio, ajoutez une référence d’assembly .NET au fichier que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="d8de3-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8de3-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8de3-121">See also</span></span>

- [<span data-ttu-id="d8de3-122">Al.exe</span><span class="sxs-lookup"><span data-stu-id="d8de3-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="d8de3-123">Sn.exe (outil Strong Name Tool)</span><span class="sxs-lookup"><span data-stu-id="d8de3-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="d8de3-124">Comment : créer une paire de clés de Public-Private</span><span class="sxs-lookup"><span data-stu-id="d8de3-124">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="d8de3-125">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="d8de3-125">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
