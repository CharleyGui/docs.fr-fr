---
title: "Erreur lors de la création du manifeste d'assembly : <error message>"
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 560635718a931cc9cdb687154a1d23970136de97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972291"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="29986-102">Erreur lors de la création \<du manifeste d’assembly : message d’erreur ></span><span class="sxs-lookup"><span data-stu-id="29986-102">Error creating assembly manifest: \<error message></span></span>
<span data-ttu-id="29986-103">Le compilateur Visual Basic appelle Assembly Linker (al. exe, également appelé ALink) pour générer un assembly avec un manifeste.</span><span class="sxs-lookup"><span data-stu-id="29986-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="29986-104">L'éditeur de liens a signalé une erreur dans la phase de préémission de création de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="29986-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="29986-105">Cela peut être dû à des problèmes avec le fichier de clé ou le conteneur de clé indiqué.</span><span class="sxs-lookup"><span data-stu-id="29986-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="29986-106">Pour signer un assembly, vous devez fournir un fichier de clé valide contenant des informations relatives aux clés publiques et privées.</span><span class="sxs-lookup"><span data-stu-id="29986-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="29986-107">Pour différer la signature d’un assembly, vous devez cocher la case **Différer la signature uniquement** et fournir un fichier de clé valide contenant des informations de clés publiques.</span><span class="sxs-lookup"><span data-stu-id="29986-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="29986-108">La clé privée n'est pas nécessaire quand la signature d'un assembly est différée.</span><span class="sxs-lookup"><span data-stu-id="29986-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="29986-109">Pour plus d'informations, voir [Procédure : signer un assembly avec un nom fort](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="29986-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>  
  
 <span data-ttu-id="29986-110">**ID d’erreur :** BC30140</span><span class="sxs-lookup"><span data-stu-id="29986-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29986-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="29986-111">To correct this error</span></span>  
  
1. <span data-ttu-id="29986-112">Examinez le message d’erreur cité et consultez la rubrique [al. exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="29986-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="29986-113">pour obtenir une explication et des conseils supplémentaires sur l’erreur</span><span class="sxs-lookup"><span data-stu-id="29986-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="29986-114">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29986-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29986-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29986-115">See also</span></span>

- [<span data-ttu-id="29986-116">Guide pratique pour signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="29986-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="29986-117">Page Signature, Concepteur de projet</span><span class="sxs-lookup"><span data-stu-id="29986-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="29986-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="29986-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="29986-119">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="29986-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
