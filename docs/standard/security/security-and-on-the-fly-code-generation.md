---
title: Sécurité et génération de code immédiate
description: La génération de code pour le compte d’un code de confiance moindre qui s’exécute à un niveau de confiance supérieur est un problème de sécurité, en particulier lorsqu’un appelant peut influencer la génération de code.
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: a3fc51c346feffa85537d95ccdbd23d943827edf
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555693"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="704d2-103">Sécurité et génération de code immédiate</span><span class="sxs-lookup"><span data-stu-id="704d2-103">Security and On-the-Fly Code Generation</span></span>

<span data-ttu-id="704d2-104">Certaines bibliothèques fonctionnent en générant du code et en l'exécutant afin d'effectuer certaines opérations pour l'appelant.</span><span class="sxs-lookup"><span data-stu-id="704d2-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="704d2-105">Le problème de base est la génération de code pour le compte de code d'un niveau de confiance moindre et son exécution à un niveau de confiance supérieur.</span><span class="sxs-lookup"><span data-stu-id="704d2-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="704d2-106">Ce problème se complique quand l'appelant peut influencer la génération du code ; vous devez donc vous assurer que seul du code que vous estimez sécurisé est généré.</span><span class="sxs-lookup"><span data-stu-id="704d2-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
<span data-ttu-id="704d2-107">Vous devez toujours savoir précisément quel code vous générez.</span><span class="sxs-lookup"><span data-stu-id="704d2-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="704d2-108">Cela signifie que vous devez avoir un contrôle strict sur toutes les valeurs que vous recevez d'un utilisateur, qu'il s'agisse de chaînes entourées de guillemets (qui devraient être échappées, car elles ne peuvent pas inclure d'éléments de code inattendus), d'identificateurs (dont la validité doit être vérifiée) ou de tout autre élément.</span><span class="sxs-lookup"><span data-stu-id="704d2-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="704d2-109">Les identificateurs peuvent être dangereux, car vous pouvez modifier un assembly compilé pour que ses identificateurs contiennent des caractères étranges qui risquent de le bloquer (bien qu'il s'agisse rarement d'une faille en matière de sécurité).</span><span class="sxs-lookup"><span data-stu-id="704d2-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
<span data-ttu-id="704d2-110">Nous vous recommandons de générer votre code à l'aide de l'émission de réflexion, qui vous aide souvent à éviter la plupart de ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="704d2-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
<span data-ttu-id="704d2-111">Pendant la compilation du code, examinez s'il est possible pour un programme nuisible de le modifier.</span><span class="sxs-lookup"><span data-stu-id="704d2-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="704d2-112">Existe-t-il un laps de temps durant lequel du code nuisible peut changer du code source sur le disque avant sa lecture par le compilateur ou avant le chargement par votre code du fichier .dll ?</span><span class="sxs-lookup"><span data-stu-id="704d2-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="704d2-113">Si c’est le cas, vous devez protéger le répertoire contenant ces fichiers à l’aide d’une liste de contrôle d’accès dans le fichier système, en fonction de la situation.</span><span class="sxs-lookup"><span data-stu-id="704d2-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704d2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="704d2-114">See also</span></span>

- [<span data-ttu-id="704d2-115">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="704d2-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="704d2-116">Sécurité ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="704d2-116">ASP.NET Core Security</span></span>](/aspnet/core/security/)
